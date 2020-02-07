---
title: Authentification fédérée haute disponibilité, phase 1 configurer Azure
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Résumé : configurez l’infrastructure Microsoft Azure pour qu’elle héberge l’authentification fédérée haute disponibilité pour Office 365.'
ms.openlocfilehash: c669df7e719d8ff8516ad556817921e1440558d3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840341"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Authentification fédérée haute disponibilité, phase 1 : Configurer Azure

Dans cette phase, vous créez les groupes de ressources, le réseau virtuel et les groupes à haute disponibilité dans Azure qui hébergeront les machines virtuelles dans les phases 2, 3 et 4. Vous devez effectuer cette phase avant de passer à la [phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Reportez-vous à la rubrique [Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.
  
Azure doit être mis en service avec ces composants de base :
  
- Groupes de ressources
    
- Un réseau virtuel Azure entre différents locaux avec des sous-réseaux pour l’hébergement des machines virtuelles Azure
    
- Groupes de sécurité réseau pour effectuer l'isolation des sous-réseaux
    
- Groupes à haute disponibilité
    
## <a name="configure-azure-components"></a>Configurer les composants Azure

Avant de commencer à configurer les composants Azure, renseignez les tableaux suivants. Pour vous aider dans les procédures de configuration Azure, imprimez cette section et notez les informations nécessaires ou copiez cette section dans un document et remplissez-le. Pour les paramètres du réseau virtuel, remplissez le tableau V.
  
|**Item**|**Paramètre de configuration**|**Description**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nom du réseau virtuel  <br/> |Nom à attribuer au réseau virtuel (exemple FedAuthNet).  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Emplacement du réseau virtuel  <br/> |Le centre de centres Azure régional qui contiendra le réseau virtuel.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adresse IP du périphérique VPN  <br/> |Adresse IPv4 publique de l'interface de votre périphérique VPN sur Internet.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Espace d'adressage du réseau virtuel  <br/> |Espace d'adressage du réseau virtuel. Renseignez-vous auprès de votre service informatique pour déterminer cet espace d'adressage.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Clé partagée IPsec  <br/> |Chaîne alphanumérique aléatoire de 32 caractères, utilisée pour authentifier les deux côtés de la connexion VPN de site à site. Renseignez-vous auprès de votre service informatique ou de sécurité pour déterminer cette valeur de clé. Vous pouvez également consulter la page relative à la [création d'une chaîne aléatoire pour une clé prépartagée IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tableau V : configuration de réseau virtuel entre différents locaux**
  
Remplissez ensuite le Tableau S pour les sous-réseaux de cette solution. Tous les espaces d'adressage doivent être au format de routage CIDR (Classless Interdomain Routing), également appelé format de préfixe de réseau. Par exemple, 10.24.64.0/20.
  
Pour les trois premiers sous-réseaux, spécifiez un nom et un espace d’adressage IP unique en fonction de l’espace d’adressage du réseau virtuel. Pour le sous-réseau de passerelle, déterminez l’espace d’adressage 27 bits (avec une longueur de préfixe de/27) pour le sous-réseau de passerelle Azure avec les éléments suivants :
  
1. Définissez la variable bits de l'espace d'adressage du réseau virtuel sur 1, jusqu'aux bits utilisés par le sous-réseau de passerelle, puis définissez les autres sur 0.
    
2. Convertissez les bits résultants en nombres décimaux et exprimez-les sous forme d'espace d'adressage, en définissant la longueur du préfixe sur une valeur équivalente à la taille du sous-réseau de passerelle.
    
Voir [calculatrice d’espace d’adressage pour les sous-réseaux de la passerelle Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) pour un bloc de commandes PowerShell et une application de consoles C# ou python qui effectue ce calcul pour vous.
  
Renseignez-vous auprès de votre service informatique pour déterminer ces espaces d'adressage à partir de l'espace d'adressage de réseau virtuel.
  
|**Élément**|**Nom du sous-réseau**|**Espace d'adressage de sous-réseau**|**Objectif**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Le sous-réseau utilisé par le contrôleur de domaine des services de domaine Active Directory (AD DS) et les machines virtuelles du serveur de synchronisation d’annuaires.  <br/> |
|2.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Sous-réseau utilisé par les machines virtuelles AD FS.  <br/> |
|3.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Sous-réseau utilisé par les machines virtuelles de proxy d’application Web.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Le sous-réseau utilisé par les machines virtuelles de la passerelle Azure.  <br/> |
   
 **Tableau S : sous-réseaux dans le réseau virtuel**
  
Ensuite, renseignez le Tableau I pour les adresses IP statiques affectées à des machines virtuelles et à des instances d'équilibreur de charge.
  
|**Élément**|**Objectif**|**Adresse IP sur le sous-réseau**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Adresse IP statique du premier contrôleur de domaine  <br/> |La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 1 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Adresse IP statique du deuxième contrôleur de domaine  <br/> |La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 1 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adresse IP statique du serveur de synchronisation d’annuaires  <br/> |La sixième adresse IP possible pour l’espace d’adressage du sous-réseau défini dans l’élément 1 du tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Adresse IP statique de l’équilibreur de charge interne pour les serveurs AD FS  <br/> |La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Adresse IP statique du premier serveur AD FS  <br/> |La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Adresse IP statique du deuxième serveur AD FS  <br/> |La sixième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Adresse IP statique du premier serveur proxy d’application Web  <br/> |La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 3 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Adresse IP statique du deuxième serveur proxy d’application Web  <br/> |La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 3 du Tableau S.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tableau I : Adresses IP statiques dans le réseau virtuel**
  
Pour les deux serveurs DNS (Domain Name System) de votre réseau local que vous souhaitez utiliser lors de la configuration initiale des contrôleurs de domaine de votre réseau virtuel, renseignez le tableau D. collaborez avec votre service informatique pour déterminer cette liste.
  
|**Item**|**Nom convivial du serveur DNS**|**Adresse IP du serveur DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tableau D : serveurs DNS locaux**
  
Pour acheminer les paquets à partir du réseau intersites vers le réseau de votre organisation à travers la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local disposant d’une liste des espaces d’adressage (en notation CIDR) pour toutes les connexions accessibles. emplacements sur le réseau local de votre organisation. La liste des espaces d'adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec l'espace d'adressage utilisé pour d'autres réseaux virtuels ou d'autres réseaux locaux.
  
Pour l'ensemble des espaces d'adressage du réseau local, remplissez le tableau L. Notez que le tableau comporte trois entrées vides, mais vous aurez généralement besoin d'en ajouter. Renseignez-vous auprès de votre service informatique pour déterminer cette liste d'espaces d'adressage.
  
|**Élément**|**Espace d'adressage du réseau local**|
|:-----|:-----|
|1.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tableau L : préfixes d'adresse pour le réseau local**
  
Commençons à présent à créer l’infrastructure Azure pour héberger votre authentification fédérée pour Office 365.
  
> [!NOTE]
> [!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Consultez la rubrique [prise en main d’Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps). 
  
Tout d'abord, démarrez une invite PowerShell Azure et connectez-vous à votre compte.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Pour générer des blocs de commandes PowerShell prêts à l’emploi en fonction de vos paramètres personnalisés, utilisez ce [classeur de configuration Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx). 

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Pour les versions antérieures d’Azure PowerShell, utilisez cette commande à la place.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Définissez votre abonnement Azure. Remplacez tout le texte entre guillemets, \< y compris les caractères et >, par le nom correct.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ensuite, créez les groupes de ressources. Pour déterminer un ensemble unique de noms de groupes de ressources, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Renseignez le tableau suivant pour l'ensemble unique de noms de groupes de ressources.
  
|**Élément**|**Nom de groupe de ressources**|**Objectif**|
|:-----|:-----|:-----|
|1.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Contrôleurs de domaine  <br/> |
|2.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Serveurs AD FS  <br/> |
|3.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Serveurs proxy d’application Web  <br/> |
|4.  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |Éléments de l'infrastructure  <br/> |
   
 **Tableau R : Groupes de ressources**
  
Créez vos nouveaux groupes de ressources avec ces commandes.
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ensuite, vous créez le réseau virtuel Azure et ses sous-réseaux.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Ensuite, créez des groupes de sécurité réseau pour chaque sous-réseau qui a des machines virtuelles. Pour isoler des sous-réseaux, vous pouvez ajouter des règles pour certains types de trafic autorisés ou refusés vers le groupe de sécurité d'un sous-réseau.
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> L’authentification fédérée d’utilisateurs individuels n’utilise aucune ressource locale. Toutefois, si cette connexion VPN de site à site devient indisponible, les contrôleurs de domaine dans le réseau virtuel ne recevront pas les mises à jour des comptes d’utilisateur et des groupes créés dans les services de domaine Active Directory locaux. Pour éviter ce problème, vous pouvez configurer une haute disponibilité pour votre connexion VPN de site à site. Pour plus d'informations, reportez-vous à l'article [Configuration haute disponibilité pour la connectivité entre les réseaux locaux et la connectivité entre deux réseaux virtuels](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Ensuite, enregistrez l'adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel à partir de l'affichage de cette commande :
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Ensuite, configurez votre périphérique VPN local de sorte qu'il se connecte à la passerelle VPN Azure. Pour plus d'informations, reportez-vous à la rubrique [À propos des périphériques VPN pour les connexions de la passerelle VPN de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Pour configurer votre périphérique VPN local, vous avez besoin des éléments suivants :
  
- L'adresse IPv4 publique de la passerelle VPN Azure.
    
- La clé prépartagée IPsec pour la connexion VPN de site à site (Tableau V - Élément 5 - colonne Valeur).
    
Ensuite, vérifiez que l'espace d'adressage du réseau virtuel est accessible à partir de votre réseau local. Pour cela, il convient généralement d'ajouter un chemin de routage correspondant à l'espace d'adressage du réseau virtuel à votre périphérique VPN puis d'annoncer ce chemin de routage au reste de l'infrastructure de routage du réseau de votre organisation. Renseignez-vous auprès de votre service informatique pour savoir comment procéder.
  
Ensuite, définissez les noms de trois groupes à haute disponibilité. Remplissez le Tableau A. 
  
|**Élément**|**Objectif**|**Nom du groupe de disponibilité**|
|:-----|:-----|:-----|
|1.  <br/> |Contrôleurs de domaine  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Serveurs AD FS  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Serveurs proxy d’application Web  <br/> |![ligne](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tableau A : Groupes de disponibilité**
  
Vous aurez besoin de ces noms lorsque vous créerez les machines virtuelles aux phases 2, 3 et 4.
  
Créez les nouveaux groupes de disponibilité avec ces commandes Azure PowerShell.
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

Voici la configuration obtenue à la fin de cette phase.
  
**Phase 1 : l’infrastructure Azure pour l’authentification fédérée haute disponibilité pour Office 365**

![Phase 1 de l’authentification fédérée Office 365 à haute disponibilité dans Azure avec l’infrastructure Azure](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Étape suivante

Utilisez la [phase 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) pour poursuivre la configuration de cette charge de travail.
  
## <a name="see-also"></a>Voir aussi

[Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Présentation de l’identité Office 365 et d’Azure Active Directory](about-office-365-identity.md)


