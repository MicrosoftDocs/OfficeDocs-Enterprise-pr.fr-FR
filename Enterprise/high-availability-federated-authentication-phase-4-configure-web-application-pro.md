---
title: Authentification fédérée haute disponibilité, phase 4 configurer les proxys d'application Web
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Résumé: conFigurez les serveurs proxy d'application Web pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure."
ms.openlocfilehash: c5472c8c7268d39dd6d3ca5ef78bde9e4bdde7a3
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491284"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="faeb6-103">Authentification fédérée haute disponibilité, phase 4 : Configurer les proxys d’application web</span><span class="sxs-lookup"><span data-stu-id="faeb6-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="faeb6-104">**Résumé:** ConFigurez les serveurs proxy d'application Web pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="faeb6-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="faeb6-105">Au cours de cette phase du déploiement de la haute disponibilité pour l’authentification fédérée Office 365 dans les services d’infrastructure Azure, vous avez créé un équilibreur de charge interne et deux serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="faeb6-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="faeb6-106">Vous devez effectuer cette phase avant de passer à [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span><span class="sxs-lookup"><span data-stu-id="faeb6-106">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="faeb6-107">Reportez-vous à la rubrique [Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.</span><span class="sxs-lookup"><span data-stu-id="faeb6-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="faeb6-108">Créer l’équilibreur de charge connecté à Internet dans Azure</span><span class="sxs-lookup"><span data-stu-id="faeb6-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="faeb6-109">Vous devez créer un équilibreur de charge connecté à Internet pour permettre à Azure de répartir équitablement le trafic d’authentification client entrant à partir d’Internet sur les deux serveurs proxy d’application web.</span><span class="sxs-lookup"><span data-stu-id="faeb6-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="faeb6-110">[!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faeb6-110">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="faeb6-111">Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="faeb6-111">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="faeb6-112">Une fois que vous avez indiqué les valeurs d’emplacement et de groupe de ressources, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="faeb6-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="faeb6-113">Pour afficher l’adresse IP publique affectée à votre équilibreur de charge connecté à Internet, exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="faeb6-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="faeb6-114">Déterminer le nom de domaine complet de votre service de fédération et créer des enregistrements DNS</span><span class="sxs-lookup"><span data-stu-id="faeb6-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="faeb6-p103">Vous devez déterminer le nom DNS pour identifier le nom de votre service de fédération sur Internet. Azure AD Connect configure Office 365 avec ce nom au cours de la Phase 5 pour qu’il fasse partie de l’URL envoyée par Office 365 aux clients qui se connectent pour obtenir un jeton de sécurité. Ce nom est, par exemple, fs.contoso.com (fs signifie federation service : service de fédération).</span><span class="sxs-lookup"><span data-stu-id="faeb6-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="faeb6-118">Une fois que le nom de domaine complet du service de fédération a été obtenu, créez un enregistrement DNS de domaine public A pour le nom de domaine complet pour le résoudre en adresse IP publique de l’équilibreur de charge Azure connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="faeb6-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="faeb6-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="faeb6-119">**Name**</span></span>|<span data-ttu-id="faeb6-120">**Type**</span><span class="sxs-lookup"><span data-stu-id="faeb6-120">**Type**</span></span>|<span data-ttu-id="faeb6-121">**TTL (Durée de vie)**</span><span class="sxs-lookup"><span data-stu-id="faeb6-121">**TTL**</span></span>|<span data-ttu-id="faeb6-122">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="faeb6-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="faeb6-123">Nom de domaine complet du service de fédération</span><span class="sxs-lookup"><span data-stu-id="faeb6-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="faeb6-124">A</span><span class="sxs-lookup"><span data-stu-id="faeb6-124">A</span></span>  <br/> |<span data-ttu-id="faeb6-125">3600</span><span class="sxs-lookup"><span data-stu-id="faeb6-125">3600</span></span>  <br/> |<span data-ttu-id="faeb6-126">adresse IP publique de l’équilibreur de charge Azure connecté à Internet (affiché par la commande **Write-Host** dans la section précédente)</span><span class="sxs-lookup"><span data-stu-id="faeb6-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="faeb6-127">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="faeb6-127">Here is an example:</span></span>
  
|<span data-ttu-id="faeb6-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="faeb6-128">**Name**</span></span>|<span data-ttu-id="faeb6-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="faeb6-129">**Type**</span></span>|<span data-ttu-id="faeb6-130">**TTL (Durée de vie)**</span><span class="sxs-lookup"><span data-stu-id="faeb6-130">**TTL**</span></span>|<span data-ttu-id="faeb6-131">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="faeb6-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="faeb6-132">FS.contoso.com</span><span class="sxs-lookup"><span data-stu-id="faeb6-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="faeb6-133">A</span><span class="sxs-lookup"><span data-stu-id="faeb6-133">A</span></span>  <br/> |<span data-ttu-id="faeb6-134">3600</span><span class="sxs-lookup"><span data-stu-id="faeb6-134">3600</span></span>  <br/> |<span data-ttu-id="faeb6-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="faeb6-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="faeb6-136">Ensuite, ajoutez un enregistrement d’adresse DNS à l’espace de noms DNS privé de votre organisation pour résoudre le nom de domaine complet de votre service de fédération en adresse IP privée affectée à l’équilibreur de charge interne pour les serveurs AD FS (tableau I, élément 4, colonne Valeur).</span><span class="sxs-lookup"><span data-stu-id="faeb6-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="faeb6-137">Créer les machines virtuelles des serveurs proxy d’application web dans Azure</span><span class="sxs-lookup"><span data-stu-id="faeb6-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="faeb6-138">Utilisez le bloc de commandes Azure PowerShell suivant pour créer les machines virtuelles pour les deux serveurs proxy d’application web. </span><span class="sxs-lookup"><span data-stu-id="faeb6-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="faeb6-139">Notez que l’ensemble de commandes Azure PowerShell suivant utilise des valeurs provenant des tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="faeb6-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="faeb6-140">Tableau M, pour vos machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="faeb6-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="faeb6-141">Tableau R, pour vos groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="faeb6-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="faeb6-142">Tableau V, pour vos paramètres de réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="faeb6-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="faeb6-143">Tableau S, pour vos sous-réseaux</span><span class="sxs-lookup"><span data-stu-id="faeb6-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="faeb6-144">Tableau I, pour vos adresses IP statiques</span><span class="sxs-lookup"><span data-stu-id="faeb6-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="faeb6-145">Tableau A, pour vos groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="faeb6-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="faeb6-146">Rappelez-vous que vous avez défini le tableau M dans [High Availability Federated authenticAtion phase 2: configurer](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) les contrôleurs de domaine et les tableaux R, V, S, I et A dans [High Availability Federated Authentication phase 1: configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="faeb6-146">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="faeb6-147">Lorsque vous avez fourni toutes les valeurs correctes, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="faeb6-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="faeb6-p104">Étant donné que ces machines virtuelles sont pour une application intranet, aucune adresse IP publique ni étiquette de nom de domaine DNS ne leur est affectée et elles ne sont pas connectées à Internet. Toutefois, vous ne pouvez pas vous y connecter à partir du portail Azure. L’option **Se connecter** n’est pas disponible lorsque vous affichez les propriétés de la machine virtuelle. Utilisez l’accessoire de connexion Bureau à distance ou un autre outil de Bureau à distance pour vous connecter à la machine virtuelle à l’aide de son adresse IP privée ou de son nom DNS intranet, ainsi que les informations d’identification du compte Administrateur local.</span><span class="sxs-lookup"><span data-stu-id="faeb6-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="faeb6-152">Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="faeb6-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="faeb6-153">**Phase 4 : L’équilibreur de charge connecté à Internet et les serveurs proxy d’application web de votre infrastructure d’authentification fédérée haute disponibilité dans Azure**</span><span class="sxs-lookup"><span data-stu-id="faeb6-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 4 de l'infrastructure d'authentification fédérée haute disponibilité Office 365 dans Azure avec les serveurs proxy d'application Web](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="faeb6-155">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="faeb6-155">Next step</span></span>

<span data-ttu-id="faeb6-156">Utilisez [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) pour poursuivre la configuration de cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="faeb6-156">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="faeb6-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faeb6-157">See Also</span></span>

[<span data-ttu-id="faeb6-158">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="faeb6-158">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="faeb6-159">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="faeb6-159">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="faeb6-160">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="faeb6-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="faeb6-161">Options d'authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="faeb6-161">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


