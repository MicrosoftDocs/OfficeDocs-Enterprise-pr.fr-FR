---
title: Introduction à l’optimisation des performances pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Cet article décrit les aspects spécifiques que vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
ms.openlocfilehash: 4743364f6e8a1e84800085d0875abad84491780b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067210"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="9c272-103">Introduction à l’optimisation des performances pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="9c272-104">Cet article décrit les aspects spécifiques que vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c272-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="9c272-105">Métriques SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-105">SharePoint Online metrics</span></span>

<span data-ttu-id="9c272-106">Les grandes mesures suivantes de SharePoint Online fournissent des données réelles sur les performances:</span><span class="sxs-lookup"><span data-stu-id="9c272-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="9c272-107">La vitesse de chargement des pages</span><span class="sxs-lookup"><span data-stu-id="9c272-107">How fast pages load</span></span>
    
- <span data-ttu-id="9c272-108">Nombre de boucles requises par page</span><span class="sxs-lookup"><span data-stu-id="9c272-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="9c272-109">Problèmes liés au service</span><span class="sxs-lookup"><span data-stu-id="9c272-109">Issues with the service</span></span>
    
- <span data-ttu-id="9c272-110">Autres facteurs entraînant une dégradation des performances</span><span class="sxs-lookup"><span data-stu-id="9c272-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="9c272-111">Conclusions établies en raison des données</span><span class="sxs-lookup"><span data-stu-id="9c272-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="9c272-112">Les données nous indiquent:</span><span class="sxs-lookup"><span data-stu-id="9c272-112">The data tells us:</span></span>
  
- <span data-ttu-id="9c272-113">La plupart des pages fonctionnent correctement sur SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c272-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="9c272-114">Les pages non personnalisées sont chargées très rapidement.</span><span class="sxs-lookup"><span data-stu-id="9c272-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="9c272-115">OneDrive entreprise, les sites d’équipe et les pages système, telles que _ layouts, etc., sont tous rapides à charger.</span><span class="sxs-lookup"><span data-stu-id="9c272-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="9c272-116">Le chargement des pages SharePoint Online les plus lentes est de plus de 5 000 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="9c272-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="9c272-117">Il est possible de mesurer les performances en comparant le temps de chargement de votre propre portail et le temps de chargement de la page d’accueil de OneDrive entreprise, car il utilise peu de fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9c272-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="9c272-118">Il s’agit souvent de la première étape que vous devez prendre en charge pour résoudre les problèmes de performances réseau.</span><span class="sxs-lookup"><span data-stu-id="9c272-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="9c272-119">Utiliser un compte d’utilisateur standard lors de la vérification des performances</span><span class="sxs-lookup"><span data-stu-id="9c272-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="9c272-120">Un administrateur de collection de sites, un propriétaire de site, un éditeur ou un collaborateur appartient à des groupes de sécurité supplémentaires, disposent d’autorisations supplémentaires et, par conséquent, ont des éléments supplémentaires chargés par SharePoint sur une page.</span><span class="sxs-lookup"><span data-stu-id="9c272-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="9c272-121">Ceci s’applique à SharePoint Online et SharePoint Online, mais dans un scénario local, les différences ne seront pas aussi facilement remarquées que dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c272-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="9c272-122">Pour évaluer correctement l’exécution d’une page pour les utilisateurs, vous devez utiliser un compte d’utilisateur standard afin d’éviter de charger les contrôles de création et le trafic supplémentaire lié aux groupes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9c272-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="9c272-123">Catégories de connexion pour le réglage des performances</span><span class="sxs-lookup"><span data-stu-id="9c272-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="9c272-124">Vous pouvez catégoriser les connexions entre le serveur et l’utilisateur en trois composants principaux.</span><span class="sxs-lookup"><span data-stu-id="9c272-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="9c272-125">Tenez compte de ces éléments lors de la conception de pages SharePoint Online pour un aperçu des temps de chargement.</span><span class="sxs-lookup"><span data-stu-id="9c272-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="9c272-126">**Server (serveur** ) Les serveurs que Microsoft héberge dans les centres de contenu.</span><span class="sxs-lookup"><span data-stu-id="9c272-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="9c272-127">**Réseau** Le réseau Microsoft, Internet et votre réseau local entre le centre de connaissances et vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9c272-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="9c272-128">**Explorateur** Emplacement de chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="9c272-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="9c272-129">Au sein de ces trois connexions, il existe généralement cinq raisons qui causent 95% de pages chargées.</span><span class="sxs-lookup"><span data-stu-id="9c272-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="9c272-130">Chacune de ces raisons est abordée dans cet article:</span><span class="sxs-lookup"><span data-stu-id="9c272-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="9c272-131">Problèmes de navigation</span><span class="sxs-lookup"><span data-stu-id="9c272-131">Navigation issues</span></span>
    
- <span data-ttu-id="9c272-132">Cumul de contenu</span><span class="sxs-lookup"><span data-stu-id="9c272-132">Content roll up</span></span>
    
- <span data-ttu-id="9c272-133">Fichiers volumineux</span><span class="sxs-lookup"><span data-stu-id="9c272-133">Large files</span></span>
    
- <span data-ttu-id="9c272-134">Nombreuses requêtes adressées au serveur</span><span class="sxs-lookup"><span data-stu-id="9c272-134">Many requests to the server</span></span>
    
- <span data-ttu-id="9c272-135">Traitement des composants WebPart</span><span class="sxs-lookup"><span data-stu-id="9c272-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="9c272-136">Connexion au serveur</span><span class="sxs-lookup"><span data-stu-id="9c272-136">Server connection</span></span>

<span data-ttu-id="9c272-137">De nombreux problèmes qui affectent les performances avec SharePoint en local s’appliquent également à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c272-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="9c272-138">Comme vous pouvez vous y attendre, vous avez beaucoup plus de contrôle sur la façon dont les serveurs effectuent SharePoint sur site.</span><span class="sxs-lookup"><span data-stu-id="9c272-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="9c272-139">Avec SharePoint Online, les choses sont un peu différentes.</span><span class="sxs-lookup"><span data-stu-id="9c272-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="9c272-140">Plus le nombre de tâches que vous effectuez sur un serveur est long, plus le rendu d’une page est long.</span><span class="sxs-lookup"><span data-stu-id="9c272-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="9c272-141">Avec SharePoint, le plus grand coupable de ce sujet sont des pages complexes avec plusieurs composants WebPart.</span><span class="sxs-lookup"><span data-stu-id="9c272-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="9c272-142">SharePoint Server en local</span><span class="sxs-lookup"><span data-stu-id="9c272-142">SharePoint Server on-premises</span></span>
  
![Capture d’écran du serveur local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="9c272-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-144">SharePoint Online</span></span>
  
![Capture d’écran du serveur en ligne](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="9c272-146">Avec SharePoint Online, certaines demandes de page peuvent réellement appeler plusieurs serveurs.</span><span class="sxs-lookup"><span data-stu-id="9c272-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="9c272-147">Vous pouvez obtenir une matrice des demandes entre les serveurs pour une demande individuelle.</span><span class="sxs-lookup"><span data-stu-id="9c272-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="9c272-148">Ces interactions sont coûteuses du point de vue du chargement des pages et rendent les choses plus lentes.</span><span class="sxs-lookup"><span data-stu-id="9c272-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="9c272-149">Voici quelques exemples d’interactions serveur à serveur:</span><span class="sxs-lookup"><span data-stu-id="9c272-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="9c272-150">Web vers les serveurs SQL</span><span class="sxs-lookup"><span data-stu-id="9c272-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="9c272-151">Web vers les serveurs d’applications</span><span class="sxs-lookup"><span data-stu-id="9c272-151">Web to application servers</span></span>
    
<span data-ttu-id="9c272-152">Les échecs de cache sont les autres opérations qui ralentissent les interactions du serveur.</span><span class="sxs-lookup"><span data-stu-id="9c272-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="9c272-153">Contrairement à SharePoint sur site, il existe une très faible probabilité que vous atteigniez le même serveur pour une page que vous avez visitée précédemment; Cela rend la mise en cache d’objets obsolète.</span><span class="sxs-lookup"><span data-stu-id="9c272-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="9c272-154">Connexion réseau </span><span class="sxs-lookup"><span data-stu-id="9c272-154">Network connection</span></span>

<span data-ttu-id="9c272-155">Avec SharePoint sur site qui n’utilise pas de réseau étendu (WAN), vous pouvez utiliser une connexion à haut débit entre le centre de données et les utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="9c272-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="9c272-156">En règle générale, les choses sont faciles à gérer du point de vue du réseau.</span><span class="sxs-lookup"><span data-stu-id="9c272-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="9c272-157">Avec SharePoint Online, il existe quelques facteurs supplémentaires à prendre en compte; par exemple:</span><span class="sxs-lookup"><span data-stu-id="9c272-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="9c272-158">Le réseau Microsoft</span><span class="sxs-lookup"><span data-stu-id="9c272-158">The Microsoft network</span></span>
    
- <span data-ttu-id="9c272-159">Internet</span><span class="sxs-lookup"><span data-stu-id="9c272-159">The Internet</span></span>
    
- <span data-ttu-id="9c272-160">Le fournisseur de services Internet</span><span class="sxs-lookup"><span data-stu-id="9c272-160">The ISP</span></span>
    
<span data-ttu-id="9c272-161">Quelle que soit la version de SharePoint (et le réseau) que vous utilisez, les éléments qui entraînent généralement la disponibilité du réseau sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="9c272-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="9c272-162">Grande charge utile</span><span class="sxs-lookup"><span data-stu-id="9c272-162">Large payload</span></span>
    
- <span data-ttu-id="9c272-163">Nombreux fichiers</span><span class="sxs-lookup"><span data-stu-id="9c272-163">Many files</span></span>
    
- <span data-ttu-id="9c272-164">Grande distance physique vers le serveur</span><span class="sxs-lookup"><span data-stu-id="9c272-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="9c272-165">L’une des fonctionnalités que vous pouvez utiliser dans SharePoint Online est le réseau de distribution de contenu (CDN) Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c272-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="9c272-166">Un CDN est fondamentalement une collection distribuée de serveurs déployés sur plusieurs centres de contenu.</span><span class="sxs-lookup"><span data-stu-id="9c272-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="9c272-167">Avec un CDN, le contenu sur les pages peut être hébergé sur un serveur proche du client même si le client est éloigné du serveur SharePoint d’origine.</span><span class="sxs-lookup"><span data-stu-id="9c272-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="9c272-168">Microsoft utilisera cette version plus prochaine pour stocker les instances locales des pages qui ne peuvent pas être personnalisées, par exemple la page d’accueil de l’administration SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c272-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="9c272-169">Pour plus d’informations sur CDN, consultez la rubrique [Content Delivery Networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="9c272-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="9c272-170">La vitesse de connexion de votre fournisseur de services Internet (ISP) ne vous indiquera peut-être pas que vous devez prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="9c272-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="9c272-171">Un outil de test rapide vous indiquera la vitesse de connexion.</span><span class="sxs-lookup"><span data-stu-id="9c272-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="9c272-172">Connexion de navigateur</span><span class="sxs-lookup"><span data-stu-id="9c272-172">Browser connection</span></span>

<span data-ttu-id="9c272-173">Il existe quelques facteurs à prendre en compte pour les navigateurs Web du point de vue des performances.</span><span class="sxs-lookup"><span data-stu-id="9c272-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="9c272-174">La consultation des pages complexes affectera les performances.</span><span class="sxs-lookup"><span data-stu-id="9c272-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="9c272-175">La plupart des navigateurs ont seulement un petit cache (environ 90MB), tandis que la page Web moyenne est généralement d’environ 1,6 Mo.</span><span class="sxs-lookup"><span data-stu-id="9c272-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="9c272-176">L’utilisation de cette valeur n’est pas assez longue.</span><span class="sxs-lookup"><span data-stu-id="9c272-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="9c272-177">La bande passante peut également être un problème.</span><span class="sxs-lookup"><span data-stu-id="9c272-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="9c272-178">Par exemple, si un utilisateur regarde des vidéos dans une autre session, cela aura une incidence sur les performances de votre page SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9c272-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="9c272-179">Bien que vous ne puissiez pas empêcher les utilisateurs de diffuser des médias en continu, vous pouvez contrôler le chargement d’une page pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9c272-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="9c272-180">Consultez les articles suivants pour connaître les différentes techniques de personnalisation des pages SharePoint Online et d’autres meilleures pratiques pour obtenir des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="9c272-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="9c272-181">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-182">Utiliser l’outil de diagnostics de page pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="9c272-183">Optimisation des images pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-184">Différer le chargement des images et des éléments JavaScript dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-185">Minimisation et regroupement dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-186">Utilisation de réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="9c272-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-187">Utilisation du composant WebPart de recherche de contenu au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="9c272-188">Planification de la capacité et test de charge SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-189">Diagnostic des problèmes de performances avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-190">Utilisation du cache d’objets avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="9c272-191">Procédure : éviter les limitations ou les blocages dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c272-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

