---
title: "Authentification fédérée haute disponibilité Azure de configurer Phase 1"
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Résumé : Configurer l’infrastructure de Microsoft Azure à haute disponibilité de l’hôte l’authentification fédérée pour Office 365."
ms.openlocfilehash: fed6b24af2ba54bef95be22641fd140f7c1be717
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Authentification fédérée haute disponibilité, phase 1 : Configurer Azure

 **Résumé :** Configurer l’infrastructure de Microsoft Azure pour authentifier les hôtes haute disponibilité fédérée pour Office 365.
  
Dans cette phase, vous créez les groupes de ressources, les comptes de stockage, les jeux virtuels de réseau (VNet) et la disponibilité dans Azure qui hébergera les ordinateurs virtuels dans les phases 2, 3 et 4. Vous devez terminer cette phase avant de passer à [haute disponibilité fédérés d’authentification Phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Pour toutes les phases, reportez-vous à la section [authentification fédérée de haute disponibilité déploiement pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .
  
Azure doit être configurée avec les composants de base :
  
- Groupes de ressources
    
- Un réseau virtuel Azure intersites (VNet) avec des sous-réseaux pour l’hébergement des machines virtuelles Azure
    
- Groupes de sécurité réseau pour effectuer l’isolation des sous-réseaux
    
- Groupes à haute disponibilité
    
## <a name="configure-azure-components"></a>Configurer les composants Azure

Avant de commencer la configuration des composants d’Azure, renseignez les tableaux ci-dessous. Pour vous aider dans les procédures de configuration d’Azure, imprimer cette section et notez les informations nécessaires ou copier cette section à un document et le remplir. Pour les paramètres de le VNet, indiquez dans le tableau V.
  
|**Élément**|**Paramètre de configuration**|**Description**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nom du réseau virtuel  <br/> |Un nom à attribuer au réseau virtuel (exemple FedAuthNet).  <br/> |_______________________________  <br/> |
|2.  <br/> |Emplacement de VNet  <br/> |Le centre de données Azure régional qui contiendra le réseau virtuel.  <br/> |_______________________________  <br/> |
|3.  <br/> |Adresse IP du périphérique VPN  <br/> |Adresse IPv4 publique de l’interface de votre périphérique VPN sur Internet.   <br/> |_______________________________  <br/> |
|4.  <br/> |Espace d’adressage du réseau virtuel  <br/> |Espace d’adressage du réseau virtuel. Renseignez-vous auprès de votre service informatique pour déterminer cet espace d’adressage.  <br/> |_______________________________  <br/> |
|5.  <br/> |Clé partagée IPsec  <br/> |32 caractères alphanumérique, aléatoire chaîne qui sera utilisée pour authentifier les deux côtés de la connexion VPN de site à site. Fonctionne avec votre service informatique ou un service de sécurité afin de déterminer la valeur de cette clé. Alternativement, consultez [créer une chaîne aléatoire pour une clé pré-partagée IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).<br/> |_______________________________  <br/> |
   
 **Tableau V : configuration de réseau virtuel entre différents locaux**
  
Remplissez ensuite le Tableau S pour les sous-réseaux de cette solution. Tous les espaces d’adressage doivent être au format de routage CIDR (Classless Interdomain Routing), également appelé format de préfixe de réseau. Par exemple, 10.24.64.0/20.
  
Pour les trois premiers sous-réseaux, indiquez un nom et un espace d’adressage IP unique fondé sur l’espace d’adressage de réseau virtuel. Pour le sous-réseau de passerelle, déterminez l’espace d’adressage 27 bits (avec une longueur de préfixe de /27) pour le sous-réseau de passerelle Azure en procédant comme suit :
  
1. Définissez la variable bits de l’espace d’adressage du réseau virtuel sur 1, jusqu’aux bits utilisés par le sous-réseau de passerelle, puis définissez les autres sur 0.
    
2. Convertissez les bits résultants en nombres décimaux et exprimez-les sous forme d’espace d’adressage, en définissant la longueur du préfixe sur une valeur équivalente à la taille du sous-réseau de passerelle.
    
Consultez le [calculateur d’espace adresse des sous-réseaux de la passerelle Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) pour un bloc de commande PowerShell et une application de console C# ou Python qui effectue ce calcul pour vous.
  
Renseignez-vous auprès de votre service informatique pour déterminer ces espaces d’adressage à partir de l’espace d’adressage de réseau virtuel.
  
|**Élément**|**Nom du sous-réseau**|**Espace d'adressage de sous-réseau**|**Objectif**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Le sous-réseau utilisé par le contrôleur de domaine Windows Server Active Directory (AD) et les machines virtuelles du serveur DirSync.  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Le sous-réseau utilisé par les machines virtuelles AD FS.  <br/> |
|3.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Le sous-réseau utilisé par les machines virtuelles du proxy d’application web.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |_______________________________  <br/> |Sous-réseau utilisé par les machines virtuelles de la passerelle Azure.  <br/> |
   
 **Tableau S : sous-réseaux dans le réseau virtuel**
  
Ensuite, renseignez le Tableau I pour les adresses IP statiques affectées à des machines virtuelles et à des instances d’équilibreur de charge.
  
|**Élément**|**Objectif**|**Adresse IP du sous-réseau**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Adresse IP statique du premier contrôleur de domaine  <br/> |La quatrième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 1 du Tableau S.  <br/> |_______________________________  <br/> |
|2.  <br/> |Adresse IP statique du deuxième contrôleur de domaine  <br/> |La cinquième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 1 du Tableau S.  <br/> |_______________________________  <br/> |
|3.  <br/> |Adresse IP statique du serveur DirSync  <br/> |La sixième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 1 du Tableau S.   <br/> |_______________________________  <br/> |
|4.  <br/> |Adresse IP statique de l’équilibreur de charge interne des serveurs AD FS  <br/> |La quatrième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 2 du Tableau S.  <br/> |_______________________________  <br/> |
|5.  <br/> |Adresse IP statique du premier serveur AD FS  <br/> |La cinquième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 2 du Tableau S.  <br/> |_______________________________  <br/> |
|6.  <br/> |Adresse IP statique du deuxième serveur AD FS  <br/> |La sixième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 2 du Tableau S.  <br/> |_______________________________  <br/> |
|7.  <br/> |Adresse IP statique du premier serveur proxy d’application web  <br/> |La quatrième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 3 du Tableau S.  <br/> |_______________________________  <br/> |
|8.  <br/> |Adresse IP statique du deuxième serveur proxy d’application web  <br/> |La cinquième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’Élément 3 du Tableau S.  <br/> |_______________________________  <br/> |
   
 **Table i : statique adresses du réseau virtuel**
  
Pour deux serveurs DNS (Domain Name System) de votre réseau local que vous souhaitez utiliser lors de la configuration initiale des contrôleurs de domaine dans votre réseau virtuel, renseignez le tableau D. Renseignez-vous auprès de votre service informatique pour déterminer cette liste.
  
|**Élément**|**Nom convivial du serveur DNS**|**Adresse IP du serveur DNS**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
   
 **Tableau D : serveurs DNS locaux**
  
Pour acheminer les paquets du réseau virtuel intersites vers le réseau de votre organisation par le biais de la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local qui contient la liste des espaces d’adressage (utilisant la notation CIDR) pour l’ensemble des emplacements qui doivent être atteints sur le réseau local de votre organisation. La liste des espaces d’adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec l’espace d’adressage utilisé pour d’autres réseaux virtuels ou d’autres réseaux locaux.
  
Pour l’ensemble des espaces d’adressage du réseau local, remplissez le tableau L. Notez que le tableau comporte trois entrées vides, mais vous aurez généralement besoin d’en ajouter. Renseignez-vous auprès de votre service informatique pour déterminer cette liste d’espaces d’adressage.
  
|**Élément**|**Espace d'adressage du réseau local**|
|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |
|3.  <br/> |_______________________________  <br/> |
   
 **Tableau L : préfixes d'adresse pour le réseau local**
  
Commençons à présent à créer l’infrastructure Azure pour héberger votre authentification fédérée pour Office 365.
  
> [!NOTE]
> La commande suivante définit utiliser la dernière version de PowerShell d’Azure. Reportez-vous à la section [mise en route avec les applets de commande PowerShell d’Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Tout d’abord, démarrez une invite PowerShell Azure et connectez-vous à votre compte.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Pour un fichier texte qui contient toutes les commandes de PowerShell dans cet article et un classeur Microsoft Excel configuration qui génère des blocs de commande PowerShell prête à exécuter en fonction de vos paramètres personnalisés, consultez la [l’authentification fédérée pour Office 365 dans Kit de déploiement d’Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
Obtenez le nom de votre abonnement à l'aide de la commande suivante.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Pour les versions antérieures de PowerShell d’Azure, utilisez plutôt cette commande.
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

Définissez votre abonnement Azure. Remplacez tout entre guillemets, y compris la \< et > caractères, avec le nom correct.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Ensuite, vous allez créer les nouveaux groupes de ressources. Pour déterminer un ensemble unique de noms de groupes de ressources, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Renseignez le tableau suivant pour l’ensemble unique de noms de groupes de ressources.
  
|**Élément**|**Nom du groupe de ressources**|**Objectif**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |Contrôleurs de domaine  <br/> |
|2.  <br/> |_______________________________  <br/> |Serveurs AD FS  <br/> |
|3.  <br/> |_______________________________  <br/> |Serveurs proxy d’application web  <br/> |
|4.  <br/> |_______________________________  <br/> |Éléments de l’infrastructure  <br/> |
   
 **Table R: les groupes de ressources**
  
Créez vos nouveaux groupes de ressources avec ces commandes.
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Créez ensuite le réseau virtuel Azure et ses sous-réseaux.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Ensuite, vous créez le réseau pour chaque sous-réseau contenant des ordinateurs virtuels, les groupes de sécurité. Pour effectuer l’isolation de sous-réseau, vous pouvez ajouter des règles pour les types spécifiques de trafic autorisé ou refusé au groupe de sécurité réseau d’un sous-réseau.
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Authentification fédérée des utilisateurs individuels ne repose pas sur toutes les ressources locales. Toutefois, si cette connexion VPN de site à site devient indisponible, les contrôleurs de domaine dans le VNet ne recevront pas les mises à jour des comptes d’utilisateurs et de groupes dans l’Active Directory du serveur Windows local. Pour vous assurer que cela ne se produit pas, vous pouvez configurer la haute disponibilité pour votre connexion VPN de site à site. Pour plus d’informations, reportez-vous à la section [hautement disponible coexistence et VNet à VNet connectivité](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Ensuite, enregistrez l’adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel à partir de l’affichage de cette commande :
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Ensuite, configurez votre périphérique VPN local pour se connecter à la passerelle VPN d’Azure. Pour plus d’informations, voir [configurer l’appareil VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Pour configurer votre périphérique VPN local, vous avez besoin des éléments suivants :
  
- L’adresse IPv4 publique de la passerelle VPN Azure.
    
- La clé pré-partagée IPsec pour la connexion VPN de site à site (colonne de Table V - article 5 - valeur).
    
Ensuite, vérifiez que l’espace d’adressage du réseau virtuel est accessible à partir de votre réseau local. Pour cela, il convient généralement d’ajouter un chemin de routage correspondant à l’espace d’adressage du réseau virtuel à votre périphérique VPN puis d’annoncer ce chemin de routage au reste de l’infrastructure de routage du réseau de votre organisation. Renseignez-vous auprès de votre service informatique pour savoir comment procéder.
  
Ensuite, définissez les noms des trois groupes de disponibilité. Remplissez le Tableau A.  
  
|**Élément**|**Objectif**|**Nom du jeu de disponibilité**|
|:-----|:-----|:-----|
|1.  <br/> |Contrôleurs de domaine  <br/> |_______________________________  <br/> |
|2.  <br/> |Serveurs AD FS  <br/> |_______________________________  <br/> |
|3.  <br/> |Serveurs proxy d’application web  <br/> |_______________________________  <br/> |
   
 **Jeux de table a : disponibilité**
  
Vous aurez besoin de ces noms lorsque vous créerez les machines virtuelles aux phases 2, 3 et 4.
  
Créez les nouveaux groupes de disponibilité avec ces commandes Azure PowerShell.
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

Voici la configuration obtenue à la fin de cette phase.
  
**Phase 1 : Infrastructure Azure pour l’authentification fédérée de haute disponibilité pour Office 365**

![Phase 1 de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure à l’aide de l’infrastructure Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Étape suivante

Utilisation [haute disponibilité fédérés d’authentification Phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) pour poursuivre la configuration de cette charge de travail.
  
## <a name="see-also"></a>See Also

[Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Identité fédérée pour Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


