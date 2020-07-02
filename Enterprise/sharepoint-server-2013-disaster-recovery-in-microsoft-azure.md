---
title: Récupération d'urgence SharePoint Server 2013 dans Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998166"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Récupération d’urgence SharePoint Server 2013 dans Microsoft Azure

 À l’aide d’Azure, vous pouvez créer un environnement de récupération d’urgence pour votre batterie de serveurs SharePoint locale. Cet article décrit comment concevoir et implémenter cette solution.

 **Regardez la vidéo de présentation de la récupération d’urgence SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
Utilisez cet article avec le modèle de solution suivant : **Récupération d'urgence SharePoint dans Microsoft Azure**.
  
[![Procédure de récupération d’urgence SharePoint vers Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Utilisation des services d’infrastructure Azure pour la récupération d’urgence

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
Avantages de la solution Services d'infrastructure Azure :
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **Réduction du nombre de centres de données nécessaires**: utilisez la solution Services d'infrastructure Azure au lieu d'investir dans un centre de données secondaire dans une autre région.
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**Tableau : Environnements de récupération**

|**Type d'environnement de récupération**|**Description**|
|:-----|:-----|
|Automatique  <br/> |Une batterie de secours entièrement à l’échelle est configurée, mise à jour et exécutée.  <br/> |
|Semi-automatique  <br/> |La batterie de serveurs est créée et des machines virtuelles sont en cours d’exécution et mises à jour.  <br/> La récupération inclut l’attachement de bases de données de contenu, la configuration des applications de service et l’analyse de contenu.  <br/> La batterie de serveurs peut être une version réduite de la batterie de serveurs de production avant que la taille de ses instances soit augmentée pour prendre en charge l’intégralité de la base d’utilisateurs.  <br/> |
|À reprise progressive  <br/> |La batterie de serveurs est entièrement créée, mais les machines virtuelles sont arrêtées.  <br/> La gestion de l’environnement consiste à démarrer les machines virtuelles de temps en temps, à appliquer des mises à jour correctives, à procéder à des mises à jour et à vérifier l’environnement.  <br/> Démarrez l’environnement complet en cas d’incident.  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
Pour plus d’informations sur les solutions de récupération d’urgence, voir [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) et [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Description de la solution

La solution de récupération d’urgence de secours semi-automatique requiert l’environnement suivant :
  
- Une batterie de serveurs de production SharePoint locale
    
- Une batterie de serveurs de récupération SharePoint dans Azure
    
- Une connexion VPN de site à site entre les deux environnements
    
Le schéma suivant illustre ces trois éléments.
  
**Schéma : Éléments d'une solution de secours semi-automatique dans Azure**

![Éléments d’une solution de secours semi-automatique SharePoint dans Azure](media/AZarch-AZWarmStndby.png)
  
La copie des journaux de transaction SQL Server avec la réplication du système de fichiers DFS permet de copier les sauvegardes de base de données et les journaux de transaction vers la batterie de serveurs de récupération dans Azure : 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- Les journaux sont relus vers SQL Server dans l'environnement de récupération dans Azure.
    
- N'attachez pas les bases de données de contenu SharePoint dont les journaux de transaction ont été copiés à l'environnement de récupération tant qu'aucun exercice de récupération n'a été effectué.
    
Exécutez les étapes suivantes pour procéder à la récupération de la batterie de serveurs :
  
1. Arrêtez la copie des journaux de transaction.
    
2. Arrêtez d’accepter du trafic vers la batterie principale.
    
3. Relisez les journaux de transaction finaux.
    
4. Attachez les bases de données de contenu à la batterie de serveurs.
    
5. Restaurez les applications de service à partir de bases de données de services répliquées.
    
6. Mettez à jour les enregistrements du système DNS pour qu’ils pointent vers la batterie de serveurs de récupération.
    
7. Démarrez une analyse complète.
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
Après l’exécution d’une récupération, cette solution fournit les éléments répertoriés dans le tableau suivant.
  
**Tableau : Objectifs de récupération de la solution**

|**Élément**|**Description**|
|:-----|:-----|
|Sites et contenu  <br/> |Les sites et le contenu sont disponibles dans l’environnement de récupération.  <br/> |
|Nouvelle instance de recherche  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|Services  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Collecte de données relatives à l’utilisation et à l’état <br/>  Service d’états temporaires <br/>  Word Automation <br/>  Tous les autres services qui n'utilisent pas de base de données <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**Tableau : Autres éléments pouvant être traités par MCS ou un partenaire**

|**Élément**|**Description**|
|:-----|:-----|
|Synchronisation des solutions de batterie de serveurs personnalisée  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|Connexions aux données sources locales  <br/> |Il peut s’avérer peu pratique de répliquer les connexions aux systèmes de données de serveurs principaux, telles que les connexions du contrôleur secondaire de domaine et les sources de contenu de recherche.  <br/> |
|Scénarios de restauration de recherche  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
Les instructions fournies dans cet article partent du principe que la batterie de serveurs locale est déjà conçue et déployée.
  
## <a name="detailed-architecture"></a>Architecture détaillée

Idéalement, la configuration de la batterie de serveurs de récupération dans Azure est identique à celle de la batterie de serveurs de production locale. Elle doit avoir :
  
- La même représentation des rôles serveur
    
- La même configuration des personnalisations
    
- La même configuration des composants de recherche
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>Environnements de secours semi-automatique

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
Le schéma suivant illustre une solution de récupération d'urgence à partir d'une batterie de serveurs SharePoint locale vers une batterie de serveurs SharePoint basée dans Azure et configurée comme un environnement de secours semi-automatique.
  
**Schéma : Topologie et principaux éléments d'une batterie de production et d'une batterie de récupération de secours semi-automatique.**

![Topologie d’une batterie de serveurs SharePoint et d’une batterie de serveurs de récupération de secours semi-automatique](media/AZarch-AZWarmStndby.png)
  
Dans ce schéma :
  
- Deux environnements sont illustrés côte à côte : la batterie de serveurs SharePoint locale et la batterie de serveurs de récupération de secours semi-automatique dans Azure.
    
- Chaque environnement inclut un partage de fichiers.
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- La réplication DFS copie les fichiers du partage de fichiers situé dans l'environnement local vers le partage de fichiers situé dans l'environnement Azure.
    
- La copie des journaux de transaction relit les journaux de transaction depuis le partage de fichiers situé dans l'environnement Azure vers le réplica principal situé dans le groupe de disponibilité AlwaysOn SQL Server dans l'environnement de récupération.
    
### <a name="cold-standby-environments"></a>Environnements à reprise progressive

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- Le partage de fichiers
    
- Le serveur de la base de données principale
    
- Au moins une machine virtuelle exécutant les services de domaine Windows Server Active Directory et les services DNS
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**Schéma : Batterie de récupération à reprise progressive avec machines virtuelles exécutées**

![Éléments d’une solution de reprise progressive SharePoint dans Azure.](media/AZarch-AZColdStndby.png)
  
Après le basculement vers un environnement à reprise progressive, toutes les machines virtuelles sont démarrées et la méthode pour obtenir une haute disponibilité des serveurs de base de données doit être configurée, par exemple les groupes de disponibilité AlwaysOn SQL Server.
  
Si plusieurs groupes de stockage sont implémentés (les bases de données sont réparties sur plusieurs groupes à haute disponibilité SQL Server), la base de données principale pour chaque groupe de stockage doit être en cours d'exécution pour accepter les journaux associés à son groupe de stockage.
  
### <a name="skills-and-experience"></a>Compétences et expérience

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [Services de réplication de système de fichiers DFS](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Clustering de basculement Windows Server (WSFC) avec SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [Groupes de disponibilité AlwaysOn (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Sauvegarde et restauration des bases de données SQL Server ](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Déploiement de batterie de serveurs et installation de SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>Feuille de route de récupération d’urgence

![Représentation visuelle de la feuille de route de récupération d’urgence SharePoint.](media/Azure-DRroadmap.png)
  
Cette feuille de route part du principe que vous disposez déjà d'une batterie de serveurs SharePoint Server 2013 déployée en production.
  
**Tableau : Feuille de route de récupération d'urgence**

|**Étape**|**Description**|
|:-----|:-----|
|Étape 1  <br/> |Conception de l’environnement de récupération d’urgence.  <br/> |
|Étape 2  <br/> |Création du réseau virtuel Azure et de la connexion VPN.  <br/> |
|Étape 3  <br/> |Déploiement d’Active Directory et des services de nom de domaine sur le réseau Azure Virtual Network.  <br/> |
|Étape 4  <br/> |Déploiement de la batterie de serveurs de récupération SharePoint dans Azure.  <br/> |
|Étape 5  <br/> |Configuration de DFSR entre les batteries de serveurs.  <br/> |
|Étape 6  <br/> |Configuration de la copie des journaux de transaction vers la batterie de récupération.  <br/> |
|Étape 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  Arrêt de la copie des journaux de transaction <br/>  Restauration des sauvegardes <br/>  Analyse du contenu <br/>  Récupération des services <br/>  Gestion des enregistrements DNS <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Étape 1 : Conception de l’environnement de récupération d’urgence

Utilisez les instructions figurant dans la rubrique [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) pour concevoir l'environnement de récupération d'urgence, y compris la batterie de serveurs de récupération SharePoint. Vous pouvez utiliser les graphiques de la [solution de récupération d’urgence SharePoint dans](https://go.microsoft.com/fwlink/p/?LinkId=392554) le fichier Azure Visio pour démarrer le processus de conception. Il est recommandé de concevoir l'intégralité de l'environnement avant de commencer à travailler dans l'environnement Azure.
  
Outre les instructions fournies dans la rubrique [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) pour la conception du réseau virtuel, de la connexion VPN, d'Active Directory et de la batterie SharePoint, veillez à ajouter un rôle de partage de fichiers à l'environnement Azure.
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Schéma : Placement d'un serveur de fichiers utilisé pour une solution de récupération d'urgence**

![Présente un ordinateur virtuel de partage de fichiers ajouté au même service cloud qui contient les rôles serveur de base de données SharePoint.](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Étape 2 : Création du réseau virtuel Azure et de la connexion VPN

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- Planification de l'espace d'adressage IP privé du réseau Virtual Network.
    
- Planification des modifications d'infrastructure de routage pour le réseau Virtual Network.
    
- Planification des règles de pare-feu pour le trafic vers et depuis le périphérique VPN local.
    
- Création du réseau virtuel entre différents locaux dans Azure.
    
- Configuration du routage entre votre réseau local et le réseau Virtual Network.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Étape 3 : Déploiement d’Active Directory et des services de nom de domaine sur le réseau Azure Virtual Network.

Cette étape comprend le déploiement de Windows Server Active Directory et de DNS pour le réseau Virtual Network dans un scénario hybride comme décrit dans [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) et comme l'illustre le schéma suivant.
  
**Schéma : Configuration du domaine Active Directory hybride**

![Deux machines virtuelles déployées sur le réseau virtuel Azure et le sous-réseau de batterie de serveurs SharePoint sont des contrôleurs de domaine répliqués et des serveurs DNS](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Pour obtenir des instructions détaillées sur la configuration d'un contrôleur de domaine dans Azure, voir [Installation d'un contrôleur de domaine Active Directory de réplication dans un réseau virtuel Azure](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Étape 4 : Déploiement de la batterie de serveurs de récupération SharePoint dans Azure

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
Tenez compte des pratiques suivantes, que nous avons apprises en créant notre environnement de preuve de concept :
  
- Créez des machines virtuelles à l’aide du portail Azure ou de PowerShell.
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- Utilisez une convention d’attribution de noms pour les machines virtuelles.
    
- Soyez vigilant quant à l’emplacement de centre de données où les machines virtuelles sont déployées.
    
- La fonctionnalité de mise à l’échelle automatique dans Azure n’est pas prise en charge pour les rôles SharePoint.
    
- Ne configurez pas d’éléments dans la batterie de serveurs qui sera restaurée, comme des collections de sites. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Étape 5 : Configuration de DFSR entre les batteries de serveurs

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
Sur le tableau de bord du gestionnaire de serveur, procédez comme suit :
  
- Configurez le serveur local.
    
- Démarrez l' **Assistant Ajout de rôles et de fonctionnalités**.
    
- Ouvrez le nœud **Services de fichiers et de stockage**.
    
- Sélectionnez **Espaces de noms DFS** et **Réplication DFS**.
    
- Cliquez sur **Suivant** pour terminer l'Assistant.
    
Le tableau suivant fournit des liens vers des articles de référence sur la réplication DFS et des billets de blog.
  
**Tableau : Articles de référence pour la réplication DFS**

|**Titre**|**Description**|
|:-----|:-----|
|[Réplication](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |Rubrique TechNet sur la gestion du service DFS avec des liens pour la réplication  <br/> |
|[Réplication DFS : guide de survie](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Wiki avec des liens vers des informations DFS  <br/> |
|[Réplication DFS : forum aux questions (FAQ)](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |Rubrique TechNet sur la réplication DFS  <br/> |
|[Blog de Jose Barreto](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Article de blog rédigé par un responsable de programme principal sur l’équipe de serveur de fichiers de Microsoft  <br/> |
|[L'équipe de stockage de Microsoft : blog sur le fichier CAB](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Blog sur les services de fichiers et les fonctionnalités de stockage dans Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Étape 6 : Configuration de la copie des journaux de transaction vers la batterie de récupération

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Étape 7 : Validation du basculement et de la récupération

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>Arrêt de la copie des journaux de transaction

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Restauration des sauvegardes

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Analyse de la source de contenu

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
Pour démarrer une analyse complète, procédez comme suit :
  
1. Dans l'Administration centrale de SharePoint 2013, accédez à **Gestion des applications** > **Applications de service** > **Gérer les applications de service**, puis cliquez sur l'application de service de recherche que vous souhaitez analyser.
    
2. Sur la page **Administration de la recherche**, cliquez sur **Sources de contenu**, pointez sur la source de contenu que vous voulez analyser, cliquez sur la flèche, puis sur **Démarrer l'analyse complète**.
    
### <a name="recover-farm-services"></a>Récupération des services de batterie de serveurs

Le tableau suivant montre comment récupérer les services dotés de bases de données dont les journaux de transaction ont été copiés, les services dotés de bases de données mais dont la restauration à l’aide des journaux des transactions n’est pas recommandée et les services qui n’ont pas de bases de données.
  
> [!IMPORTANT]
> La restauration d’une base de données SharePoint locale dans l’environnement Azure ne permet pas de récupérer les services SharePoint que vous n’avez pas déjà installés dans Azure manuellement. 
  
**Tableau : Référence de base de données d'application de service**

|**Restaurer ces services à partir des bases de données dont les journaux de transaction ont été copiés**|**Les services suivants ont des bases de données, mais il est recommandé de démarrer ces services sans restaurer leurs bases de données**|**Les services suivants ne stockent pas de données dans des bases de données ; démarrez ces services après le basculement**|
|:-----|:-----|:-----|
| Service de traduction automatique <br/>  Service de métadonnées gérées <br/>  Service Banque d’informations sécurisé <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Service de paramètres d’abonnement Microsoft SharePoint Foundation <br/> | Collecte de données relatives à l’utilisation et à l’état <br/>  Service d’états temporaires <br/>  Word Automation <br/> | Excel Services <br/>  PerformancePoint Services <br/>  Conversion PowerPoint <br/>  Service Graphiques Visio <br/>  Gestion du travail <br/> |
   
L’exemple suivant montre comment restaurer le service de métadonnées gérées à partir d’une base de données.
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
Tout d'abord, utilisez  `New-SPMetadataServiceApplication` et spécifiez le commutateur `DatabaseName` avec le nom de la base de données restaurée.
  
Configurez ensuite la nouvelle application de service de métadonnées gérées sur le serveur secondaire, comme suit :
  
- Nom : service de métadonnées gérées
    
- Serveur de base de données : nom de la base de données du journal des transactions copié
    
- Nom de la base de donnéesManaged_Metadata_DB
    
- Pool d'applications : applications de service SharePoint 
    
### <a name="manage-dns-records"></a>Gestion des enregistrements DNS

Vous devez créer manuellement des enregistrements DNS pour qu’ils pointent vers votre batterie de serveurs SharePoint.
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
Pour l’accès externe à votre batterie de serveurs SharePoint, vous pouvez créer un enregistrement d’hôte sur un serveur DNS externe avec la même URL que les clients utilisent sur votre intranet (par exemple, `https://sharepoint.contoso.com` ) qui pointe vers une adresse IP externe dans votre pare-feu. (En utilisant cet exemple, nous vous recommandons de configurer le DNS fractionné de sorte que le serveur DNS interne fasse autorité `contoso.com` et achemine les demandes directement vers le cluster de batterie de serveurs SharePoint, au lieu de router les demandes DNS vers votre serveur DNS externe.) Vous pouvez ensuite mapper l’adresse IP externe sur l’adresse IP interne de votre cluster local afin que les clients puissent trouver les ressources qu’ils recherchent.
  
À ce stade, vous pouvez rencontrer deux scénarios de récupération d’urgence :
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
Si vous utilisez des collections de sites nommées par l’hôte, comme recommandé dans l' [architecture et le déploiement de la collection de sites nommée par l’hôte (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), vous pouvez avoir plusieurs collections de sites hébergées par la même application Web dans votre batterie de serveurs SharePoint, avec des noms DNS uniques (par exemple, `https://sales.contoso.com` et `https://marketing.contoso.com` ). Dans ce cas, vous pouvez créer des enregistrements DNS pour chaque collection de sites qui pointe vers l'adresse IP de votre cluster. Lorsqu'une requête atteint vos serveurs web frontaux SharePoint, ces derniers acheminent chaque requête vers la collection de sites appropriée.
  
## <a name="microsoft-proof-of-concept-environment"></a>Environnement de preuve de concept Microsoft

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
Le tableau suivant décrit les machines virtuelles Hyper-V que nous avons créées et configurées pour l'environnement de test local.
  
**Tableau : Machines virtuelles pour le test local**

|**Nom du serveur**|**Rôle**|**Configuration**|
|:-----|:-----|:-----|
|DC1  <br/> |Contrôleur de domaine avec Active Directory.  <br/> |Deux processeurs  <br/> De 512 Mo à 4 Go de RAM  <br/> 1 disque dur de 127 Go  <br/> |
|RRAS  <br/> |Serveur configuré avec le rôle Service Routage et accès distant (RRAS).  <br/> |Deux processeurs  <br/> De 2 à 8 Go de RAM  <br/> 1 disque dur de 127 Go  <br/> |
|FS1  <br/> |Serveur de fichiers avec des partages pour les sauvegardes et un point de terminaison pour la réplication DFS.  <br/> |Quatre processeurs  <br/> De 2 à 12 Go de RAM  <br/> 1 disque dur de 127 Go  <br/> 1 disque dur de 1 To (SAN)  <br/> 1 disque dur de 750 Go  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Serveurs web frontaux.  <br/> |Quatre processeurs  <br/> 16 Go de RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Serveurs d’applications.  <br/> |Quatre processeurs  <br/> De 2 à 16 Go de RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |Quatre processeurs  <br/> De 2 à 16 Go de RAM  <br/> |
   
Le tableau suivant décrit les configurations des lecteurs pour les machines virtuelles Hyper-V que nous avons créées et configurées pour les serveurs web frontaux et les serveurs d'applications pour l'environnement de test local.
  
**Tableau : Configurations requises des lecteurs des machines virtuelles pour les serveurs web frontaux et les serveurs d'applications pour le test local**

|**Lettre du lecteur**|**Taille**|**Nom de répertoire**|**Chemin**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Lecteur système  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Lecteur de journaux (40 Go)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |80  <br/> |Page (36 Go)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**Tableau : Configurations requises des lecteurs des machines virtuelles pour le serveur de base de données pour le test local**

|**Lettre du lecteur**|**Taille**|**Nom de répertoire**|**Chemin**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Répertoire racine de données  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Répertoire de base de données utilisateur  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |500  <br/> |Répertoire de journal de base de données utilisateur  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|G  <br/> |500  <br/> |Répertoire de base de données temporaire  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Répertoire de journal de base de données temporaire  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Configuration de l’environnement de test

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
Nous avons déployé notre environnement de test en trois étapes :
  
- Configuration de l'infrastructure hybride
    
- Configuration de serveurs
    
- Déploiement des batteries de serveurs SharePoint
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Configuration de l’infrastructure hybride

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>Configuration de serveurs

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>Déploiement des batteries de serveurs SharePoint

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Nous avons créé la batterie de serveurs et ajouté des serveurs supplémentaires dans l’ordre suivant :
  
- Configuration de SP-SQL-HA1 et SP-SQL-HA2.
    
- Configuration d’AlwaysOn et création des trois groupes de disponibilité pour la batterie de serveurs. 
    
- Configuration de SP-APP1 pour héberger l’Administration centrale.
    
- Configuration de SP-WFE1 et SP-WFE2 pour héberger le cache distribué. 
    
Nous avons utilisé le paramètre  _skipRegisterAsDistributedCachehost_ lorsque nous avons exécuté **psconfig.exe** sur la ligne de commande. Pour plus d'informations, voir [Planifier les flux et le service de cache distribué dans SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Nous avons répété les étapes suivantes dans l’environnement de récupération :
  
- Configuration d’AZ-SQL-HA1 et AZ-SQL-HA2.
    
- Configuration d’AlwaysOn et création des trois groupes de disponibilité pour la batterie de serveurs.
    
- Configuration d’AZ-APP1 pour héberger l’Administration centrale.
    
- Configuration d’AZ-WFE1 et d’AZ-WFE2 pour héberger le cache distribué.
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
Le tableau suivant décrit les machines virtuelles, les sous-réseaux et les groupes à haute disponibilité que nous avons configurés pour notre batterie de serveurs de récupération.
  
**Tableau : Infrastructure de la batterie de serveurs de récupération**

|**Nom du serveur**|**Rôle**|**Configuration**|**Sous-réseau**|**Groupes à haute disponibilité**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Contrôleur de domaine Active Directory  <br/> |Deux processeurs  <br/> De 512 Mo à 4 Go de RAM  <br/> 1 disque dur de 127 Go  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Serveur de fichiers avec des partages pour les sauvegardes et un point de terminaison pour la réplication DFS  <br/> | Configuration A5 : <br/>  Deux processeurs <br/>  14 Go de RAM <br/>  1 disque dur de 127 Go <br/>  1 disque dur de 135 Go <br/>  1 disque dur de 127 Go <br/>  1 disque dur de 150 Go <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Serveurs web frontaux  <br/> | Configuration A5 : <br/>  Deux processeurs <br/>  14 Go de RAM <br/>  1 disque dur de 127 Go <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Serveurs d’applications  <br/> | Configuration A5 : <br/>  Deux processeurs <br/>  14 Go de RAM <br/>  1 disque dur de 127 Go <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |Serveurs de base de données et réplicas principal et secondaire pour les groupes de disponibilité AlwaysOn  <br/> | Configuration A5 : <br/>  Deux processeurs <br/>  14 Go de RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Opérations

Après avoir stabilisé les environnements de batterie de serveurs et terminé les tests fonctionnels, l’équipe de test a démarré les tâches d’opérations suivantes, requises pour configurer l’environnement de récupération local :
  
- Configuration des sauvegardes complètes et différentielles
    
- Configuration de la réplication DFS sur les serveurs de fichiers qui transfèrent les journaux des transactions entre l'environnement local et l'environnement Azure
    
- Configuration des journaux des transactions sur le serveur de la base de données principale
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>Bases de données

Nos tests de basculement ont été effectués avec les bases de données suivantes : 
  
- WSS_Content
    
- ManagedMetadata
    
- Base de données de profils
    
- Base de données de synchronisation
    
- Base de données sociale
    
- Concentrateur de type de contenu (base de données pour concentrateur de syndication de type de contenu dédié)
    
## <a name="troubleshooting-tips"></a>Conseils de dépannage

Cette section décrit les problèmes rencontrés lors de nos tests et leurs solutions. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>L'utilisation de l'outil de gestion du magasin de termes a provoqué une erreur. Le message d'erreur indique que le magasin de métadonnées gérées ou la connexion n'est pas disponible actuellement.

Vérifiez que le compte de pool d’applications utilisé par l’application web dispose de l’autorisation Magasin de termes avec accès en lecture.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Les ensembles de termes personnalisés ne sont pas disponibles dans la collection de sites

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>La commande Windows PowerShell Get-ADForest génère une erreur indiquant que le terme Get-ADForest n'est pas reconnu comme le nom de la cmdlet, de la fonction, du fichier de script ou d'un programme exécutable.

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Échec de la création du groupe de disponibilité au démarrage de la session XEvent « AlwaysOn_health » sur « <server name> »

Veillez à ce que l'état des deux nœuds de votre cluster de basculement soit « En cours » et non « En pause » ou « Arrêté ». 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>Échec du travail de copie des journaux SQL Server et accès refusé lors de la tentative de connexion au partage de fichiers

Assurez-vous que votre agent SQL Server est exécuté avec les informations d’identification réseau, et non les informations d’identification par défaut.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>Travail de copie des journaux SQL Server réussi, mais aucun fichier n’a été copié

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Le service de métadonnées gérées (ou un autre service SharePoint) ne démarre pas automatiquement après l’installation

Les services peuvent mettre plusieurs minutes à démarrer, selon les performances et la charge actuelle de votre serveur SharePoint. Cliquez sur le bouton **Démarrer** pour le service concerné et accordez suffisamment de temps au démarrage, tout en actualisant de temps à autre les services sur l'écran du serveur pour contrôler son état. Si le service est encore arrêté, activez la journalisation des diagnostics SharePoint, essayez de redémarrer le service et vérifiez si le journal contient des erreurs. Pour plus d’informations, voir [configurer la journalisation des diagnostics dans SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Après avoir modifié le service DNS sur l’environnement de basculement Azure, les navigateurs clients continuent à utiliser l’ancienne adresse IP pour le site SharePoint

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Ressources supplémentaires

[Options de haute disponibilité et de récupération d’urgence prises en charge pour les bases de données SharePoint](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Configurer des groupes de disponibilité AlwaysOn SQL Server 2012 pour SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>Voir aussi

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.yml)



