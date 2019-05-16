---
title: 'Diagramme accessible : Options de plateforme Microsoft SharePoint 2013'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Cet article est une version texte accessible du diagramme nommé Options de plateforme Microsoft SharePoint 2013.
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068600"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagramme accessible : Options de plateforme Microsoft SharePoint 2013

**Résumé:** Cet article est une version texte accessible du diagramme intitulé options de plateforme Microsoft SharePoint 2013.
  
Quels sont les décideurs d’entreprise (BDM) et les architectes doivent savoir sur Office 365, Microsoft Azure et les déploiements sur site. 
  
Cette affiche comprend deux sections : 
  
- Une comparaison de quatre déploiements différents pour SharePoint 2013: SharePoint dans Office 365, un environnement hybride d’Office 365 avec un déploiement local de SharePoint 2013, Azure et un déploiement local de SharePoint 2013. 
    
- Description des trois charges de travail classiques à déplacer vers Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Une comparaison de quatre déploiements distincts pour la plateforme SharePoint 2013.

La comparaison fournit des informations sur chaque option de déploiement en relation avec les sections suivantes : 
  
- Une vue d’ensemble des différentes fonctionnalités de déploiement 
    
- Une présentation de chaque type de déploiement  
    
- Critères de licence 
    
- Tâches architecture nécessaires pour la mise en œuvre  
    
- Responsabilités des professionnels de l’informatique pour la mise en œuvre  
    
### <a name="overview"></a>Vue d’ensemble

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 dans Office 365

Gagnez en efficacité et optimisez les coûts avec les plans mutualisés Office 365. 
  
Le diagramme associé présente SharePoint Online avec un client Azure Active Directory, qui synchronise les mots de passe et les noms de compte entre l’environnement Active Directory local et le client Azure Active Directory. 
  
Description des fonctionnalités : 
  
- Software as a Service (SaaS). 
    
- L’ensemble de fonctionnalités enrichies est toujours à jour.  
    
- Comprend un client Azure Active Directory (peut être utilisé avec d’autres applications). 
    
- L’intégration d’annuaire inclut la synchronisation des noms de compte et des mots de passe entre l’environnement Active Directory local et le client Azure Active Directory. 
    
- Si l’authentification unique (SSO) est requise, les services AD FS (Active Directory Federation Services) peuvent être implémentés.   
    
- Communication client sur Internet grâce à un accès chiffré et authentifié (port 443).  
    
- La migration des données est limitée à ce qui peut être téléchargé sur Internet.  
    
- Personnalisations : Applications pour Office, SharePoint et SharePoint Designer 2013.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

Combinez les avantages d’Office 365 avec un déploiement local de SharePoint 2013. 
  
Le diagramme associé montre Office 365 avec SharePoint Online à l’aide de Business Connectivity Services (BCS) pour se connecter à une batterie de serveurs SharePoint Server 2013 sur site. 
  
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
  
Le diagramme associé affiche Azure, qui contient deux services Cloud, une batterie de serveurs SharePoint 2013 et Windows Server Active Directory avec DNS connecté aux utilisateurs via Internet ou se connectant à Active Directory local via un tunnel VPN. 
  
Les fonctionnalités sont les suivantes :  
  
-  Azure est une plateforme qui fournit les services d’infrastructure et d’application nécessaires pour héberger une batterie de serveurs SharePoint 2013.
    
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

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 dans Office 365

- Sécurisez le partage et la collaboration externes. (fonctionnalité unique !)  
    
- Intranet - Sites d’équipe, Mes sites et collaboration interne.  
    
- Stockage des documents et suivi des versions dans le cloud.  
    
- Site web de base destiné au public.  
    
Fonctionnalités supplémentaires avec les plans d’abonnement dédié Office 365: 
  
- Équipement du centre de données Microsoft dédié à votre organisation et non partagé avec une autre organisation.   
    
- Chaque environnement client réside dans un réseau séparé physiquement.  
    
- Communication client sur un VPN sécurisé IPSec ou connexion privée appartenant au client. L’authentification à deux facteurs est facultative.  
    
- Plans de support ITAR.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

- Utilisez Office 365 pour le partage externe et la collaboration au lieu de configurer un environnement extranet. 
    
- Déplacez Mes sites (OneDrive for Business) dans le cloud pour permettre aux utilisateurs d’accéder à leurs fichiers à distance plus facilement.   
    
- Démarrez les nouveaux sites d’équipe dans Office 365. 
    
- Intégrer un site Office 365 à un environnement SharePoint BCS local. 
    
#### <a name="azure"></a>Azure

- SharePoint pour les sites Internet – Sites destinés au public. Tirez parti d’Azure AD pour les comptes client et l’authentification. 
    
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
    
- Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels qui ne sont pas pris en charge par les services d’infrastructure Azure. 
    
- Restrictions de confidentialité qui empêchent la synchronisation des comptes Active Directory avec Azure Active Directory (configuration requise pour Office 365). 
    
- Organisations qui préfèrent bénéficier du contrôle de l’ensemble de la plateforme et de la solution. 
    
### <a name="license-requirements"></a>Critères de licence

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 dans Office 365

Modèle d’abonnement. Aucune licence supplémentaire nécessaire. 
  
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

- Office 365  Modèle d'abonnement. Aucune licence supplémentaire nécessaire. 
    
- Local — Toutes les licences locales s’appliquent. 
    
#### <a name="azure"></a>Azure

-  Abonnement Azure (y compris le système d’exploitation du serveur)
    
- SQL Server 
    
- Licence de serveur SharePoint 2013 
    
- Licence d’accès au client SharePoint 2013 
    
#### <a name="on-premises"></a>Sur site

- Système d’exploitation du serveur 
    
- SQL Server 
    
- Licence de serveur SharePoint 2013 
    
- Licence d’accès au client SharePoint 2013 
    
### <a name="architecture-tasks"></a>Tâches d’architecture

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 dans Office 365

- Planifiez et concevez l’intégration Directory. Deux options. Les deux options peuvent être déployées sur site ou dans Azure: synchronisation de mot de passe (nécessite un serveur 1 64 bits). Authentification unique (nécessite AD FS et plusieurs serveurs). 
    
- Garantir la capacité et la disponibilité du réseau grâce à des pare-feu, des serveurs proxy, des passerelles et des liaisons WAN. 
    
- Acquérez des certificats SSL tiers pour fournir une sécurité d’entreprise pour les offres de service Office 365. 
    
- Planifiez le nom du client et concevez l’architecture et la gouvernance du site de collection.  
    
- Planifiez des personnalisations, des solutions et des applications pour SharePoint Online.  
    
- Déterminez si vous souhaitez vous connecter à Office 365 à l’aide du protocole Internet 6 (IPv6). Cela n’est pas courant. 
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

En plus des tâches pour les environnements Office 365 et locaux : 
  
- Déterminez le niveau d’intégration des fonctions souhaité et choisissez la topologie hybride. Reportez-vous à l’affiche modèle suivante : Quelle topologie hybride dois-je utiliser ?  
    
- Si nécessaire, déterminez le dispositif de serveur proxy qui sera utilisé.  
    
#### <a name="azure"></a>Azure

Concevez l’environnement réseau Azure: 
  
- Réseau virtuel dans Azure, y compris les sous-réseaux. 
    
- Environnement de domaine et intégration avec les serveurs sur site.  
    
- Adresses IP et DNS.  
    
- Groupes d’affinité et comptes de stockage.  
    
Concevez l’environnement SharePoint dans Azure: 
  
- Topologie de batterie SharePoint et architecture logique.  
    
-  Les groupes à haute disponibilité Azure et les domaines de mise à jour.
    
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

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 dans Office 365

- Assurez-vous que les stations de travail utilisateur répondent aux conditions préalables du client Office 365. 
    
- Implémentez le plan d’intégration Directory. 
    
- Planification et implémentation du routage et des enregistrements DNS internes et externes. 
    
- Configurez le proxy ou le pare-feu pour l’adresse IP et les URL requises pour Office 365. 
    
- Créez et attribuez des autorisations d’accès à des collections de sites.  
    
- Implémentez des personnalisations, des solutions et des applications pour SharePoint Online.  
    
- Surveillez la disponibilité du réseau et identifiez les éventuels goulets d’étranglement.  
    
#### <a name="hybrid-with-office-365"></a>Hybride avec Office 365

En plus des tâches pour les environnements Office 365 et locaux : 
  
- Configurez le périphérique de serveur proxy, si nécessaire. 
    
- Configurez l’infrastructure de gestion des identités hybrides : SSO et authentification de serveur à serveur entre les deux environnements.  
    
- Configurez l’intégration des fonctionnalités choisies : Search, BCS, Duet Enterprise Online.  
    
#### <a name="azure"></a>Azure

Déployez et gérez l’environnement Azure et SharePoint: 
  
- Implémentez et gérez l’environnement réseau Azure. 
    
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
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Trois charges de travail classiques à déplacer vers Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Composants d’annuaire Office 365 plus dans Azure

Le déploiement des composants d’intégration d’annuaire Office 365 dans Azure est plus rapide, car il peut déployer des machines virtuelles à la demande. 
  
#### <a name="directory-synchronization-server-only"></a>Serveur de synchronisation d’annuaires uniquement

Au lieu de déployer le serveur de synchronisation d’annuaires 64 bits dans votre environnement local, vous devez configurer un ordinateur virtuel dans Azure. 
  
Le diagramme associé présente SharePoint Online avec un client Azure Active Directory, qui synchronise les mots de passe et les noms de compte entre l’environnement Active Directory local et le client Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Synchronisation d’annuaire plus AD FS

Cette option vous permet de prendre en charge les identités fédérées Office 365 (SSO) sans ajouter de matériel à votre infrastructure locale. Elle fournit également la résilience si l'environnement Active Directory local n'est pas disponible. 
  
- Les composants d’intégration d’annuaire résident dans Azure. 
    
- AD FS est publié sur Internet par le biais de proxies AD FS dans Azure. 
    
- Le trafic d’authentification client, pour les utilisateurs qui se connectent depuis n’importe quel emplacement, est géré par les serveurs et les proxys AD FS qui sont déployés sur Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Site Internet public et Azure AD pour l’authentification du client

Tirez parti de la possibilité de faire évoluer facilement à la demande en plaçant votre site Internet dans Azure. Utiliser Azure AD pour stocker les comptes client. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Avantages Azure pour les sites Internet

- Payez uniquement pour les ressources dont vous avez besoin en adaptant le nombre de machines virtuelles à l’utilisation de la batterie.  
    
- Ajoutez des rapports détaillés et des analyses web. 
    
- Concentrez-vous sur le développement d’un site de qualité plutôt que sur la construction d’une infrastructure. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD offre des fonctionnalités de gestion des identités et de contrôle d’accès pour les services dans le nuage. Les fonctionnalités comprennent un magasin cloud pour les données d’annuaire et un ensemble principal de services d’identité, incluant des processus d’ouverture de session, des services d’authentification et des services AD FS. Les services d’identité fournis avec Azure AD s’intègrent facilement à vos déploiements Active Directory locaux et prennent entièrement en charge les fournisseurs d’identité tiers. 
  
Le diagramme associé montre la configuration des zones et l’authentification qui sont importantes pour les sites exposés à Internet. Le diagramme montre le client Azure Active Directory, qui contient une batterie de serveurs SharePoint sur Azure avec deux zones: 
  
- Une zone Internet qui interagit avec des visiteurs et des clients anonymes et authentifiés en dehors du réseau  
    
- Une zone par défaut qui contient des NTLM pour l’analyse et l’authentification Windows qui interagit avec votre déploiement Active Directory en local sur un tunnel VPN.   
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Batterie de serveurs locale et récupération d’urgence dans Azure

Choisissez une option de récupération d’urgence qui correspond à vos besoins professionnels. Azure propose des options d’entrée de gamme pour les entreprises qui utilisent la récupération d’urgence et des options avancées pour les entreprises ayant des exigences de haute résistance. 
  
#### <a name="cold-standby"></a>Reprise progressive

- La batterie de serveurs est entièrement créée, mais les machines virtuelles sont arrêtées. (Vous payez uniquement lorsqu’ils sont en cours d’exécution!) 
    
- La gestion de l’environnement consiste à démarrer les machines virtuelles de temps en temps, à appliquer des mises à jour correctives, à procéder à des mises à jour et à vérifier l’environnement. 
    
- Démarrez l’environnement complet en cas d’incident. 
    
#### <a name="warm-standby"></a>Secours semi-automatique

- Il s’agit d’une petite batterie qui est mise en service et en fonctionnement.   
    
- La batterie peut immédiatement être utilisée par les utilisateurs en cas de panne.   
    
- Mettez rapidement la batterie à l’échelle pour qu’elle puisse servir à la base d’utilisateurs complète.  
    
#### <a name="hot-standby"></a>Secours automatique

Une batterie de secours entièrement à l’échelle est configurée et exécutée. 
  
Le diagramme associé illustre une batterie de serveurs locale qui interagit avec l’environnement de récupération d’urgence SharePoint sur Azure. Les bases de données locales utilisent Log Shipping SQL Server via le tunnel VPN pour accéder à l’environnement de récupération d’urgence SharePoint, qui comprend deux serveurs de base de données SQL contenant les bases de données SharePoint, deux serveurs frontaux web et deux serveurs d’applications SharePoint. 
  

