---
title: 'Diagramme accessible : Flux de découverte électronique local'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: 'Cet article est une version texte accessible du diagramme nommé Flux eDiscovery local :'
ms.openlocfilehash: bdaf46c552b346d0e6966cd3589f239146ddadc5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068530"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="e6a4b-103">Diagramme accessible : Flux de découverte électronique local</span><span class="sxs-lookup"><span data-stu-id="e6a4b-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="e6a4b-104">**Résumé:** Cet article est une version texte accessible du diagramme, appelé flux de découverte électronique local.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="e6a4b-105">Cette affiche fournit des détails sur l’architecture et le flux de données dans tous les produits de serveur.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="e6a4b-106">Sur SharePoint, Exchange, Lync et partages de fichiers</span><span class="sxs-lookup"><span data-stu-id="e6a4b-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="e6a4b-107">Le diagramme montre un utilisateur envoyant une requête qui accède à deux batteries de serveurs, une batterie d’applications SharePoint 2013 Enterprise et une batterie de services SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="e6a4b-108">La batterie de services SharePoint 2013 communique avec une batterie de serveurs de contenu SharePoint 2013, Exchange Server 2013 (qui communique avec Lync 2013) et les partages de fichiers Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="e6a4b-109">La liste flux eDiscovery décrit le flux de données et l’ordre dans lequel se produisent les actions de requête eDiscovery au sein de SharePoint, Exchange, Lync et des partages de fichiers. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="e6a4b-110">La liste flux eDiscovery est tout d’abord décrite en détail, suivie d’une description détaillée des fonctionnalités illustrées dans le diagramme. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="e6a4b-111">Liste flux eDiscovery</span><span class="sxs-lookup"><span data-stu-id="e6a4b-111">eDiscovery Flow List</span></span>

<span data-ttu-id="e6a4b-p102">Les chiffres pour chacune des étapes décrites dans cette liste se rapportent à une étape illustrée dans le diagramme. Le diagramme est décrit en détail plus loin dans ce document. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="e6a4b-114">Les cas eDiscovery sont créés, gérés et utilisés dans le centre eDiscovery (EDC).</span><span class="sxs-lookup"><span data-stu-id="e6a4b-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="e6a4b-115">L’EDC est une collection de sites SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="e6a4b-116">C’est à cet endroit que les cas sont définis, les sources devant être suivies identifiées, les requêtes émises, les résultats des requêtes examinés et les conservations de contenu placées ou supprimées.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="e6a4b-117">La requête ou l’action eDiscovery (Hold, ReleaseHold, ou GetStatus) est relayée de l’EDC au proxy de l’application Service de recherche (SSA) dans la batterie d’applications Entreprise.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="e6a4b-118">Le proxy SSA transmet ensuite le trafic à l’application de service de recherche (SSA) dans la batterie des applications de services.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="e6a4b-119">Dans cet exemple, la demande doit placer tout élément dans la batterie de serveurs de contenu SharePoint avec «CONTOSO» dans le nom de fichier en conservation.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="e6a4b-p105">Si la demande consiste à rechercher un cas, la SSA consulte l’index de recherche. Ensuite, le résultat de requête eDiscovery défini est renvoyé à l’utilisateur par le biais de l’EDC. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="e6a4b-122">Si la demande est une action (insérer une action Hold ou ReleaseHold, par exemple), cette action est écrite dans Actions_Table dans la base de données administrative SSA.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="e6a4b-123">Dans cet exemple, une demande de conservation pour tout élément de la batterie de contenu SharePoint avec «CONTOSO» est écrite dans le Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="e6a4b-124">À intervalles réguliers, le travail du minuteur de conservation inaltérable eDiscovery de la batterie de contenu est activé et génère une demande pour les actions en attente, puis envoie des mises à jour d’état via le proxy SSA à l’application de service de recherche.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="e6a4b-125">La requête pour les actions en attente est transmise à la SSA centrale, qui consulte Action_Table pour connaître les actions en attente pour la batterie de contenu.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="e6a4b-126">Le travail du minuteur de conservation inaltérable de la batterie de contenu envoie également des mises à jour d’état pour les objets et les actions qu’il a reçus, qui sont écrits dans ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="e6a4b-127">La demande de blocage de tout contenu avec «CONTOSO» dans le nom de la batterie de contenu SharePoint 2013 est envoyée par la SSA au travail du minuteur de conservation inaltérable eDiscovery dans la batterie de contenu.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="e6a4b-128">Le travail du minuteur de conservation inaltérable eDiscovery place le «site CONTOSO» et le «contenu CONTOSO» en conservation.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="e6a4b-129">Le travail du minuteur de conservation inaltérable eDiscovery s’exécute périodiquement dans la batterie d’applications Enterprise pour vérifier l’état des actions de détection et mettre l’état à jour. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="e6a4b-130">La requête d’état est relayée par le biais du proxy SSA de la batterie d’applications Enterprise à la SSA de la batterie des services SharePoint. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="e6a4b-131">La SSA récupère l’état de la table Actions et le renvoie au travail du minuteur dans la batterie des applications Enterprise, qui propose les mises à jour d’état à l’EDC.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="e6a4b-132">Lorsque l’utilisateur eDiscovery recherche (ou effectue une action sur) des sources Exchange (boîte aux lettres ou contenu Lync archivé, par exemple), la SSA centrale utilise le proxy des services web Exchange (EWS) pour interroger des services web Exchange.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="e6a4b-133">Exchange possède sa propre infrastructure eDiscovery et de recherche et gère tous les appels eDiscovery en interne.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="e6a4b-134">Des services web Exchange répondent à la SSA avec des résultats de recherche eDiscovery ou une réponse à une demande d’état pour une conservation basée sur une requête, qui à son tour est relayée à l’EDC. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="e6a4b-135">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e6a4b-135">Prerequisites</span></span>

- <span data-ttu-id="e6a4b-136">La recherche de contenu d’entreprise SharePoint doit être configurée, des analyses de recherche sur les sources de contenu (SharePoint et partages de fichiers Windows) sont en cours d’exécution et l’ensemble des sources de contenu sont dans l’index. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="e6a4b-137">L’approbation et l’authentification de serveur à serveur doivent être configurées entre la batterie de services SharePoint et Exchange et également entre Exchange et Lync. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="e6a4b-138">Description des composants du diagramme</span><span class="sxs-lookup"><span data-stu-id="e6a4b-138">Description of components in the diagram</span></span>

<span data-ttu-id="e6a4b-139">Le diagramme montre un utilisateur envoyant une requête, qui accède à deux batteries de serveurs, une batterie d’applications SharePoint 2013 Enterprise et une batterie de services SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="e6a4b-140">La batterie de serveurs SharePoint Services est dotée d’une batterie de serveurs de contenu SharePoint 2013, d’Exchange Server 2013 (qui est une interface avec Lync 2013) et de partages de fichiers Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="e6a4b-141">Batterie de serveurs SharePoint 2013 Enterprise App</span><span class="sxs-lookup"><span data-stu-id="e6a4b-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="e6a4b-142">La batterie de serveurs SharePoint 2013 Enterprise App contient les composants suivants:</span><span class="sxs-lookup"><span data-stu-id="e6a4b-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="e6a4b-143">EDC</span><span class="sxs-lookup"><span data-stu-id="e6a4b-143">EDC</span></span>
    
- <span data-ttu-id="e6a4b-144">Proxy SSA </span><span class="sxs-lookup"><span data-stu-id="e6a4b-144">SSA proxy</span></span> 
    
- <span data-ttu-id="e6a4b-145">Travail du minuteur</span><span class="sxs-lookup"><span data-stu-id="e6a4b-145">Timer job</span></span> 
    
<span data-ttu-id="e6a4b-p110">Une requête ou une action envoyée par l’utilisateur est envoyée à l’EDC dans la batterie d’applications Enterprise. Les actions suivantes se produisent : </span><span class="sxs-lookup"><span data-stu-id="e6a4b-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="e6a4b-148">La requête ou l’action accède au proxy SSA. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="e6a4b-p111">Le proxy SSA envoie une requête d’état ou une réponse au travail du minuteur dans la batterie d’applications Enterprise et il envoie également une requête d’état ou une réponse au service SSA dans la batterie de services SharePoint. Les actions qui en découlent sont décrites dans la section sur la batterie de services SharePoint. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="e6a4b-151">Lorsqu’il reçoit une réponse, le travail du minuteur envoie la réponse au proxy SSA et à l’EDC. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="e6a4b-152">Tous les résultats de la requête ou de l’action sont envoyés à l’utilisateur de l’EDC. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="e6a4b-153">Batterie de services SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e6a4b-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="e6a4b-154">La batterie de services SharePoint 2013 contient les composants suivants:</span><span class="sxs-lookup"><span data-stu-id="e6a4b-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="e6a4b-155">Service SSA </span><span class="sxs-lookup"><span data-stu-id="e6a4b-155">SSA Service</span></span> 
    
- <span data-ttu-id="e6a4b-156">Base de données de l’index de recherche</span><span class="sxs-lookup"><span data-stu-id="e6a4b-156">Search index database</span></span> 
    
- <span data-ttu-id="e6a4b-157">Base de données SSA admin_db.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-157">SSA admin_db database.</span></span> <span data-ttu-id="e6a4b-158">Le tableau d’actions dans cette base de données contient : Hold Release Hold GetStatus</span><span class="sxs-lookup"><span data-stu-id="e6a4b-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="e6a4b-159">Proxy EWS </span><span class="sxs-lookup"><span data-stu-id="e6a4b-159">EWS proxy</span></span> 
    
<span data-ttu-id="e6a4b-160">Lorsque le proxy SSA de la batterie d’applications Enterprise SharePoint envoie une requête d’état au SSA de la batterie de services SharePoint, les actions suivantes se produisent : </span><span class="sxs-lookup"><span data-stu-id="e6a4b-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="e6a4b-p113">Si la demande est une requête, le SSA consulte l’index de recherche. La réponse de découverte est renvoyée au SSA, puis à l’utilisateur par le biais de l’EDC. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="e6a4b-163">Si la demande est une action d’écriture, le service SSA envoie l’action d’écriture au SSAadmin_db. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="e6a4b-164">Une demande d’analyse et de résultats de réponse est envoyée de la SSA à la batterie de contenu SharePoint 2013 et une réponse est renvoyée au SSA.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="e6a4b-165">Une demande d’analyse et de résultats est envoyée à partir du SSA aux partages de fichiers Windows et une réponse est renvoyée au SSA. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="e6a4b-166">Une requête pour une ou plusieurs actions, réponses ou mises à jour d’état en attente est envoyée à partir du SSA vers le proxy SSA de la batterie de contenu SharePoint, et une réponse est renvoyée au SSA. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="e6a4b-167">Une demande d’état/d’action Exchange est envoyée à partir du SSA vers le proxy EWS, qui envoie une demande d’état/d’action Exchange au Service web Exchange sur le serveur Exchange 2013.  </span><span class="sxs-lookup"><span data-stu-id="e6a4b-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="e6a4b-168">Une requête/réponse d’état est envoyée à partir du SSA au SSA admin_db et est renvoyé au SSA. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="e6a4b-169">Une requête/réponse d’action en attente est envoyée à partir du SSA au SSA admin_db et est renvoyée au SSA. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="e6a4b-170">Batterie de contenu SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e6a4b-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="e6a4b-171">La batterie de contenu SharePoint 2013 contient les composants suivants:</span><span class="sxs-lookup"><span data-stu-id="e6a4b-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="e6a4b-172">Proxy SSA </span><span class="sxs-lookup"><span data-stu-id="e6a4b-172">SSA proxy</span></span> 
    
- <span data-ttu-id="e6a4b-173">Travail du minuteur</span><span class="sxs-lookup"><span data-stu-id="e6a4b-173">Timer job</span></span> 
    
- <span data-ttu-id="e6a4b-174">Site SharePoint Contoso </span><span class="sxs-lookup"><span data-stu-id="e6a4b-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="e6a4b-175">Contenu SharePoint Contoso </span><span class="sxs-lookup"><span data-stu-id="e6a4b-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="e6a4b-176">Lorsque le  SSA de la batterie de services SharePoint envoie une requête d’état au proxy SSA de la batterie de contenu SharePoint, les actions suivantes se produisent : </span><span class="sxs-lookup"><span data-stu-id="e6a4b-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="e6a4b-177">Le proxy SSA de la batterie de contenu SharePoint envoie une requête pour la réponse d’actions/d’états en attente pour le travail du minuteur. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="e6a4b-178">Le travail du minuteur envoie une demande au site SharePoint Contoso, qui examine le contenu de SharePoint Contoso. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="e6a4b-179">La réponse à la requête d’actions/d’état en attente est envoyée à partir du travail du minuteur vers le proxy SSA de la batterie de contenu SharePoint et elle est ensuite envoyée au service SSA de la batterie de services SharePoint </span><span class="sxs-lookup"><span data-stu-id="e6a4b-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="e6a4b-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="e6a4b-180">Exchange 2013</span></span>

<span data-ttu-id="e6a4b-181">Le composant de serveur Exchange 2013 contient le service web Exchange et fournit les éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="e6a4b-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="e6a4b-182">L’approbation de serveur à serveur/OAuth est gérée entre la batterie de contenu SharePoint 2013 et Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="e6a4b-183">L’approbation de serveur à serveur/OAuth est gérée entre Exchange 2013 et Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="e6a4b-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="e6a4b-184">Lync 2013</span></span>

<span data-ttu-id="e6a4b-185">Le composant de Lync 2013 archive le contenu Lync dans Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="e6a4b-186">Partages de fichiers Windows</span><span class="sxs-lookup"><span data-stu-id="e6a4b-186">Windows File Shares</span></span>

<span data-ttu-id="e6a4b-187">Le composant de partages de fichiers Windows fournit les résultats d’analyse pour le SSA de la batterie de services SharePoint. </span><span class="sxs-lookup"><span data-stu-id="e6a4b-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="e6a4b-188">Légende</span><span class="sxs-lookup"><span data-stu-id="e6a4b-188">Legend</span></span>

<span data-ttu-id="e6a4b-189">La légende pour ce diagramme représente graphiquement les différents types de trafic décrits parmi les composants à l’aide de lignes de couleur comme suit : </span><span class="sxs-lookup"><span data-stu-id="e6a4b-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="e6a4b-190">Ligne bleu clair: requête/action-requête eDiscovery ou données d’action</span><span class="sxs-lookup"><span data-stu-id="e6a4b-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="e6a4b-191">Ligne orange: réponse eDisovery-données de réponse à la requête eDiscovery</span><span class="sxs-lookup"><span data-stu-id="e6a4b-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="e6a4b-192">Ligne verte: état requête/réponse-État eDiscovery requête/réponse données</span><span class="sxs-lookup"><span data-stu-id="e6a4b-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="e6a4b-193">Ligne violette: demande d’état/d’action Exchange-demande eDiscovery pour l’état de l’action pour le trafic Exchange.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="e6a4b-194">Ligne rouge: réponse d’état/de données Exchange-requête eDiscovery ou réponse d’État à partir d’Exchange.</span><span class="sxs-lookup"><span data-stu-id="e6a4b-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="e6a4b-195">Ligne noire en pointillés : Approbation de serveur à serveur/Oauth </span><span class="sxs-lookup"><span data-stu-id="e6a4b-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="e6a4b-196">Ligne noire continue : Analyse/résultats </span><span class="sxs-lookup"><span data-stu-id="e6a4b-196">Solid black line: Crawl/results</span></span> 
    

