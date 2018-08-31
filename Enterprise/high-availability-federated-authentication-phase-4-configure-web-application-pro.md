---
title: Haute disponibilité fédérés proxys d’application web Phase 4 configurer l’authentification
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Résumé : Configurez les serveurs de proxy d’application web pour l’authentification fédérée de haute disponibilité pour Office 365 dans Microsoft Azure.'
ms.openlocfilehash: 0f0299fe8fecdea608330eebc12aea01098f8cec
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915809"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Authentification fédérée haute disponibilité, phase 4 : Configurer les proxys d’application web

 **Résumé :** Configurer les serveurs de proxy d’application web pour l’authentification fédérée de haute disponibilité pour Office 365 dans Microsoft Azure.
  
Au cours de cette phase du déploiement de la haute disponibilité pour l’authentification fédérée Office 365 dans les services d’infrastructure Azure, vous avez créé un équilibreur de charge interne et deux serveurs AD FS.
  
Vous devez effectuer cette phase avant de passer à [haute disponibilité fédérés authentification Phase 5 : configurer l’authentification fédérée pour Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Voir [authentification fédérée de déploiement haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Créer l’équilibreur de charge connecté à Internet dans Azure

Vous devez créer un équilibreur de charge connecté à Internet pour permettre à Azure de répartir équitablement le trafic d’authentification client entrant à partir d’Internet sur les deux serveurs proxy d’application web.
  
> [!NOTE]
> Les ensembles de commandes suivants utilisent la dernière version d’Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Une fois que vous avez indiqué les valeurs d’emplacement et de groupe de ressources, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.
  
> [!TIP]
> Pour un fichier texte qui contient toutes les commandes PowerShell dans cet article et un classeur Microsoft Excel configuration qui génère des blocs de commande PowerShell prête à exécuter en fonction de vos paramètres personnalisés, voir l’authentification fédérée pour Office 365 [dans Kit de déploiement Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
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

Pour afficher l’adresse IP publique affectée à votre équilibreur de charge connecté à Internet, exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local :
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Déterminer le nom de domaine complet de votre service de fédération et créer des enregistrements DNS

Vous devez déterminer le nom DNS pour identifier le nom de votre service de fédération sur Internet. Azure AD Connect configure Office 365 avec ce nom au cours de la Phase 5 pour qu’il fasse partie de l’URL envoyée par Office 365 aux clients qui se connectent pour obtenir un jeton de sécurité. Ce nom est, par exemple, fs.contoso.com (fs signifie federation service : service de fédération).
  
Une fois que le nom de domaine complet du service de fédération a été obtenu, créez un enregistrement DNS de domaine public A pour le nom de domaine complet pour le résoudre en adresse IP publique de l’équilibreur de charge Azure connecté à Internet.
  
|**Nom**|**Type**|**TTL**|**Valeur**|
|:-----|:-----|:-----|:-----|
|Nom de domaine complet du service de fédération  <br/> |A  <br/> |3600  <br/> |adresse IP publique de l’équilibreur de charge Azure connecté à Internet (affiché par la commande **Write-Host** dans la section précédente) <br/> |
   
Voici un exemple :
  
|**Nom**|**Type**|**TTL**|**Valeur**|
|:-----|:-----|:-----|:-----|
|FS.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Ensuite, ajoutez un enregistrement d’adresse DNS à l’espace de noms DNS privé de votre organisation pour résoudre le nom de domaine complet de votre service de fédération en adresse IP privée affectée à l’équilibreur de charge interne pour les serveurs AD FS (tableau I, élément 4, colonne Valeur).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Créer les machines virtuelles des serveurs proxy d’application web dans Azure

Utilisez le bloc de commandes Azure PowerShell suivant pour créer les machines virtuelles pour les deux serveurs proxy d’application web.  
  
Notez que l’ensemble de commandes Azure PowerShell suivant utilise des valeurs provenant des tableaux suivants :
  
- Tableau M, pour vos machines virtuelles
    
- Tableau R, pour vos groupes de ressources
    
- Tableau V, pour vos paramètres de réseau virtuel
    
- Tableau S, pour vos sous-réseaux
    
- Tableau I, pour vos adresses IP statiques
    
- Tableau A, pour vos groupes à haute disponibilité
    
Rappelez-vous que vous avez défini le tableau M dans [haute disponibilité fédérés authentification Phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) et Tables R, V, S, I et dans [haute disponibilité fédérés authentification Phase 1 : Azure configurer](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Lorsque vous avez fourni toutes les valeurs correctes, exécutez le bloc obtenu à l’invite de commandes Azure PowerShell ou dans le PowerShell ISE.
  
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
> Étant donné que ces machines virtuelles sont pour une application intranet, aucune adresse IP publique ni étiquette de nom de domaine DNS ne leur est affectée et elles ne sont pas connectées à Internet. Toutefois, vous ne pouvez pas vous y connecter à partir du portail Azure. L’option **Se connecter** n’est pas disponible lorsque vous affichez les propriétés de la machine virtuelle. Utilisez l’accessoire de connexion Bureau à distance ou un autre outil de Bureau à distance pour vous connecter à la machine virtuelle à l’aide de son adresse IP privée ou de son nom DNS intranet, ainsi que les informations d’identification du compte Administrateur local.
  
Lorsque cette phase est terminée, voici la configuration résultante, avec les noms d’ordinateur de l’espace réservé.
  
**Phase 4 : L’équilibreur de charge connecté à Internet et les serveurs proxy d’application web de votre infrastructure d’authentification fédérée haute disponibilité dans Azure**

![Phase 4 de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure à l’aide des serveurs proxy d’application web](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Étape suivante

Utilisez [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) pour poursuivre la configuration de cette charge de travail.
  
## <a name="see-also"></a>Voir aussi

[Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Options d’authentification fédérée](about-office-365-identity.md#federated-authentication-options)


