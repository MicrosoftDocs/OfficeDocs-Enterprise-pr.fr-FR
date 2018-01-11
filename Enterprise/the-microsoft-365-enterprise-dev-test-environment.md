---
title: "Environnement de développement/test Microsoft 365 Entreprise"
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
- Ent_TLGs
- Strat_O365_Enterprise
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test incluant Office 365 E5, mobilité d’entreprise + E5 de sécurité (EMS) et un ordinateur exécutant Windows 10 Enterprise."
ms.openlocfilehash: f6baabaee10c25243690918aa6c9b2c68ff3758b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Environnement de développement/test Microsoft 365 Entreprise

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test incluant Office 365 E5, mobilité d’entreprise + E5 de sécurité (EMS) et un ordinateur exécutant Windows 10 Enterprise.
  
Cet article vous fournit des instructions pas à pas pour créer un environnement simplifié pour tester les fonctionnalités [d’Entreprise de Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>Phase 1 : Création de votre abonnement Office 365 E5

Suivez les étapes de la Phase 2 et 3 de Phase de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md) pour créer un environnement de développement/test lightweight Office 365, comme illustré dans la Figure 1.
  
**Figure 1 : Votre abonnement Office 365 E5 avec ses comptes d’utilisateurs et les clients de Azure Active Directory (AD)**

![Phase 1 de l’environnement de développement/test Microsoft 365 Entreprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a>Phase 2 : Ajout d’EMS

Dans cette phase, vous vous inscrivez pour l’abonnement à la version d’évaluation d’EMS E5 et l’ajoutez à la même organisation que votre abonnement à la version d’évaluation d’Office 365 E5.
  
Tout d’abord, ajouter l’abonnement d’évaluation EMS E5 et affecter une licence EMS à votre compte d’administrateur global.
  
1. Avec une instance privée d’un navigateur Internet, connectez-vous au portail Office 365 avec vos informations d’identification du compte administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
7. Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.
    
8. Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
9. Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
> [!NOTE]
> L’abonnement à la version d’évaluation d’Enterprise Mobility + Security E5 est de 90 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
 ***Si vous avez terminé la Phase 3 de*** [Environnement de développement/test d’office 365](office-365-dev-test-environment.md) , répétez les étapes 8 et 9 de la procédure précédente pour l’ensemble de vos autres comptes (utilisateur 2, utilisateur 3, utilisateur 4 et 5 de l’utilisateur).
  
Votre environnement de développement/test comporte maintenant :
  
- Des abonnements d’évaluation Office 365 E5 Entreprise et EMS qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Tous vos comptes d’utilisateur appropriés (uniquement l’administrateur global ou tous les cinq comptes d’utilisateur) sont activés pour utiliser Office 365 E5 et EMS E5.
    
La figure 2 montre la configuration obtenue, qui ajoute EMS.
  
**Figure 2 : Ajout de l’abonnement d’évaluation EMS**

![Phase 2 de l’environnement de développement/test Microsoft 365 Entreprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>Phase 3 : Création d’un ordinateur Windows 10 Entreprise

Au cours de cette phase, vous allez créer un ordinateur autonome exécutant Windows 10 Entreprise.
  
### <a name="physical-computer"></a>Ordinateur physique

Obtenir un ordinateur personnel et installer Windows 10 Enterprise. Vous pouvez télécharger le Windows 10 Enterprise d’évaluation [ici](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Machine virtuelle

Créer un ordinateur virtuel à l’aide de l’hyperviseur de votre choix et installer Windows 10 Enterprise. Vous pouvez télécharger le Windows 10 Enterprise d’évaluation [ici](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Machine virtuelle dans Azure

Pour créer un ordinateur virtuel de Windows 10 de Microsoft Azure, ***vous devez posséder un abonnement basé sur Visual Studio***, qui a accès à l’image 10 de Windows. Autres types d’abonnements Azure, tels que des abonnements d’essai et payés, n’ont pas d’accès à cette image.
  
> [!NOTE]
> La commande suivante définit utiliser la version la plus récente de PowerShell d’Azure te. Reportez-vous à la section [mise en route avec les applets de commande PowerShell d’Azure](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Ces jeux de génération commande un ordinateur virtuel de Windows 10 Enterprise nommé WIN10 et l’ensemble de l’infrastructure requise, y compris un réseau virtuel, un compte de stockage et un groupe de ressources. Si vous êtes déjà familiarisé avec les services d’infrastructure Azure, veuillez s’adapter ces instructions en fonction de votre infrastructure actuellement déployé. 
  
Tout d’abord, lancez une invite Microsoft PowerShell.
  
Connectez-vous à votre compte Azure avec la commande suivante.
  
```
Login-AzureRMAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Définissez votre abonnement Azure. Remplacez tout entre guillemets, y compris la \< et > caractères, avec le nom correct.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Ensuite, créez un nouveau groupe de ressources. Pour déterminer un nom de groupe de ressources unique, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes. Remplacez tout entre guillemets, y compris la \< et > caractères, avec le nom correct.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Machines virtuelles basées sur le Gestionnaire de ressources nécessite un compte de stockage basé sur le Gestionnaire de ressources. Vous devez choisir un nom unique pour votre compte de stockage *qui contient uniquement des minuscules et chiffres* . Vous pouvez utiliser cette commande pour répertorier les comptes de stockage existants.
  
```
Get-AzureRMStorageAccount | Sort StorageAccountName | Select StorageAccountName
```

Utilisez cette commande pour vérifier si un nom proposé pour un compte de stockage est unique.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

Créez un compte de stockage pour votre nouvel environnement de test avec ces commandes.
  
```
$rgName="<your new resource group name>"
$saName="<storage account name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

Ensuite, créez une ressource virtuelle et la machine virtuelle WIN10 avec ces commandes. Lorsque vous y êtes invité, indiquez le nom et le mot de passe du compte d’administrateur local pour WIN10, et enregistrez ces informations dans un emplacement sécurisé.
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$storageAcc=Get-AzureRMStorageAccount -ResourceGroupName $rgName -Name $saName
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftVisualStudio -Offer Windows -Skus Windows-10-N-x64 -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$osDiskUri=$storageAcc.PrimaryEndpoints.Blob.ToString() + "vhds/WIN10-TestLab-OSDisk.vhd"
$vm=Set-AzureRMVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -VhdUri $osDiskUri -CreateOption fromImage
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>Phase 4 : Association de votre ordinateur Windows 10 à Azure AD

Lorsque la machine physique ou virtuelle est créée, configurée avec Windows 10 Entreprise et en cours d’exécution, connectez-vous avec un compte d’administrateur local.
  
> [!NOTE]
> Pour un ordinateur virtuel dans Azure, se connecter à l’aide de [ces instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Connectez-vous avec les informations d’identification du compte administrateur local. 
  
Ensuite, associez l’ordinateur WIN10 au client Azure AD de vos abonnements Office 365 et EMS.
  
1. Sur le bureau de l’ordinateur WIN10, cliquez sur **Démarrer > Paramètres > comptes > travail d’accès ou à l’école > Connect**.
    
2. Dans la boîte de dialogue **configurer un compte de travail ou à l’école** , cliquez sur **joindre ce périphérique pour Azure Active Directory**.
    
3. Dans **travail ou le compte de l’école**, tapez le nom du compte administrateur global de votre abonnement à Office 365, puis cliquez sur **suivant**.
    
4. Dans l' **entrée de mot de passe**, tapez le mot de passe pour votre compte d’administrateur global, puis cliquez sur **se connecter**.
    
5. Lorsque vous êtes invité à vous assurer que c’est votre organisation, cliquez sur **joindre**, puis cliquez sur **terminé**.
    
6. Fermez la fenêtre Paramètres.
    
Ensuite, installez Office 2016 sur l’ordinateur WIN10.
  
1. Ouvrez le navigateur de Microsoft Edge et vous connecter au portail Office 365 avec vos informations d’identification du compte administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **installer un 2016 Office**.
    
3. Lorsque vous y êtes invité par la procédure à suivre, cliquez sur **exécuter**, puis cliquez sur **Oui** pour le **Contrôle de compte d’utilisateur**.
    
4. Attendez que Office terminer l’installation. Lorsque vous consultez **vous tous !**, cliquez deux fois sur **Fermer** .
    
La figure 3 illustre l’environnement obtenu, avec l’ordinateur WIN10 associé au client Azure AD de vos abonnements Office 365 et EMS.
  
**Figure 3 : Ajouter le compte d’ordinateur WIN10 au locataire Azure AD**

![Phase 4 de l’environnement de développement/test Microsoft 365 Entreprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
Vous êtes maintenant prêt à essayer des fonctionnalités [d’Entreprise de Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Étapes suivantes

Ces articles supplémentaires vous feront découvrir les fonctionnalités de Microsoft 365 Entreprise :
  
- [Ajouter des stratégies d’application mobile management (MAM)](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Inscrire les périphériques iOS ou Android](https://technet.microsoft.com/library/mt743077.aspx)
    
- [Configurer et tester la gestion avancée de la sécurité](https://technet.microsoft.com/library/mt757250.aspx)
    
- [Configurer et tester la protection avancée contre les menaces](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>Voir aussi

[L’environnement de développement/test d’un nuage de Microsoft](the-one-microsoft-cloud-dev-test-environment.md)

[Documentation Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)




