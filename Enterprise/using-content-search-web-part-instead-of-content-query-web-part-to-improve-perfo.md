---
title: À l’aide du composant WebPart de recherche au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Cet article explique comment améliorer les performances en remplaçant le composant WebPart requête de contenu par le composant WebPart recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540643"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>À l’aide du composant WebPart de recherche au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online

Cet article explique comment améliorer les performances en remplaçant le composant WebPart requête de contenu par le composant WebPart recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
  
Parmi les nouvelles fonctionnalités de SharePoint Server 2013 et SharePoint Online plus puissantes est le composant WebPart de contenu recherche (CSWP). Ce composant WebPart utilise l’index de recherche pour extraire rapidement des résultats qui sont affichés à l’utilisateur. Utilisez le composant WebPart de recherche de contenu au lieu du contenu requête Web amélioration du composant dans vos pages pour améliorer les performances de vos utilisateurs.
  
À l’aide d’un composant WebPart de recherche sur un composant WebPart requête de contenu presque toujours entraînera sensiblement meilleures performances de chargement de page dans SharePoint Online. Il est une peu une configuration supplémentaire pour obtenir la requête droite, mais les récompenses des employés sont optimisation des performances et satisfaire les utilisateurs.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparer le gain de performances obtenus à partir de composant WebPart de recherche au lieu du composant WebPart requête de contenu

Les exemples suivants montrent les gains de performances relative que peut s’afficher lorsque vous utilisez un composant WebPart de recherche au lieu d’un composant WebPart requête de contenu. Les effets sont plus évidentes avec une structure de site complexes et les requêtes de contenu très large.
  
Cet exemple de site présente les caractéristiques suivantes :
  
- 8 niveaux de sous-sites.
    
- Listes à l’aide d’un type de contenu personnalisé « fruits ».
    
- Dans le composant WebPart, la requête de contenu est large, retourner tous les éléments dont le type de contenu de « fruits ».
    
- L’exemple utilise uniquement 50 éléments entre les 8 sites. Les effets seront encore plus prononcés pour les sites avec plus de contenu.
    
Voici une capture d’écran des résultats du composant WebPart requête de contenu.
  
![Figure illustrant la requête de contenu pour le composant WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Dans Internet Explorer, utilisez l’onglet **réseau** des outils de développement F12 pour examiner les détails de l’en-tête de réponse. Dans l’écran suivant, la valeur de la **SPRequestDuration** pour le chargement de cette page est 924 millisecondes. 
  
![Capture d’écran montrant la durée de demande de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indique la quantité de travail est effectuée sur le serveur afin de préparer la page. Composants WebPart requête de contenu avec des composants WebPart de recherche de contenu de commutation considérablement réduit le temps que nécessaire pour afficher la page. En revanche, une page avec un composant WebPart de recherche contenu équivalente, retourner le même nombre de résultats a la valeur **SPRequestDuration** 106 millisecondes comme indiqué dans cette capture d’écran : 
  
![Capture d’écran montrant la durée de demande de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Ajout d’un composant WebPart de recherche de contenu dans SharePoint Online

Ajout d’un composant WebPart de recherche est très similaire à un composant WebPart de requête de contenu régulière. Consultez la section *« Ajouter un composant recherche de contenu Web »* de [configurer un composant WebPart de recherche dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Création de la requête de recherche de droite pour votre composant WebPart recherche de contenu

Une fois que vous avez ajouté un composant WebPart de recherche, vous pouvez affiner la recherche et renvoyer les éléments souhaités. Pour obtenir des instructions détaillées sur la procédure à suivre, voir la section, *« Afficher le contenu en configurant une requête dans un composant WebPart de recherche avancée »* de [configurer un composant WebPart de recherche de contenu dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Créer et tester l’outil de requête

Pour un outil créer et tester des requêtes complexes, consultez l' [Outil de requête de recherche](https://sp2013searchtool.codeplex.com/) sur Codeplex. 
  

