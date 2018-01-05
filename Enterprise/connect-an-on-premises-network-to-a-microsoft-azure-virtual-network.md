---
title: "Connecter un réseau local à Microsoft Azure Virtual Network"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "Résumé : Découvrez comment configurer un réseau virtuel Azure intersites pour les charges de travail de serveur Office."
ms.openlocfilehash: 83e5842a4b3192ee2f65048cefe57790cd1e2341
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Connecter un réseau local à Microsoft Azure Virtual Network

 **Résumé :** Découvrez comment configurer un réseau virtuel Azure intersites pour les charges de travail de serveur Office.
  
Un réseau virtuel Azure entre différents locaux est connecté à votre réseau local, étendant ainsi votre réseau pour inclure des sous-réseaux et machines virtuelles hébergés dans les services d'infrastructure Azure. Cette connexion permet aux ordinateurs de votre réseau local d'accéder directement aux machines virtuelles dans Azure et inversement. Par exemple, un serveur DirSync en cours d'exécution sur une machine virtuelle Azure doit interroger vos contrôleurs de domaine locaux pour apporter des modifications aux comptes et synchroniser ces modifications avec votre abonnement Office 365. Cet article vous explique comment configurer un réseau virtuel Azure prêt à héberger des machines virtuelles Azure.
  
Contenu de cet article :
  
- [Vue d'ensemble](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [Planification de votre réseau Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [Feuille de route de déploiement](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## <a name="overview"></a>Vue d’ensemble
<a name="Overview"> </a>

Vos machines virtuelles dans Azure n'ont pas besoin d'être isolées de votre environnement local. Pour connecter des machines virtuelles Azure à des ressources réseau locales, vous devez configurer un réseau virtuel Azure local. Le diagramme suivant montre les composants requis pour déployer un réseau virtuel Azure entre différents locaux avec une machine virtuelle dans Azure.
  
![Réseau local connecté à Microsoft Azure via une connexion VPN de site à site](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
Dans le diagramme, il existe deux réseaux connectés via une connexion de réseau privé virtuel (VPN) de site à site : le réseau local et le réseau virtuel Azure. La connexion VPN de site à site se termine par un périphérique VPN sur le réseau local et par une passerelle VPN Azure sur le réseau virtuel Azure. Le réseau virtuel Azure dispose de machines virtuelles. Le trafic réseau provenant des machines virtuelles sur le réseau virtuel Azure est acheminé vers la passerelle VPN, laquelle transmet le trafic de la connexion VPN de site à site sur le périphérique VPN sur le réseau local. L'infrastructure de routage du réseau local transmet ensuite le trafic à sa destination.
  
Pour configurer la connexion VPN entre votre réseau Azure Virtual Network et votre réseau local, procédez comme suit : 
  
1. **Local :** Définissez et créez un itinéraire réseau local pour l'espace d'adressage du réseau virtuel Azure qui pointe vers votre périphérique VPN local.
    
2. **Microsoft Azure :** créez un réseau virtuel Azure avec une connexion VPN de site à site. Cet article ne décrit pas l'utilisation d'[ExpressRoute]((https://azure.microsoft.com/services/expressroute/)).
    
3. **Local :** Configurez votre périphérique VPN matériel ou logiciel local pour marquer la fin de la connexion VPN en utilisant la sécurité du protocole Internet (IPsec).
    
Après avoir établi la connexion VPN de site à site, vous ajoutez des machines virtuelles Azure aux sous-réseaux du réseau virtuel.
  
## <a name="plan-your-azure-virtual-network"></a>Planification de votre réseau Azure Virtual Network
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Conditions préalables
<a name="Prerequisites"> </a>

- Un abonnement Azure. Pour plus d'informations sur les abonnements Azure, accédez à la [page des abonnements Microsoft Azure]((https://azure.microsoft.com/pricing/purchase-options/)).
    
- Un espace d’adressage IPv4 privé disponible à affecter au réseau virtuel et à ses sous-réseaux, avec suffisamment d’espace pour leur croissance afin d’accueillir le nombre de machines virtuelles nécessaires maintenant et à l’avenir.
    
- Un périphérique VPN disponible dans votre réseau local pour marquer la fin de la connexion VPN de site à site qui prend en charge la configuration requise IPsec. Pour plus d'informations, voir [À propos des périphériques VPN pour les connexions de réseau virtuel de site à site](https://go.microsoft.com/fwlink/p/?LinkId=393093).
    
- La modification de votre infrastructure de routage pour que le trafic routé vers l'espace d'adressage du réseau virtuel Azure soit acheminé vers le périphérique VPN qui héberge la connexion VPN de site à site.
    
- Un proxy web fournissant un accès à Internet aux ordinateurs connectés au réseau local et au réseau virtuel Azure.
    
### <a name="solution-architecture-design-assumptions"></a>Hypothèses en matière de conception de l’architecture de la solution
<a name="DesignAssumptions"> </a>

La liste suivante répertorie les choix de conception qui ont été faits pour l'architecture de cette solution. 
  
- Cette solution utilise un seul réseau virtuel Azure avec une connexion VPN de site à site. Le réseau virtuel Azure héberge un sous-réseau unique qui contient plusieurs machines virtuelles. 
    
- Vous pouvez utiliser le service Routage et accès distant (RRAS) dans Windows Server 2016 ou Windows Server 2012 pour établir une connexion VPN de site à site IPsec entre le réseau local et le réseau virtuel Azure. Vous pouvez également utiliser d'autres options, telles que des périphériques VPN Cisco ou Juniper Networks.
    
- Le réseau local peut tout de même disposer de services réseau, tels que Windows Server Active Directory (AD), un système DNS (Domain Name System) et des serveurs proxy. Selon vos besoins, il peut être utile de placer certaines de ces ressources réseau dans le réseau virtuel Azure.
    
Pour un réseau virtuel Azure existant comportant un ou plusieurs sous-réseaux, déterminez s'il reste assez d'espace d'adressage pour qu'un sous-réseau supplémentaire puisse héberger les machines virtuelles dont vous avez besoin. Si vous n'avez pas assez d'espace d'adressage restant pour un sous-réseau supplémentaire, créez un réseau virtuel supplémentaire qui dispose de sa propre connexion VPN de site à site.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Planification des modifications d’infrastructure de routage pour le réseau virtuel Azure
<a name="routing"> </a>

Vous devez configurer votre infrastructure de routage locale pour acheminer le trafic destiné à l'espace d'adressage du réseau virtuel Azure au périphérique VPN local qui héberge la connexion VPN de site à site.
  
La méthode de mise à jour exacte de votre infrastructure de routage dépend de votre gestion des informations de routage, c’est-à-dire :
  
- Des mises à jour de la table de routage en fonction de la configuration manuelle.
    
- Des mises à jour de la table de routage en fonction des protocoles de routage, tels que le protocole RIP (Routing Information Protocol) ou le protocole OSPF (Open Shortest Path First).
    
Consultez votre spécialiste du routage pour vous assurer que le trafic destiné au réseau virtuel Azure est transféré au périphérique VPN local.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Planification des règles de pare-feu pour le trafic vers et depuis le périphérique VPN local
<a name="firewall"> </a>

Si votre périphérique VPN se trouve sur un réseau de périmètre qui dispose d’un pare-feu entre le réseau de périmètre et Internet, vous devrez peut-être configurer le pare-feu pour que les règles suivantes autorisent la connexion VPN de site à site.
  
- Trafic vers le périphérique VPN (entrant, à partir d’Internet) :
    
  - Adresse IP de destination du périphérique VPN et protocole IP 50
    
  - Adresse IP de destination du périphérique VPN et port 500 de destination UDP
    
  - Adresse IP de destination du périphérique VPN et port 4500 de destination UDP
    
- Trafic provenant du périphérique VPN (sortant, en direction d’Internet) :
    
  - Adresse IP source du périphérique VPN et protocole IP 50
    
  - Adresse IP source du périphérique VPN et port 500 source UDP
    
  - Adresse IP source du périphérique VPN et port 4500 source UDP
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Planification de l’espace d’adressage IP privé du réseau virtuel Azure
<a name="IPAddresses"> </a>

L'espace d'adressage IP privé du réseau virtuel Azure doit pouvoir prendre en charge les adresses utilisées par Azure pour héberger le réseau virtuel et au moins un sous-réseau disposant de suffisamment d'adresses pour vos machines virtuelles Azure.
  
Pour déterminer le nombre d’adresses nécessaires pour le sous-réseau, comptez le nombre de machines virtuelles dont vous avez besoin maintenant, estimez la croissance future, puis utilisez le tableau suivant pour déterminer la taille du sous-réseau.
  
|**Nombre de machines virtuelles nécessaires**|**Nombre de bits d'hôte requis**|**Taille du sous-réseau**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Planification de la feuille de travail pour la configuration de votre réseau virtuel Azure
<a name="worksheet"> </a>

Avant de créer un réseau virtuel Azure pour héberger des machines virtuelles, vous devez déterminer les paramètres nécessaires dans les tableaux suivants.
  
Pour les paramètres du réseau virtuel, remplissez le tableau V.
  
 **Tableau V : configuration de réseau virtuel entre différents locaux**
  
|**Élément**|**Élément Configuration**|**Description**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nom du réseau virtuel  <br/> |Nom à affecter au réseau virtuel Azure (par exemple, DirSyncNet).  <br/> |__________________  <br/> |
|2.  <br/> |Emplacement du réseau virtuel  <br/> |Centre de données Azure qui contiendra le réseau virtuel (par exemple, Ouest des États-Unis).  <br/> |__________________  <br/> |
|3.  <br/> |Adresse IP du périphérique VPN  <br/> |Adresse IPv4 publique de l’interface de votre périphérique VPN sur Internet. Renseignez-vous auprès de votre service informatique pour déterminer cette adresse.  <br/> |__________________  <br/> |
|4.  <br/> |Espace d’adressage du réseau virtuel  <br/> |Espace d’adressage (défini dans un préfixe d’adresse privée unique) pour le réseau virtuel. Renseignez-vous auprès de votre service informatique pour déterminer cet espace d’adressage. L’espace d’adressage doit être au format de routage CIDR (Classless Interdomain Routing), également appelé format de préfixe de réseau. Par exemple, 10.24.64.0/20.  <br/> |__________________  <br/> |
|5.  <br/> |Clé partagée IPsec  <br/> |Chaîne alphanumérique aléatoire de 32 caractères, qui sera utilisée pour authentifier les deux côtés de la connexion VPN de site à site. Renseignez-vous auprès de votre service informatique ou de sécurité pour déterminer la valeur de cette clé, puis stockez-la dans un emplacement sécurisé. Vous pouvez également consulter la page relative à la [création d'une chaîne aléatoire pour une clé prépartagée IPsec]((https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)).<br/> |__________________  <br/> |
   
Remplissez le tableau S pour les sous-réseaux de cette solution.
  
- Pour le premier sous-réseau, déterminez un espace d'adressage 28 bits (avec une longueur de préfixe de /28) pour le sous-réseau de passerelle Azure. Voir la rubrique sur le [calcul de l'espace d'adressage de sous-réseau de passerelle pour les réseaux virtuels Azure]((https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/)) pour savoir comment déterminer cet espace d'adressage.
    
- Pour le deuxième sous-réseau, indiquez un nom convivial, un espace d’adressage IP unique fondé sur l’espace d’adressage de réseau virtuel et une description de l’objectif.
    
Renseignez-vous auprès de votre service informatique pour déterminer ces espaces d’adressage à partir de l’espace d’adressage de réseau virtuel. Les deux espaces d’adressage doivent être au format CIDR.
  
 **Tableau S : sous-réseaux dans le réseau virtuel**
  
|**Élément**|**Nom du sous-réseau**|**Espace d'adressage de sous-réseau**|**Objectif**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |_____________________________  <br/> |Sous-réseau utilisé par la passerelle Azure.  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Concernant les serveurs DNS locaux qui doivent être utilisés par les machines virtuelles du réseau virtuel, remplissez le tableau D. Donnez un nom convivial et une adresse IP unique à chaque serveur DNS. Ce nom convivial n’a pas besoin de correspondre au nom d’hôte ou au nom de l’ordinateur du serveur DNS. Notez que le tableau comporte deux entrées vides, mais vous pouvez en ajouter d’autres. Renseignez-vous auprès de votre service informatique pour déterminer cette liste.
  
 **Tableau D : serveurs DNS locaux**
  
|**Élément**|**Nom convivial du serveur DNS**|**Adresse IP du serveur DNS**|
|:-----|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Pour acheminer les paquets du réseau virtuel Azure vers le réseau de votre organisation par le biais de la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local. Ce réseau local contient la liste des espaces d’adressage (au format CIDR) pour l’ensemble des emplacements sur le réseau local de votre organisation que les machines virtuelles du réseau virtuel doivent atteindre. Il peut s’agir de l’ensemble des emplacements sur le réseau local ou un sous-ensemble. La liste des espaces d’adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec les espaces d’adressage utilisés pour ce réseau virtuel ou vos autres réseaux virtuels entre différents locaux.
  
Pour l’ensemble des espaces d’adressage du réseau local, remplissez le tableau L. Notez que le tableau comporte trois entrées vides, mais vous aurez généralement besoin d’en ajouter. Renseignez-vous auprès de votre service informatique pour déterminer cette liste.
  
 **Tableau L : préfixes d'adresse pour le réseau local**
  
|**Élément**|**Espace d'adressage du réseau local**|
|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |
|3.  <br/> |_____________________________  <br/> |
   
## <a name="deployment-roadmap"></a>Feuille de route de déploiement
<a name="DeploymentRoadmap"> </a>

La création du réseau virtuel entre différents locaux et l'ajout de machines virtuelles dans Azure se composent de trois phases :
  
- Phase 1 : préparer votre réseau local.
    
- Phase 2 : créer le réseau virtuel entre différents locaux dans Azure.
    
- Phase 3 (facultative) : ajouter des machines virtuelles.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Phase 1 : préparer votre réseau local
<a name="Phase1"> </a>

Vous devez configurer votre réseau local avec un itinéraire qui pointe vers l’espace d’adressage du réseau virtuel et remet finalement le trafic qui y est destiné au routeur sur le périmètre du réseau local. Contactez votre administrateur réseau pour savoir comment ajouter l’itinéraire à l’infrastructure de routage de votre réseau local.
  
Voici la configuration finale.
  
![Le réseau local doit disposer d’un itinéraire pour l’espace d’adressage du réseau virtuel qui pointe vers l’appareil VPN.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Phase 2 : créer le réseau virtuel entre différents locaux dans Azure
<a name="Phase2"> </a>

Tout d'abord, ouvrez une invite PowerShell Azure. Si vous n'avez pas installé Azure PowerShell, reportez-vous à l'article sur la [prise en main des cmdlets Azure PowerShell]((https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)).
  
> [!NOTE]
> Ces commandes sont destinées à Azure PowerShell 1.0 et versions précédentes. Pour accéder à un fichier texte qui contient toutes les commandes PowerShell décrites dans cet article, cliquez [ici]((https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19)). 
  
Ensuite, connectez-vous à votre compte Azure avec cette commande.
  
```
Login-AzureRMAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

Définissez votre abonnement Azure avec les commandes suivantes. Remplacez tout le texte entre guillemets, y compris les caractères < et >, par le nom d’abonnement correct.
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

Ensuite, créez un nouveau groupe de ressources pour votre réseau virtuel. Pour déterminer un nom de groupe de ressources unique, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes.
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

Les machines virtuelles basées sur le gestionnaire des ressources requièrent un compte de stockage basé sur le gestionnaire des ressources. Vous devez choisir un nom global unique pour votre compte de stockage, contenant uniquement des lettres minuscules et des chiffres. Vous pouvez utiliser cette commande pour répertorier les comptes de stockage existants.
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

Utilisez cette commande pour vérifier si un nom proposé pour un compte de stockage est unique.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

Pour créer un nouveau compte de stockage, exécutez ces commandes.
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

Ensuite, créez le réseau virtuel Azure.
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )

# Get the shortened version of the location
$rg=Get-AzureRmResourceGroup -Name $rgName
$locShortName=$rg.Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

Voici la configuration finale.
  
![Le réseau virtuel n’est pas encore connecté au réseau local.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Voici la configuration finale.
  
![Le réseau virtuel dispose maintenant d’une passerelle.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Ensuite, configurez votre périphérique VPN local de sorte qu'il se connecte à la passerelle VPN Azure. Pour plus d'informations, voir [À propos des périphériques VPN pour les connexions du réseau virtuel Azure de site à site]((https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)).
  
Pour configurer votre périphérique VPN, vous avez besoin des éléments suivants :
  
- L'adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel. Utilisez la commande **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** pour afficher cette adresse.
    
- La clé prépartagée IPsec pour la connexion VPN de site à site (Tableau V - Élément 5 - colonne Valeur).
    
Voici la configuration finale.
  
![Le réseau virtuel est désormais connecté au réseau local.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Phase 3 (facultative) : ajouter des machines virtuelles
<a name="Phase2"> </a>

Créez les machines virtuelles dont vous avez besoin dans Azure. Pour plus d'informations, voir [Créer votre première machine virtuelle Windows dans le portail Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Utilisez les paramètres suivants :
  
- Dans le volet **De base**, sélectionnez le même abonnement et le même groupe de ressources que votre réseau virtuel. Enregistrez le nom d'utilisateur et le mot de passe dans un emplacement sécurisé. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle.
    
- Dans le volet **Taille**, choisissez la taille appropriée.
    
- Dans le volet **Paramètres**, dans la section **Stockage**, sélectionnez le type de stockage **Standard** et le compte de stockage configuré avec votre réseau virtuel. Dans la section **Réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l'hébergement de machines virtuelles (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.
    
Vérifiez que votre machine virtuelle utilise le DNS correctement en vérifiant votre DNS interne pour vous assurer que les enregistrements d’adresse (A) ont été ajoutés pour votre nouvelle machine virtuelle. Pour accéder à Internet, vos machines virtuelles Azure doivent être configurées pour utiliser le serveur proxy de votre réseau local. Contactez votre administrateur réseau pour les étapes de configuration supplémentaires à effectuer sur le serveur.
  
Voici la configuration finale.
  
![Le réseau virtuel héberge maintenant des machines virtuelles qui sont accessibles à partir du réseau local.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="see-also"></a>Voir aussi

<a name="DeploymentRoadmap"> </a>

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Déployer la synchronisation d'annuaires (DirSync) Office 365 dans Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)

[Comment créer la machine virtuelle](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[À propos des périphériques VPN pour les connexions de la passerelle VPN de site à site]((https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/))
  
[Installation et configuration d'Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)



