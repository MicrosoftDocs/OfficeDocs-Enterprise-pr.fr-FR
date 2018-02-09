---
title: "Diagramme accessible : Options de plateforme Microsoft SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "Cet article est une version texte accessible du diagramme nommé Options de plateforme Microsoft SharePoint 2013."
ms.openlocfilehash: 1f0d2bf4e74c7e1d28aaa27c6f88dac04f02b4a9
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagramme accessible : Options de plateforme Microsoft SharePoint 2013

**Résumé :** Cet article est une version texte accessible du diagramme intitulée Options de plate-forme Microsoft SharePoint 2013.
  
Les architectes et les décideurs d’entreprise (BDM) ont besoin de savoir sur Office 365, Microsoft Azure et les déploiements sur site de. 
  
Cette affiche comprend deux sections : 
  
- Une comparaison des quatre différents déploiements de SharePoint 2013 : SharePoint dans Office 365, un hybride d’Office 365 avec un déploiement sur site de SharePoint 2013, Azure et un déploiement sur site de SharePoint 2013. 
    
- Description de trois charges de travail habituelles pour déplacer vers Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Une comparaison de quatre déploiements distincts pour la plateforme SharePoint 2013.

La comparaison fournit des informations sur chaque option de déploiement en relation avec les sections suivantes : 
  
- Une vue d’ensemble des différentes fonctionnalités de déploiement 
    
- Une présentation de chaque type de déploiement  
    
- Critères de licence 
    
- Tâches architecture nécessaires pour la mise en œuvre  
    
- Responsabilités des professionnels de l’informatique pour la mise en œuvre  
    
### <a name="overview"></a>Vue d’ensemble

#### <a name="sharepoint-2013-in-office-365"></a>2013 SharePoint dans Office 365

Gagner en efficacité et optimiser les coûts avec les plans mutualisées d’Office 365. 
  
Le diagramme qui l’accompagne présente SharePoint Online avec un locataire Azure Active Directory, qui synchronise les noms de compte et des mots de passe entre l’environnement Active Directory local et le locataire Azure Active Directory. 
  
Description des fonctionnalités : 
  
- Software as a Service (SaaS). 
    
- L’ensemble de fonctionnalités enrichies est toujours à jour.  
    
- Inclut un locataire Azure Active Directory (il peut être utilisé avec d’autres applications). 
    
- Intégration d’annuaire inclut la synchronisation des noms de compte et des mots de passe entre l’environnement Active Directory local et le locataire Azure Active Directory. 
    
- Si l’authentification unique (SSO) est requise, les services AD FS (Active Directory Federation Services) peuvent être implémentés.   
    
- Communication client sur Internet grâce à un accès chiffré et authentifié (port 443).  
    
- La migration des données est limitée à ce qui peut être téléchargé sur Internet.  
    
- Personnalisations : Applications pour Office, SharePoint et SharePoint Designer 2013.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

Combiner les avantages d’Office 365 avec un déploiement sur site de SharePoint 2013. 
  
Le diagramme qui l’accompagne présente Office 365 SharePoint Online à l’aide des Services Business Connectivity (BCS) pour se connecter à une batterie de serveurs SharePoint Server 2013 sur site. 
  
Choisissez les fonctionnalités à intégrer parmi les suivantes :  
  
Recherche SharePoint 
  
- Les utilisateurs peuvent afficher les résultats de recherche de deux environnements.   
    
- Les utilisateurs de l’extranet peuvent se connecter à distance avec un compte Active Directory sur site et utiliser toutes les fonctionnalités hybrides disponibles.  
    
BCS
  
De SharePoint Online : Les utilisateurs peuvent effectuer à la fois des opérations de lecture et d’écriture. Le service BCS se connecte à une batterie SharePoint Server 2013 sur site. Le service BCS configuré sur la batterie sur site crée la connexion avec les points de terminaison de service OData sur site.   
  
Duet Enterprise Online 
  
À partir de SharePoint Online, les utilisateurs peuvent effectuer des opérations de lecture et d’écriture sur un système SAP sur site.  
  
#### <a name="azure"></a>Azure

Profitez du cloud tout en conservant un contrôle total de la plateforme et des fonctionnalités.   
  
Le diagramme qui l’accompagne présente Azure, qui contient deux services en nuage, une batterie de serveurs SharePoint 2013 et Windows Server Active Directory avec DNS qui se connectent aux utilisateurs via Internet ou la connexion à sur site Active Directory via le tunnel VPN. 
  
Les fonctionnalités sont les suivantes :  
  
-  Azure est une plateforme qui fournit les services d’infrastructure et d’application nécessaires à l’hébergement d’une batterie de serveurs SharePoint 2013.
    
- Services d’infrastructure. 
    
- Meilleure plateforme de cloud native pour SQL Server et SharePoint.  
    
- Les ressources informatiques sont disponibles presque immédiatement sans engagement.  
    
- Mettez l’accent sur les applications, plutôt que sur les centres de données et l’infrastructure.  
    
- Développement et environnements de test peu coûteux.  
    
- Les solutions SharePoint peuvent être accessibles à partir d’Internet ou uniquement à partir d’un environnement d’entreprise via un tunnel VPN de site à site.  
    
- Les personnalisations ne sont pas limitées.  
    
#### <a name="on-premises"></a>Sur site

Vous disposez de tous ces éléments.   
  
Le diagramme associé présente un environnement local où les serveurs web, les serveurs d’applications et Active Directory communiquent avec toutes les bases de données et les serveurs d’applications dédiés à la recherche.  
  
Les fonctionnalités sont les suivantes :  
  
- Planification et dimensionnement de la capacité. 
    
- Configuration et acquisition du serveur. 
    
- Déploiement. 
    
- Mise à l’échelle, mise à jour corrective et opérations. 
    
- Sauvegarde des données. 
    
- Maintien d’un environnement de récupération d’urgence. 
    
- Les personnalisations ne sont pas limitées.  
    
### <a name="deployment-type-is-best-for---"></a>Ce type de déploiement est idéal pour...

#### <a name="sharepoint-2013-in-office-365"></a>2013 SharePoint dans Office 365

- Sécurisez le partage et la collaboration externes. (fonctionnalité unique !)  
    
- Intranet - Sites d’équipe, Mes sites et collaboration interne.  
    
- Stockage des documents et suivi des versions dans le cloud.  
    
- Site web de base destiné au public.  
    
Fonctions supplémentaires avec les programmes d’abonnement dédié de Office 365 : 
  
- Équipement du centre de données Microsoft dédié à votre organisation et non partagé avec une autre organisation.   
    
- Chaque environnement client réside dans un réseau séparé physiquement.  
    
- Communication client sur un VPN sécurisé IPSec ou connexion privée appartenant au client. L’authentification à deux facteurs est facultative.  
    
- Plans de support ITAR.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

- Utiliser Office 365 externe de partage et de collaboration au lieu de configurer un environnement extranet. 
    
- Déplacez Mes sites (OneDrive for Business) dans le cloud pour permettre aux utilisateurs d’accéder à leurs fichiers à distance plus facilement.   
    
- Démarrer les nouveaux sites d’équipe dans Office 365. 
    
- Environnement de BCS SharePoint local s’intègrent un site Office 365. 
    
#### <a name="azure"></a>Azure

- SharePoint pour Sites Internet, Public sites exposés. Tirer parti des Azure AD pour l’authentification et de comptes client. 
    
- Environnements de développeur, test et transit – Mise à disposition et retrait rapides d’environnements entiers.  
    
- Applications hybrides – Applications qui couvrent votre centre de données et le cloud.  
    
- Environnement de récupération d’urgence – Récupération rapide après un sinistre. Vous ne payez que ce que vous utilisez.  
    
- Batteries nécessitant des audits et des rapports détaillés.  
    
- Web Analytics. 
    
- Chiffrement des données au repos (les données sont cryptées dans les bases de données SQL).  
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Chiffrement des données au repos (les données sont cryptées dans les bases de données SQL)

- Batteries dans le pays (lorsque les données sont tenues de résider dans une juridiction).  
    
- Solutions BI complexes devant résider à proximité des données BI.  
    
- Solutions de cloud privées.  
    
- Les solutions hautement personnalisées. 
    
- Solutions ancienne génération avec des composants tiers qui dépendent du matériel et des logiciels qui ne sont pas pris en charge sur les Services d’Infrastructure Azure. 
    
- Restrictions de confidentialité qui empêchent la synchronisation des comptes Active Directory avec Azure Active Directory (il s’agit d’une exigence pour Office 365). 
    
- Organisations qui préfèrent bénéficier du contrôle de l’ensemble de la plateforme et de la solution. 
    
### <a name="license-requirements"></a>Critères de licence

#### <a name="sharepoint-2013-in-office-365"></a>2013 SharePoint dans Office 365

Modèle d’abonnement Aucune licence supplémentaire nécessaire.  
  
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

- Office 365  Modèle d'abonnement. Aucune licence supplémentaire nécessaire. 
    
- Local — Toutes les licences locales s’appliquent. 
    
#### <a name="azure"></a>Azure

-  Abonnement Azure (inclut le système d’exploitation)
    
- SQL Server 
    
- Licence de serveur SharePoint 2013 
    
- Licence d’accès au client SharePoint 2013 
    
#### <a name="on-premises"></a>Sur site

- Système d’exploitation du serveur 
    
- SQL Server 
    
- Licence de serveur SharePoint 2013 
    
- Licence d’accès au client SharePoint 2013 
    
### <a name="architecture-tasks"></a>Tâches d’architecture

#### <a name="sharepoint-2013-in-office-365"></a>2013 SharePoint dans Office 365

- Intégration d’annuaire de planification et de conception. Deux options. L’option peut être déployée sur site ou dans Azure : synchronisation de mot de passe (requiert un serveur 64 bits). Authentification unique (requiert AD FS et des serveurs). 
    
- Garantir la capacité et la disponibilité du réseau grâce à des pare-feu, des serveurs proxy, des passerelles et des liaisons WAN. 
    
- Acquérez des certificats SSL tiers pour fournir une sécurité d’entreprise pour les offres de service Office 365. 
    
- Planifiez le nom du client et concevez l’architecture et la gouvernance du site de collection.  
    
- Planifiez des personnalisations, des solutions et des applications pour SharePoint Online.  
    
- Si vous souhaitez vous connecter à Office 365 à l’aide de la 6 du protocole Internet (IPv6). Cela n’est pas courant. 
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

En plus des tâches pour les environnements Office 365 et locaux : 
  
- Déterminez le niveau d’intégration des fonctions souhaité et choisissez la topologie hybride. Reportez-vous à l’affiche modèle suivante : Quelle topologie hybride dois-je utiliser ?  
    
- Si nécessaire, déterminez le dispositif de serveur proxy qui sera utilisé.  
    
#### <a name="azure"></a>Azure

Conception de l’environnement réseau Azure : 
  
- Réseau virtuel dans Azure, y compris des sous-réseaux. 
    
- Environnement de domaine et intégration avec les serveurs sur site.  
    
- Adresses IP et DNS.  
    
- Groupes d’affinité et comptes de stockage.  
    
Conception de l’environnement SharePoint dans Azure : 
  
- Topologie de batterie SharePoint et architecture logique.  
    
-  Jeux de disponibilité Azure et les domaines de la mise à jour.
    
- Tailles des machines virtuelles.   
    
- Chargez le point de terminaison équilibré.  
    
- Points de terminaison externes pour l’accès public, si c’est préférable.   
    
- Environnement de récupération d’urgence.  
    
#### <a name="on-premises"></a>Sur site

Concevez l’environnement SharePoint dans un environnement sur site existant :  
  
- Topologie de batterie SharePoint et architecture logique.  
    
- Matériel serveur. 
    
- Environnement virtuel, si utilisé.  
    
- Équilibrage de charge. 
    
- Intégration avec AD DS et DNS.   
    
- Environnement de récupération d’urgence.  
    
### <a name="it-pro-responsibilities"></a>Responsabilités des professionnels de l’informatique

#### <a name="sharepoint-2013-in-office-365"></a>2013 SharePoint dans Office 365

- Assurez-vous que les stations de travail répondent aux conditions requises du client Office 365. 
    
- Implémentez le plan d’intégration Directory. 
    
- Planification et implémentation du routage et des enregistrements DNS internes et externes. 
    
- Configurer le proxy ou le pare-feu pour Office 365 adresseIP et aux exigences des URL. 
    
- Créez et attribuez des autorisations d’accès à des collections de sites.  
    
- Implémentez des personnalisations, des solutions et des applications pour SharePoint Online.  
    
- Surveillez la disponibilité du réseau et identifiez les éventuels goulets d’étranglement.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

En plus des tâches pour les environnements Office 365 et locaux : 
  
- Configurez le périphérique de serveur proxy, si nécessaire. 
    
- Configurez l’infrastructure de gestion des identités hybrides : SSO et authentification de serveur à serveur entre les deux environnements.  
    
- Configurez l’intégration des fonctionnalités choisies : Search, BCS, Duet Enterprise Online.  
    
#### <a name="azure"></a>Azure

Déployer et gérer l’environnement Azure et SharePoint : 
  
- Implémenter et gérer l’environnement de réseau Azure. 
    
- Déployez l’environnement SharePoint. 
    
- Mettez à jour les serveurs de la batterie SharePoint.  
    
- Ajoutez ou arrêtez les machines virtuelles en fonction de l’utilisation de la batterie.  
    
- Augmentez ou diminuez les tailles des machines virtuelles, si nécessaire.  
    
- Sauvegardez l’environnement SharePoint. 
    
- Implémentez l’environnement de récupération d’urgence et le protocole.  
    
#### <a name="on-premises"></a>Sur site

Déployez et gérez l’environnement sur site SharePoint :  
  
- Serveurs de mise en service. 
    
- Déployez l’environnement SharePoint. 
    
- Mettez à jour les serveurs de la batterie SharePoint.  
    
- Ajoutez ou supprimez des serveurs de batterie en fonction de l’utilisation de la batterie.  
    
- Sauvegardez l’environnement SharePoint. 
    
- Implémentez l’environnement de récupération d’urgence et le protocole.  
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Trois charges de travail habituelles pour déplacer vers Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 plus de composants d’annuaire dans Azure

Déploiement de composants d’intégration d’annuaire Office 365 dans Azure est plus rapide car elle peut déployer des machines virtuelles à la demande. 
  
#### <a name="directory-synchronization-server-only"></a>Serveur de synchronisation d’annuaires uniquement

Au lieu de déployer le serveur de synchronisation d’annuaire de 64 bits dans votre environnement local, mettre en service un ordinateur virtuel dans Azure à la place. 
  
Le diagramme qui l’accompagne présente SharePoint Online avec un locataire Azure Active Directory, qui synchronise les noms de compte et des mots de passe entre l’environnement Active Directory local et le locataire Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Synchronisation d’annuaire plus AD FS

Cette option vous permet de prendre en charge des identités d’Office 365 fédéré (SSO) sans ajout de matériel pour votre infrastructure sur site. Il fournit également une résilience si l’environnement Active Directory local n’est pas disponible. 
  
- Composants d’intégration d’annuaire résident dans Azure. 
    
- AD FS est publié sur Internet par l’intermédiaire de proxys AD FS dans Azure. 
    
- Le trafic d’authentification client, pour les utilisateurs qui se connectent à partir de n’importe quel emplacement, est géré par les serveurs AD FS et des serveurs proxy qui est déployés sur Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Site d’Internet accessible au public et Azure AD pour l’authentification du client

Tirer parti de la possibilité d’évoluer à la demande en plaçant votre site Internet dans Azure. Annonce Azure permet de stocker des comptes client. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Avantages Azure pour les sites Internet

- Payez uniquement pour les ressources dont vous avez besoin en adaptant le nombre de machines virtuelles à l’utilisation de la batterie.  
    
- Ajoutez des rapports détaillés et des analyses web. 
    
- Concentrez-vous sur le développement d’un site de qualité plutôt que sur la construction d’une infrastructure. 
    
#### <a name="azure-ad"></a>Azure AD

Annonce Azure fournit l’identité gestion et accès aux fonctionnalités de contrôle des services en nuage. Les fonctions incluent une banque basée sur le cloud pour les données d’annuaire et un ensemble de services d’identité, y compris les processus d’ouverture de session utilisateur et services d’authentification AD FS. Les services d’identité qui sont inclus avec AD Azure s’intègrent facilement avec vos déploiements d’Active Directory sur site et prend totalement en charge les fournisseurs d’identité du tiers. 
  
Le diagramme qui l’accompagne présente la configuration de zones et d’authentification qui est importante pour les sites exposés à Internet. Le schéma montre les clients d’annuaire actif Azure, qui contient une batterie de serveurs SharePoint sur Azure avec deux zones : 
  
- Une zone Internet qui interagit avec des visiteurs et des clients anonymes et authentifiés en dehors du réseau  
    
- Une zone par défaut qui contient des NTLM pour l’analyse et l’authentification Windows qui interagit avec votre déploiement Active Directory en local sur un tunnel VPN.   
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Batterie de serveurs sur site et de reprise après sinistre dans Azure

Choisissez une option de récupération après sinistre qui correspond aux besoins de votre entreprise. Azure fournit des options d’entrée de gamme pour les entreprises de mise en route de la reprise après sinistre et les options avancées pour les entreprises ayant des exigences de résistance élevée. 
  
#### <a name="cold-standby"></a>Reprise progressive

- La batterie de serveurs est totalement intégrée, mais les ordinateurs virtuels sont arrêtés. (Vous payez uniquement lorsqu’ils exécutent !) 
    
- La gestion de l’environnement consiste à démarrer les machines virtuelles de temps en temps, à appliquer des mises à jour correctives, à procéder à des mises à jour et à vérifier l’environnement. 
    
- Démarrez l’environnement complet en cas d’incident. 
    
#### <a name="warm-standby"></a>Secours semi-automatique

- Il s’agit d’une petite batterie qui est mise en service et en fonctionnement.   
    
- La batterie peut immédiatement être utilisée par les utilisateurs en cas de panne.   
    
- Mettez rapidement la batterie à l’échelle pour qu’elle puisse servir à la base d’utilisateurs complète.  
    
#### <a name="hot-standby"></a>Secours automatique

Une batterie de secours entièrement à l’échelle est configurée et exécutée. 
  
Le diagramme qui l’accompagne présente une batterie de serveurs sur site interagit avec l’environnement de récupération après sinistre SharePoint sur Azure. Les bases de données sur site utilisent l’envoi de journaux SQL Server via le tunnel VPN pour accéder à l’environnement de reprise après sinistre de SharePoint, qui comprend deux serveurs de base de données SQL qui contiennent les bases de données SharePoint, deux serveurs Web Front-End et deux SharePoint Serveurs d’applications. 
  

