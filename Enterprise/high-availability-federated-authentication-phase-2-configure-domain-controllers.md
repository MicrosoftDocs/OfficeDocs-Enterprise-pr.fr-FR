---
title: Authentification fédérée haute disponibilité, phase 2 configurer les contrôleurs de domaine
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Résumé : configurez les contrôleurs de domaine et le serveur de synchronisation d’annuaires pour votre authentification fédérée haute disponibilité pour Microsoft 365 dans Microsoft Azure.'
ms.openlocfilehash: c10fb2d32ea572280b43d32da56b9e4d6affa22a
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998052"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Authentification fédérée haute disponibilité, phase 2 : Configurer les contrôleurs de domaine

Dans cette phase de déploiement de la haute disponibilité pour l’authentification fédérée Microsoft 365 dans les services d’infrastructure Azure, vous configurez deux contrôleurs de domaine et le serveur de synchronisation d’annuaires dans le réseau virtuel Azure. Les requêtes web client d’authentification peuvent ensuite être authentifiées dans le réseau virtuel Azure, plutôt que d’envoyer ce trafic d’authentification sur le VPN de site à site à votre réseau local.
  
> [!NOTE]
> Active Directory Federation Services (AD FS) ne peut pas utiliser Azure Active Directory (Azure AD) comme substitut pour les contrôleurs de domaine des services de domaine Active Directory (AD DS). 
  
Vous devez effectuer cette phase avant de passer à la [phase 3 : configurer les serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Consultez la rubrique [Deploy High Availability Federated Authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Créer les machines virtuelles du contrôleur de domaine dans Azure

Tout d'abord, vous devez remplir la colonne du **nom de la machine virtuelle** du tableau M et modifier les tailles de machine virtuelle selon vos besoins dans la colonne **Taille minimale**.
  
|**Élément**|**Nom de la machine virtuelle**|**Image de la galerie**|**Type de stockage**|**Taille minimale**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![ligne](./media/Common-Images/TableLine.png)  (premier contrôleur de domaine, par exemple DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![ligne](./media/Common-Images/TableLine.png)  (deuxième contrôleur de domaine, par exemple DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![ligne](./media/Common-Images/TableLine.png) (serveur de synchronisation d’annuaires, exemple DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![ligne](./media/Common-Images/TableLine.png) (premier serveur AD FS, exemple ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![ligne](./media/Common-Images/TableLine.png) (deuxième serveur AD FS, exemple ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![ligne](./media/Common-Images/TableLine.png) (premier serveur proxy d’application Web, exemple WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![ligne](./media/Common-Images/TableLine.png) (deuxième serveur proxy d’application Web, exemple WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tableau M-machines virtuelles pour l’authentification fédérée haute disponibilité pour Microsoft 365 dans Azure**
  
Pour obtenir la liste complète des tailles de machine virtuelle, reportez-vous à la rubrique [Tailles des machines virtuelles Windows dans Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).
  
Le bloc de commandes Azure PowerShell suivant permet de créer les machines virtuelles pour les deux contrôleurs de domaine. Spécifiez les valeurs des variables, en supprimant les \< and > caractères. Notez que ce bloc de commandes Azure PowerShell utilise des valeurs provenant des tableaux suivants :
  
- Tableau M, pour vos machines virtuelles
    
- Tableau R, pour vos groupes de ressources
    
- Tableau V, pour vos paramètres de réseau virtuel
    
- Tableau S, pour vos sous-réseaux
    
- Tableau I, pour vos adresses IP statiques
    
- Tableau A, pour vos groupes à haute disponibilité
    
Rappelez-vous que vous avez défini les tableaux R, V, S, I et A à la [phase 1 : configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> [!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Consultez la rubrique [prise en main d’Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps). 
  
Lorsque vous avez indiqué toutes les valeurs correctes, exécutez le bloc résultant à l’invite de commandes Azure PowerShell ou dans l’environnement d'écriture de scripts intégré de Windows PowerShell (ISE) sur votre ordinateur local.
  
> [!TIP]
> Pour générer des blocs de commandes PowerShell prêts à l’emploi en fonction de vos paramètres personnalisés, utilisez ce [classeur de configuration Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.
  
## <a name="configure-the-first-domain-controller"></a>Configurer le premier contrôleur de domaine

Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
Ensuite, ajoutez le disque de données supplémentaire au premier contrôleur de domaine à l’aide de cette commande à partir d’une invite de commandes Windows PowerShell **sur la première machine virtuelle du contrôleur de domaine**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ensuite, testez la connectivité du premier contrôleur de domaine vers des emplacements du réseau de votre organisation à l'aide de la commande **ping** pour effectuer un test ping des noms et des adresses IP des ressources du réseau de votre organisation.
  
This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.
  
Ensuite, à partir de l’invite de commandes Windows PowerShell sur le premier contrôleur de domaine, exécutez les commandes suivantes :
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
## <a name="configure-the-second-domain-controller"></a>Configurer le deuxième contrôleur de domaine

Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
Ensuite, vous devez ajouter le disque de données supplémentaire au deuxième contrôleur de domaine à l’aide de cette commande à partir d’une invite de commandes Windows PowerShell **sur la deuxième machine virtuelle du contrôleur de domaine**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ensuite, exécutez les commandes suivantes :
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
Ensuite, vous devez mettre à jour les serveurs DNS pour votre réseau virtuel afin que Azure affecte aux machines virtuelles les adresses IP des deux nouveaux contrôleurs de domaine à utiliser comme serveurs DNS. Renseignez les variables, puis exécutez ces commandes à partir d’une invite de commandes Windows PowerShell sur votre ordinateur local :
  
```powershell
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

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.
  
Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Configurer le serveur de synchronisation d’annuaires

Utilisez le client Bureau à distance de votre choix et créez une connexion de bureau à distance à la machine virtuelle du serveur de synchronisation d’annuaires. Utilisez son nom d'ordinateur ou son nom DNS intranet et les informations d'identification du compte Administrateur local.
  
Ensuite, associez-le au domaine AD DS approprié à l’aide de ces commandes à l’invite Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.
  
**Phase 2 : les contrôleurs de domaine et le serveur de synchronisation d’annuaires pour votre infrastructure d’authentification fédérée haute disponibilité dans Azure**

![Phase 2 de l’infrastructure d’authentification fédérée haute disponibilité Microsoft 365 dans Azure avec contrôleurs de domaine](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Étape suivante

Utilisez la [phase 3 : configurer les serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) pour poursuivre la configuration de cette charge de travail.
  
## <a name="see-also"></a>Voir aussi

[Déployer une authentification fédérée haute disponibilité pour Microsoft 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identité fédérée pour votre environnement de développement/test Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.yml)


