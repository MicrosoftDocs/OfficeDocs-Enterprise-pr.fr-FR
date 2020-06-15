---
title: Authentification fédérée haute disponibilité, phase 3 configurer les serveurs AD FS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 'Résumé : créez et configurez les serveurs AD FS (Active Directory Federation Services) pour votre authentification fédérée haute disponibilité pour Microsoft 365 dans Microsoft Azure.'
ms.openlocfilehash: 7b32c39ada30059df78ccb5429dba11c1576dff7
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711927"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="54d4f-103">Authentification fédérée haute disponibilité, phase 3 : Configurer les serveurs AD FS</span><span class="sxs-lookup"><span data-stu-id="54d4f-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

<span data-ttu-id="54d4f-104">Dans cette phase de déploiement de la haute disponibilité pour l’authentification fédérée Microsoft 365 dans les services d’infrastructure Azure, vous créez un équilibreur de charge interne et deux serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="54d4f-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="54d4f-105">Vous devez effectuer cette phase avant de passer à la [phase 4 : configurer les proxys d’application Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span><span class="sxs-lookup"><span data-stu-id="54d4f-105">You must complete this phase before moving on to [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="54d4f-106">Consultez la rubrique [Deploy High Availability Federated Authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.</span><span class="sxs-lookup"><span data-stu-id="54d4f-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="54d4f-107">Créer les machines virtuelles du serveur AD FS dans Azure</span><span class="sxs-lookup"><span data-stu-id="54d4f-107">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="54d4f-p102">Utilisez le bloc de commandes PowerShell suivant pour créer les machines virtuelles pour les deux serveurs AD FS. Cet ensemble de commandes PowerShell utilise des valeurs provenant des tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="54d4f-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="54d4f-110">Tableau M, pour vos machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="54d4f-110">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="54d4f-111">Tableau R, pour vos groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="54d4f-111">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="54d4f-112">Tableau V, pour vos paramètres de réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="54d4f-112">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="54d4f-113">Tableau S, pour vos sous-réseaux</span><span class="sxs-lookup"><span data-stu-id="54d4f-113">Table S, for your subnets</span></span>
    
- <span data-ttu-id="54d4f-114">Tableau I, pour vos adresses IP statiques</span><span class="sxs-lookup"><span data-stu-id="54d4f-114">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="54d4f-115">Tableau A, pour vos groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="54d4f-115">Table A, for your availability sets</span></span>
    
<span data-ttu-id="54d4f-116">Rappelez-vous que vous avez défini le tableau M à la [phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) et les tableaux R, V, S, I et A à la [phase 1 : configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="54d4f-116">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="54d4f-117">[!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54d4f-117">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="54d4f-118">Consultez la rubrique [prise en main d’Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="54d4f-118">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="54d4f-119">Tout d’abord, vous créez un équilibreur de charge interne Azure pour les deux serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="54d4f-119">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="54d4f-120">Spécifiez les valeurs des variables, en supprimant les \< and > caractères.</span><span class="sxs-lookup"><span data-stu-id="54d4f-120">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="54d4f-121">Lorsque vous avez fourni toutes les valeurs correctes, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="54d4f-121">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="54d4f-122">Pour générer des blocs de commandes PowerShell prêts à l’emploi en fonction de vos paramètres personnalisés, utilisez ce [classeur de configuration Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="54d4f-122">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="54d4f-123">Créez ensuite les machines virtuelles du serveur AD FS.</span><span class="sxs-lookup"><span data-stu-id="54d4f-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="54d4f-124">Lorsque vous avez fourni toutes les valeurs correctes, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="54d4f-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="54d4f-p105">Étant donné que ces machines virtuelles sont destinées à une application intranet, aucune adresse IP publique ni étiquette de nom de domaine DNS ne leur est affectée et elles ne sont pas connectées à Internet. Toutefois, cela signifie également que vous ne pouvez pas vous y connecter à partir du portail Azure. L’option de **connexion** n’est pas disponible lorsque vous affichez les propriétés de la machine virtuelle. Utilisez l’accessoire de connexion Bureau à distance ou un autre outil de Bureau à distance pour vous connecter à la machine virtuelle à l’aide de son adresse IP privée ou de son nom DNS intranet.</span><span class="sxs-lookup"><span data-stu-id="54d4f-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="54d4f-p106">Pour chaque machine virtuelle, utilisez le client Bureau à distance de votre choix et créez une connexion de Bureau à distance. Utilisez son nom d’ordinateur ou son nom DNS intranet et les informations d’identification du compte Administrateur local.</span><span class="sxs-lookup"><span data-stu-id="54d4f-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="54d4f-131">Pour chaque machine virtuelle, associez-les au domaine des services de domaine Active Directory (AD DS) approprié à l’aide de ces commandes à l’invite Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54d4f-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="54d4f-132">Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="54d4f-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="54d4f-133">**Phase 3 : Les serveurs AD FS et l’équilibreur de charge interne pour votre infrastructure d’authentification fédérée haute disponibilité dans Azure.**</span><span class="sxs-lookup"><span data-stu-id="54d4f-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 3 de l’infrastructure d’authentification fédérée haute disponibilité Microsoft 365 dans Azure avec les serveurs AD FS](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="54d4f-135">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="54d4f-135">Next step</span></span>

<span data-ttu-id="54d4f-136">Utilisez la [phase 4 : configurer les proxys d’application Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) pour poursuivre la configuration de cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="54d4f-136">Use [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54d4f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54d4f-137">See Also</span></span>

[<span data-ttu-id="54d4f-138">Déployer l’authentification fédérée haute disponibilité pour Microsoft 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="54d4f-138">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="54d4f-139">Identité fédérée pour votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="54d4f-139">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)


