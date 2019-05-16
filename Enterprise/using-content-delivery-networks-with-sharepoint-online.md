---
title: Utiliser des réseaux de livraison de contenu avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Résumé: cet article décrit les réseaux de distribution de contenu (CDN) et explique comment vous pouvez les utiliser pour augmenter les performances de SharePoint Online.'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070580"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Utiliser des réseaux de livraison de contenu avec SharePoint Online

 **Résumé:** Cet article décrit les réseaux de distribution de contenu (CDN) et explique comment vous pouvez les utiliser pour augmenter les performances de SharePoint Online. 
  
Dans les communautés de développement Web actuelles, il existe de nombreuses bibliothèques communes (telles que les fichiers JavaScript et CSS) que vous pouvez inclure dans votre solution SharePoint. Un grand nombre de ces éléments sont hébergés par Microsoft sur leur CDN ASP. Cela signifie que vous pouvez référencer ces bibliothèques à partir de ces serveurs distribués et permettre aux systèmes de routage DNS intégrés à Internet de trouver le serveur le plus proche de votre utilisateur. Les exemples de cet article montrent comment la différence de temps entre le téléchargement de la célèbre bibliothèque jQuery à partir du serveur SharePoint Online et le CDN ASP est assez importante. L’utilisateur peut également disposer de la version de CDN mise en cache sur l’ordinateur local afin qu’il n’ait pas besoin de télécharger le fichier. Cela peut être important si vous avez des utilisateurs répartis dans le monde entier et loin du centre de contenu hébergeant votre site SharePoint Online.
  
Lors de la création de pages pour SharePoint Online, la latence peut être affectée par la distance physique entre vos utilisateurs et l’emplacement de l’instance de SharePoint Online. Ceci est particulièrement important pour les organisations qui ont une présence mondiale où un site peut être hébergé sur un continent, tandis que les utilisateurs de l’autre côté du monde accèdent à son contenu. CDN aide à atténuer cette situation en hébergeant certains éléments Web populaires dans différents emplacements, plus près des utilisateurs finaux.
  
Étant donné qu’un CDN est un réseau mondial de serveurs qui hébergent les mêmes fichiers, les URL Internet des fichiers stockés sur le CDN sont interprétées par l’ordinateur client de sorte que le serveur le plus proche de l’utilisateur serve le fichier. Cette opération permet de réduire considérablement les retards causés par les allers-retours réseau.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>Le défi d’héberger les sites SharePoint Online pour une audience globale

Les sites SharePoint Online sont hébergés dans des centres de donnée par rapport à l’emplacement (spécifié par l’utilisateur) sélectionné lors de votre inscription à Office 365. Par exemple, si votre site est sur des serveurs aux États-Unis et que des utilisateurs accèdent au site à partir de l’Asie de l’est, des problèmes de latence peuvent survenir en raison de la distance que les données doivent emprunter sur un câble fibre optique.
  
De nombreux fichiers statiques utilisés par l’interface utilisateur SharePoint par défaut sont déjà hébergés sur le réseau mondial de Microsoft de CDN. Cela permet d’améliorer les performances au fil du temps. Toutefois, si vous utilisez des éléments JavaScript et CSS populaires (par exemple, JQuery, Modernizr, bootstrap ou ASP.NET AJAX) vous pouvez améliorer les temps de chargement de ces fichiers à l’aide de la CDN disponible gratuitement.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Avantages de l’utilisation de CDN pour améliorer la vitesse de téléchargement

L’utilisation de CDN peut améliorer les temps de chargement des pages pour diverses raisons. L’une des raisons est que la distance entre le CDN et l’utilisateur peut être inférieure à la distance de l’instance de SharePoint Online. Ces réseaux sont hautement distribués et sont également conçus pour avoir des temps de disponibilité et de réponse très élevés. Une autre raison est que si vous utilisez une bibliothèque populaire de fichiers CSS, conjointement avec un CDN, il se peut que l’utilisateur ait déjà mis en cache la bibliothèque et qu’il n’ait même pas besoin de le télécharger.
  
Les captures d’écran suivantes illustrent les avantages de l’utilisation de CDN. Ces captures d’écran sont extraites de l’onglet **réseau** dans les outils de développement Internet Explorer 11. Ces captures d’écran montrent la latence sur la bibliothèque jQuery. Pour afficher cet écran, dans Internet Explorer, appuyez sur **F12** et sélectionnez l’onglet **réseau** qui est symbolisé par une icône Wi-Fi. 
  
![Capture d’écran du réseau F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Cette capture d’écran montre la bibliothèque téléchargée vers la Galerie de pages maîtres sur le site SharePoint Online proprement dit. Le temps nécessaire au chargement de la bibliothèque est de 1,51 secondes.
  
![Capture d’écran du temps de chargement de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La deuxième capture d’écran montre le même fichier fourni par le CDN de Microsoft. Cette fois, la latence est d’environ 496 millisecondes. Il s’agit d’une amélioration importante qui montre qu’une seconde entière est éclatée du temps total pour télécharger le contenu de la page.
  
![Capture d’écran du temps de chargement de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Utilisation de CDN avec SharePoint Server 2013

L’utilisation de CDN n’a de sens que dans un contexte SharePoint Online et doit être évitée avec SharePoint Server 2013. Cela est dû au fait que tous les avantages liés à l’emplacement géographique ne sont pas vrais si le serveur est situé localement ou géographiquement fermé. En outre, s’il existe une connexion réseau aux serveurs où elle est hébergée, le site peut être utilisé sans connexion Internet et par conséquent ne peut pas récupérer les fichiers CDN. Dans le cas contraire, vous devez utiliser un CDN s’il en existe une disponible et stable pour la bibliothèque et les fichiers dont vous avez besoin pour votre site.
  
## <a name="popular-cdns-and-how-to-use-them"></a>CDN populaires et comment les utiliser

Le CDN Ajax de Microsoft offre la plupart des bibliothèques populaires, notamment jQuery (et toutes ses autres bibliothèques), ASP.NET AJAX, bootstrap, Knockout. js, et bien d’autres encore.
  
Pour inclure ces scripts dans votre projet, il suffit de remplacer les références à ces bibliothèques disponibles publiquement par des références à l’adresse CDN au lieu de les inclure dans votre projet lui-même. Par exemple, utilisez le code suivant pour créer un lien vers jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Pour plus d’informations sur CDN, consultez la rubrique [Content Delivery Networks](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Autres rubriques sur l’utilisation de CDN avec SharePoint

[Hébergement du composant WebPart côté client à partir du CDN Office 365](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

