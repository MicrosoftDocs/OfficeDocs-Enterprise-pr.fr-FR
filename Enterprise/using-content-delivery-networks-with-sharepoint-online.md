---
title: Utiliser des réseaux de livraison de contenu avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Résumé : Cet article décrit comment vous pouvez les utiliser pour améliorer les performances de SharePoint Online et les réseaux de distribution de contenu (CDN).'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540436"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="465e6-103">Utiliser des réseaux de livraison de contenu avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="465e6-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="465e6-104">**Résumé :** Cet article décrit comment vous pouvez les utiliser pour améliorer les performances de SharePoint Online et les réseaux de distribution de contenu (CDN).</span><span class="sxs-lookup"><span data-stu-id="465e6-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="465e6-p101">Dans les Communautés de développement web aujourd'hui, il existe plusieurs bibliothèques communes (tels que des fichiers CSS et JavaScript) que vous pouvez inclure dans votre solution SharePoint. La plupart de ces sont hébergées par Microsoft sur leurs CDN ASP. Cela signifie que vous pouvez faire référence à ces bibliothèques à partir de ces serveurs distribués et autoriser intégrés DNS des systèmes de routage d’internet trouver le serveur à l’utilisateur le plus proche. Les exemples dans cet article montrent comment la différence entre le téléchargement de la bibliothèque populaires jQuery à partir du serveur SharePoint Online et du CDN ASP est très importante. L’utilisateur peut avoir déjà également la version CDN mis en cache sur l’ordinateur local afin qu’ils n’ont pas à télécharger le fichier. Cela peut être important si vous avez des utilisateurs répartis dans le monde entier et éloigné du centre de données qui héberge votre site SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="465e6-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="465e6-p102">Lorsque vous créez des pages pour SharePoint Online, la distance physique entre les utilisateurs et l’emplacement de l’instance de SharePoint Online peuvent avoir un impact négatif sur la latence. Cela est particulièrement important pour les organisations qui sont présentes dans le monde entier et pour lesquelles un site peut être hébergé sur un continent alors que des utilisateurs accèdent à son contenu de l’autre côté du globe. Les CDN permettent d’atténuer les problèmes engendrés par cette situation en hébergeant les ressources web les plus demandées sur d’autres emplacements plus proches des utilisateurs finals.</span><span class="sxs-lookup"><span data-stu-id="465e6-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="465e6-p103">Dans la mesure où un CDN est un réseau mondial de serveurs qui hébergent les mêmes fichiers, les URL Internet menant vers des fichiers stockés sur les CDN sont interprétées par l’ordinateur client de sorte que le serveur le plus proche de l’utilisateur fournisse le fichier. Cette opération réduit considérablement les lenteurs causées par les allers-retours sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="465e6-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="465e6-116">Le défi que représente l’hébergement de sites SharePoint Online pour un public mondial</span><span class="sxs-lookup"><span data-stu-id="465e6-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="465e6-p104">Les sites SharePoint Online sont hébergés dans des centres de données en fonction de l’emplacement (spécifié par l’utilisateur) sélectionné lorsque vous vous êtes inscrit à Office 365. Par exemple, si votre site est hébergé sur des serveurs aux États-Unis et que des utilisateurs accèdent au site depuis l’Asie de l’Est, des problèmes de latence peuvent survenir en raison de la distance que les données doivent parcourir par fibre optique.</span><span class="sxs-lookup"><span data-stu-id="465e6-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="465e6-p105">Nombre de fichiers statique utilisé par l’interface utilisateur de SharePoint par défaut est déjà hébergé sur réseau CDN mondial de Microsoft. Cela améliore les performances au fil du temps. Toutefois, si vous utilisez les éléments populaires JavaScript et CSS (par exemple ; JQuery, Modernizr, démarrage ou ASP.NET Ajax) vous pouvez améliorer les temps de chargement de ces fichiers à l’aide disponible gratuitement CDN.</span><span class="sxs-lookup"><span data-stu-id="465e6-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="465e6-122">Avantages de l’utilisation de CDN pour accélérer la vitesse de téléchargement</span><span class="sxs-lookup"><span data-stu-id="465e6-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="465e6-p106">À l’aide du CDN peut améliorer les temps de chargement de page pour plusieurs raisons. Une raison est que la distance entre le CDN et l’utilisateur peut être inférieure à la distance à l’instance de SharePoint Online. Ces réseaux est très distribuées et est également conçus pour que les heures de disponibilité et une réponse très élevés. Une autre raison est que si vous utilisez une bibliothèque de fichiers CSS populaires, conjointement avec un CDN, l’utilisateur peut avoir déjà la bibliothèque de mise en cache et ils ne doivent même télécharger tout.</span><span class="sxs-lookup"><span data-stu-id="465e6-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="465e6-p107">Les captures d’écran suivantes illustrent les avantages de l’utilisation du CDN. Ces captures d’écran sont à partir de l’onglet **réseau** dans les outils de développement Internet Explorer 11. Ces captures d’écran affichent la latence de la bibliothèque populaires jQuery. Pour afficher cet écran, dans Internet Explorer, appuyez sur la touche **F12** et sélectionnez l’onglet **réseau** qui est symbolisée par une icône Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="465e6-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Capture d’écran du réseau F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="465e6-p108">Cette capture d’écran montre la bibliothèque téléchargée vers la galerie de pages maîtres sur le site SharePoint Online proprement dit. Le temps que nécessaire pour télécharger la bibliothèque est 1,51 secondes.</span><span class="sxs-lookup"><span data-stu-id="465e6-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Capture d’écran du temps de chargement de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="465e6-p109">La deuxième capture d’écran montre le même fichier transmis par Microsoft du CDN. Cette fois-ci la latence est environ 496 millisecondes. Ceci est une grande amélioration et indique qu’une seconde entière est shaved désactive le temps total pour télécharger le contenu de la page.</span><span class="sxs-lookup"><span data-stu-id="465e6-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Capture d’écran du temps de chargement de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="465e6-139">Utilisation des CDN avec SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="465e6-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="465e6-p110">À l’aide du CDN uniquement significatif dans un contexte de SharePoint Online doit être évitée avec SharePoint Server 2013. Il s’agit, car tous les avantages autour de position géographique de ne pas avoir la valeur true si le serveur est situé sur site ou fermer géographiquement. En outre, s’il existe une connexion de réseau vers les serveurs où il est hébergé, le site peut être utilisé sans une connexion Internet et par conséquent ne peut pas récupérer les fichiers CDN. Dans le cas contraire, vous devez utiliser un CDN si disponible et stables pour la bibliothèque et les fichiers que vous avez besoin pour votre site.</span><span class="sxs-lookup"><span data-stu-id="465e6-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="465e6-144">CDN populaires et leur utilisation</span><span class="sxs-lookup"><span data-stu-id="465e6-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="465e6-145">Microsoft Ajax CDN offre la plupart des bibliothèques populaires, y compris jQuery (et toutes ses autres bibliothèques), ASP.NET Ajax, programme d’amorçage, Knockout.js et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="465e6-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="465e6-p111">Pour inclure ces scripts dans votre projet, il suffit de remplacer les références à ces bibliothèques accessibles au public par des références à l’adresse du CDN, au lieu de l’inclure directement dans votre projet. Par exemple, utilisez le code suivant pour créer un lien vers jQuery :</span><span class="sxs-lookup"><span data-stu-id="465e6-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="465e6-148">Pour plus d’informations sur CDN, voir [réseaux de distribution de contenu](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="465e6-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="465e6-149">Rubriques supplémentaires sur l’utilisation des CDN avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="465e6-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="465e6-150">Composant WebPart côté client d’hébergement à partir d’Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="465e6-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

