---
title: Diagramme accessible  Options de plateforme Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Exchange 2013, qui est disponible dans la rubrique Diagrammes techniques.
ms.openlocfilehash: ce1fe525b6a339c64d757b82a6f1c9ea4b82d23e
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027568"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagramme accessible : Options de plateforme Microsoft Exchange 2013

**Résumé :** Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Exchange 2013, qui est disponible dans la rubrique [Diagrammes techniques](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Cette affiche décrit ce que les architectes et les décideurs d’entreprise (BDM) doivent savoir sur les déploiements Exchange Online et Exchange Server et inclut : 
  
- Une comparaison des quatre options de plateforme disponibles pour Exchange 2013 : Exchange Online (Office 365), Exchange hybride, Exchange Server local et Exchange hébergé par un fournisseur. 
    
- Des descriptions de trois fonctionnalités nouvelles ou mises à jour dans Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Une comparaison de quatre déploiements distincts pour la plateforme Exchange 2013.

La comparaison fournit des informations sur chaque option de déploiement dans les sections suivantes : 
  
- Une vue d’ensemble des différentes fonctionnalités de déploiement 
    
- Avantages de l'implémentation de chaque option de déploiement 
    
- Critères de licence 
    
- Tâches architecturales requises 
    
- Responsabilités des professionnels informatiques pour l’implémentation de chaque option de déploiement 
    
### <a name="overview"></a>Vue d’ensemble

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Vous gagnez en efficacité et réduisez les coûts grâce à Office 365.
  
Le schéma associé présente Exchange Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local des services de domaine Active Directory (AD DS) et le client Azure Active Directory. Les services ADFS (Active Directory Federation Services) sont requis pour l'authentification unique. 
  
Description des fonctions et fonctionnalités :
  
- Fonctionnement des serveurs et des logiciels de serveur géré par Microsoft.
    
- Riche ensemble de fonctionnalités d'Exchange Server 2013 en tant que service informatique.
    
- Toujours à jour avec les dernières fonctionnalités.
    
- Exchange Online Protection (EOP) inclus pour la protection contre le courrier indésirable/contre les programmes malveillants.
    
- Haute disponibilité intégrée avec un contrat de niveau de service (SLA) de 99,9 %.
    
- La synchronisation d'annuaires inclut les mots de passe entre les services AD DS (Active Directory Domain Services) et le client Azure Active Directory. Les services AD FS (Active Directory Federation Services) sont requis pour l'authentification unique.
    
#### <a name="exchange-hybrid"></a>Environnement Exchange hybride

Vous pouvez tirer profit d'Office 365 tout en conservant Exchange Server en local.
  
Le diagramme associé présente un environnement Office 365 avec Exchange Online, dans lequel certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne. Il présente également un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local des services de domaine Active Directory (AD DS) et le client Azure Active Directory.
  
Description des fonctions et fonctionnalités :
  
- Certains utilisateurs sont hébergés localement et d’autres sont hébergés en ligne. En outre, les utilisateurs partagent le même espace d’adressage de messagerie électronique.
    
- Utilisation de votre infrastructure Exchange Server existante.
    
- Migration à partir d’Exchange en local vers Exchange Online dans le temps, selon votre planification.
    
- Intégration d'autres applications Office 365, y compris Lync Online et SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Environnement Exchange Server local

Vous pouvez concevoir et gérer votre propre infrastructure Exchange Server 2013.
  
Le diagramme associé présente une infrastructure Exchange Server avec un environnement local des services de domaine Active Directory (AD DS) dans lequel les utilisateurs sont hébergés localement.
  
Description des fonctions et fonctionnalités :
  
- Niveau de contrôle et de personnalisation le plus élevé pour votre configuration.
    
- Aucune dépendance concernant la gestion de l’affinité de session au niveau de la couche d’équilibrage de charge.
    
- Haute disponibilité et résilience de site simples à l’aide de groupes de disponibilité de base de données (DAG).
    
- Disponibilité gérée qui vous permet de conserver une très bonne expérience utilisateur.
    
- Utilisation de l’infrastructure de stockage et matérielle existante.
    
#### <a name="provider-hosted-exchange"></a>Environnement Exchange hébergé par un fournisseur

Vous pouvez externaliser votre charge de travail Exchange Server vers un fournisseur de solutions Exchange Server.
  
Le diagramme associé présente un environnement Exchange Server géré et tenu à jour par un fournisseur.
  
Description des fonctions et fonctionnalités :
  
- Le fonctionnement des serveurs et des logiciels de serveur est géré par votre fournisseur.
    
- La planification, le dimensionnement, la mise à l’échelle et la maintenance de l’infrastructure Exchange Server sont délégués à votre fournisseur.
    
- La maintenance du service est gérée par votre fournisseur.
    
- L’ensemble de fonctionnalités Exchange est limité à la version du logiciel déployée par votre fournisseur.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Avantages de l’implémentation de chaque option de déploiement

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Cette option de déploiement est idéale pour :
  
- Les organisations qui cherchent à réduire les coûts d’exploitation pour les déploiements Exchange locaux.
    
- Les organisations qui prévoient de tirer profit d'autres offres Office 365, telles que SharePoint Online et Lync Online.
    
#### <a name="exchange-hybrid"></a>Environnement Exchange hybride

Cette option de déploiement est idéale pour :
  
- Faciliter une migration d’Exchange en local vers Exchange Online.
    
- Prendre en charge des sites distants sans avoir à investir dans une infrastructure de succursale.
    
- Les sociétés multinationales avec des filiales qui exigent que les données soient hébergées sur site.
    
#### <a name="exchange-server-on-premises"></a>Environnement Exchange Server local

Cette option de déploiement est idéale pour :
  
- Les solutions hautement personnalisées.
    
- Les solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Exchange Online.
    
- Les organisations soumises à des réglementations de gouvernance de données qui exigent que les données soient hébergées sur site.
    
- Les organisations qui souhaitent conserver le contrôle de l’ensemble de la plateforme et de la solution.
    
#### <a name="provider-hosted-exchange"></a>Environnement Exchange hébergé par un fournisseur

Cette option de déploiement est idéale pour :
  
- Les organisations qui ont besoin d’une fonctionnalité Exchange Server, mais qui souhaitent sous-traiter son déploiement et sa maintenance.
    
- Les organisations qui ont besoin d’options de support personnalisées.
    
- Les solutions personnalisées et l’intégration avec des applications personnalisées proposées par le fournisseur.
    
- Les solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Exchange Online.
    
### <a name="license-requirements"></a>Critères de licence

Le tableau suivant détaille les critères de licence pour chaque option de déploiement.
  
|**Option de déploiement**|**Critères de licence**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modèle d’abonnement  <br/> |
|Environnement Exchange hybride  <br/> | Office 365 : modèle d'abonnement <br/>  Environnement local : toutes les licences locales s'appliquent (révision des licences pour Exchange Server en local) <br/>  Licence de serveur hybride* <br/> |
|Environnement Exchange Server local  <br/> | Système d’exploitation du serveur <br/>  Licence de serveur Exchange 2013 <br/>  Licence d’accès au client Exchange 2013 <br/> |
|Environnement Exchange hébergé par un fournisseur  <br/> |Les coûts sont déterminés en fonction de l’accord avec le fournisseur  <br/> |
   
### <a name="architecture-tasks"></a>Tâches d’architecture

Cette section répertorie les tâches d’architecture pour chaque option de déploiement.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Planifier et concevoir la synchronisation d’annuaires.
    
- Vérifier la connectivité et la capacité du réseau via les pare-feu, les serveurs proxy, les passerelles et sur l’ensemble des liaisons de réseau étendu (WAN).
    
#### <a name="exchange-hybrid"></a>Environnement Exchange hybride

En plus des tâches d'architecture pour les environnements Office 365 et locaux :
  
- Décider de rendre disponible ou non l’authentification unique.
    
- Décider d’acheminer le courrier Internet entrant via une organisation locale ou via Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Environnement Exchange Server local

- Concevoir la topologie Exchange.
    
- Planifier la capacité du matériel de serveur.
    
- Concevoir la topologie de routage.
    
- Concevoir l’équilibrage de charge pour les serveurs d’accès au client.
    
- Planifier la haute disponibilité à l’aide de groupes de disponibilité de base de données.
    
#### <a name="provider-hosted-exchange"></a>Environnement Exchange hébergé par un fournisseur

Assurez-vous que la capacité et la disponibilité du réseau via les pare-feu, les serveurs proxy, les passerelles et sur l’ensemble des liaisons WAN sont disponibles pour votre fournisseur.
  
### <a name="it-pro-responsibilities"></a>Responsabilités des professionnels de l’informatique

Cette section répertorie les responsabilités des professionnels de l’informatique pour chaque option de déploiement.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implémentation du plan de synchronisation d’annuaires.
    
- Planification et implémentation du routage et des enregistrements DNS internes et externes.
    
- Configuration du serveur proxy ou du pare-feu pour les exigences en matière d'URL et d'adresse IP Office 365.
    
- Gestion des comptes d’utilisateurs et des paramètres Exchange Online.
    
#### <a name="exchange-hybrid"></a>Environnement Exchange hybride

En plus des responsabilités des professionnels de l'informatique pour les environnements locaux et Office 365 :
  
- Configuration des services ADFS (Active Directory Federation Services) pour l’authentification unique (le cas échéant).
    
- Configuration des certificats Exchange pour des communications sécurisées entre les serveurs Exchange 2013 et Office 365.
    
- Configuration des enregistrements DNS pour le chemin de messagerie Internet entrant souhaité.
    
#### <a name="exchange-server-on-premises"></a>Environnement Exchange Server local

- Configuration des certificats requis pour les services Exchange.
    
- Configuration des serveurs.
    
- Implémentation de la topologie de routage de messages Exchange.
    
- Implémentation des groupes de disponibilité de base de données.
    
- Mise à jour et gestion des serveurs Exchange.
    
- En fonction de l’utilisation, ajout ou suppression de serveurs selon les besoins.
    
#### <a name="provider-hosted-exchange"></a>Environnement Exchange hébergé par un fournisseur

Les responsabilités du fournisseur sont les suivantes :
  
- Maintenance du service et du système.
    
- Déploiement des fonctionnalités.
    
- Protection des données et récupération d’urgence.
    
Les responsabilités du personnel informatique de votre organisation incluent la création et la gestion de comptes d'utilisateurs.
  
#### <a name="more-information"></a>Plus d’informations

Pour en savoir plus sur Exchange Online (Office 365), consultez les rubriques suivantes :
  
- [Description du service Exchange Online](https://aka.ms/EXOSD)
    
- [Bibliothèque Exchange Online sur TechNet](https://aka.ms/EXOTN)
    
- [Portail Exchange Online](https://aka.ms/EXO)
    
Pour plus d’informations sur l’environnement Exchange hybride, consultez les rubriques suivantes :
  
- [Déploiements hybrides Exchange 2013](https://aka.ms/ExchangeHybrid). Veuillez noter que la licence de serveur hybride est uniquement requise pour les scénarios suivants : organisation Exchange 2010 avec un serveur hybride Exchange 2013 et organisation Exchange 2007 avec un serveur hybride Exchange 2010 ou Exchange 2013.
    
- [Page de connexion à Office 365](https://aka.ms/HybridKey)
    
Pour en savoir plus sur l’environnement Exchange local, consultez les rubriques suivantes :
  
- [Bibliothèque Exchange Server 2013 sur TechNet](https://aka.ms/Ex2013TN)
    
- [Portail Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Architecture Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Pour en savoir plus sur l’environnement Exchange hébergé par un fournisseur, consultez la rubrique suivante :
  
[Solutions et guide d'hébergement et d'architecture mutualisée Exchange Server 2013](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descriptions de trois fonctionnalités nouvelles ou mises à jour dans Exchange 2013

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) fournit une protection contre le courrier indésirable et contre les programmes malveillants pour tout déploiement en proposant une couche de fonctionnalités de protection déployées sur un réseau mondial de centres de données. Cette protection vous permet de gérer vos environnements de messagerie plus facilement. EOP est inclus dans les abonnements Exchange Online, mais vous pouvez également l’utiliser pour les déploiements hybrides et locaux.
  
Les diagrammes associés présentent les déploiements Exchange Online, Exchange hybride et Exchange local qui comprennent la couche EOP dans le réseau global.
  
### <a name="exchange-server-deployment-assistant"></a>Assistant de déploiement Exchange Server

L’Assistant de déploiement Exchange Server est un outil web qui vous pose quelques questions concernant votre environnement actuel, puis génère une liste de contrôle détaillée et personnalisée pour vous aider à déployer Exchange Server pour différents types de scénarios. Que vous migriez depuis une version antérieure d’Exchange vers Exchange 2013, vers Exchange Online ou que vous planifiiez une infrastructure hybride, l’Assistant de déploiement Exchange Server crée une liste de contrôle personnalisée pour le déploiement de votre scénario.
  
La capture d’écran associée présente un exemple de liste de contrôle créée à l’aide de l’Assistant de déploiement Exchange Server.
  
### <a name="integration-with-lync-and-sharepoint"></a>Intégration avec Lync et SharePoint

Exchange Server 2013 inclut de nombreuses fonctionnalités qui s'intègrent à Lync Server 2013 et SharePoint Server 2013. Ensemble, ces produits proposent un large éventail de fonctionnalités et améliorent la collaboration au sein de votre organisation. 
  
Un diagramme d’illustration présente l’affiche portant sur l’authentification de serveur à serveur et comprend un lien vers celle-ci. 
  
- Archivage, mise en attente et découverte électronique
    
- Boîtes aux lettres de site
    
- Magasin de contacts unifié
    
- Photos haute résolution de l’utilisateur
    
- Fonctionnalité de présence Lync dans Outlook et Outlook Web App
    
- Authentification de serveur à serveur
    
- Messagerie vocale
    
- Enregistrements de réunions
    
- Synchronisation de tâches Exchange
    
Un diagramme d'illustration présente l'affiche Architecture d'Exchange Server 2013 SP1 et fournit un lien vers celle-ci.
  

