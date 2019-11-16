---
title: Utilisation du composant WebPart de recherche de contenu au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Cet article explique comment augmenter les performances en remplaçant le composant WebPart de requête de contenu par le composant WebPart de recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
ms.openlocfilehash: e2a3a1dd5a0010fcf1bbf61a039ca1d23292f70d
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38077943"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Utilisation du composant WebPart de recherche de contenu au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online

Cet article explique comment augmenter les performances en remplaçant le composant WebPart de requête de contenu par le composant WebPart de recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
  
L’une des nouvelles fonctionnalités les plus puissantes de SharePoint Server 2013 et SharePoint Online est le composant WebPart de recherche de contenu (composant WebPart recherche). Ce composant WebPart utilise l’index de recherche pour récupérer rapidement les résultats présentés à l’utilisateur. Utilisez le composant WebPart recherche de contenu au lieu du composant WebPart de requête de contenu (CQWP) dans vos pages pour améliorer les performances de vos utilisateurs.
  
L’utilisation d’un composant WebPart de recherche de contenu sur un composant WebPart de requête de contenu entraîne presque toujours une amélioration considérable des performances de chargement de pages sur SharePoint Online. Il existe une configuration supplémentaire pour obtenir la bonne requête, mais les récompenses sont des performances accrues et des utilisateurs plus heureux.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparaison des gains de performances que vous obtenez en utilisant le composant WebPart de recherche de contenu au lieu du composant WebPart requête de contenu

Les exemples suivants montrent les gains de performances relatifs que vous pouvez recevoir lorsque vous utilisez un composant WebPart de recherche de contenu au lieu d’un composant WebPart de requête de contenu. Les effets sont plus évidents avec une structure de site complexe et des requêtes de contenu très étendues.
  
Cet exemple de site présente les caractéristiques suivantes :
  
- 8 niveaux de sous-sites.
    
- Répertorie les données à l’aide d’un type de contenu « fruit » personnalisé.
    
- Dans le composant WebPart, la requête de contenu est large et renvoie tous les éléments dont le type de contenu est « fruit ».
    
- L’exemple utilise uniquement 50 éléments sur les 8 sites. Les effets seront encore plus prononcés pour les sites avec davantage de contenu.
    
Voici une capture d’écran des résultats du composant WebPart de requête de contenu.
  
![Figure illustrant la requête de contenu pour le composant WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Dans Internet Explorer, utilisez l’onglet **réseau** des outils de développement F12 pour consulter les détails de l’en-tête de la réponse. Dans la capture d’écran suivante, la valeur de la **SPRequestDuration** pour ce chargement de page est de 924 millisecondes. 
  
![Capture d’écran montrant la durée de demande de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indique le volume de travail réalisé sur le serveur pour préparer la page. Le changement de contenu par composants WebPart de requête avec le contenu par composants WebPart de recherche réduit considérablement le temps nécessaire au rendu de la page. En revanche, une page avec un composant WebPart de recherche de contenu équivalent, renvoyant le même nombre de résultats a une valeur **SPRequestDuration** de 106 millisecondes, comme illustré dans cette capture d’écran : 
  
![Capture d’écran montrant la durée de demande de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Ajout d’un composant WebPart de recherche de contenu dans SharePoint Online

L’ajout d’un composant WebPart de recherche de contenu est très similaire à un composant WebPart de requête de contenu normal. Voir la section *« Ajouter un composant WebPart de recherche de contenu »* dans [Configure a Content Search Web part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Création de la requête de recherche appropriée pour votre composant WebPart de recherche de contenu

Une fois que vous avez ajouté un composant WebPart de recherche de contenu, vous pouvez affiner la recherche et renvoyer les éléments de votre choix. Pour obtenir des instructions détaillées sur la procédure à suivre, voir la section *« afficher du contenu en configurant une requête avancée dans un composant WebPart recherche de contenu »* dans [Configure a Content Search Web part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Outil de création et de test de requêtes

Pour obtenir un outil permettant de créer et de tester des requêtes complexes, consultez l' [outil de requête de recherche](https://sp2013searchtool.codeplex.com/) sur CodePlex. 
  

