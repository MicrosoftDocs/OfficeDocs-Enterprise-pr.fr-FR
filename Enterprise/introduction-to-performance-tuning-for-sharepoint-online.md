---
title: Introduction à l’optimisation des performances pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Cet article explique les aspects spécifiques, vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540333"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="bf52c-103">Introduction à l’optimisation des performances pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="bf52c-104">Cet article explique les aspects spécifiques, vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf52c-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="bf52c-105">Contenu de cet article</span><span class="sxs-lookup"><span data-stu-id="bf52c-105">In this article</span></span>

- <span data-ttu-id="bf52c-106">[Mesures de SharePoint Online](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) et [Conclusions atteint en raison de données](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="bf52c-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="bf52c-107">Utilisez un compte d’utilisateur standard lors de la vérification des performances</span><span class="sxs-lookup"><span data-stu-id="bf52c-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="bf52c-108">[Pour régler les performances des catégories de connexion](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [connexion au serveur](introduction-to-performance-tuning-for-sharepoint-online.md#server), de [connexion réseau](introduction-to-performance-tuning-for-sharepoint-online.md#network)et de [connexion du navigateur](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="bf52c-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="bf52c-109">Indicateurs de performances SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-109">SharePoint Online metrics</span></span>
<span data-ttu-id="bf52c-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-110"></span></span>

<span data-ttu-id="bf52c-111">Les indicateurs globaux suivants pour SharePoint Online fournissent des données réelles sur les performances :</span><span class="sxs-lookup"><span data-stu-id="bf52c-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="bf52c-112">La vitesse de chargement des pages</span><span class="sxs-lookup"><span data-stu-id="bf52c-112">How fast pages load</span></span>
    
- <span data-ttu-id="bf52c-113">Le nombre de boucles nécessaires par page</span><span class="sxs-lookup"><span data-stu-id="bf52c-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="bf52c-114">Les problèmes avec le service</span><span class="sxs-lookup"><span data-stu-id="bf52c-114">Issues with the service</span></span>
    
- <span data-ttu-id="bf52c-115">Autres éléments qui provoquent la dégradation des performances</span><span class="sxs-lookup"><span data-stu-id="bf52c-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="bf52c-116">Conclusions des données recueillies</span><span class="sxs-lookup"><span data-stu-id="bf52c-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="bf52c-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-117"></span></span>

<span data-ttu-id="bf52c-118">Les données nous ont permis de tirer les conclusions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf52c-118">The data tells us:</span></span>
  
- <span data-ttu-id="bf52c-119">Les performances de la plupart des pages sont bonnes sur SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf52c-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="bf52c-120">Le chargement des pages non personnalisées est très rapide.</span><span class="sxs-lookup"><span data-stu-id="bf52c-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="bf52c-121">Le chargement de OneDrive Entreprise, des sites d’équipe et des pages système, telles que _layouts, etc., est rapide.</span><span class="sxs-lookup"><span data-stu-id="bf52c-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="bf52c-122">Le chargement des pages SharePoint Online les plus lentes (à hauteur de 1 % de l’ensemble des pages) s’élève à plus de 5 000 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="bf52c-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="bf52c-p101">Pour effectuer un test simple d’évaluation, vous pouvez mesurer les performances en comparant le temps de chargement de votre propre portail au temps de chargement de la page d’accueil OneDrive Entreprise, car elle utilise peu de fonctionnalités personnalisées. Si vous contactez l’assistance technique pour des problèmes de performances réseau, il vous sera généralement demandé d’exécuter ce test pour commencer.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="bf52c-125">Utilisez un compte d’utilisateur standard lors de la vérification des performances</span><span class="sxs-lookup"><span data-stu-id="bf52c-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="bf52c-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-126"></span></span>

<span data-ttu-id="bf52c-127">Un administrateur de Collection de sites, propriétaire de Site, l’éditeur ou collaborateur appartiennent à des groupes de sécurité, disposer d’autorisations supplémentaires et donc des éléments supplémentaires SharePoint charges sur une page.</span><span class="sxs-lookup"><span data-stu-id="bf52c-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="bf52c-128">Ceci s’applique à SharePoint sur site et SharePoint Online, mais dans un scénario local les différences ne seront pas aussi facilement perceptibles comme dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf52c-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="bf52c-129">Pour pouvoir évaluer correctement comment une page effectue pour les utilisateurs, vous devez utiliser un compte d’utilisateur standard pour éviter de charger la création de contrôles et le trafic supplémentaire relatives aux groupes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="bf52c-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="bf52c-130">Catégories de connexion pour l’optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="bf52c-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="bf52c-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-131"></span></span>

<span data-ttu-id="bf52c-p102">Vous pouvez classer les connexions entre le serveur et l’utilisateur en trois composants principaux. Prenez-les en compte lors de la conception de pages SharePoint Online pour obtenir une vision globale du processus de chargement des pages.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="bf52c-134">**Server.** Les serveurs que Microsoft héberge dans les centres de données.</span><span class="sxs-lookup"><span data-stu-id="bf52c-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="bf52c-135">**Réseau.** Le réseau Microsoft, Internet et votre réseau local entre le centre de données et de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bf52c-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="bf52c-136">**Navigateur.** Où la page est chargée.</span><span class="sxs-lookup"><span data-stu-id="bf52c-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="bf52c-p103">Ces trois connexions présentent généralement cinq raisons susceptibles d’être à l’origine de 95 % de la lenteur de chargement des pages. Chacune de ces raisons est décrite dans cet article :</span><span class="sxs-lookup"><span data-stu-id="bf52c-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="bf52c-139">Problèmes de navigation</span><span class="sxs-lookup"><span data-stu-id="bf52c-139">Navigation issues</span></span>
    
- <span data-ttu-id="bf52c-140">Regroupement de contenu</span><span class="sxs-lookup"><span data-stu-id="bf52c-140">Content roll up</span></span>
    
- <span data-ttu-id="bf52c-141">Fichiers volumineux</span><span class="sxs-lookup"><span data-stu-id="bf52c-141">Large files</span></span>
    
- <span data-ttu-id="bf52c-142">Grand nombre de demandes au serveur</span><span class="sxs-lookup"><span data-stu-id="bf52c-142">Many requests to the server</span></span>
    
- <span data-ttu-id="bf52c-143">Traitement des composants WebPart</span><span class="sxs-lookup"><span data-stu-id="bf52c-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="bf52c-144">Connexion au serveur</span><span class="sxs-lookup"><span data-stu-id="bf52c-144">Server connection</span></span>
<span data-ttu-id="bf52c-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-145"></span></span>

<span data-ttu-id="bf52c-146">Un grand nombre des problèmes qui ont un impact négatif sur les performances de SharePoint local s’appliquent également à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf52c-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="bf52c-p104">Comme on pouvait s’y attendre, avec SharePoint local, vous contrôlez davantage les performances des serveurs. Avec SharePoint Online, ce n’est pas exactement la même chose. Plus vous demandez de travail à un serveur, plus le temps d’affichage d’une page sera long. Avec SharePoint, les pages complexes contenant plusieurs composants WebPart constituent la plus grande cause de ralentissement.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="bf52c-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-151">SharePoint Online</span></span>
  
![Capture d’écran du serveur en ligne](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="bf52c-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="bf52c-153">SharePoint</span></span>
  
![Capture d’écran du serveur local](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="bf52c-p105">Avec SharePoint Online, certaines demandes de page peuvent réellement finir par appeler plusieurs serveurs. Vous pourriez vous retrouver avec une matrice de demandes entre serveurs pour une simple demande unique. Ces interactions pèsent sur le chargement des pages et ralentissent ce processus.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="bf52c-158">Voici quelques exemples de ces interactions de serveur à serveur :</span><span class="sxs-lookup"><span data-stu-id="bf52c-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="bf52c-159">Serveur web vers serveur SQL</span><span class="sxs-lookup"><span data-stu-id="bf52c-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="bf52c-160">Serveur web vers serveur d’applications</span><span class="sxs-lookup"><span data-stu-id="bf52c-160">Web to application servers</span></span>
    
<span data-ttu-id="bf52c-p106">Les interactions avec le serveur peuvent également être ralenties par les échecs liés au cache. Contrairement à SharePoint local, il est très peu probable que ce soit le même serveur qui vous fournisse une page que vous avez consultée précédemment. La mise en cache de l’objet est donc obsolète.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="bf52c-163">Connexion réseau</span><span class="sxs-lookup"><span data-stu-id="bf52c-163">Network connection</span></span>
<span data-ttu-id="bf52c-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-164"></span></span>

<span data-ttu-id="bf52c-p107">SharePoint local qui n’utilisent un réseau étendu, vous pouvez utiliser une connexion rapide entre des centres de données et les utilisateurs finaux. En règle générale, les éléments sont faciles à gérer à partir d’un point de vue du réseau.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="bf52c-167">Avec SharePoint Online, il existe d’autres facteurs à prendre en compte, par exemple :</span><span class="sxs-lookup"><span data-stu-id="bf52c-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="bf52c-168">Le réseau Microsoft</span><span class="sxs-lookup"><span data-stu-id="bf52c-168">The Microsoft network</span></span>
    
- <span data-ttu-id="bf52c-169">Internet</span><span class="sxs-lookup"><span data-stu-id="bf52c-169">The Internet</span></span>
    
- <span data-ttu-id="bf52c-170">Le fournisseur de services Internet</span><span class="sxs-lookup"><span data-stu-id="bf52c-170">The ISP</span></span>
    
<span data-ttu-id="bf52c-171">Quelle que soit la version de SharePoint (et le réseau) que vous utilisez, voici les principaux facteurs d’indisponibilité du réseau :</span><span class="sxs-lookup"><span data-stu-id="bf52c-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="bf52c-172">Charge utile de grande taille</span><span class="sxs-lookup"><span data-stu-id="bf52c-172">Large payload</span></span>
    
- <span data-ttu-id="bf52c-173">Grand nombre de fichiers</span><span class="sxs-lookup"><span data-stu-id="bf52c-173">Many files</span></span>
    
- <span data-ttu-id="bf52c-174">Grande distance physique pour atteindre le serveur</span><span class="sxs-lookup"><span data-stu-id="bf52c-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="bf52c-p108">Une fonctionnalité que vous pouvez tirer parti de SharePoint Online est CDN (Content Delivery Network) Microsoft. Un CDN est simplement un ensemble distribué de serveurs déployés dans plusieurs centres de données. Avec un CDN, contenu sur les pages peut être hébergé sur un serveur a presque atteint le client, même si le client est éloignée du serveur d’origine SharePoint. Microsoft utilisera cette plus à l’avenir pour stocker les instances locales des pages qui ne peuvent pas être personnalisées, par exemple la page d’accueil d’administration SharePoint Online. Pour plus d’informations sur CDN, voir [réseaux de distribution de contenu](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span><span class="sxs-lookup"><span data-stu-id="bf52c-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="bf52c-p109">Il existe un autre élément que vous devez connaître, même si vous ne pourrez sûrement rien y faire ; il s’agit de la vitesse de connexion de votre fournisseur de services Internet. Un simple outil de test de vitesse vous indiquera la vitesse de connexion.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="bf52c-182">Connexion du navigateur</span><span class="sxs-lookup"><span data-stu-id="bf52c-182">Browser connection</span></span>
<span data-ttu-id="bf52c-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="bf52c-183"></span></span>

<span data-ttu-id="bf52c-184">Il existe quelques facteurs de performances à prendre en compte concernant les navigateurs web.</span><span class="sxs-lookup"><span data-stu-id="bf52c-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="bf52c-p110">Visitez les pages complexes affecte les performances. La plupart des navigateurs ne disposez que d’un cache de petite taille (environ 90 Mo), lors de la moyenne page web est généralement environ 1,6 Mo. Cela n’est pas en long pour obtenir utilisé.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="bf52c-p111">Bande passante peut également être un problème. Par exemple, si un utilisateur est regarder des vidéos dans une autre session, cela affecte les performances de votre page SharePoint. Lorsque vous ne pouvez pas empêcher les utilisateurs de diffusion multimédia par flux, vous pouvez contrôler la façon dont une page se charge pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bf52c-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="bf52c-191">Consultez les articles suivants pour différentes techniques de personnalisation de la page SharePoint Online et d’autres meilleures pratiques pour vous aider à optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="bf52c-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="bf52c-192">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-193">Utilisez l’outil de diagnostic de la Page pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="bf52c-194">Optimisation des images pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-195">Différer le chargement des images et des éléments JavaScript dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-196">Minimisation et regroupement dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-197">Utilisation de réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="bf52c-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-198">À l’aide du composant WebPart de recherche au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="bf52c-199">La capacité de planification et de test SharePoint Online de charge</span><span class="sxs-lookup"><span data-stu-id="bf52c-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-200">Diagnostic des problèmes de performances avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-201">Utilisation du cache d’objets avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="bf52c-202">Procédure : éviter les limitations ou les blocages dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf52c-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

