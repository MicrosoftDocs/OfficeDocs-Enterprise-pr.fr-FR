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
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "Résumé : Configurer une authentification fédérée pour votre environnement de développement/test d’Office 365."
ms.openlocfilehash: 8458e8e11547c14e479a64d037707d5292afcc02
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="0b15f-103">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="0b15f-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="0b15f-104">**Résumé :** Configurer l’authentification fédérée pour votre environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b15f-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0b15f-p101">Office 365 prend en charge des identités fédérées. Cela signifie qu’au lieu d’effectuer la validation des informations d’identification lui-même, Office 365 fait référence l’utilisateur qui se connecte à un serveur d’authentification fédérée qui approuve d’Office 365. Si les informations d’identification sont correctes, le serveur d’authentification fédérée délivre un jeton de sécurité que le client envoie ensuite vers Office 365 comme preuve d’authentification. Une identité fédérée permet le déchargement et l’évolution verticale de l’authentification pour un abonnement à Office 365 et scénarios avancés d’authentification et de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="0b15f-109">Cet article explique comment configurer l’authentification fédérée pour l’environnement de développement/test Office 365, pour le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="0b15f-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="0b15f-110">**Figure 1 : L’authentification fédérée pour l’environnement de développement/test d’Office 365**</span><span class="sxs-lookup"><span data-stu-id="0b15f-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="0b15f-112">La configuration illustrée dans la figure 1 est constituée des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="0b15f-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="0b15f-113">Un abonnement d’évaluation Office 365 E5, qui arrive à expiration 30 jours après sa création.</span><span class="sxs-lookup"><span data-stu-id="0b15f-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="0b15f-p102">Un intranet d’organisation simplifié et connecté à Internet, composé de cinq machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1, CLIENT1, ADFS1 et PROXY1). Azure AD Connect s’exécute sur APP1 pour synchroniser la liste de comptes dans le domaine Windows Server AD avec Office 365. PROXY1 reçoit les demandes d’authentification entrantes. ADFS1 valide les informations d’identification avec DC1 et émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="0b15f-118">Les cinq phases de configuration de cet environnement de développement/test sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b15f-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="0b15f-119">Créez l’environnement de développement/test Office 365 d’entreprise simulé avec DirSync.</span><span class="sxs-lookup"><span data-stu-id="0b15f-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="0b15f-120">Créez le serveur AD FS (ADFS1).</span><span class="sxs-lookup"><span data-stu-id="0b15f-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="0b15f-121">Créez le serveur proxy web (PROXY1).</span><span class="sxs-lookup"><span data-stu-id="0b15f-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="0b15f-122">Créez un certificat auto-signé et configurez ADFS1 et PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="0b15f-123">Configurez Office 365 pour l’identité fédérée.</span><span class="sxs-lookup"><span data-stu-id="0b15f-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="0b15f-124">Pour exécuter un déploiement de production d’authentification fédérée pour Office 365 dans Azure, consultez [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="0b15f-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0b15f-125">Vous ne pouvez pas configurer cet environnement de développement/test avec un abonnement à la version d’évaluation d’Azure.</span><span class="sxs-lookup"><span data-stu-id="0b15f-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="0b15f-126">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="0b15f-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="0b15f-127">Phase 1 : création de l’environnement de développement/test Office 365 d’entreprise simulé avec DirSync</span><span class="sxs-lookup"><span data-stu-id="0b15f-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="0b15f-128">Suivez les instructions dans [la synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md) pour créer l’environnement de développement/test simulées entreprise Office 365 avec APP1 comme serveur de synchronisation d’annuaire et identité synchronisée entre Office 365 et l’Active Directory de Windows Server comptes sur DC1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-128">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="0b15f-p103">Ensuite, créer un nom de domaine DNS public en fonction de votre nom de domaine actuel et l’ajouter à votre abonnement à Office 365. Nous recommandons d’utiliser le nom **labo de test.** \<votre domaine public >. Par exemple, si votre nom de domaine public est contoso.com, ajouter la testlab.contoso.com de nom de domaine public.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="0b15f-132">Pour obtenir des instructions sur la façon de créer les enregistrements DNS corrects de votre fournisseur DNS et ajouter le domaine à votre abonnement d’évaluation d’Office 365, reportez-vous à la section [Ajouter des utilisateurs et domaine à Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span><span class="sxs-lookup"><span data-stu-id="0b15f-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="0b15f-133">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="0b15f-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="0b15f-134">**La figure 2 : Synchronisation d’annuaire pour l’environnement de développement/test d’Office 365**</span><span class="sxs-lookup"><span data-stu-id="0b15f-134">**Figure 2: DirSync for Office 365 dev/test environment**</span></span>

![Environnement de développement/test d’Office 365 avec DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="0b15f-136">La figure 2 illustre la synchronisation d’annuaire pour l’environnement de développement/test Office 365, qui comprend Office 365, ainsi que les machines virtuelles CLIENT1, APP1 et DC1 dans un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="0b15f-136">Figure 2 shows the DirSync for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="0b15f-137">Phase 2 : création du serveur AD FS (ADFS1)</span><span class="sxs-lookup"><span data-stu-id="0b15f-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="0b15f-138">Un serveur AD FS fournit une authentification fédérée entre Office 365 et les comptes dans le domaine corp.contoso.com hébergé sur DC1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="0b15f-139">Pour créer un ordinateur virtuel Azure pour ADFS1, indiquez le nom de votre abonnement et le groupe de ressources et l’emplacement Azure pour votre Configuration de Base et puis exécuter ces commandes à l’invite de commande PowerShell de Azure sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0b15f-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
> <span data-ttu-id="0b15f-140">Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) pour obtenir un fichier texte qui contient toutes les commandes de PowerShell dans cet article.</span><span class="sxs-lookup"><span data-stu-id="0b15f-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="0b15f-141">Ensuite, le [portail Azure](http://portal.azure.com) permet de se connecter à l’ordinateur virtuel ADFS1 à l’aide du nom du compte administrateur local ADFS1 et le mot de passe et puis ouvrez une invite de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b15f-141">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0b15f-142">Pour vérifier la communication réseau et la résolution de nom entre ADFS1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.</span><span class="sxs-lookup"><span data-stu-id="0b15f-142">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="0b15f-143">Ensuite, associez la machine virtuelle ADFS1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur ADFS1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-143">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="0b15f-144">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="0b15f-144">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="0b15f-145">**Figure 3 : Ajouter le serveur AD FS**</span><span class="sxs-lookup"><span data-stu-id="0b15f-145">**Figure 3: Adding the AD FS server**</span></span>

![Le serveur AD FS ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="0b15f-147">La figure 3 illustre l’ajout du serveur ADFS1 à DirSync pour l’environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b15f-147">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="0b15f-148">Phase 3 : création du serveur proxy web (PROXY1)</span><span class="sxs-lookup"><span data-stu-id="0b15f-148">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="0b15f-149">PROXY1 permet le traitement proxy des messages d’authentification entre les utilisateurs tentant de s’authentifier et ADFS1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-149">PROXY1 provides proxying of authentication messages between users attempting to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="0b15f-150">Pour créer une machine virtuelle Azure pour PROXY1, indiquez le nom de votre groupe de ressources et l’emplacement Azure, puis exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0b15f-150">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
> <span data-ttu-id="0b15f-151">Une adresse IP publique statique est affectée à PROXY1, car vous créez un enregistrement DNS public qui pointe vers celle-ci et elle ne doit pas être modifiée lorsque vous redémarrez la machine virtuelle PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-151">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="0b15f-p104">Ensuite, ajoutez une règle au groupe de sécurité réseau pour le sous-réseau du réseau d’entreprise pour autoriser le trafic entrant non sollicité à partir d’Internet pour les adresses IP privées de PROXY1 et le port TCP 443. Exécuter ces commandes à l’invite de commande PowerShell de Azure sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

<span data-ttu-id="0b15f-154">Ensuite, le [portail Azure](http://portal.azure.com) permet de se connecter à la machine virtuelle PROXY1 en utilisant le nom du compte administrateur local PROXY1 et le mot de passe et puis ouvrez une invite de commande Windows PowerShell sur PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-154">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="0b15f-155">Pour vérifier la communication réseau et la résolution de nom entre PROXY1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.</span><span class="sxs-lookup"><span data-stu-id="0b15f-155">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="0b15f-156">Ensuite, associez la machine virtuelle PROXY1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-156">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="0b15f-157">Affichez l’adresse IP publique de PROXY1 avec ces commandes Azure PowerShell sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="0b15f-157">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="0b15f-p105">Ensuite, travailler avec votre fournisseur DNS public et créer un nouvel enregistrement A DNS public pour **fs.testlab.** \<le nom de votre domaine DNS > qui est résolu en l’adresse IP affichée par la commande **Write-Host** . Le **fs.testlab.** \<le nom de votre domaine DNS > est désigné comme le *service federation service de nom de domaine complet* .</span><span class="sxs-lookup"><span data-stu-id="0b15f-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="0b15f-160">Ensuite, utilisez le [portail Azure](http://portal.azure.com) pour se connecter à la machine virtuelle de DC1 à l’aide de l’entreprise\\informations d’identification d’Utilisateur1 et exécuter ce qui suit à une invite de commande Windows PowerShell au niveau de l’administrateur des commandes :</span><span class="sxs-lookup"><span data-stu-id="0b15f-160">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="0b15f-161">Ces commandes créent un enregistrement A DNS pour votre nom de domaine complet du service FS (Federation Service) que les machines virtuelles sur le réseau virtuel Azure peuvent résoudre sur l’adresse IP privée d’ADFS1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-161">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="0b15f-162">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="0b15f-162">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="0b15f-163">**Figure 4 : Ajout du serveur de proxy d’application web**</span><span class="sxs-lookup"><span data-stu-id="0b15f-163">**Figure 4: Adding the web application proxy server**</span></span>

![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de développement/test Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="0b15f-165">La figure 4 illustre l’ajout du serveur PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-165">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="0b15f-166">Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1</span><span class="sxs-lookup"><span data-stu-id="0b15f-166">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="0b15f-167">Au cours de cette phase, vous créez un certificat numérique auto-signé pour votre nom de domaine complet du service FS (Federation Service) et vous configurez ADFS1 et PROXY1 en tant que batterie de serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="0b15f-167">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="0b15f-168">Tout d’abord, utilisez le [portail Azure](http://portal.azure.com) pour se connecter à la machine virtuelle de DC1 à l’aide de l’entreprise\\invite de commande des informations d’identification d’Utilisateur1 et puis ouvrez un Windows PowerShell de niveau administrateur.</span><span class="sxs-lookup"><span data-stu-id="0b15f-168">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0b15f-169">Ensuite, créez un compte de service AD FS avec cette commande à l’invite de commande Windows PowerShell sur DC1 :</span><span class="sxs-lookup"><span data-stu-id="0b15f-169">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="0b15f-p106">Notez que cette commande vous invite à indiquer le mot de passe du compte. Choisissez un mot de passe fort et enregistrez-le dans un emplacement sécurisé. Vous en aurez besoin pour cette phase et la phase 5.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="0b15f-p107">Le [portail Azure](http://portal.azure.com) permet de se connecter à l’ordinateur virtuel ADFS1 à l’aide de l’entreprise\\informations d’identification d’utilisateur1. Ouvrez une invite de commandes au niveau de l’administrateur de Windows PowerShell sur ADFS1, renseignez votre nom de domaine complet du service de fédération et puis exécutez ces commandes pour créer un certificat auto-signé :</span><span class="sxs-lookup"><span data-stu-id="0b15f-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

<span data-ttu-id="0b15f-175">Ensuite, utilisez ces étapes pour enregistrer le nouveau certificat auto-signé en tant que fichier.</span><span class="sxs-lookup"><span data-stu-id="0b15f-175">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="0b15f-176">Cliquez sur **Démarrer**, tapez **mmc.exe**et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-176">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="0b15f-177">Cliquez sur **fichier > Ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-177">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="0b15f-178">Dans **Ajouter ou supprimer des composants**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-178">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="0b15f-179">Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-179">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0b15f-180">Dans le volet d’arborescence, ouvrez **certificats (ordinateur Local) > Personal > certificats**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-180">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="0b15f-181">Cliquez sur le certificat avec votre nom de domaine complet du service de fédération et cliquez sur **toutes les tâches**, puis cliquez sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-181">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="0b15f-182">Dans la page **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-182">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="0b15f-183">Dans la page **Exportation de clé privée** , cliquez sur **Oui**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-183">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0b15f-184">Dans la page **Format de fichier d’exportation** , cliquez sur **Exporter toutes les propriétés étendues**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-184">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="0b15f-185">Dans la page **sécurité** , cliquez sur **mot de passe** et tapez un mot de passe **mot de passe** et **Confirmer mot de passe.**</span><span class="sxs-lookup"><span data-stu-id="0b15f-185">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="0b15f-186">Dans la page **fichier à exporter** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-186">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="0b15f-187">Accédez à la **C:\\certificats** dossier, tapez **SSL** dans **nom de fichier**, puis cliquez sur **Enregistrer.**</span><span class="sxs-lookup"><span data-stu-id="0b15f-187">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="0b15f-188">Dans la page **fichier à exporter** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-188">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="0b15f-p108">Dans la page **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**. Lorsque vous y êtes invité, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="0b15f-191">Ensuite, installez le service AD FS avec cette commande à l’invite de commande Windows PowerShell sur ADFS1 :</span><span class="sxs-lookup"><span data-stu-id="0b15f-191">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="0b15f-192">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="0b15f-192">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="0b15f-193">Ensuite, configurez le service AD FS en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="0b15f-193">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="0b15f-194">Cliquez sur **Démarrer**, puis cliquez sur l’icône du **Gestionnaire de serveur** .</span><span class="sxs-lookup"><span data-stu-id="0b15f-194">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="0b15f-195">Dans le volet d’arborescence du Gestionnaire de serveur, cliquez sur **AD FS**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-195">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="0b15f-196">Dans la barre d’outils en haut, cliquez sur le symbole Attention orange, puis cliquez sur **configurer le service de fédération sur ce serveur**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-196">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="0b15f-197">Dans la page **Bienvenue** de l’Assistant Configuration des Services de fédération Active Directory, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-197">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="0b15f-198">Sur la page de **connexion aux services AD DS** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-198">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="0b15f-199">Dans la page **Spécifier les propriétés de Service** :</span><span class="sxs-lookup"><span data-stu-id="0b15f-199">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="0b15f-200">**Certificat SSL**, cliquez sur la flèche vers le bas, puis cliquez sur le certificat avec le nom de votre nom de domaine complet du service de fédération.</span><span class="sxs-lookup"><span data-stu-id="0b15f-200">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="0b15f-201">Dans la zone **Nom complet du Service Federation**, tapez le nom de votre organisation fictive.</span><span class="sxs-lookup"><span data-stu-id="0b15f-201">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="0b15f-202">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-202">Click **Next**.</span></span>
    
7. <span data-ttu-id="0b15f-203">Dans la page **Spécifier le compte de Service** , cliquez sur **Sélectionner** pour le **nom du compte**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-203">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="0b15f-204">Dans, **Sélectionnez l’utilisateur ou le compte de Service**, tapez **Service ADFS**, cliquez sur **Vérifier les noms**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-204">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="0b15f-205">Dans **Mot de passe**, tapez le mot de passe pour le compte de Service ADFS et puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-205">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="0b15f-206">Dans la page **Spécifier la base de données de Configuration** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-206">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="0b15f-207">Dans la page **Options de révision** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-207">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="0b15f-208">Sur la page **Contrôle de condition préalable** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-208">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="0b15f-209">Sur la page de **résultats** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-209">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="0b15f-210">Cliquez sur **Démarrer**, cliquez sur l’icône d’alimentation, cliquez sur **redémarrer**, puis cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-210">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="0b15f-211">Dans le [portail Azure](http://portal.azure.com), connectez-vous à PROXY1 avec le CORP\\informations d’identification de compte utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-211">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="0b15f-212">Ensuite, suivez ces étapes pour installer le certificat auto-signé et configurer PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-212">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="0b15f-213">Cliquez sur **Démarrer**, tapez **mmc.exe**et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-213">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="0b15f-214">Cliquez sur **fichier > Ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-214">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="0b15f-215">Dans **Ajouter ou supprimer des composants**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-215">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="0b15f-216">Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-216">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0b15f-217">Dans le volet d’arborescence, ouvrez **certificats (ordinateur Local) > Personal > certificats**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-217">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="0b15f-218">Cliquez droit sur **personnel**et cliquez sur **toutes les tâches**, puis cliquez sur **Importer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-218">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="0b15f-219">Dans la page **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-219">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="0b15f-220">Dans la page **fichier à importer** , tapez ** \\ \\adfs1\\certificats\\ssl.pfx**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-220">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0b15f-221">Sur la page de **protection par clé privée** , tapez le mot de passe de certificat de **mot de passe**, puis cliquez sur **Suivant.**</span><span class="sxs-lookup"><span data-stu-id="0b15f-221">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="0b15f-222">Dans la page **magasin de certificats** , cliquez sur **Suivant.**</span><span class="sxs-lookup"><span data-stu-id="0b15f-222">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="0b15f-223">Sur la page de **fin** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-223">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="0b15f-224">Dans la page **Magasin de certificats** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-224">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="0b15f-225">Lorsque vous y êtes invité, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-225">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="0b15f-226">Dans le volet d’arborescence, cliquez sur **certificats** .</span><span class="sxs-lookup"><span data-stu-id="0b15f-226">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="0b15f-227">Cliquez sur le certificat, puis cliquez sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-227">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="0b15f-228">Dans le volet d’arborescence, ouvrez **autorités de Certification racines de confiance > certificats**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-228">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="0b15f-229">Placez le pointeur de la souris sous la liste de certificats installés, avec le bouton droit, puis cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-229">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="0b15f-230">Ouvrez une invite de commande PowerShell de niveau administrateur et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b15f-230">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="0b15f-231">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="0b15f-231">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="0b15f-232">Suivez ces étapes pour configurer le service de proxy d’application web de manière à ce qu’il utilise ADFS1 comme serveur de fédération :</span><span class="sxs-lookup"><span data-stu-id="0b15f-232">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="0b15f-233">Cliquez sur **Démarrer**, puis cliquez sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-233">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="0b15f-234">Dans le volet d’arborescence, cliquez sur **Accès à distance**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-234">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="0b15f-235">Dans la barre d’outils en haut, cliquez sur le symbole Attention orange, puis cliquez sur **Ouvrir l’Assistant de Proxy d’Application Web**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-235">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="0b15f-236">Dans la page **Bienvenue** de l’Assistant de Configuration de Proxy Web Application, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-236">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="0b15f-237">Sur la page **Serveur de fédération** :</span><span class="sxs-lookup"><span data-stu-id="0b15f-237">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="0b15f-238">Tapez votre nom de domaine complet du service de fédération dans le **nom de service de fédération**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-238">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="0b15f-239">Type de **CORP\\utilisateur1** **nom**de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0b15f-239">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="0b15f-240">Dans **mot de passe**, tapez le mot de passe pour le compte d’utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-240">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="0b15f-241">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-241">Click **Next**.</span></span>
    
6. <span data-ttu-id="0b15f-242">Dans la page **Certificat de serveur Proxy AD FS** , cliquez sur la flèche vers le bas, cliquez sur le certificat avec votre nom de domaine complet du service de fédération, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-242">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="0b15f-243">Dans la page de **Confirmation** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-243">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="0b15f-244">Sur la page de **résultats** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-244">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="0b15f-245">Phase 5 : configuration d’Office 365 pour l’identité fédérée</span><span class="sxs-lookup"><span data-stu-id="0b15f-245">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="0b15f-246">Le [portail Azure](http://portal.azure.com) permet de se connecter à la machine virtuelle de APP1 avec le CORP\\informations d’identification de compte utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-246">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="0b15f-247">Suivez ces étapes pour configurer Azure AD Connect et votre abonnement Office 365 pour l’authentification fédérée :</span><span class="sxs-lookup"><span data-stu-id="0b15f-247">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="0b15f-248">Sur le bureau, double-cliquez sur **Azure Connect d’Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-248">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="0b15f-249">Dans la page **Bienvenue dans Azure Connect d’Active Directory** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-249">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="0b15f-250">Dans la page **des tâches supplémentaires** , cliquez sur **modification authentification de l’utilisateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-250">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="0b15f-251">Sur la page de **connexion à Azure AD** , tapez votre nom de compte d’administrateur global Office 365 et d’un mot de passe, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-251">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="0b15f-252">Sur la page **Connexion utilisateur**, cliquez sur **Fédération avec AD FS**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-252">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="0b15f-253">Sur la page de la **batterie de serveurs ADFS** , cliquez sur **utiliser une batterie Federation Services existante**, tapez **ADFS1** dans la zone **Nom du serveur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-253">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="0b15f-254">À l’invite d’informations d’identification du serveur, entrez les informations d’identification de l’entreprise\\User1 du compte, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-254">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="0b15f-255">Sur la page informations d’identification **d’Administrateur de domaine** , tapez **CORP\\utilisateur1** **nom d’utilisateur** et le mot de passe de compte de **mot de passe**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-255">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0b15f-256">Dans la page **compte de service AD FS** , tapez **CORP\\-Service ADFS** dans **Nom d’utilisateur de domaine** et le mot de passe du compte de **Domaine mot de passe**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-256">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="0b15f-257">Dans la page **Domaine de AD Azure** , dans un **domaine**, sélectionnez le nom du domaine précédemment créé et ajouté à votre abonnement à Office 365 à la Phase 1, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-257">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="0b15f-258">Dans la page **prêt à configurer** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-258">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="0b15f-259">Dans la page **Installation terminée** , cliquez sur **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-259">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="0b15f-260">Vous devriez voir des messages vous indiquant que les configurations intranet et Internet ont été vérifiées.</span><span class="sxs-lookup"><span data-stu-id="0b15f-260">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="0b15f-261">Sur la page **Installation terminée**, cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-261">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="0b15f-262">Pour vérifier que l’authentification fédérée fonctionne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0b15f-262">To demonstrate that federated authentication is working, do the following:</span></span>
  
1. <span data-ttu-id="0b15f-263">Ouvrez une nouvelle instance privée de votre navigateur sur votre ordinateur local et accédez à [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="0b15f-263">Open a new private instance of your browser on your local computer and go to [https://portal.office.com](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="0b15f-264">Pour les informations de connexion, tapez **utilisateur1 @**\<le domaine créé dans la Phase 1 >.</span><span class="sxs-lookup"><span data-stu-id="0b15f-264">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="0b15f-265">Par exemple, si votre domaine de test est **testlab.contoso.com**, vous devez taper **user1@testlab.contoso.com**. Appuyez sur TAB ou permettre à Office 365 vous rediriger automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0b15f-265">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="0b15f-p109">Vous devez maintenant voir une page **votre connexion n’est pas privée** . Vous obtenez cette erreur, car vous avez installé un certificat signé automatiquement sur ADFS1 que votre ordinateur de bureau ne peut pas valider. Dans un déploiement de production d’authentification fédérée, vous devez utiliser un certificat auprès d’une autorité de certification de confiance et vos utilisateurs ne verra pas cette page.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p109">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="0b15f-269">Dans la page **votre connexion n’est pas privée** , cliquez sur **Avancé**, puis cliquez sur **continuer à \<nom de domaine complet de votre service de fédération >**.</span><span class="sxs-lookup"><span data-stu-id="0b15f-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="0b15f-270">Sur la page contenant le nom de votre organisation fictive, connectez-vous avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0b15f-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="0b15f-271">**CORP\\utilisateur1** pour le nom</span><span class="sxs-lookup"><span data-stu-id="0b15f-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="0b15f-272">le mot de passe du compte User1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="0b15f-273">Vous devez voir la page **d’Accueil de Microsoft Office** .</span><span class="sxs-lookup"><span data-stu-id="0b15f-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="0b15f-p110">Cette procédure montre que votre abonnement d’évaluation d’Office 365 est fédéré avec le domaine corp.contoso.com Windows Server Active Directory hébergé sur DC1. Voici les notions de base du processus d’authentification :</span><span class="sxs-lookup"><span data-stu-id="0b15f-p110">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="0b15f-276">Lorsque vous utilisez le domaine fédéré que vous avez créé à la phase 1 dans le nom de compte de connexion, Office 365 redirige votre navigateur vers votre nom de domaine complet du service FS (Federation Service) et PROXY1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="0b15f-277">PROXY1 envoie la page de connexion de l’entreprise fictive à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0b15f-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="0b15f-278">Lorsque vous envoyez CORP\\User1 et mot de passe à PROXY1, il les transfère à ADFS1.</span><span class="sxs-lookup"><span data-stu-id="0b15f-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="0b15f-279">ADFS1 valide CORP\\Utilisateur1 et le mot de passe avec DC1 et l’envoie à l’ordinateur local un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b15f-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="0b15f-280">Votre ordinateur local envoie le jeton de sécurité à Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b15f-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="0b15f-281">Office 365 confirme que le jeton de sécurité a été créé par ADFS1 et autorise l’accès.</span><span class="sxs-lookup"><span data-stu-id="0b15f-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="0b15f-p111">Votre abonnement à la version d’évaluation d’Office 365 est désormais configuré avec l’authentification fédérée. Vous pouvez utiliser cet environnement de développement/test pour les scénarios d’authentification avancés.</span><span class="sxs-lookup"><span data-stu-id="0b15f-p111">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="0b15f-284">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="0b15f-284">Next Step</span></span>

<span data-ttu-id="0b15f-285">Lorsque vous êtes prêt à déployer le prêt pour la production, l’authentification fédérée de haute disponibilité pour Office 365 dans Azure, consultez [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="0b15f-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b15f-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b15f-286">See Also</span></span>

[<span data-ttu-id="0b15f-287">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="0b15f-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0b15f-288">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="0b15f-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="0b15f-289">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="0b15f-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0b15f-290">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="0b15f-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0b15f-291">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="0b15f-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


