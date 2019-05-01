---
title: 'Diagramme accessible : Récupération d’urgence SharePoint vers Microsoft Azure'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Cet article est une version texte accessible du diagramme Récupération d’urgence SharePoint Server dans Microsoft Azure.
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487720"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagramme accessible : Récupération d’urgence SharePoint vers Microsoft Azure

**Résumé:** Cet article est une version texte accessible du diagramme appelé SharePoint disAster Recovery to Microsoft Azure.
  
Cette affiche fournit des exemples d’architectures pour la création d’un environnement de récupération dans Azure.  
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Environnement local avec un environnement de récupération Azure

Le diagramme associé représente un exemple d’architecture utilisé pour l’environnement de production d’un environnement local utilisant Azure pour la récupération.  
  
### <a name="on-premises-production-environment"></a>Environnement de production local

Le diagramme associé représente un environnement de production actif à quatre niveaux de serveurs dans une batterie de serveurs.  
  
#### <a name="tier-1"></a>Niveau 1

Il existe deux serveurs pour les services frontaux et le traitement des requêtes. Une partition d’index fournit une copie des deux serveurs.  
  
#### <a name="tier-2"></a>Niveau 2

Ce niveau possède deux serveurs pour le cache distribué.  
  
#### <a name="tier-3"></a>Niveau 3

Ce niveau comporte trois serveurs. Chaque serveur fournit les services suivants :  
  
- Services principaux  
    
- Admin 
    
- Gestionnaire de flux de travail 
    
- Analyse 
    
- Traitement de contenu 
    
- Analyse 
    
#### <a name="tier-4"></a>Niveau 4

Ce niveau comporte deux serveurs. Les deux serveurs possèdent trois groupes de disponibilité, comme suit :  
  
- Le groupe de disponibilité n° 1 fournit des fonctionnalités de recherche.  
    
- Le groupe de disponibilité n° 2 fournit des applications de contenu, de configuration et de service.  
    
- Le groupe de disponibilité n° 3 fournit du contenu.  
    
Ce niveau comporte également un serveur de partage de fichiers. Les serveurs du niveau 4 utilisent la copie des journaux de transaction pour communiquer avec ce serveur. Ce serveur, à son tour, communique à l’aide de la réplication du système de fichiers DFS avec un serveur de partage de fichiers dans l’environnement de récupération d’urgence semi-automatique Azure, comme décrit dans la section suivante.  
  
### <a name="azure-recovery-environment"></a>Environnement de récupération Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Environnements de secours semi-automatique exécutant des machines virtuelles

Le diagramme associé représente un environnement local répliqué à l’identique dans l’environnement de récupération Azure. Le serveur de partage de fichiers de cet environnement est lié à l’environnement local par l’intermédiaire de la réplication du système de fichiers DFS. La réplication du système de fichiers DFS transfère les journaux depuis l’environnement de production vers l’environnement de récupération par l’intermédiaire du serveur de partage de fichiers.  
  
### <a name="overview"></a>Vue d’ensemble

L'environnement de récupération d'urgence pour une batterie de serveurs SharePoint 2013 sur site peut être hébergé dans Azure. 
  
-   Azure Infrastructure Services fournit un centre de données secondaire. 
    
- Payez uniquement pour les ressources que vous utilisez. 
    
- Les batteries de serveurs de récupération de petite taille peuvent monter en charge après un incident afin de répondre aux objectifs d’échelle et de capacité.  
    
La configuration de la batterie de serveurs de récupération dans Azure doit être aussi proche que possible de celle de la batterie de serveurs locale de production.  
  
- Même représentation des rôles serveur.  
    
- Même configuration des personnalisations.  
    
- Même configuration des fonctionnalités de recherche (peuvent être présentes sur une version plus petite de la batterie de serveurs de production).  
    
La copie des journaux de transaction et la réplication du système de fichiers DFS permettent de copier les sauvegardes et les journaux des transactions de base de données vers la batterie de serveurs dans Azure.  
  
- La réplication du système de fichiers DFS permet de transférer les journaux depuis l’environnement de production vers l’environnement de récupération. Dans un scénario WAN, la réplication DFS est plus efficace que la copie directe des journaux vers le serveur secondaire dans Azure. 
    
- Les journaux sont relus vers les ordinateurs SQL Server basés sur Azure.  
    
- Les bases de données dont les journaux de transaction sont copiés ne sont pas attachées à la batterie de serveurs tant qu’aucun exercice de récupération n’est effectué.   
    
Procédures de basculement :  
  
1. Arrêtez la copie des journaux de transaction. 
    
2. Arrêtez d’accepter du trafic vers la batterie principale. 
    
3. Relisez les journaux de transaction finaux. 
    
4. Attachez les bases de données de contenu à la batterie de serveurs. 
    
5. Démarrez une analyse complète. 
    
6. Restaurez les applications de service à partir de bases de données de services répliquées. 
    
Les objectifs de récupération de cette solution sont les suivants :  
  
- Sites et contenu 
    
- Recherche (nouvelle analyse, aucun historique de recherche)  
    
- Services
    
Autres éléments pouvant être traités par Microsoft Consulting Services ou un partenaire :  
  
- Synchronisation des solutions de batterie de serveurs personnalisée 
    
- Connexions aux sources de données locales (BDC, Business Data Connectivity) et sources de contenu de recherche)  
    
- Scénarios de restauration de recherche 
    
- Objectifs de temps de récupération (RTO) et objectifs de point de récupération (RPO)  
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Environnement à reprise progressive exécutant des machines virtuelles

Les environnements à reprise progressive ont besoin de plus de temps pour démarrer, mais coûtent moins cher.  
  
- La batterie de serveurs est entièrement créée, mais les machines virtuelles sont arrêtées une fois la batterie de serveurs créée. Vous ne réglez les coûts de traitement que lorsque les machines virtuelles sont en cours d’exécution, mais devrez payer des frais de transfert des données réseau et de stockage.  
    
- En cas d’urgence, toutes les machines virtuelles de la batterie sont démarrées et corrigées.  
    
- Les sauvegardes et les journaux des transactions sont appliqués aux bases de données de la batterie de serveurs.  
    
La liste suivante décrit les procédures supplémentaires pour des environnements de récupération progressive :  
  
- Activez les machines virtuelles régulièrement pour corriger, mettre à jour et vérifier l’environnement.  
    
- Exécutez les procédures d’actualisation des adresses IP et DNS.  
    
- Configurez SQL AlwaysOn après un basculement.  
    
Le diagramme associé représente un environnement de récupération dupliqué sur des machines virtuelles. Après le basculement vers un environnement à reprise progressive, toutes les machines virtuelles sont démarrées et les groupes de disponibilité sont configurés à l’aide des journaux de relecture pour rendre les serveurs de bases de données disponibles.  
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Environnement de récupération SharePoint dans Azure

Concevez et créez l’environnement de basculement dans Azure.  
  
- Créez un réseau virtuel dans Azure.  
    
- Connectez-vous au réseau local avec le réseau virtuel dans Azure à l’aide d’une connexion VPN de site à site. Cette connexion utilise une passerelle dynamique dans Azure.  
    
- Déployez un ou plusieurs contrôleurs de domaine vers le réseau virtuel Azure et configurez-les afin qu’ils fonctionnent avec votre domaine local. Ces contrôleurs de domaine sont des serveurs de catalogue.  
    
- Adaptez la batterie de serveurs SharePoint aux services cloud et aux groupes à haute disponibilité.   
    
- Déployez la batterie de serveurs SharePoint, ainsi qu’un serveur de fichiers pour héberger les partages de fichiers.  
    
- Configurez la copie des journaux de transaction et la réplication du système de fichiers DFS entre l’environnement local et l’environnement de récupération Azure.  
    
Le diagramme associé représente un environnement local et le réseau virtuel Azure avec les fonctionnalités suivantes :  
  
### <a name="on-premises-environment"></a>Environnement local

- Windows Server 2012 RRAS 
    
- Serveur Active Directory  
    
Le réseau local communique avec le réseau virtuel Azure via une passerelle de réseau privé virtuel (VPN).  
  
### <a name="azure-virtual-network"></a>Réseau privé Azure

La passerelle VPN communique avec un sous-réseau de passerelle VPN actif.  
  
Les trois services cloud suivants existent dans le réseau virtuel Azure : 
  
- Le premier service cloud possède deux serveurs Active Directory et DNS avec un groupe à haute disponibilité.  
    
- Le second service cloud possède trois groupes de serveurs : Deux serveurs de cache distribué avec un groupe à haute disponibilité. Deux serveurs frontaux avec un groupe à haute disponibilité. Trois serveurs frontaux avec un groupe à haute disponibilité.
    
- Le troisième service cloud possède trois serveurs de bases de données avec un groupe à haute disponibilité. L’un de ces serveurs de base de données est un partage de fichiers pour la copie des journaux de transaction et le troisième nœud d’un nœud majoritaire pour SQL Server AlwaysOn.  
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Créer l’environnement hybride AD DS

La configuration des services AD DS pour cette solution constitue un scénario de déploiement hybride dans lequel les services AD DS sont déployés en partie localement et en partie sur des machines virtuelles Azure.  
  
Important: avant de déployer AD DS dans Azure, lisez les instructions de déploiement de Windows Server Active Directory sur des machines virtuelleshttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)Microsoft Azure (. 
  
Pour obtenir des instructions complètes sur la conception et le déploiement d'environnements http://TechNet.microsoft.comActive Directory, reportez-vous à la rubrique. 
  
Cette architecture de référence inclut deux machines virtuelles configurées comme contrôleurs de domaine. Elles sont toutes deux configurées de la manière suivante :  
  
- Taille : petite.  
    
- Système d’exploitation : Windows Server 2012.   
    
- Rôle : contrôleur de domaine AD DS désigné en tant que serveur de catalogue global. Cette configuration permet de réduire le trafic sortant de la connexion VPN. Dans un environnement multidomaine dont la fréquence de modification est élevée, configurez les contrôleurs de domaine locaux afin qu’ils ne se synchronisent pas avec les serveurs de catalogue globaux dans Azure.   
    
- Disques de données : placez SYSVOL, les journaux et la base de données AD DS sur les disques de données Azure. Ne les placez pas sur le disque du système d’exploitation ou sur les disques temporaires fournis par Azure. Cette consigne est importante. 
    
- Rôle : installez et configurez le serveur DNS Windows sur les contrôleurs de domaine. 
    
- Adresses IP : utilisez des adresses IP dynamiques. Pour ce faire, vous devez créer un réseau virtuel Azure.  
    

