---
title: 'Diagramme accessible : Récupération d’urgence SharePoint vers Microsoft Azure'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Cet article est une version texte accessible du diagramme Récupération d’urgence SharePoint Server dans Microsoft Azure.
ms.openlocfilehash: e711452f6e019ceb280d43c2e0167507a0b0ef20
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038233"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="409dc-103">Diagramme accessible : Récupération d’urgence SharePoint vers Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="409dc-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="409dc-104">**Résumé :** Cet article est une version texte accessible du diagramme appelé SharePoint Disaster Recovery to Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="409dc-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="409dc-105">Cette affiche fournit des exemples d’architectures pour la création d’un environnement de récupération dans Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="409dc-106">Environnement local avec un environnement de récupération Azure</span><span class="sxs-lookup"><span data-stu-id="409dc-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="409dc-107">Le diagramme associé représente un exemple d’architecture utilisé pour l’environnement de production d’un environnement local utilisant Azure pour la récupération. </span><span class="sxs-lookup"><span data-stu-id="409dc-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="409dc-108">Environnement de production local</span><span class="sxs-lookup"><span data-stu-id="409dc-108">On-premises production environment</span></span>

<span data-ttu-id="409dc-109">Le diagramme associé représente un environnement de production actif à quatre niveaux de serveurs dans une batterie de serveurs. </span><span class="sxs-lookup"><span data-stu-id="409dc-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="409dc-110">Niveau 1</span><span class="sxs-lookup"><span data-stu-id="409dc-110">Tier 1</span></span>

<span data-ttu-id="409dc-p101">Il existe deux serveurs pour les services frontaux et le traitement des requêtes. Une partition d’index fournit une copie des deux serveurs. </span><span class="sxs-lookup"><span data-stu-id="409dc-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="409dc-113">Niveau 2</span><span class="sxs-lookup"><span data-stu-id="409dc-113">Tier 2</span></span>

<span data-ttu-id="409dc-114">Ce niveau possède deux serveurs pour le cache distribué. </span><span class="sxs-lookup"><span data-stu-id="409dc-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="409dc-115">Niveau 3</span><span class="sxs-lookup"><span data-stu-id="409dc-115">Tier 3</span></span>

<span data-ttu-id="409dc-p102">Ce niveau comporte trois serveurs. Chaque serveur fournit les services suivants : </span><span class="sxs-lookup"><span data-stu-id="409dc-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="409dc-118">Services principaux </span><span class="sxs-lookup"><span data-stu-id="409dc-118">Backend services</span></span> 
    
- <span data-ttu-id="409dc-119">Admin</span><span class="sxs-lookup"><span data-stu-id="409dc-119">Admin</span></span> 
    
- <span data-ttu-id="409dc-120">Gestionnaire de flux de travail</span><span class="sxs-lookup"><span data-stu-id="409dc-120">Workflow manager</span></span> 
    
- <span data-ttu-id="409dc-121">Analyse</span><span class="sxs-lookup"><span data-stu-id="409dc-121">Crawl</span></span> 
    
- <span data-ttu-id="409dc-122">Traitement de contenu</span><span class="sxs-lookup"><span data-stu-id="409dc-122">Content processing</span></span> 
    
- <span data-ttu-id="409dc-123">Données d’analyse</span><span class="sxs-lookup"><span data-stu-id="409dc-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="409dc-124">Niveau 4</span><span class="sxs-lookup"><span data-stu-id="409dc-124">Tier 4</span></span>

<span data-ttu-id="409dc-p103">Ce niveau comporte deux serveurs. Les deux serveurs possèdent trois groupes de disponibilité, comme suit : </span><span class="sxs-lookup"><span data-stu-id="409dc-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="409dc-127">Le groupe de disponibilité n° 1 fournit des fonctionnalités de recherche. </span><span class="sxs-lookup"><span data-stu-id="409dc-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="409dc-128">Le groupe de disponibilité n° 2 fournit des applications de contenu, de configuration et de service. </span><span class="sxs-lookup"><span data-stu-id="409dc-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="409dc-129">Le groupe de disponibilité n° 3 fournit du contenu. </span><span class="sxs-lookup"><span data-stu-id="409dc-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="409dc-p104">Ce niveau comporte également un serveur de partage de fichiers. Les serveurs du niveau 4 utilisent la copie des journaux de transaction pour communiquer avec ce serveur. Ce serveur, à son tour, communique à l’aide de la réplication du système de fichiers DFS avec un serveur de partage de fichiers dans l’environnement de récupération d’urgence semi-automatique Azure, comme décrit dans la section suivante. </span><span class="sxs-lookup"><span data-stu-id="409dc-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="409dc-133">Environnement de récupération Azure</span><span class="sxs-lookup"><span data-stu-id="409dc-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="409dc-134">Environnements de secours semi-automatique exécutant des machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="409dc-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="409dc-p105">Le diagramme associé représente un environnement local répliqué à l’identique dans l’environnement de récupération Azure. Le serveur de partage de fichiers de cet environnement est lié à l’environnement local par l’intermédiaire de la réplication du système de fichiers DFS. La réplication du système de fichiers DFS transfère les journaux depuis l’environnement de production vers l’environnement de récupération par l’intermédiaire du serveur de partage de fichiers. </span><span class="sxs-lookup"><span data-stu-id="409dc-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="409dc-138">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="409dc-138">Overview</span></span>

<span data-ttu-id="409dc-139">L’environnement de récupération d’urgence pour une batterie de serveurs SharePoint 2013 sur site peut être hébergé dans Azure.</span><span class="sxs-lookup"><span data-stu-id="409dc-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="409dc-140"> Azure Infrastructure Services fournit un centre de données secondaire. </span><span class="sxs-lookup"><span data-stu-id="409dc-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="409dc-141">Payez uniquement pour les ressources que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="409dc-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="409dc-142">Les batteries de serveurs de récupération de petite taille peuvent monter en charge après un incident afin de répondre aux objectifs d’échelle et de capacité. </span><span class="sxs-lookup"><span data-stu-id="409dc-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="409dc-143">La configuration de la batterie de serveurs de récupération dans Azure doit être aussi proche que possible de celle de la batterie de serveurs locale de production. </span><span class="sxs-lookup"><span data-stu-id="409dc-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="409dc-144">Même représentation des rôles serveur. </span><span class="sxs-lookup"><span data-stu-id="409dc-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="409dc-145">Même configuration des personnalisations. </span><span class="sxs-lookup"><span data-stu-id="409dc-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="409dc-146">Même configuration des fonctionnalités de recherche (peuvent être présentes sur une version plus petite de la batterie de serveurs de production). </span><span class="sxs-lookup"><span data-stu-id="409dc-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="409dc-147">La copie des journaux de transaction et la réplication du système de fichiers DFS permettent de copier les sauvegardes et les journaux des transactions de base de données vers la batterie de serveurs dans Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="409dc-p106">La réplication du système de fichiers DFS permet de transférer les journaux depuis l’environnement de production vers l’environnement de récupération. Dans un scénario WAN, la réplication DFS est plus efficace que la copie directe des journaux vers le serveur secondaire dans Azure.</span><span class="sxs-lookup"><span data-stu-id="409dc-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="409dc-150">Les journaux sont relus vers les ordinateurs SQL Server basés sur Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="409dc-151">Les bases de données dont les journaux de transaction sont copiés ne sont pas attachées à la batterie de serveurs tant qu’aucun exercice de récupération n’est effectué.  </span><span class="sxs-lookup"><span data-stu-id="409dc-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="409dc-152">Procédures de basculement : </span><span class="sxs-lookup"><span data-stu-id="409dc-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="409dc-153">Arrêtez la copie des journaux de transaction.</span><span class="sxs-lookup"><span data-stu-id="409dc-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="409dc-154">Arrêtez d’accepter du trafic vers la batterie principale.</span><span class="sxs-lookup"><span data-stu-id="409dc-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="409dc-155">Relisez les journaux de transaction finaux.</span><span class="sxs-lookup"><span data-stu-id="409dc-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="409dc-156">Attachez les bases de données de contenu à la batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="409dc-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="409dc-157">Démarrez une analyse complète.</span><span class="sxs-lookup"><span data-stu-id="409dc-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="409dc-158">Restaurez les applications de service à partir de bases de données de services répliquées.</span><span class="sxs-lookup"><span data-stu-id="409dc-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="409dc-159">Les objectifs de récupération de cette solution sont les suivants : </span><span class="sxs-lookup"><span data-stu-id="409dc-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="409dc-160">Sites et contenu</span><span class="sxs-lookup"><span data-stu-id="409dc-160">Sites and content</span></span> 
    
- <span data-ttu-id="409dc-161">Recherche (nouvelle analyse, aucun historique de recherche) </span><span class="sxs-lookup"><span data-stu-id="409dc-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="409dc-162">Services</span><span class="sxs-lookup"><span data-stu-id="409dc-162">Services</span></span>
    
<span data-ttu-id="409dc-163">Autres éléments pouvant être traités par Microsoft Consulting Services ou un partenaire : </span><span class="sxs-lookup"><span data-stu-id="409dc-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="409dc-164">Synchronisation des solutions de batterie de serveurs personnalisée</span><span class="sxs-lookup"><span data-stu-id="409dc-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="409dc-165">Connexions aux sources de données locales (BDC, Business Data Connectivity) et sources de contenu de recherche) </span><span class="sxs-lookup"><span data-stu-id="409dc-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="409dc-166">Scénarios de restauration de recherche</span><span class="sxs-lookup"><span data-stu-id="409dc-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="409dc-167">Objectifs de temps de récupération (RTO) et objectifs de point de récupération (RPO) </span><span class="sxs-lookup"><span data-stu-id="409dc-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="409dc-168">Environnement à reprise progressive exécutant des machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="409dc-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="409dc-169">Les environnements à reprise progressive ont besoin de plus de temps pour démarrer, mais coûtent moins cher. </span><span class="sxs-lookup"><span data-stu-id="409dc-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="409dc-p107">La batterie de serveurs est entièrement créée, mais les machines virtuelles sont arrêtées une fois la batterie de serveurs créée. Vous ne réglez les coûts de traitement que lorsque les machines virtuelles sont en cours d’exécution, mais devrez payer des frais de transfert des données réseau et de stockage. </span><span class="sxs-lookup"><span data-stu-id="409dc-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="409dc-172">En cas d’urgence, toutes les machines virtuelles de la batterie sont démarrées et corrigées. </span><span class="sxs-lookup"><span data-stu-id="409dc-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="409dc-173">Les sauvegardes et les journaux des transactions sont appliqués aux bases de données de la batterie de serveurs. </span><span class="sxs-lookup"><span data-stu-id="409dc-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="409dc-174">La liste suivante décrit les procédures supplémentaires pour des environnements de récupération progressive : </span><span class="sxs-lookup"><span data-stu-id="409dc-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="409dc-175">Activez les machines virtuelles régulièrement pour corriger, mettre à jour et vérifier l’environnement. </span><span class="sxs-lookup"><span data-stu-id="409dc-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="409dc-176">Exécutez les procédures d’actualisation des adresses IP et DNS. </span><span class="sxs-lookup"><span data-stu-id="409dc-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="409dc-177">Configurez SQL AlwaysOn après un basculement. </span><span class="sxs-lookup"><span data-stu-id="409dc-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="409dc-p108">Le diagramme associé représente un environnement de récupération dupliqué sur des machines virtuelles. Après le basculement vers un environnement à reprise progressive, toutes les machines virtuelles sont démarrées et les groupes de disponibilité sont configurés à l’aide des journaux de relecture pour rendre les serveurs de bases de données disponibles. </span><span class="sxs-lookup"><span data-stu-id="409dc-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="409dc-180">Environnement de récupération SharePoint dans Azure</span><span class="sxs-lookup"><span data-stu-id="409dc-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="409dc-181">Concevez et créez l’environnement de basculement dans Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="409dc-182">Créez un réseau virtuel dans Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="409dc-p109">Connectez-vous au réseau local avec le réseau virtuel dans Azure à l’aide d’une connexion VPN de site à site. Cette connexion utilise une passerelle dynamique dans Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="409dc-p110">Déployez un ou plusieurs contrôleurs de domaine vers le réseau virtuel Azure et configurez-les afin qu’ils fonctionnent avec votre domaine local. Ces contrôleurs de domaine sont des serveurs de catalogue. </span><span class="sxs-lookup"><span data-stu-id="409dc-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="409dc-187">Adaptez la batterie de serveurs SharePoint aux services cloud et aux groupes à haute disponibilité.  </span><span class="sxs-lookup"><span data-stu-id="409dc-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="409dc-188">Déployez la batterie de serveurs SharePoint, ainsi qu’un serveur de fichiers pour héberger les partages de fichiers. </span><span class="sxs-lookup"><span data-stu-id="409dc-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="409dc-189">Configurez la copie des journaux de transaction et la réplication du système de fichiers DFS entre l’environnement local et l’environnement de récupération Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="409dc-190">Le diagramme associé représente un environnement local et le réseau virtuel Azure avec les fonctionnalités suivantes : </span><span class="sxs-lookup"><span data-stu-id="409dc-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="409dc-191">Environnement local</span><span class="sxs-lookup"><span data-stu-id="409dc-191">On-premises environment</span></span>

- <span data-ttu-id="409dc-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="409dc-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="409dc-193">Serveur Active Directory </span><span class="sxs-lookup"><span data-stu-id="409dc-193">Active Directory server</span></span> 
    
<span data-ttu-id="409dc-194">Le réseau local communique avec le réseau virtuel Azure via une passerelle de réseau privé virtuel (VPN). </span><span class="sxs-lookup"><span data-stu-id="409dc-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="409dc-195">Réseau privé Azure</span><span class="sxs-lookup"><span data-stu-id="409dc-195">Azure virtual network</span></span>

<span data-ttu-id="409dc-196">La passerelle VPN communique avec un sous-réseau de passerelle VPN actif. </span><span class="sxs-lookup"><span data-stu-id="409dc-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="409dc-197">Les trois services cloud suivants existent dans le réseau virtuel Azure :</span><span class="sxs-lookup"><span data-stu-id="409dc-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="409dc-198">Le premier service cloud possède deux serveurs Active Directory et DNS avec un groupe à haute disponibilité. </span><span class="sxs-lookup"><span data-stu-id="409dc-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="409dc-199">Le second service cloud possède trois groupes de serveurs : Deux serveurs de cache distribué avec un groupe à haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="409dc-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="409dc-200">Deux serveurs frontaux avec un groupe à haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="409dc-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="409dc-201">Trois serveurs frontaux avec un groupe à haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="409dc-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="409dc-p112">Le troisième service cloud possède trois serveurs de bases de données avec un groupe à haute disponibilité. L’un de ces serveurs de base de données est un partage de fichiers pour la copie des journaux de transaction et le troisième nœud d’un nœud majoritaire pour SQL Server AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="409dc-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="409dc-204">Créer l’environnement hybride AD DS</span><span class="sxs-lookup"><span data-stu-id="409dc-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="409dc-205">La configuration des services AD DS pour cette solution constitue un scénario de déploiement hybride dans lequel les services AD DS sont déployés en partie localement et en partie sur des machines virtuelles Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="409dc-206">Important : avant de déployer AD DS dans Azure, lisez les instructions de déploiement de Windows Server Active Directory sur des machines virtuelleshttps://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)Microsoft Azure (.</span><span class="sxs-lookup"><span data-stu-id="409dc-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (https://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).</span></span> 
  
 
<span data-ttu-id="409dc-p113">Cette architecture de référence inclut deux machines virtuelles configurées comme contrôleurs de domaine. Elles sont toutes deux configurées de la manière suivante : </span><span class="sxs-lookup"><span data-stu-id="409dc-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="409dc-209">Taille : petite. </span><span class="sxs-lookup"><span data-stu-id="409dc-209">Size — Small.</span></span> 
    
- <span data-ttu-id="409dc-210">Système d’exploitation : Windows Server 2012.  </span><span class="sxs-lookup"><span data-stu-id="409dc-210">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="409dc-p114">Rôle : contrôleur de domaine AD DS désigné en tant que serveur de catalogue global. Cette configuration permet de réduire le trafic sortant de la connexion VPN. Dans un environnement multidomaine dont la fréquence de modification est élevée, configurez les contrôleurs de domaine locaux afin qu’ils ne se synchronisent pas avec les serveurs de catalogue globaux dans Azure.  </span><span class="sxs-lookup"><span data-stu-id="409dc-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="409dc-p115">Disques de données : placez SYSVOL, les journaux et la base de données AD DS sur les disques de données Azure. Ne les placez pas sur le disque du système d’exploitation ou sur les disques temporaires fournis par Azure. Cette consigne est importante.</span><span class="sxs-lookup"><span data-stu-id="409dc-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="409dc-217">Rôle : installez et configurez le serveur DNS Windows sur les contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="409dc-217">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="409dc-p116">Adresses IP : utilisez des adresses IP dynamiques. Pour ce faire, vous devez créer un réseau virtuel Azure. </span><span class="sxs-lookup"><span data-stu-id="409dc-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

