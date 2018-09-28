---
title: Utilisation du cache d’objets avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056163"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="4ada8-103">Utilisation du cache d’objets avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4ada8-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="4ada8-104">Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4ada8-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="4ada8-p101">Le fait de compter sur le cache d’objets a un impact négatif conséquent sur le déploiement SharePoint Online. réduira la fiabilité de votre page.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="4ada8-107">Comment le SharePoint Online et SharePoint Server 2013 objet cache fonctionne</span><span class="sxs-lookup"><span data-stu-id="4ada8-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="4ada8-p102">Lorsque SharePoint Server 2013 est hébergée sur site, le client a des serveurs web frontaux privée qui hébergent le cache d’objets. Cela signifie que le cache est dédié à un seul client et est limité uniquement par la quantité de mémoire est disponible et allouée au cache d’objets. Car un seul client est pris en charge dans le scénario locale les serveurs web frontaux ont généralement les utilisateurs effectuent des demandes pour les sites même indéfiniment. Cela signifie que le cache complète rapidement et reste complète des résultats de requête de liste et des objets SharePoint que vos utilisateurs demandent régulièrement.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Affiche le trafic et la charge vers les serveurs web frontaux locaux](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="4ada8-p103">Par conséquent, lorsqu’un utilisateur consulte une page pour la deuxième fois, le temps de chargement de la page diminue. Après au moins quatre chargements de la même page, la page est mise en cache sur tous les serveurs web frontaux.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="4ada8-p104">En revanche, dans SharePoint Online sont nombreux serveurs mais également davantage de sites. Chaque utilisateur peut se connecter à un autre serveur web frontal qui ne dispose pas le cache rempli. Ou, par exemple le cache sont rempli pour un serveur, mais l’utilisateur à ce serveur web frontal suivant demande une page à partir d’un autre site. Ou, même si l’utilisateur suivant demande la même page que sur leur visite précédente, ils sont à charge équilibrée pour un autre serveur web frontal qui ne possède pas de cette page dans son cache. Dans ce dernier cas, la mise en cache n’aide les utilisateurs à tout.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="4ada8-p105">Dans la figure suivante, chaque point représente une page qu’un utilisateur demande et l’emplacement où elle est mise en cache. Les différentes couleurs représentent plusieurs clients qui se partagent l’infrastructure SaaS.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Affiche les résultats de la mise en cache d’objets dans SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="4ada8-p106">Comme vous pouvez le constater dans le diagramme, les risques d’un utilisateur donné en appuyant sur un serveur avec la version en cache de leur page sont très faible. En outre, en raison de la grande débit et fait que les serveurs sont partagées entre plusieurs sites, le cache ne dure depuis longtemps bien espace uniquement pour la mise en cache est disponible.</span><span class="sxs-lookup"><span data-stu-id="4ada8-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="4ada8-125">Ces différents points démontrent que pour assurer une expérience utilisateur de qualité et un temps de chargement des pages efficace dans SharePoint Online, il n’est pas pertinent de compter sur la mise en cache des objets des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4ada8-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="4ada8-126">Alors, si nous ne pouvons pas compter sur le cache d’objets pour améliorer les performances dans SharePoint Online, que devons-nous utiliser ?</span><span class="sxs-lookup"><span data-stu-id="4ada8-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="4ada8-p107">Puisque nous ne recommandons pas de compter sur la mise en cache dans SharePoint Online, vous devez évaluer les autres approches de conception pour les personnalisations SharePoint qui utilisent le cache d’objets. Pour résoudre les problèmes de performances et obtenir des résultats satisfaisants pour les utilisateurs, vous devez donc utiliser des approches qui ne reposent pas sur la mise en cache d’objets. Ces approches font l’objet d’autres articles de cette série, dont notamment :</span><span class="sxs-lookup"><span data-stu-id="4ada8-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="4ada8-130">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4ada8-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="4ada8-131">Minimisation et regroupement dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4ada8-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="4ada8-132">Utilisation de réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="4ada8-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="4ada8-133">Différer le chargement des images et des éléments JavaScript dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4ada8-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

