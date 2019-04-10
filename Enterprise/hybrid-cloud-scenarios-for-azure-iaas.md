---
title: Scénarios de cloud hybride pour les services IaaS Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Résumé: comprendre l'architecture hybride et les scénarios pour les offres Cloud de Microsoft infrastructure en tant que service IaaS dans Azure."
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741360"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Scénarios de cloud hybride pour Azure IaaS

 **Résumé:** Comprendre l'architecture hybride et les scénarios pour les offres de Cloud IaaS (infrastructure as a service) de Microsoft dans Azure.
  
Étendez votre infrastructure de calcul et d’identité au cloud en hébergeant des charges de travail informatiques exécutées dans des réseaux virtuels Azure intersites.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Architecture de scénario hybride pour les services IaaS Azure

La figure 1 présente l’architecture des scénarios hybrides IaaS de Microsoft dans Azure.
  
**Figure 1 : Scénarios hybrides Microsoft IaaS dans Azure**

![Scénarios hybrides Microsoft IaaS dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Pour chaque couche de l’architecture :
  
- Applications et scénarios
    
    Une charge de travail informatique est généralement une application multiniveau à haut niveau de disponibilité qui est composée d’ordinateurs virtuels Azure.
    
- Identité
    
    Ajoutez des serveurs d'identité, tels que les contrôleurs de domaine des services de domaine Active Directory (AD DS), à l'ensemble des serveurs exécutés dans Azure réseaux virtuels pour l'authentification locale.
    
- Réseau
    
    Utilisez une connexion VPN de site à site via Internet ou une connexion ExpressRoute avec homologation privée vers les services IaaS Azure.
    
- Sur site
    
    Contient des serveurs d’identité qui sont synchronisés avec les serveurs d’identité exécutés dans Azure. Peut également contenir des ressources auxquelles les ordinateurs virtuels exécutés dans Azure peuvent accéder, telles que le stockage et l’infrastructure de gestion des systèmes.
    
## <a name="directory-synchronization-server-for-office-365"></a>Serveur de synchronisation d'annuaires pour Office 365

L'exécution de votre serveur de synchronisation d'annuaires à partir d'un réseau virtuel Azure, comme illustré dans la figure 2, est un exemple d'extension de votre infrastructure informatique et d'identité dans le Cloud.
  
**Figure 2: serveur de synchronisation d'annuaires pour Office 365 dans Azure IaaS**

![Serveur de synchronisation d'annuaires pour Office 365 dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
Dans la figure 2, un réseau local héberge une infrastructure AD DS, avec un serveur proxy et un routeur sur son serveur Edge. Le routeur se connecte à une passerelle Azure sur le serveur Edge d'un réseau virtuel Azure avec une connexion VPN de site à site ou ExpressRoute. À l'intérieur du réseau virtuel, un serveur de synchronisation d'annuaires exécute Azure AD Connect.
  
Un serveur de synchronisation d'annuaires pour Office 365 synchronise la liste des comptes dans AD DS avec le client Azure AD d'un abonnement Office 365.
  
Un serveur de synchronisation d'annuaires est un serveur Windows qui exécute Azure AD Connect. Pour une mise en service plus rapide ou pour réduire le nombre de serveurs locaux dans votre organisation, déployez votre serveur de synchronisation d'annuaires dans un réseau virtuel dans Azure IaaS.
  
Le serveur de synchronisation d'annuaire interroge AD DS pour les modifications, puis les synchronise avec l'abonnement Office 365.
  
Pour plus d'informations, reportez-vous à la rubrique [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Application métier

La figure 3 illustre la configuration d’une application métier basée sur un serveur exécutée dans Azure IaaS.
  
**Figure 3 : Application métier dans Azure IaaS**

![Application métier basée sur un serveur dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
Dans la Figure 3, un réseau local héberge des utilisateurs et une infrastructure d’identité. Il est connecté à une passerelle Azure IaaS avec une connexion ExpressRoute ou VPN de site à site. Azure IaaS héberge un réseau virtuel qui contient les serveurs de l’application métier.
  
Vous pouvez créer des applications métier exécutées sur des ordinateurs virtuels Azure qui résident sur des sous-réseaux d’un réseau virtuel Azure dans un centre de données Azure (également appelé « emplacement »).
  
Étant donné que vous cherchez à étendre votre infrastructure locale à Azure, vous devez attribuer un espace d’adressage privé unique à vos réseaux virtuels et mettre à jour vos tables de routage locales afin de veiller à ce que chaque réseau virtuel soit accessible.
  
Une fois connectés, ces ordinateurs virtuels peuvent être gérés via des connexions Bureau à distance ou via votre logiciel de gestion de systèmes, tout comme vos serveurs locaux.
  
En configurant des ports exposés publiquement, des utilisateurs mobile ou distants peuvent également accéder à ces ordinateurs virtuels via Internet.
  
Pour consulter une configuration avec preuve de concept, reportez-vous à la rubrique [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Les attributs des applications métier hébergées sur des ordinateurs virtuels Azure sont les suivants :
  
- Multiniveau
    
    Les applications métier classiques utilisent une approche à plusieurs niveaux. Les ensembles de serveurs fournissent des fonctionnalités de traitement des identités et des base de données, de traitement logique et applicatif ainsi que des serveurs web frontaux réservés à l’accès des employés ou des clients.  
    
- Disponibilité élevée
    
    Les applications métier classiques offrent une disponibilité élevée en utilisant plusieurs serveurs dans chaque niveau. Azure IaaS fournit un SLA de disponibilité de 99,9 % pour les serveurs des groupes à haute disponibilité Azure.  
    
- Répartition de la charge
    
    Pour répartir la charge de trafic réseau entre plusieurs serveurs dans un niveau, vous pouvez utiliser un équilibreur de charge Azure accessible sur Internet ou interne. Vous pouvez aussi utiliser un équilibreur de charge dédié disponible sur le marketplace Azure.
    
- Sécurité
    
    Pour protéger les serveurs du trafic entrant non sollicité provenant d’Internet, vous pouvez utiliser des groupes de sécurité réseau Azure. Vous pouvez définir un trafic autorisé ou refusé pour un sous-réseau ou l’interface réseau d’un ordinateur virtuel individuel.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Batterie SharePoint Server 2016 dans Azure

Une batterie de serveurs SharePoint Server 2016 est un exemple d’application métier hautement disponible à plusieurs niveaux dans Azure, comme illustré dans la figure 4.
  
**Figure 4 : Batterie SharePoint Server 2016 à disponibilité élevée dans Azure IaaS**

![Une batterie de serveurs SharePoint Server 2016 haute disponibilité dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
Dans la figure 4, un réseau local héberge des utilisateurs et une infrastructure d’identité. Il est connecté à une passerelle Azure IaaS avec une connexion ExpressRoute ou VPN de site à site. Le réseau virtuel Azure contient les serveurs de la batterie SharePoint Server 2016, qui inclut des niveaux séparés pour les serveurs frontaux, les serveurs d’applications, le cluster SQL Server et les contrôleurs de domaine.
  
Cette configuration a les attributs suivants des applications métier dans Azure :  
  
- Niveaux
    
    Les serveurs exécutant différents rôles au sein de la batterie créent les niveaux et chaque niveau possède son propre sous-réseau.
    
- Haute disponibilité
    
    Obtenue à l’aide de plusieurs serveurs dans chaque niveau et en plaçant tous les serveurs d’un niveau dans le même groupe à disponibilité élevée.
    
- Répartition de la charge
    
    Les équilibreurs de charge Azure internes distribuent le trafic web client entrant vers les serveurs frontaux (WEB1 et WEB2) et vers l’adresse IP d’écouteur du cluster SQL Server (SQL1 SQL2 et MN1).
    
- Sécurité
    
    Les groupes de sécurité réseau pour chaque sous-réseau vous permettent de configurer le trafic entrant et sortant autorisé.
    
Suivez cette procédure pour une adoption réussie :
  
1. Évaluer et expérimenter
    
    Voir [SharePoint server 2016 dans Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) pour comprendre les avantages de l'exécution de sharepoint server 2016 dans Azure.
    
    Voir [Intranet SharePoint Server 2016 dans un environnement de développement/test Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) pour créer un environnement de développement/test simulé
    
2. Conception
    
    Voir [conception d'une batterie de serveurs SharePoint Server 2016 dans Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) pour parcourir un processus afin de déterminer l'ensemble des éléments de mise en réseau, de calcul et de stockage d'Azure IaaS pour héberger votre batterie de serveurs et leurs paramètres.
    
3. Déployer
    
    RePortez-vous à la rubrique [deployIng SharePoint server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) pour parcourir la configuration de bout en bout de la batterie de haute disponibilité en cinq phases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identité fédérée pour Office 365 dans Azure

Un autre exemple d'application métier à plusieurs niveaux hautement disponible dans Azure est l'identité fédérée pour Office 365.
  
**Figure 5: infrastructure d'identité fédérée haute disponibilité pour Office 365 dans Azure IaaS**

![Une infrastructure d'authentification fédérée Office 365 à haute disponibilité dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
Dans la figure 5, un réseau local héberge une infrastructure d'identité et des utilisateurs. Il est connecté à une passerelle Azure IaaS avec une connexion ExpressRoute ou VPN de site à site. Le réseau virtuel Azure contient des serveurs proxy Web, des serveurs AD FS (Active Directory Federation Services) et des contrôleurs de domaine AD DS (Active Directory Domain Services).
  
Cette configuration a les attributs suivants des applications métier dans Azure : 
  
- **Niveaux:** Il existe des niveaux pour les serveurs de proxy Web, les serveurs AD FS et les contrôleurs de domaine AD DS.
    
- **Distribution de la charge:** Un équilibreur de charge Azure externe répartit les demandes d'authentification client entrantes vers les proxys Web et un équilibreur de charge Azure interne distribue les demandes d'authentification aux serveurs AD FS.
    
Suivez cette procédure pour une adoption réussie :
  
1. Évaluer et expérimenter
    
    Voir [identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md) pour créer un environnement de développement/test simulé pour l'authentification fédérée avec Office 365.
    
2. Déployer
    
    Consultez la rubrique [Deploy High Availability Federated Authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour parcourir la configuration de bout en bout de l'infrastructure AD FS haute disponibilité en cinq phases.
    
    
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d’entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


