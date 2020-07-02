---
title: Architectures Microsoft Azure pour SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997891"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Architectures Microsoft Azure pour SharePoint 2013

Azure est un environnement propice à l'hébergement d'une solution SharePoint Server 2013. Dans la plupart des cas, nous recommandons Microsoft 365, mais une batterie de serveurs SharePoint Server hébergée dans Azure peut être une option intéressante pour des solutions spécifiques. Cet article explique comment créer des solutions SharePoint adaptées à la plateforme Azure. Les deux solutions spécifiques suivantes sont utilisées comme exemples :
  
- [Récupération d'urgence SharePoint Server 2013 dans Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Solutions SharePoint recommandées pour la solution Azure Infrastructure Services

Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.
  
|**Solution**|**Pourquoi cette solution est recommandée pour Azure**|
|:-----|:-----|
|Environnements de test et de développement  <br/> |Il est facile de créer et de gérer ces environnements.  <br/> |
|Récupération d'urgence de batteries de serveurs SharePoint locales sur Azure  <br/> |**Centre de données secondaire hébergé** Utilisez Azure au lieu d'investir dans un centre de données secondaire dans une autre région. <br/> **Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. <br/> **More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. <br/> Voir [Récupération d'urgence SharePoint Server 2013 dans Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Sites accessibles sur Internet qui utilisent des fonctionnalités et une mise à l’ampleur non disponibles dans Microsoft 365  <br/> |**Concentrez vos efforts** Concentrez-vous sur le développement d'un site de qualité plutôt que sur la construction d'une infrastructure. <br/> **Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). <br/> **Utilisez Azure Active Directory (AD)** Tirez parti d'Azure AD pour les comptes client. <br/> **Ajouter des fonctionnalités SharePoint non disponibles dans Microsoft 365** Ajoutez des rapports détaillés et des analyses Web. <br/> Voir [Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Batteries de serveurs d’application pour prendre en charge Microsoft 365 ou des environnements locaux  <br/> |**Créez, testez et hébergez des applications** dans Azure pour prendre en charge à la fois les environnements locaux et cloud. <br/> **Hébergez ce rôle** dans Azure au lieu d'acheter du nouveau matériel pour les environnements locaux. <br/> |
   
Pour des solutions et des charges de travail de collaboration et intranet, envisagez les options suivantes :
  
- Déterminez si Microsoft 365 répond aux besoins de votre entreprise ou s’il peut faire partie de la solution. Microsoft 365 fournit un jeu de fonctionnalités enrichi qui est toujours à jour.
    
- Si Microsoft 365 ne répond pas à tous les besoins de votre entreprise, envisagez une implémentation standard de SharePoint 2013 sur site à partir de Microsoft Consulting Services (MCS). Une architecture standard peut représenter pour vous une solution plus rapide, moins onéreuse et plus simple à prendre en charge qu'une architecture personnalisée. 
    
- Si une implémentation standard ne répond pas aux besoins de votre entreprise, envisagez une solution locale personnalisée.
    
- If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.
    
## <a name="before-you-design-the-azure-environment"></a>Avant de concevoir l’environnement Azure

While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:
  
- [Conception de l'architecture pour les professionnels de l'informatique SharePoint 2013](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [Plan for performance and capacity management in SharePoint Server 2013](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Déterminer le type de domaine Active Directory

Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.
  
|**Option**|**Description**|
|:-----|:-----|
|Domaine dédié  <br/> |You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.  <br/> |
|Étendre le domaine local via une connexion entre différents locaux  <br/> |When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.  <br/> Une connexion entre différents locaux est requise pour la création d'un environnement de récupération d'urgence dans Azure vers lequel basculer à partir de votre batterie de serveurs locale.  <br/> |
   
This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.
  
## <a name="design-the-virtual-network"></a>Concevoir le réseau virtuel

First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.
  
Si vous étendez votre réseau local à Azure via une connexion entre différents locaux (requise pour un environnement de récupération d'urgence), vous devez choisir un espace d'adressage privé qui ne soit pas déjà utilisé dans le réseau de votre organisation. Il peut inclure votre environnement local et d'autres réseaux virtuels Azure. 
  
**Figure 1 : environnement local avec un réseau virtuel dans Azure**

![Microsoft Azure virtual network design for a SharePoint solution. One subnet for the Azure gateway. One subnet for the virtual machines.](media/OPrrasconWA-AZarch.png)
  
Dans ce schéma :
  
- A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.
    
- At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.
    
## <a name="add-cross-premises-connectivity"></a>Ajouter une connectivité entre différents locaux

The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space. 
  
Lorsque vous planifiez une connexion entre différents locaux, vous définissez et créez une passerelle Azure et la connexion à un périphérique de passerelle local.
  
**Figure 2 : utilisation d'une passerelle Azure et d'un périphérique de passerelle local pour fournir une connectivité de site à site entre l'environnement local et Azure**

![Environnement local connecté à un réseau virtuel Azure via une connexion entre les différents locaux, qui peut être une connexion VPN de site à site ou ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
Dans ce schéma :
  
- Par rapport au schéma précédent, l’environnement local est connecté au réseau virtuel Azure via une connexion entre les différents locaux, qui peut être une connexion VPN de site à site ou ExpressRoute.
    
- Une passerelle Azure se trouve sur un sous-réseau de passerelle.
    
- L’environnement local inclut un périphérique de passerelle, tel qu’un routeur ou un serveur VPN.
    
Pour plus d'informations sur la planification et la création d'un réseau virtuel entre différents locaux, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Ajouter des services de domaine Active Directory (AD DS) et du DNS

Pour une récupération d'urgence dans Azure, déployez Windows Server AD et un DNS dans une configuration hybride où Windows Server AD est déployé à la fois en local et sur des machines virtuelles Azure.
  
**Figure 3 : configuration de domaine Active Directory hybride**

![Deux machines virtuelles déployées sur le réseau virtuel Azure et le sous-réseau de batterie de serveurs SharePoint sont des contrôleurs de domaine répliqués et des serveurs DNS](media/AZarch-HyADdomainConfig.png)
  
This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment. 
  
The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.
  
|**Élément**|**Configuration**|
|:-----|:-----|
|Taille de machine virtuelle dans Azure  <br/> |Taille A1 ou A2 du niveau Standard  <br/> |
|Système d’exploitation  <br/> |Windows Server 2012 R2  <br/> |
|Rôle Active Directory  <br/> |AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.  <br/> Dans un environnement multidomaine avec des taux élevés de changement (cela n'est pas courant), configurez les contrôleurs de domaine en local pour qu'ils ne se synchronisent pas avec les serveurs de catalogue global dans Azure, afin de réduire le trafic de réplication.  <br/> |
|Rôle DNS  <br/> |Installez et configurez le service Serveur DNS sur les contrôleurs de domaine.  <br/> |
|Disques de données  <br/> |Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.  <br/> |
|Adresses IP  <br/> |Utilisez des adresses IP statiques et configurez le réseau virtuel pour affecter ces adresses aux machines virtuelles du réseau virtuel une fois que les contrôleurs de domaine ont été configurés.  <br/> |
   
> [!IMPORTANT]
> Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution. 
  
## <a name="add-the-sharepoint-farm"></a>Ajouter la batterie de serveurs SharePoint

Placez les machines virtuelles de la batterie de serveurs SharePoint dans des niveaux des sous-réseaux appropriés.
  
**Figure 4 : placement des machines virtuelles SharePoint**

![Serveurs de base de données et rôles de serveur SharePoint ajoutés au réseau virtuel Azure dans le sous-réseau de batterie de serveurs SharePoint](media/AZarch-SPVMsinCloudSer.png)
  
Ce schéma, qui s’appuie sur les schémas précédents, ajoute les rôles de serveur de batterie de serveurs SharePoint dans leurs niveaux respectifs.
  
- Deux machines virtuelles de base de données exécutant SQL Server créent le niveau de base de données.
    
- Deux machines virtuelles exécutant SharePoint Server 2013 pour chacun des niveaux suivants : serveurs frontaux, serveurs de cache distribué et serveurs principaux.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Concevoir et ajuster les rôles serveur pour les groupes à haute disponibilité et les domaines d’erreur

A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.
  
When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.
  
**Figure 5 : utilisation de groupes à haute disponibilité Azure pour fournir une haute disponibilité aux niveaux de batterie de serveurs SharePoint**

![Configuration de groupes à haute disponibilité dans l’infrastructure Azure pour une solution SharePoint 2013](media/AZenv-WinAzureAvailSetsHA.png)
  
This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:
  
- Active Directory et DNS
    
- Base de données
    
- Serveur principal
    
- Cache distribué
    
- Serveur frontal
    
The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.
  
Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Figure 6 : exemple de planification pour les objectifs de capacité et de performances dans une batterie de serveurs à trois niveaux**

![Architecture des sites Internet SharePoint 2013 standard avec affectations de composants répondant à des objectifs de capacité et de performances spécifiques](media/AZarch-CapPerfexmpArch.png)
  
Dans ce schéma :
  
- Une batterie de serveurs à trois niveaux est représentée : serveurs web, serveurs d’applications et serveurs de base de données.
    
- Les trois serveurs web sont configurés de manière identique avec plusieurs composants.
    
- Les deux serveurs de base de données sont configurés de manière identique.
    
- The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.
    
Examinons de plus près le niveau Serveur d'applications.
  
**Figure 7 : niveau Serveur d'applications avant ajustement**

![Exemple de niveau du serveur d’applications SharePoint Server 2013 avant ajustement pour les groupes à haute disponibilité de Microsoft Azure](media/AZarch-AppServtierBefore.png)
  
Dans ce schéma :
  
- Trois serveurs sont inclus dans le niveau Application.
    
- Le premier serveur inclut quatre composants.
    
- Le deuxième serveur inclut trois composants.
    
- Le troisième serveur inclut deux composants.
    
You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.
  
**Figure 8 : niveau Serveur d'applications après ajustement**

![Exemple de niveau du serveur d’applications SharePoint Server 2013 après ajustement pour les groupes à haute disponibilité de Microsoft Azure](media/AZarch-AppServtierAfter.png)
  
Ce schéma montre les trois serveurs d’applications configurés de façon identique avec les quatre mêmes composants.
  
Lorsque nous ajoutons des groupes à haute disponibilité aux niveaux de la batterie de serveurs SharePoint, l’implémentation est terminée.
  
**Figure 9 : batterie de serveurs SharePoint terminée dans les services d'infrastructure Azure**

![Exemple de batterie de serveurs SharePoint 2013 dans les services d’infrastructure Azure avec réseau virtuel, connectivité entre différents réseaux, sous-réseaux, machines virtuelles et groupes à haute disponibilité](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Ce schéma illustre la batterie de serveurs SharePoint implémentée dans les services d’infrastructure Azure, avec des groupes à haute disponibilité pour fournir des domaines d’erreur pour les serveurs de chaque niveau.
  
## <a name="see-also"></a>Voir aussi

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.yml)
  
[Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Récupération d'urgence SharePoint Server 2013 dans Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


