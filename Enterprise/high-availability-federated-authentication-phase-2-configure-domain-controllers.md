---
title: Haute disponibilité fédérés Phase 2 configurer les contrôleurs de domaine d’authentification
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Résumé : Configurez les contrôleurs de domaine et le serveur DirSync pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure.'
ms.openlocfilehash: 1e66403348bc2cd9a6dfab56f32735d62c986035
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915149"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="000cd-103">Authentification fédérée haute disponibilité, phase 2 : Configurer les contrôleurs de domaine</span><span class="sxs-lookup"><span data-stu-id="000cd-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="000cd-104">**Résumé :** Configurez les contrôleurs de domaine et le serveur DirSync pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="000cd-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="000cd-p101">Au cours de cette phase de déploiement de la haute disponibilité pour l’authentification fédérée Office 365 dans les services d’infrastructure Azure, vous configurez deux contrôleurs de domaine et le serveur DirSync dans le réseau virtuel Azure. Les requêtes web client d’authentification peuvent ensuite être authentifiées dans le réseau virtuel Azure, plutôt que d’envoyer ce trafic d’authentification sur le VPN de site à site à votre réseau local.</span><span class="sxs-lookup"><span data-stu-id="000cd-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="000cd-107">Active Directory Federation Services (AD FS) ne peut pas utiliser les services de domaine Active Directory d’Azure comme substitut pour les contrôleurs de domaine Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="000cd-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="000cd-p102">Vous devez effectuer cette phase avant de passer à [haute disponibilité fédérés authentification Phase 3 : configurer les serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Voir [authentification fédérée de déploiement haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.</span><span class="sxs-lookup"><span data-stu-id="000cd-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="000cd-110">Créer les machines virtuelles du contrôleur de domaine dans Azure</span><span class="sxs-lookup"><span data-stu-id="000cd-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="000cd-111">Tout d'abord, vous devez remplir la colonne du **nom de la machine virtuelle** du tableau M et modifier les tailles de machine virtuelle selon vos besoins dans la colonne **Taille minimale**.</span><span class="sxs-lookup"><span data-stu-id="000cd-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="000cd-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="000cd-112">**Item**</span></span>|<span data-ttu-id="000cd-113">**Nom de la machine virtuelle**</span><span class="sxs-lookup"><span data-stu-id="000cd-113">**Virtual machine name**</span></span>|<span data-ttu-id="000cd-114">**Image de la galerie**</span><span class="sxs-lookup"><span data-stu-id="000cd-114">**Gallery image**</span></span>|<span data-ttu-id="000cd-115">**Type de stockage**</span><span class="sxs-lookup"><span data-stu-id="000cd-115">**Storage type**</span></span>|<span data-ttu-id="000cd-116">**Taille minimale**</span><span class="sxs-lookup"><span data-stu-id="000cd-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="000cd-117">1.</span><span class="sxs-lookup"><span data-stu-id="000cd-117">1.</span></span>  <br/> |<span data-ttu-id="000cd-118">![](./media/Common-Images/TableLine.png) (premier contrôleur de domaine, par exemple DC1)</span><span class="sxs-lookup"><span data-stu-id="000cd-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="000cd-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-122">2.</span><span class="sxs-lookup"><span data-stu-id="000cd-122">2.</span></span>  <br/> |<span data-ttu-id="000cd-123">![](./media/Common-Images/TableLine.png) (deuxième contrôleur de domaine, par exemple DC2)</span><span class="sxs-lookup"><span data-stu-id="000cd-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="000cd-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-127">3.</span><span class="sxs-lookup"><span data-stu-id="000cd-127">3.</span></span>  <br/> |<span data-ttu-id="000cd-128">![](./media/Common-Images/TableLine.png)(Serveur de synchronisation d’annuaire, exemple DS1)</span><span class="sxs-lookup"><span data-stu-id="000cd-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="000cd-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-132">4.</span><span class="sxs-lookup"><span data-stu-id="000cd-132">4.</span></span>  <br/> |<span data-ttu-id="000cd-133">![](./media/Common-Images/TableLine.png)(le premier serveur d’AD FS, exemple ADFS1)</span><span class="sxs-lookup"><span data-stu-id="000cd-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="000cd-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-137">5.</span><span class="sxs-lookup"><span data-stu-id="000cd-137">5.</span></span>  <br/> |<span data-ttu-id="000cd-138">![](./media/Common-Images/TableLine.png)(le second serveur d’AD FS, exemple ADFS2)</span><span class="sxs-lookup"><span data-stu-id="000cd-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="000cd-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-142">6.</span><span class="sxs-lookup"><span data-stu-id="000cd-142">6.</span></span>  <br/> |<span data-ttu-id="000cd-143">![](./media/Common-Images/TableLine.png)(première application serveur proxy web, exemple WEB1)</span><span class="sxs-lookup"><span data-stu-id="000cd-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="000cd-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="000cd-147">7.</span><span class="sxs-lookup"><span data-stu-id="000cd-147">7.</span></span>  <br/> |<span data-ttu-id="000cd-148">![](./media/Common-Images/TableLine.png)(deuxième application serveur proxy web, exemple WEB2)</span><span class="sxs-lookup"><span data-stu-id="000cd-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="000cd-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="000cd-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="000cd-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="000cd-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="000cd-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="000cd-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="000cd-152">**Tableau M - ordinateurs virtuels pour l’authentification fédérée de haute disponibilité pour Office 365 dans Azure**</span><span class="sxs-lookup"><span data-stu-id="000cd-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="000cd-153">Pour obtenir la liste complète des tailles de machine virtuelle, reportez-vous à la rubrique [Tailles des machines virtuelles Windows dans Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="000cd-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="000cd-p103">Le bloc de commande PowerShell Azure suivant crée les ordinateurs virtuels pour les deux contrôleurs de domaine. Spécifiez les valeurs pour les variables, suppression de la \< et > caractères. Notez que ce bloc de commande PowerShell Azure utilise des valeurs dans les tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="000cd-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="000cd-157">Tableau M, pour vos machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="000cd-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="000cd-158">Tableau R, pour vos groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="000cd-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="000cd-159">Tableau V, pour vos paramètres de réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="000cd-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="000cd-160">Tableau S, pour vos sous-réseaux</span><span class="sxs-lookup"><span data-stu-id="000cd-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="000cd-161">Tableau I, pour vos adresses IP statiques</span><span class="sxs-lookup"><span data-stu-id="000cd-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="000cd-162">Tableau A, pour vos groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="000cd-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="000cd-163">Rappel défini de Tables R, V, S, I et dans [haute disponibilité fédérés authentification Phase 1 : Azure configurer](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="000cd-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="000cd-p104">Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="000cd-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="000cd-166">Lorsque vous avez indiqué toutes les valeurs correctes, exécutez le bloc résultant à l’invite de commandes Azure PowerShell ou dans l’environnement d'écriture de scripts intégré de Windows PowerShell (ISE) sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="000cd-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="000cd-167">Pour un fichier texte qui contient toutes les commandes PowerShell dans cet article et un classeur Microsoft Excel configuration qui génère des blocs de commande PowerShell prête à exécuter en fonction de vos paramètres personnalisés, voir l’authentification fédérée pour Office 365 [dans Kit de déploiement Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="000cd-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="000cd-p105">Étant donné que ces machines virtuelles sont pour une application intranet, ils ne sont pas attribués une adresse IP publique ou une étiquette de nom de domaine DNS et exposés à Internet. Cependant, cela signifie également que vous ne pouvez pas vous connecter à leur à partir du portail Azure. L’option **connexion** n’est pas disponible lorsque vous affichez les propriétés de l’ordinateur virtuel. Utilisez l’accessoire connexion Bureau à distance ou un autre outil de bureau à distance pour se connecter à l’ordinateur virtuel à l’aide de son privé IP adresse intranet ou le nom DNS.</span><span class="sxs-lookup"><span data-stu-id="000cd-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="000cd-172">Configurer le premier contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="000cd-172">Configure the first domain controller</span></span>

<span data-ttu-id="000cd-p106">Utilisez le client Bureau à distance de votre choix et créez une connexion de Bureau à distance pour la machine virtuelle du premier contrôleur de domaine. Utilisez son nom d’ordinateur ou son nom DNS intranet et les informations d’identification du compte Administrateur local.</span><span class="sxs-lookup"><span data-stu-id="000cd-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="000cd-175">Ensuite, ajoutez le disque de données supplémentaires pour le premier contrôleur de domaine avec cette commande à partir d’un Windows PowerShell invite de commandes **sur le premier ordinateur virtuel de contrôleur domaine**:</span><span class="sxs-lookup"><span data-stu-id="000cd-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="000cd-176">Ensuite, testez la connectivité du premier contrôleur de domaine vers des emplacements du réseau de votre organisation à l'aide de la commande **ping** pour effectuer un test ping des noms et des adresses IP des ressources du réseau de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="000cd-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="000cd-p107">Cette procédure permet de vérifier que la résolution de noms DNS fonctionne correctement (que la machine virtuelle est configurée correctement avec les serveurs DNS locaux) et que des paquets peuvent être envoyés vers et depuis le réseau virtuel intersites. Si ce test de base échoue, contactez votre service informatique pour résoudre les problèmes de résolution de noms DNS et de livraison de paquets.</span><span class="sxs-lookup"><span data-stu-id="000cd-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="000cd-179">Ensuite, à partir de l’invite de commandes Windows PowerShell sur le premier contrôleur de domaine, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="000cd-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="000cd-p108">Vous êtes invité à fournir les informations d’identification d’un compte Administrateur de domaine. L’ordinateur redémarre.</span><span class="sxs-lookup"><span data-stu-id="000cd-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="000cd-182">Configurer le deuxième contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="000cd-182">Configure the second domain controller</span></span>

<span data-ttu-id="000cd-p109">Utilisez le client Bureau à distance de votre choix et créez une connexion de Bureau à distance pour la machine virtuelle du deuxième contrôleur de domaine. Utilisez son nom d’ordinateur ou son nom DNS intranet et les informations d’identification du compte Administrateur local.</span><span class="sxs-lookup"><span data-stu-id="000cd-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="000cd-185">Ensuite, vous devez ajouter le disque de données supplémentaires au deuxième contrôleur de domaine avec cette commande à partir d’un Windows PowerShell invite de commandes **sur l’ordinateur virtuel de contrôleur de deuxième domaine**:</span><span class="sxs-lookup"><span data-stu-id="000cd-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="000cd-186">Ensuite, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="000cd-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="000cd-p110">Vous êtes invité à fournir les informations d’identification d’un compte Administrateur de domaine. L’ordinateur redémarre.</span><span class="sxs-lookup"><span data-stu-id="000cd-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="000cd-p111">Ensuite, vous devez mettre à jour les serveurs DNS pour votre réseau virtuel afin que Azure affecte les machines virtuelles les adresses IP de deux nouveaux contrôleurs de domaine à utiliser en tant que leurs serveurs DNS. Renseignez les variables, puis exécutez ces commandes à partir d’une invite de commandes Windows PowerShell sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="000cd-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="000cd-p112">Notez que nous redémarrons les deux contrôleurs de domaine afin qu’ils ne soient pas configurés avec les serveurs DNS locaux comme serveurs DNS. Comme ils sont tous les deux des serveurs DNS, ils ont été automatiquement configurés avec les serveurs DNS locaux comme redirecteurs DNS lorsqu’ils ont été promus comme contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="000cd-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="000cd-p113">Ensuite, nous devons créer un site de réplication Active Directory pour vérifier que les serveurs du réseau virtuel Azure utilisent les contrôleurs de domaine locaux. Connectez-vous à l’un des contrôleurs de domaine avec un compte Administrateur de domaine et exécutez les commandes suivantes à partir d’une invite de commandes Windows PowerShell au niveau de l’administrateur :</span><span class="sxs-lookup"><span data-stu-id="000cd-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="000cd-195">Configurer le serveur de DirSync</span><span class="sxs-lookup"><span data-stu-id="000cd-195">Configure the DirSync server</span></span>

<span data-ttu-id="000cd-p114">Utiliser le client Bureau à distance de votre choix et créer une connexion Bureau à distance à l’ordinateur virtuel de serveur DirSync. Utilisez son nom d’ordinateur ou DNS intranet et les informations d’identification du compte d’administrateur local.</span><span class="sxs-lookup"><span data-stu-id="000cd-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="000cd-198">Ensuite, associez-la au domaine Windows Server AD approprié avec ces commandes à l’invite Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="000cd-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="000cd-199">Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="000cd-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="000cd-200">**Phase 2 : Les contrôleurs de domaine et le serveur DirSync pour votre infrastructure d’authentification fédérée haute disponibilité dans Azure.**</span><span class="sxs-lookup"><span data-stu-id="000cd-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 2 de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure à l’aide des contrôleurs de domaine](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="000cd-202">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="000cd-202">Next step</span></span>

<span data-ttu-id="000cd-203">Utilisez [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) pour poursuivre la configuration de cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="000cd-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="000cd-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="000cd-204">See Also</span></span>

[<span data-ttu-id="000cd-205">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="000cd-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="000cd-206">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="000cd-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="000cd-207">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="000cd-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="000cd-208">Options d’authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="000cd-208">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


