---
title: Réseau virtuel intersites simulé dans Azure.
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
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 'Résumé : Créez un réseau virtuel simulé coexistence dans Azure de Microsoft comme environnement de développement/test.'
ms.openlocfilehash: 41988e8201e896a7c1900b645e6c38357d0bfcd0
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="f847e-103">Réseau virtuel intersites simulé dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f847e-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="f847e-104">**Résumé :** Créer un réseau virtuel simulé coexistence dans Azure de Microsoft comme environnement de développement/test.</span><span class="sxs-lookup"><span data-stu-id="f847e-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="f847e-p101">Cet article vous guide tout au long de la création d’un environnement de cloud hybride simulé avec Microsoft Azure, à l’aide de deux réseaux virtuels Azure. Voici la configuration obtenue.  </span><span class="sxs-lookup"><span data-stu-id="f847e-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![Phase 3 de l’environnement de test/développement de réseau virtuel intersites simulé, avec la machine virtuelle DC2 dans XPrem VNet](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="f847e-108">Cette configuration simule un environnement de production cloud hybride Azure IaaS et comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f847e-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="f847e-109">	Un réseau local simulé et simplifié hébergé dans un réseau virtuel Azure (réseau virtuel TestLab).</span><span class="sxs-lookup"><span data-stu-id="f847e-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="f847e-110">	Un réseau virtuel intersites simulé hébergé dans Azure (XPrem).</span><span class="sxs-lookup"><span data-stu-id="f847e-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="f847e-111">	Une relation d’homologation VNet entre les deux réseaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="f847e-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="f847e-112">	Un contrôleur de domaine secondaire dans le réseau virtuel XPrem.</span><span class="sxs-lookup"><span data-stu-id="f847e-112">A secondary domain controller in the XPrem virtual network.</span></span>
    
<span data-ttu-id="f847e-113">Ces éléments offrent une base commune à partir de laquelle vous pouvez : </span><span class="sxs-lookup"><span data-stu-id="f847e-113">This provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="f847e-114">	Développer et tester des applications dans un environnement cloud hybride Azure IaaS simulé.</span><span class="sxs-lookup"><span data-stu-id="f847e-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="f847e-115">	Créer des configurations de test d’ordinateurs, certains au sein du réseau virtuel TestLab et d’autres au sein du réseau virtuel XPrem, afin de simuler les charges de travail informatiques dans un environnement cloud hybride.</span><span class="sxs-lookup"><span data-stu-id="f847e-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="f847e-116">Les trois phases principales pour configurer cet environnement de développement/test sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f847e-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="f847e-117">	Configurer le réseau virtuel TestLab.</span><span class="sxs-lookup"><span data-stu-id="f847e-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="f847e-118">Créer le réseau virtuel intersites.</span><span class="sxs-lookup"><span data-stu-id="f847e-118">Create the cross-premises virtual network.</span></span>
    
3. <span data-ttu-id="f847e-119">Configurer DC2</span><span class="sxs-lookup"><span data-stu-id="f847e-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f847e-120">Cette configuration nécessite un abonnement payant à Azure.</span><span class="sxs-lookup"><span data-stu-id="f847e-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Guides de laboratoire de test dans le cloud de Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="f847e-122">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="f847e-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="f847e-123">Phase 1 : Configurer le réseau virtuel TestLab</span><span class="sxs-lookup"><span data-stu-id="f847e-123">Phase 1: Configure the TestLab virtual network</span></span>

<span data-ttu-id="f847e-124">Suivez les instructions dans [l’environnement de développement/test de Configuration de Base](base-configuration-dev-test-environment.md) pour configurer les ordinateurs DC1, APP1 et CLIENT1 dans le réseau virtuel Azure nommé labo de test.</span><span class="sxs-lookup"><span data-stu-id="f847e-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="f847e-125">Il s’agit de votre configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="f847e-125">This is your current configuration.</span></span> 
  
![Phase 4 de la configuration de base dans Azure avec la machine virtuelle CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="f847e-127">Phase 2 : Créer le réseau virtuel XPrem</span><span class="sxs-lookup"><span data-stu-id="f847e-127">Phase 2: Create the XPrem virtual network</span></span>

<span data-ttu-id="f847e-128">Dans cette phase, vous devez créer et configurer le nouveau réseau virtuel XPrem et le connecter au réseau virtuel TestLab avec l’homologation VNet.</span><span class="sxs-lookup"><span data-stu-id="f847e-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="f847e-129">Tout d’abord, démarrez une invite PowerShell Azure sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f847e-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f847e-p102">La commande suivante définit utiliser la dernière version de PowerShell d’Azure. Reportez-vous à la section [mise en route avec les applets de commande PowerShell d’Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="f847e-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="f847e-132">Connectez-vous à votre compte Azure avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f847e-132">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="f847e-133">Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) pour obtenir un fichier texte qui contient toutes les commandes de PowerShell dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f847e-133">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="f847e-134">Obtenez le nom de votre abonnement à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f847e-134">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="f847e-p103">Définissez votre abonnement Azure. Remplacez tout entre guillemets, y compris la \< et > caractères, avec le nom correct.</span><span class="sxs-lookup"><span data-stu-id="f847e-p103">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

<span data-ttu-id="f847e-137">Créez ensuite le réseau virtuel XPrem et protégez-le avec un groupe de sécurité réseau, à l’aide des commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f847e-137">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

<span data-ttu-id="f847e-138">Vous devez ensuite créer la relation d’homologation VNet entre les réseaux virtuels TestLab et XPrem, à l’aide des commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f847e-138">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="f847e-139">Il s’agit de votre configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="f847e-139">This is your current configuration.</span></span> 
  
![Phase 2 de l’environnement de test/développement de réseau virtuel intersites simulé, avec XPrem VNet et la relation d’homologation VNet](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="f847e-141">Phase 3 : Configurer DC2</span><span class="sxs-lookup"><span data-stu-id="f847e-141">Phase 3: Configure DC2</span></span>

<span data-ttu-id="f847e-142">Dans cette phase, vous devez créer la machine virtuelle DC2 dans le réseau virtuel XPrem, puis la configurer comme un contrôleur de domaine répliqué.</span><span class="sxs-lookup"><span data-stu-id="f847e-142">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="f847e-p104">Tout d’abord, créez une machine virtuelle pour DC2. Exécutez ces commandes dans l’invite de commande Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f847e-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="f847e-145">Ensuite, vous connecter à la nouvelle machine virtuelle DC2 à partir du [portail Azure](https://portal.azure.com) à l’aide de son nom de compte d’administrateur local et d’un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f847e-145">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="f847e-p105">Ensuite, configurez une règle de pare-feu Windows pour autoriser le trafic afin d’effectuer des tests de connectivité de base. Exécutez ces commandes à l’invite de commande Windows PowerShell de niveau administrateur sur DC2. </span><span class="sxs-lookup"><span data-stu-id="f847e-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="f847e-p106">La commande ping doit aboutir à quatre réponses réussies à partir de l’adresse IP 10.0.0.4. Il s’agit d’un test du trafic sur la relation d’homologation VNet. </span><span class="sxs-lookup"><span data-stu-id="f847e-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="f847e-150">Ensuite, ajoutez le disque de données supplémentaires sous la forme d’un nouveau volume avec la lettre de lecteur F: avec cette commande à partir de l’invite de commande Windows PowerShell sur DC2.</span><span class="sxs-lookup"><span data-stu-id="f847e-150">Next, add the extra data disk as a new volume with the drive letter F: with this command from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="f847e-p107">Configurez ensuite DC2 en tant que contrôleur de domaine répliqué pour le domaine corp.contoso.com. Exécutez les commandes suivantes à partir de l’invite de commande Windows PowerShell sur DC2.</span><span class="sxs-lookup"><span data-stu-id="f847e-p107">Next, configure DC2 as a replica domain controller for the corp.contoso.com domain. Run these commands from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\\NTDS" -LogPath "F:\\Logs" -SysvolPath "F:\\SYSVOL"
```

<span data-ttu-id="f847e-153">Notez que vous êtes invité à fournir à la fois le CORP\\utilisateur1 mot de passe et d’un mot de passe en Mode de restauration des Services annuaire (DSRM) et redémarrez DC2.</span><span class="sxs-lookup"><span data-stu-id="f847e-153">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="f847e-p108">Maintenant que le réseau virtuel XPrem possède son propre serveur DNS (DC2), vous devez configurer le réseau virtuel XPrem pour utiliser ce serveur DNS. Exécutez ces commandes à partir de l’invite de commande Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f847e-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="f847e-p109">À partir du portail Azure sur votre ordinateur local, connectez à DC1 avec le CORP\\informations d’identification d’utilisateur1. Pour configurer le domaine CORP afin que les utilisateurs et les ordinateurs utilisent leur contrôleur de domaine local pour l’authentification, exécuter ces commandes à partir d’une invite de commande de Windows PowerShell de niveau administrateur sur DC1.</span><span class="sxs-lookup"><span data-stu-id="f847e-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="f847e-158">Il s’agit de votre configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="f847e-158">This is your current configuration.</span></span> 
  
![Phase 3 de l’environnement de test/développement de réseau virtuel intersites simulé, avec la machine virtuelle DC2 dans XPrem VNet](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="f847e-160">Votre environnement cloud hybride Azure simulé est prêt pour le test.</span><span class="sxs-lookup"><span data-stu-id="f847e-160">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="f847e-161">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="f847e-161">Next step</span></span>

<span data-ttu-id="f847e-162">Utiliser cet environnement de développement/test afin de simuler une [batterie de serveurs intranet SharePoint Server 2016 hébergé dans Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="f847e-162">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f847e-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f847e-163">See Also</span></span>

[<span data-ttu-id="f847e-164">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="f847e-164">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="f847e-165">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="f847e-165">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="f847e-166">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="f847e-166">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f847e-167">Application du nuage sécurité pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="f847e-167">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f847e-168">Avancées de protection contre les menaces pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="f847e-168">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f847e-169">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="f847e-169">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


