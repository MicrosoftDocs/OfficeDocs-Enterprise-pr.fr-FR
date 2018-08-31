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
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="c5022-103">À l’aide du composant WebPart de recherche au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5022-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="c5022-104">Cet article explique comment améliorer les performances en remplaçant le composant WebPart requête de contenu par le composant WebPart recherche de contenu dans SharePoint Server 2013 et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c5022-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="c5022-p101">Parmi les nouvelles fonctionnalités de SharePoint Server 2013 et SharePoint Online plus puissantes est le composant WebPart de contenu recherche (CSWP). Ce composant WebPart utilise l’index de recherche pour extraire rapidement des résultats qui sont affichés à l’utilisateur. Utilisez le composant WebPart de recherche de contenu au lieu du contenu requête Web amélioration du composant dans vos pages pour améliorer les performances de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c5022-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="c5022-p102">À l’aide d’un composant WebPart de recherche sur un composant WebPart requête de contenu presque toujours entraînera sensiblement meilleures performances de chargement de page dans SharePoint Online. Il est une peu une configuration supplémentaire pour obtenir la requête droite, mais les récompenses des employés sont optimisation des performances et satisfaire les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c5022-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="c5022-110">Comparer le gain de performances obtenus à partir de composant WebPart de recherche au lieu du composant WebPart requête de contenu</span><span class="sxs-lookup"><span data-stu-id="c5022-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="c5022-p103">Les exemples suivants montrent les gains de performances relative que peut s’afficher lorsque vous utilisez un composant WebPart de recherche au lieu d’un composant WebPart requête de contenu. Les effets sont plus évidentes avec une structure de site complexes et les requêtes de contenu très large.</span><span class="sxs-lookup"><span data-stu-id="c5022-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="c5022-113">Cet exemple de site présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5022-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="c5022-114">8 niveaux de sous-sites.</span><span class="sxs-lookup"><span data-stu-id="c5022-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="c5022-115">Listes à l’aide d’un type de contenu personnalisé « fruits ».</span><span class="sxs-lookup"><span data-stu-id="c5022-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="c5022-116">Dans le composant WebPart, la requête de contenu est large, retourner tous les éléments dont le type de contenu de « fruits ».</span><span class="sxs-lookup"><span data-stu-id="c5022-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="c5022-p104">L’exemple utilise uniquement 50 éléments entre les 8 sites. Les effets seront encore plus prononcés pour les sites avec plus de contenu.</span><span class="sxs-lookup"><span data-stu-id="c5022-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="c5022-119">Voici une capture d’écran des résultats du composant WebPart requête de contenu.</span><span class="sxs-lookup"><span data-stu-id="c5022-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Figure illustrant la requête de contenu pour le composant WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="c5022-p105">Dans Internet Explorer, utilisez l’onglet **réseau** des outils de développement F12 pour examiner les détails de l’en-tête de réponse. Dans l’écran suivant, la valeur de la **SPRequestDuration** pour le chargement de cette page est 924 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="c5022-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Capture d’écran montrant la durée de demande de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="c5022-p106">**SPRequestDuration** indique la quantité de travail est effectuée sur le serveur afin de préparer la page. Composants WebPart requête de contenu avec des composants WebPart de recherche de contenu de commutation considérablement réduit le temps que nécessaire pour afficher la page. En revanche, une page avec un composant WebPart de recherche contenu équivalente, retourner le même nombre de résultats a la valeur **SPRequestDuration** 106 millisecondes comme indiqué dans cette capture d’écran :</span><span class="sxs-lookup"><span data-stu-id="c5022-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Capture d’écran montrant la durée de demande de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="c5022-128">Ajout d’un composant WebPart de recherche de contenu dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5022-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="c5022-p107">Ajout d’un composant WebPart de recherche est très similaire à un composant WebPart de requête de contenu régulière. Consultez la section *« Ajouter un composant recherche de contenu Web »* de [configurer un composant WebPart de recherche dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="c5022-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="c5022-131">Création de la requête de recherche de droite pour votre composant WebPart recherche de contenu</span><span class="sxs-lookup"><span data-stu-id="c5022-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="c5022-p108">Une fois que vous avez ajouté un composant WebPart de recherche, vous pouvez affiner la recherche et renvoyer les éléments souhaités. Pour obtenir des instructions détaillées sur la procédure à suivre, voir la section, *« Afficher le contenu en configurant une requête dans un composant WebPart de recherche avancée »* de [configurer un composant WebPart de recherche de contenu dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="c5022-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="c5022-134">Créer et tester l’outil de requête</span><span class="sxs-lookup"><span data-stu-id="c5022-134">Query building and testing tool</span></span>

<span data-ttu-id="c5022-135">Pour un outil créer et tester des requêtes complexes, consultez l' [Outil de requête de recherche](https://sp2013searchtool.codeplex.com/) sur Codeplex.</span><span class="sxs-lookup"><span data-stu-id="c5022-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

