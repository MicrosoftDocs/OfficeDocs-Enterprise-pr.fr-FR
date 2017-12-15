---
title: "Haute disponibilité fédérés d’authentification Phase 4 configurer web proxy de l’application"
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
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Résumé : Configurer les serveurs proxy d’applications web pour l’authentification fédérée de haute disponibilité pour Office 365 dans Microsoft Azure."
ms.openlocfilehash: 02aeac727815a82c15cd602094e945a14ed551af
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="c1628-103">Authentification fédérée haute disponibilité, phase 4 : Configurer les proxys d’application web</span><span class="sxs-lookup"><span data-stu-id="c1628-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="c1628-104">**Résumé :** Configurer les serveurs proxy d’applications web pour l’authentification fédérée de haute disponibilité pour Office 365 dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c1628-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="c1628-105">Au cours de cette phase du déploiement de la haute disponibilité pour l’authentification fédérée Office 365 dans les services d’infrastructure Azure, vous avez créé un équilibreur de charge interne et deux serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="c1628-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="c1628-p101">Vous devez terminer cette phase avant de passer à [haute disponibilité fédérés d’authentification Phase 5 : configurez l’authentification fédérée pour Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Pour toutes les phases, reportez-vous à la section [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="c1628-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="c1628-108">Créer l’équilibreur de charge connecté à Internet dans Azure</span><span class="sxs-lookup"><span data-stu-id="c1628-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="c1628-109">Vous devez créer un équilibreur de charge connecté à Internet pour permettre à Azure de répartir équitablement le trafic d’authentification client entrant à partir d’Internet sur les deux serveurs proxy d’application web.</span><span class="sxs-lookup"><span data-stu-id="c1628-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c1628-p102">La commande suivante définit utiliser la dernière version de PowerShell d’Azure. Reportez-vous à la section [mise en route avec les applets de commande PowerShell d’Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="c1628-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c1628-112">Une fois que vous avez indiqué les valeurs d’emplacement et de groupe de ressources, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c1628-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="c1628-113">Pour un fichier texte qui contient toutes les commandes de PowerShell dans cet article et un classeur Microsoft Excel configuration qui génère des blocs de commande PowerShell prête à exécuter en fonction de vos paramètres personnalisés, consultez la [l’authentification fédérée pour Office 365 dans Kit de déploiement d’Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="c1628-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="c1628-114">Pour afficher l’adresse IP publique affectée à votre équilibreur de charge connecté à Internet, exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="c1628-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="c1628-115">Déterminer le nom de domaine complet de votre service de fédération et créer des enregistrements DNS</span><span class="sxs-lookup"><span data-stu-id="c1628-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="c1628-p103">Vous devez déterminer le nom DNS pour identifier le nom de votre service de fédération sur Internet. Azure AD Connect configure Office 365 avec ce nom au cours de la Phase 5 pour qu’il fasse partie de l’URL envoyée par Office 365 aux clients qui se connectent pour obtenir un jeton de sécurité. Ce nom est, par exemple, fs.contoso.com (fs signifie federation service : service de fédération).</span><span class="sxs-lookup"><span data-stu-id="c1628-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="c1628-119">Une fois que le nom de domaine complet du service de fédération a été obtenu, créez un enregistrement DNS de domaine public A pour le nom de domaine complet pour le résoudre en adresse IP publique de l’équilibreur de charge Azure connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="c1628-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="c1628-120">**Nom**</span><span class="sxs-lookup"><span data-stu-id="c1628-120">**Name**</span></span>|<span data-ttu-id="c1628-121">**Type**</span><span class="sxs-lookup"><span data-stu-id="c1628-121">**Type**</span></span>|<span data-ttu-id="c1628-122">**DURÉE DE VIE**</span><span class="sxs-lookup"><span data-stu-id="c1628-122">**TTL**</span></span>|<span data-ttu-id="c1628-123">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c1628-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c1628-124">Nom de domaine complet du service de fédération</span><span class="sxs-lookup"><span data-stu-id="c1628-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="c1628-125">A</span><span class="sxs-lookup"><span data-stu-id="c1628-125">A</span></span>  <br/> |<span data-ttu-id="c1628-126">3600</span><span class="sxs-lookup"><span data-stu-id="c1628-126">3600</span></span>  <br/> |<span data-ttu-id="c1628-127">adresse IP publique de l’équilibreur de charge pour Azure Internet (affiché par la commande **Write-Host** , dans la section précédente)</span><span class="sxs-lookup"><span data-stu-id="c1628-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="c1628-128">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="c1628-128">Here is an example:</span></span>
  
|<span data-ttu-id="c1628-129">**Nom**</span><span class="sxs-lookup"><span data-stu-id="c1628-129">**Name**</span></span>|<span data-ttu-id="c1628-130">**Type**</span><span class="sxs-lookup"><span data-stu-id="c1628-130">**Type**</span></span>|<span data-ttu-id="c1628-131">**DURÉE DE VIE**</span><span class="sxs-lookup"><span data-stu-id="c1628-131">**TTL**</span></span>|<span data-ttu-id="c1628-132">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c1628-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c1628-133">FS.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c1628-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="c1628-134">A</span><span class="sxs-lookup"><span data-stu-id="c1628-134">A</span></span>  <br/> |<span data-ttu-id="c1628-135">3600</span><span class="sxs-lookup"><span data-stu-id="c1628-135">3600</span></span>  <br/> |<span data-ttu-id="c1628-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="c1628-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="c1628-137">Ensuite, ajoutez un enregistrement d’adresse DNS à l’espace de noms DNS privé de votre organisation pour résoudre le nom de domaine complet de votre service de fédération en adresse IP privée affectée à l’équilibreur de charge interne pour les serveurs AD FS (tableau I, élément 4, colonne Valeur).</span><span class="sxs-lookup"><span data-stu-id="c1628-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="c1628-138">Créer les machines virtuelles des serveurs proxy d’application web dans Azure</span><span class="sxs-lookup"><span data-stu-id="c1628-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="c1628-139">Utilisez le bloc de commandes Azure PowerShell suivant pour créer les machines virtuelles pour les deux serveurs proxy d’application web. </span><span class="sxs-lookup"><span data-stu-id="c1628-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="c1628-140">Notez que l’ensemble de commandes Azure PowerShell suivant utilise des valeurs provenant des tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="c1628-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="c1628-141">Tableau M, pour vos machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="c1628-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="c1628-142">Tableau R, pour vos groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="c1628-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="c1628-143">Tableau V, pour vos paramètres de réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="c1628-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="c1628-144">Tableau S, pour vos sous-réseaux</span><span class="sxs-lookup"><span data-stu-id="c1628-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="c1628-145">Tableau I, pour vos adresses IP statiques</span><span class="sxs-lookup"><span data-stu-id="c1628-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="c1628-146">Tableau A, pour vos groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="c1628-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="c1628-147">Rappeler que vous avez défini le tableau M dans [haute disponibilité fédérés d’authentification Phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) et Tables R, V, S, I et dans [haute disponibilité fédérés d’authentification Phase 1 : configurer les Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c1628-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="c1628-148">Lorsque vous avez fourni toutes les valeurs correctes, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c1628-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="c1628-p104">Étant donné que ces machines virtuelles sont d’une application intranet, elles ne sont pas affectés une adresse IP publique ou une étiquette de nom de domaine DNS et exposés à Internet. Cependant, cela signifie également que vous ne peut pas y connecter à partir du portail Azure. L’option **se connecter** n’est pas disponible lorsque vous affichez les propriétés de l’ordinateur virtuel. Utilisez l’accessoire de connexion Bureau à distance ou un autre outil de bureau à distance pour vous connecter à l’ordinateur virtuel à l’aide de son privé IP adresse intranet ou le nom DNS et les informations d’identification du compte administrateur local.</span><span class="sxs-lookup"><span data-stu-id="c1628-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c1628-153">Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="c1628-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="c1628-154">**Phase 4 : Côté Internet charge équilibrage et les serveurs proxy d’application web pour votre infrastructure d’authentification fédérée de haute disponibilité dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c1628-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 4 de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure à l’aide des serveurs proxy d’application web](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="c1628-156">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="c1628-156">Next step</span></span>

<span data-ttu-id="c1628-157">Utilisation [haute disponibilité fédérés d’authentification Phase 5 : configurez l’authentification fédérée pour Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) pour continuer la configuration de cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="c1628-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c1628-158">See Also</span><span class="sxs-lookup"><span data-stu-id="c1628-158">See Also</span></span>

[<span data-ttu-id="c1628-159">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="c1628-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="c1628-160">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="c1628-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c1628-161">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="c1628-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c1628-162">Identité fédérée pour Office 365</span><span class="sxs-lookup"><span data-stu-id="c1628-162">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


