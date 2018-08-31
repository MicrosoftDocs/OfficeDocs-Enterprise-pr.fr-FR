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
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Utiliser des réseaux de livraison de contenu avec SharePoint Online

 **Résumé :** Cet article décrit comment vous pouvez les utiliser pour améliorer les performances de SharePoint Online et les réseaux de distribution de contenu (CDN). 
  
Dans les Communautés de développement web aujourd'hui, il existe plusieurs bibliothèques communes (tels que des fichiers CSS et JavaScript) que vous pouvez inclure dans votre solution SharePoint. La plupart de ces sont hébergées par Microsoft sur leurs CDN ASP. Cela signifie que vous pouvez faire référence à ces bibliothèques à partir de ces serveurs distribués et autoriser intégrés DNS des systèmes de routage d’internet trouver le serveur à l’utilisateur le plus proche. Les exemples dans cet article montrent comment la différence entre le téléchargement de la bibliothèque populaires jQuery à partir du serveur SharePoint Online et du CDN ASP est très importante. L’utilisateur peut avoir déjà également la version CDN mis en cache sur l’ordinateur local afin qu’ils n’ont pas à télécharger le fichier. Cela peut être important si vous avez des utilisateurs répartis dans le monde entier et éloigné du centre de données qui héberge votre site SharePoint Online.
  
Lorsque vous créez des pages pour SharePoint Online, la distance physique entre les utilisateurs et l’emplacement de l’instance de SharePoint Online peuvent avoir un impact négatif sur la latence. Cela est particulièrement important pour les organisations qui sont présentes dans le monde entier et pour lesquelles un site peut être hébergé sur un continent alors que des utilisateurs accèdent à son contenu de l’autre côté du globe. Les CDN permettent d’atténuer les problèmes engendrés par cette situation en hébergeant les ressources web les plus demandées sur d’autres emplacements plus proches des utilisateurs finals.
  
Dans la mesure où un CDN est un réseau mondial de serveurs qui hébergent les mêmes fichiers, les URL Internet menant vers des fichiers stockés sur les CDN sont interprétées par l’ordinateur client de sorte que le serveur le plus proche de l’utilisateur fournisse le fichier. Cette opération réduit considérablement les lenteurs causées par les allers-retours sur le réseau.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>Le défi que représente l’hébergement de sites SharePoint Online pour un public mondial

Les sites SharePoint Online sont hébergés dans des centres de données en fonction de l’emplacement (spécifié par l’utilisateur) sélectionné lorsque vous vous êtes inscrit à Office 365. Par exemple, si votre site est hébergé sur des serveurs aux États-Unis et que des utilisateurs accèdent au site depuis l’Asie de l’Est, des problèmes de latence peuvent survenir en raison de la distance que les données doivent parcourir par fibre optique.
  
Nombre de fichiers statique utilisé par l’interface utilisateur de SharePoint par défaut est déjà hébergé sur réseau CDN mondial de Microsoft. Cela améliore les performances au fil du temps. Toutefois, si vous utilisez les éléments populaires JavaScript et CSS (par exemple ; JQuery, Modernizr, démarrage ou ASP.NET Ajax) vous pouvez améliorer les temps de chargement de ces fichiers à l’aide disponible gratuitement CDN.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Avantages de l’utilisation de CDN pour accélérer la vitesse de téléchargement

À l’aide du CDN peut améliorer les temps de chargement de page pour plusieurs raisons. Une raison est que la distance entre le CDN et l’utilisateur peut être inférieure à la distance à l’instance de SharePoint Online. Ces réseaux est très distribuées et est également conçus pour que les heures de disponibilité et une réponse très élevés. Une autre raison est que si vous utilisez une bibliothèque de fichiers CSS populaires, conjointement avec un CDN, l’utilisateur peut avoir déjà la bibliothèque de mise en cache et ils ne doivent même télécharger tout.
  
Les captures d’écran suivantes illustrent les avantages de l’utilisation du CDN. Ces captures d’écran sont à partir de l’onglet **réseau** dans les outils de développement Internet Explorer 11. Ces captures d’écran affichent la latence de la bibliothèque populaires jQuery. Pour afficher cet écran, dans Internet Explorer, appuyez sur la touche **F12** et sélectionnez l’onglet **réseau** qui est symbolisée par une icône Wi-Fi. 
  
![Capture d’écran du réseau F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Cette capture d’écran montre la bibliothèque téléchargée vers la galerie de pages maîtres sur le site SharePoint Online proprement dit. Le temps que nécessaire pour télécharger la bibliothèque est 1,51 secondes.
  
![Capture d’écran du temps de chargement de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La deuxième capture d’écran montre le même fichier transmis par Microsoft du CDN. Cette fois-ci la latence est environ 496 millisecondes. Ceci est une grande amélioration et indique qu’une seconde entière est shaved désactive le temps total pour télécharger le contenu de la page.
  
![Capture d’écran du temps de chargement de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Utilisation des CDN avec SharePoint Server 2013

À l’aide du CDN uniquement significatif dans un contexte de SharePoint Online doit être évitée avec SharePoint Server 2013. Il s’agit, car tous les avantages autour de position géographique de ne pas avoir la valeur true si le serveur est situé sur site ou fermer géographiquement. En outre, s’il existe une connexion de réseau vers les serveurs où il est hébergé, le site peut être utilisé sans une connexion Internet et par conséquent ne peut pas récupérer les fichiers CDN. Dans le cas contraire, vous devez utiliser un CDN si disponible et stables pour la bibliothèque et les fichiers que vous avez besoin pour votre site.
  
## <a name="popular-cdns-and-how-to-use-them"></a>CDN populaires et leur utilisation

Microsoft Ajax CDN offre la plupart des bibliothèques populaires, y compris jQuery (et toutes ses autres bibliothèques), ASP.NET Ajax, programme d’amorçage, Knockout.js et bien plus encore.
  
Pour inclure ces scripts dans votre projet, il suffit de remplacer les références à ces bibliothèques accessibles au public par des références à l’adresse du CDN, au lieu de l’inclure directement dans votre projet. Par exemple, utilisez le code suivant pour créer un lien vers jQuery :
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Pour plus d’informations sur CDN, voir [réseaux de distribution de contenu](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Rubriques supplémentaires sur l’utilisation des CDN avec SharePoint

[Composant WebPart côté client d’hébergement à partir d’Office 365 CDN](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

