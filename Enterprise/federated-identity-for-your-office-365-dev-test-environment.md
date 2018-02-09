---
title: "Identité fédérée pour votre environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "Résumé : Configurer une authentification fédérée pour votre environnement de développement/test d’Office 365."
ms.openlocfilehash: e37b57d5497f3151885682f7c4d8abca7120b99e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>Identité fédérée pour votre environnement de développement/test Office 365

 **Résumé :** Configurer l’authentification fédérée pour votre environnement de développement/test d’Office 365.
  
Office 365 prend en charge des identités fédérées. Cela signifie qu’au lieu d’effectuer la validation des informations d’identification lui-même, Office 365 fait référence l’utilisateur qui se connecte à un serveur d’authentification fédérée qui approuve d’Office 365. Si les informations d’identification sont correctes, le serveur d’authentification fédérée délivre un jeton de sécurité que le client envoie ensuite vers Office 365 comme preuve d’authentification. Une identité fédérée permet le déchargement et l’évolution verticale de l’authentification pour un abonnement à Office 365 et scénarios avancés d’authentification et de sécurité.
  
Cet article explique comment configurer l’authentification fédérée pour l’environnement de développement/test Office 365, pour le résultat suivant :
  
**Figure 1 : L’authentification fédérée pour l’environnement de développement/test d’Office 365**

![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
La configuration illustrée dans la figure 1 est constituée des éléments suivants :  
  
- Un abonnement d’évaluation Office 365 E5, qui arrive à expiration 30 jours après sa création.
    
- Un intranet d’organisation simplifié et connecté à Internet, composé de cinq machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1, CLIENT1, ADFS1 et PROXY1). Azure AD Connect s’exécute sur APP1 pour synchroniser la liste de comptes dans le domaine Windows Server AD avec Office 365. PROXY1 reçoit les demandes d’authentification entrantes. ADFS1 valide les informations d’identification avec DC1 et émet des jetons de sécurité.
    
Les cinq phases de configuration de cet environnement de développement/test sont les suivantes :
  
1. Créez l’environnement de développement/test Office 365 d’entreprise simulé avec DirSync.
    
2. Créez le serveur AD FS (ADFS1).
    
3. Créez le serveur proxy web (PROXY1).
    
4. Créez un certificat auto-signé et configurez ADFS1 et PROXY1.
    
5. Configurez Office 365 pour l’identité fédérée.
    
Pour exécuter un déploiement de production d’authentification fédérée pour Office 365 dans Azure, consultez [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
> [!NOTE]
> Vous ne pouvez pas configurer cet environnement de développement/test avec un abonnement à la version d’évaluation d’Azure. 
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>Phase 1 : création de l’environnement de développement/test Office 365 d’entreprise simulé avec DirSync

Suivez les instructions dans [la synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md) pour créer l’environnement de développement/test simulées entreprise Office 365 avec APP1 comme serveur de synchronisation d’annuaire et identité synchronisée entre Office 365 et l’Active Directory de Windows Server comptes sur DC1.
  
Ensuite, créer un nom de domaine DNS public en fonction de votre nom de domaine actuel et l’ajouter à votre abonnement à Office 365. Nous recommandons d’utiliser le nom **labo de test.** \<votre domaine public >. Par exemple, si votre nom de domaine public est contoso.com, ajouter la testlab.contoso.com de nom de domaine public.
  
Pour obtenir des instructions sur la façon de créer les enregistrements DNS corrects de votre fournisseur DNS et ajouter le domaine à votre abonnement d’évaluation d’Office 365, reportez-vous à la section [Ajouter des utilisateurs et domaine à Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611). 
  
Voici la configuration finale.
  
**La figure 2 : Synchronisation d’annuaire pour l’environnement de développement/test d’Office 365**

![Environnement de développement/test d’Office 365 avec DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
La figure 2 illustre la synchronisation d’annuaire pour l’environnement de développement/test Office 365, qui comprend Office 365, ainsi que les machines virtuelles CLIENT1, APP1 et DC1 dans un réseau virtuel Azure.
  
## <a name="phase-2-create-the-ad-fs-server"></a>Phase 2 : création du serveur AD FS (ADFS1)

Un serveur AD FS fournit une authentification fédérée entre Office 365 et les comptes dans le domaine corp.contoso.com hébergé sur DC1.
  
Pour créer un ordinateur virtuel Azure pour ADFS1, indiquez le nom de votre abonnement et le groupe de ressources et l’emplacement Azure pour votre Configuration de Base et puis exécuter ces commandes à l’invite de commande PowerShell de Azure sur votre ordinateur local.
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) pour obtenir un fichier texte qui contient toutes les commandes de PowerShell dans cet article.
  
Ensuite, le [portail Azure](http://portal.azure.com) permet de se connecter à l’ordinateur virtuel ADFS1 à l’aide du nom du compte administrateur local ADFS1 et le mot de passe et puis ouvrez une invite de commande Windows PowerShell.
  
Pour vérifier la communication réseau et la résolution de nom entre ADFS1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.
  
Ensuite, associez la machine virtuelle ADFS1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur ADFS1.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Voici la configuration finale.
  
**Figure 3 : Ajouter le serveur AD FS**

![Le serveur AD FS ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
La figure 3 illustre l’ajout du serveur ADFS1 à DirSync pour l’environnement de développement/test Office 365.
  
## <a name="phase-3-create-the-web-proxy-server"></a>Phase 3 : création du serveur proxy web (PROXY1)

PROXY1 permet le traitement proxy des messages d’authentification entre les utilisateurs tentant de s’authentifier et ADFS1.
  
Pour créer une machine virtuelle Azure pour PROXY1, indiquez le nom de votre groupe de ressources et l’emplacement Azure, puis exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local.
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Une adresse IP publique statique est affectée à PROXY1, car vous créez un enregistrement DNS public qui pointe vers celle-ci et elle ne doit pas être modifiée lorsque vous redémarrez la machine virtuelle PROXY1. 
  
Ensuite, ajoutez une règle au groupe de sécurité réseau pour le sous-réseau du réseau d’entreprise pour autoriser le trafic entrant non sollicité à partir d’Internet pour les adresses IP privées de PROXY1 et le port TCP 443. Exécuter ces commandes à l’invite de commande PowerShell de Azure sur votre ordinateur local.
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

Ensuite, le [portail Azure](http://portal.azure.com) permet de se connecter à la machine virtuelle PROXY1 en utilisant le nom du compte administrateur local PROXY1 et le mot de passe et puis ouvrez une invite de commande Windows PowerShell sur PROXY1.
  
Pour vérifier la communication réseau et la résolution de nom entre PROXY1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.
  
Ensuite, associez la machine virtuelle PROXY1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur PROXY1.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Affichez l’adresse IP publique de PROXY1 avec ces commandes Azure PowerShell sur votre ordinateur local :
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Ensuite, travailler avec votre fournisseur DNS public et créer un nouvel enregistrement A DNS public pour **fs.testlab.** \<le nom de votre domaine DNS > qui est résolu en l’adresse IP affichée par la commande **Write-Host** . Le **fs.testlab.** \<le nom de votre domaine DNS > est désigné comme le *service federation service de nom de domaine complet* .
  
Ensuite, utilisez le [portail Azure](http://portal.azure.com) pour se connecter à la machine virtuelle de DC1 à l’aide de l’entreprise\\informations d’identification d’Utilisateur1 et exécuter ce qui suit à une invite de commande Windows PowerShell au niveau de l’administrateur des commandes :
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

Ces commandes créent un enregistrement A DNS pour votre nom de domaine complet du service FS (Federation Service) que les machines virtuelles sur le réseau virtuel Azure peuvent résoudre sur l’adresse IP privée d’ADFS1.
  
Voici la configuration finale.
  
**Figure 4 : Ajout du serveur de proxy d’application web**

![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
La figure 4 illustre l’ajout du serveur PROXY1.
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1

Au cours de cette phase, vous créez un certificat numérique auto-signé pour votre nom de domaine complet du service FS (Federation Service) et vous configurez ADFS1 et PROXY1 en tant que batterie de serveurs AD FS.
  
Tout d’abord, utilisez le [portail Azure](http://portal.azure.com) pour se connecter à la machine virtuelle de DC1 à l’aide de l’entreprise\\invite de commande des informations d’identification d’Utilisateur1 et puis ouvrez un Windows PowerShell de niveau administrateur.
  
Ensuite, créez un compte de service AD FS avec cette commande à l’invite de commande Windows PowerShell sur DC1 :
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Notez que cette commande vous invite à indiquer le mot de passe du compte. Choisissez un mot de passe fort et enregistrez-le dans un emplacement sécurisé. Vous en aurez besoin pour cette phase et la phase 5.
  
Le [portail Azure](http://portal.azure.com) permet de se connecter à l’ordinateur virtuel ADFS1 à l’aide de l’entreprise\\informations d’identification d’utilisateur1. Ouvrez une invite de commandes au niveau de l’administrateur de Windows PowerShell sur ADFS1, renseignez votre nom de domaine complet du service de fédération et puis exécutez ces commandes pour créer un certificat auto-signé :
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

Ensuite, utilisez ces étapes pour enregistrer le nouveau certificat auto-signé en tant que fichier.
  
1. Cliquez sur **Démarrer**, tapez **mmc.exe**et appuyez sur **entrée**.
    
2. Cliquez sur **fichier > Ajouter/supprimer un composant logiciel enfichable**.
    
3. Dans **Ajouter ou supprimer des composants**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.
    
4. Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis cliquez sur **OK**.
    
5. Dans le volet d’arborescence, ouvrez **certificats (ordinateur Local) > Personal > certificats**.
    
6. Cliquez sur le certificat avec votre nom de domaine complet du service de fédération et cliquez sur **toutes les tâches**, puis cliquez sur **Exporter**.
    
7. Dans la page **Bienvenue** , cliquez sur **suivant**.
    
8. Dans la page **Exportation de clé privée** , cliquez sur **Oui**, puis cliquez sur **suivant**.
    
9. Dans la page **Format de fichier d’exportation** , cliquez sur **Exporter toutes les propriétés étendues**, puis cliquez sur **suivant**.
    
10. Dans la page **sécurité** , cliquez sur **mot de passe** et tapez un mot de passe **mot de passe** et **Confirmer mot de passe.**
    
11. Dans la page **fichier à exporter** , cliquez sur **Parcourir**.
    
12. Accédez à la **C:\\certificats** dossier, tapez **SSL** dans **nom de fichier**, puis cliquez sur **Enregistrer.**
    
13. Dans la page **fichier à exporter** , cliquez sur **suivant**.
    
14. Dans la page **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**. Lorsque vous y êtes invité, cliquez sur **OK**.
    
Ensuite, installez le service AD FS avec cette commande à l’invite de commande Windows PowerShell sur ADFS1 :
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Ensuite, configurez le service AD FS en suivant ces étapes :
  
1. Cliquez sur **Démarrer**, puis cliquez sur l’icône du **Gestionnaire de serveur** .
    
2. Dans le volet d’arborescence du Gestionnaire de serveur, cliquez sur **AD FS**.
    
3. Dans la barre d’outils en haut, cliquez sur le symbole Attention orange, puis cliquez sur **configurer le service de fédération sur ce serveur**.
    
4. Dans la page **Bienvenue** de l’Assistant Configuration des Services de fédération Active Directory, cliquez sur **suivant**.
    
5. Sur la page de **connexion aux services AD DS** , cliquez sur **suivant**.
    
6. Dans la page **Spécifier les propriétés de Service** :
    
  - **Certificat SSL**, cliquez sur la flèche vers le bas, puis cliquez sur le certificat avec le nom de votre nom de domaine complet du service de fédération.
    
  - Dans la zone **Nom complet du Service Federation**, tapez le nom de votre organisation fictive.
    
  - Cliquez sur **Suivant**.
    
7. Dans la page **Spécifier le compte de Service** , cliquez sur **Sélectionner** pour le **nom du compte**.
    
8. Dans, **Sélectionnez l’utilisateur ou le compte de Service**, tapez **Service ADFS**, cliquez sur **Vérifier les noms**, puis cliquez sur **OK**.
    
9. Dans **Mot de passe**, tapez le mot de passe pour le compte de Service ADFS et puis cliquez sur **suivant**.
    
10. Dans la page **Spécifier la base de données de Configuration** , cliquez sur **suivant**.
    
11. Dans la page **Options de révision** , cliquez sur **suivant**.
    
12. Sur la page **Contrôle de condition préalable** , cliquez sur **configurer**.
    
13. Sur la page de **résultats** , cliquez sur **Fermer**.
    
14. Cliquez sur **Démarrer**, cliquez sur l’icône d’alimentation, cliquez sur **redémarrer**, puis cliquez sur **Continuer**.
    
Dans le [portail Azure](http://portal.azure.com), connectez-vous à PROXY1 avec le CORP\\informations d’identification de compte utilisateur1.
  
Ensuite, suivez ces étapes pour installer le certificat auto-signé et configurer PROXY1.
  
1. Cliquez sur **Démarrer**, tapez **mmc.exe**et appuyez sur **entrée**.
    
2. Cliquez sur **fichier > Ajouter/supprimer un composant logiciel enfichable**.
    
3. Dans **Ajouter ou supprimer des composants**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.
    
4. Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis cliquez sur **OK**.
    
5. Dans le volet d’arborescence, ouvrez **certificats (ordinateur Local) > Personal > certificats**.
    
6. Cliquez droit sur **personnel**et cliquez sur **toutes les tâches**, puis cliquez sur **Importer**.
    
7. Dans la page **Bienvenue** , cliquez sur **suivant**.
    
8. Dans la page **fichier à importer** , tapez ** \\ \\adfs1\\certificats\\ssl.pfx**, puis cliquez sur **suivant**.
    
9. Sur la page de **protection par clé privée** , tapez le mot de passe de certificat de **mot de passe**, puis cliquez sur **Suivant.**
    
10. Dans la page **magasin de certificats** , cliquez sur **Suivant.**
    
11. Sur la page de **fin** , cliquez sur **Terminer**.
    
12. Dans la page **Magasin de certificats** , cliquez sur **suivant**.
    
13. Lorsque vous y êtes invité, cliquez sur **OK**.
    
14. Dans le volet d’arborescence, cliquez sur **certificats** .
    
15. Cliquez sur le certificat, puis cliquez sur **Copier**.
    
16. Dans le volet d’arborescence, ouvrez **autorités de Certification racines de confiance > certificats**.
    
17. Placez le pointeur de la souris sous la liste de certificats installés, avec le bouton droit, puis cliquez sur **Coller**.
    
Ouvrez une invite de commande PowerShell de niveau administrateur et exécutez les commandes suivantes :
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Suivez ces étapes pour configurer le service de proxy d’application web de manière à ce qu’il utilise ADFS1 comme serveur de fédération :
  
1. Cliquez sur **Démarrer**, puis cliquez sur **Gestionnaire de serveur**.
    
2. Dans le volet d’arborescence, cliquez sur **Accès à distance**.
    
3. Dans la barre d’outils en haut, cliquez sur le symbole Attention orange, puis cliquez sur **Ouvrir l’Assistant de Proxy d’Application Web**.
    
4. Dans la page **Bienvenue** de l’Assistant de Configuration de Proxy Web Application, cliquez sur **suivant**.
    
5. Sur la page **Serveur de fédération** :
    
  - Tapez votre nom de domaine complet du service de fédération dans le **nom de service de fédération**.
    
  - Type de **CORP\\utilisateur1** **nom**de l’utilisateur.
    
  - Dans **mot de passe**, tapez le mot de passe pour le compte d’utilisateur1.
    
  - Cliquez sur **Suivant**.
    
6. Dans la page **Certificat de serveur Proxy AD FS** , cliquez sur la flèche vers le bas, cliquez sur le certificat avec votre nom de domaine complet du service de fédération, puis cliquez sur **suivant**.
    
7. Dans la page de **Confirmation** , cliquez sur **configurer**.
    
8. Sur la page de **résultats** , cliquez sur **Fermer**.
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>Phase 5 : configuration d’Office 365 pour l’identité fédérée

Le [portail Azure](http://portal.azure.com) permet de se connecter à la machine virtuelle de APP1 avec le CORP\\informations d’identification de compte utilisateur1.
  
Suivez ces étapes pour configurer Azure AD Connect et votre abonnement Office 365 pour l’authentification fédérée :
  
1. Sur le bureau, double-cliquez sur **Azure Connect d’Active Directory**.
    
2. Dans la page **Bienvenue dans Azure Connect d’Active Directory** , cliquez sur **configurer**.
    
3. Dans la page **des tâches supplémentaires** , cliquez sur **modification authentification de l’utilisateur**, puis cliquez sur **suivant**.
    
4. Sur la page de **connexion à Azure AD** , tapez votre nom de compte d’administrateur global Office 365 et d’un mot de passe, puis cliquez sur **suivant**.
    
5. Sur la page **Connexion utilisateur**, cliquez sur **Fédération avec AD FS**, puis sur **Suivant**.
    
6. Sur la page de la **batterie de serveurs ADFS** , cliquez sur **utiliser une batterie Federation Services existante**, tapez **ADFS1** dans la zone **Nom du serveur**, puis cliquez sur **suivant**.
    
7. À l’invite d’informations d’identification du serveur, entrez les informations d’identification de l’entreprise\\User1 du compte, puis cliquez sur **OK**.
    
8. Sur la page informations d’identification **d’Administrateur de domaine** , tapez **CORP\\utilisateur1** **nom d’utilisateur** et le mot de passe de compte de **mot de passe**, puis cliquez sur **suivant**.
    
9. Dans la page **compte de service AD FS** , tapez **CORP\\-Service ADFS** dans **Nom d’utilisateur de domaine** et le mot de passe du compte de **Domaine mot de passe**, puis cliquez sur **suivant**.
    
10. Dans la page **Domaine de AD Azure** , dans un **domaine**, sélectionnez le nom du domaine précédemment créé et ajouté à votre abonnement à Office 365 à la Phase 1, puis cliquez sur **suivant**.
    
11. Dans la page **prêt à configurer** , cliquez sur **configurer**.
    
12. Dans la page **Installation terminée** , cliquez sur **Vérifier**.
    
    Vous devriez voir des messages vous indiquant que les configurations intranet et Internet ont été vérifiées.
    
13. Sur la page **Installation terminée**, cliquez sur **Quitter**.
    
Pour vérifier que l’authentification fédérée fonctionne, procédez comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur sur votre ordinateur local et accédez à [https://portal.office.com](https://portal.office.com).
    
2. Pour les informations de connexion, tapez **utilisateur1 @**\<le domaine créé dans la Phase 1 >. 
    
    Par exemple, si votre domaine de test est **testlab.contoso.com**, vous devez taper **user1@testlab.contoso.com**. Appuyez sur TAB ou permettre à Office 365 vous rediriger automatiquement.
    
    Vous devez maintenant voir une page **votre connexion n’est pas privée** . Vous obtenez cette erreur, car vous avez installé un certificat signé automatiquement sur ADFS1 que votre ordinateur de bureau ne peut pas valider. Dans un déploiement de production d’authentification fédérée, vous devez utiliser un certificat auprès d’une autorité de certification de confiance et vos utilisateurs ne verra pas cette page.
    
3. Dans la page **votre connexion n’est pas privée** , cliquez sur **Avancé**, puis cliquez sur **continuer à \<nom de domaine complet de votre service de fédération >**. 
    
4. Sur la page contenant le nom de votre organisation fictive, connectez-vous avec les éléments suivants :
    
  - **CORP\\utilisateur1** pour le nom
    
  - le mot de passe du compte User1.
    
    Vous devez voir la page **d’Accueil de Microsoft Office** .
    
Cette procédure montre que votre abonnement d’évaluation d’Office 365 est fédéré avec le domaine corp.contoso.com Windows Server Active Directory hébergé sur DC1. Voici les notions de base du processus d’authentification :
  
1. Lorsque vous utilisez le domaine fédéré que vous avez créé à la phase 1 dans le nom de compte de connexion, Office 365 redirige votre navigateur vers votre nom de domaine complet du service FS (Federation Service) et PROXY1.
    
2. PROXY1 envoie la page de connexion de l’entreprise fictive à votre ordinateur local.
    
3. Lorsque vous envoyez CORP\\User1 et mot de passe à PROXY1, il les transfère à ADFS1.
    
4. ADFS1 valide CORP\\Utilisateur1 et le mot de passe avec DC1 et l’envoie à l’ordinateur local un jeton de sécurité.
    
5. Votre ordinateur local envoie le jeton de sécurité à Office 365.
    
6. Office 365 confirme que le jeton de sécurité a été créé par ADFS1 et autorise l’accès.
    
Votre abonnement à la version d’évaluation d’Office 365 est désormais configuré avec l’authentification fédérée. Vous pouvez utiliser cet environnement de développement/test pour les scénarios d’authentification avancés.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à déployer le prêt pour la production, l’authentification fédérée de haute disponibilité pour Office 365 dans Azure, consultez [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


