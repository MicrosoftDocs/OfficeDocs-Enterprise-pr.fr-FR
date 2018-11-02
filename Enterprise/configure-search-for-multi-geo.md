---
title: Configurer la recherche pour OneDrive Entreprise Multi-Géo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment configurer la recherche dans un environnement Multi-Géo.
ms.openlocfilehash: 5ca2a35385ab2c246b78dc8811e8435bbdec25c7
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849910"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="a8684-103">Configurer la recherche pour OneDrive Entreprise Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="a8684-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="a8684-104">Dans un environnement OneDrive Entreprise Multi-Géo, une organisation peut avoir un client Office 365, mais stocker son contenu OneDrive dans plusieurs emplacements géographiques : un emplacement central et un ou plusieurs emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="a8684-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="a8684-p101">Chaque emplacement géographique a son propre index de recherche et son centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est distribuée à tous les index et les résultats renvoyés sont fusionnés.</span><span class="sxs-lookup"><span data-stu-id="a8684-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="a8684-p102">Par exemple, un utilisateur dans un emplacement géographique peut rechercher du contenu stocké dans un autre emplacement géographique, ou du contenu sur un site SharePoint limité à un emplacement géographique différent. Si l’utilisateur a accès à ce contenu, la recherche affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="a8684-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="a8684-109">Quels sont les clients de recherche qui fonctionnent dans un environnement Multi-Géo ?</span><span class="sxs-lookup"><span data-stu-id="a8684-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="a8684-110">Ces clients peuvent renvoyer des résultats de tous les emplacements géographiques :</span><span class="sxs-lookup"><span data-stu-id="a8684-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="a8684-111">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="a8684-111">OneDrive for Business</span></span>

-   <span data-ttu-id="a8684-112">Delve</span><span class="sxs-lookup"><span data-stu-id="a8684-112">Delve</span></span>

-   <span data-ttu-id="a8684-113">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="a8684-113">The SharePoint home page</span></span>

-   <span data-ttu-id="a8684-114">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="a8684-114">The Search Center</span></span>

-   <span data-ttu-id="a8684-115">Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint</span><span class="sxs-lookup"><span data-stu-id="a8684-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="a8684-116">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="a8684-116">OneDrive for Business</span></span>

<span data-ttu-id="a8684-117">Dès que l’environnement Multi-Géo est configuré, les utilisateurs qui effectuent des recherches dans OneDrive obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="a8684-118">Delve</span><span class="sxs-lookup"><span data-stu-id="a8684-118">Delve</span></span>

<span data-ttu-id="a8684-119">Dès que l’environnement Multi-Géo est configuré, les utilisateurs qui effectuent des recherches dans Delve obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="a8684-p103">Le flux Delve et la carte de visite affichent uniquement les aperçus des fichiers qui sont stockés dans l’emplacement **central**. Pour les fichiers stockés dans des emplacements satellites, l’icône du type de fichier apparaît à la place.</span><span class="sxs-lookup"><span data-stu-id="a8684-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="a8684-122">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="a8684-122">The SharePoint home page</span></span>

<span data-ttu-id="a8684-p104">Dès que l’environnement Multi-Géo est configuré, les utilisateurs voient les actualités, les sites récents et les sites suivis de plusieurs emplacements géographiques sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche sur la page d’accueil SharePoint, ils obtiennent des résultats fusionnés provenant de plusieurs emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="a8684-125">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="a8684-125">The Search Center</span></span>

<span data-ttu-id="a8684-p105">Une fois que l’environnement Multi-Géo est configuré, chaque centre de recherche continue à afficher uniquement les résultats de son propre emplacement géographique. Les administrateurs doivent [modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir des résultats de tous les emplacements géographiques. Par la suite, les utilisateurs qui effectuent une recherche dans le centre de recherche obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="a8684-129">Applications de recherche personnalisée</span><span class="sxs-lookup"><span data-stu-id="a8684-129">Custom search applications</span></span>

<span data-ttu-id="a8684-p106">Comme d’habitude, les applications de recherche personnalisée interagissent avec les index de recherche en utilisant les API REST de recherche SharePoint existantes. Pour obtenir des résultats de tous les emplacements géographiques (ou une partie), l’application doit [appeler l’API et inclure les nouveaux paramètres de requête Multi-Géo](#_Get_custom_search) dans la demande. Cela déclenche une distribution ramifiée de la requête à tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="a8684-133">Quelles différences présente la recherche dans un environnement Multi-Géo ?</span><span class="sxs-lookup"><span data-stu-id="a8684-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="a8684-134">Certaines fonctionnalités de recherche auxquelles vous êtes habitué fonctionnent différemment dans un environnement Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="a8684-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8684-135"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="a8684-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a8684-136"><strong>Fonctionnement</strong></span><span class="sxs-lookup"><span data-stu-id="a8684-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="a8684-137"><strong>Solution de contournement</strong></span><span class="sxs-lookup"><span data-stu-id="a8684-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-138">Résultats promus</span><span class="sxs-lookup"><span data-stu-id="a8684-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="a8684-p107">Vous pouvez créer des règles de requête avec les résultats promus à différents niveaux : pour le client entier, pour une collection de sites ou pour un site. Dans un environnement Multi-Géo, définissez les résultats promus au niveau <strong>client</strong> si vous souhaitez promouvoir les résultats aux centres de recherche dans <strong>tous</strong> les emplacements géographiques. Si vous souhaitez <strong>uniquement</strong> promouvoir les résultats dans le centre de recherche qui se trouve dans l’emplacement géographique de la collection de sites ou du site, définissez les résultats au niveau <strong>collection de sites</strong> ou <strong>site</strong>.</span><span class="sxs-lookup"><span data-stu-id="a8684-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="a8684-142">Si vous n’avez pas besoin de différents résultats promus par emplacement géographique (par exemple, des règles différentes pour les déplacements), nous vous recommandons de définir les résultats promus au niveau du client.</span><span class="sxs-lookup"><span data-stu-id="a8684-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8684-143">Affinements de la recherche</span><span class="sxs-lookup"><span data-stu-id="a8684-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="a8684-p108">La recherche renvoie des affinements de tous les emplacements géographiques d’un client puis les regroupe. Le regroupement est ce qu’il y a de mieux, ce qui signifie que le nombre d’affinements peut ne pas être précis à 100 %. Pour la plupart des scénarios de recherche, cette précision est suffisante. </span><span class="sxs-lookup"><span data-stu-id="a8684-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="a8684-147">Pour les applications basées sur la recherche qui dépendent de l’intégralité de l’affinement, effectuez une requête indépendante sur chaque emplacement géographique sans utiliser la distribution ramifiée Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="a8684-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="a8684-148">La recherche Multi-Géo ne prend pas en charge la création dynamique de compartiments pour les affinements numériques.</span><span class="sxs-lookup"><span data-stu-id="a8684-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="a8684-149">Utilisez le <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre « Discretize »</a> pour les affinements numériques.</span><span class="sxs-lookup"><span data-stu-id="a8684-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8684-150">ID de document</span><span class="sxs-lookup"><span data-stu-id="a8684-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="a8684-151">Si vous développez une application basée sur la recherche qui dépend des ID de document, notez que les ID de document dans un environnement Multi-Géo ne sont pas uniques parmi les emplacements géographiques mais par emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a8684-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="a8684-p109">Nous avons ajouté une colonne qui identifie l’emplacement géographique. Utilisez cette colonne à des fins d’unicité. Cette colonne s’intitule « GeoLocationSource ».</span><span class="sxs-lookup"><span data-stu-id="a8684-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-155">Nombre de résultats</span><span class="sxs-lookup"><span data-stu-id="a8684-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="a8684-156">La page des résultats de recherche affiche les résultats combinés des emplacements géographiques, mais il n’est pas possible d’afficher plus de 500 résultats par page.</span><span class="sxs-lookup"><span data-stu-id="a8684-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="a8684-157">Quels sont les éléments qui ne sont pas pris en charge par la recherche dans un environnement Multi-Géo ?</span><span class="sxs-lookup"><span data-stu-id="a8684-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="a8684-158">Certaines fonctionnalités de recherche auxquelles vous êtes habitué ne sont pas prises en charge dans un environnement Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="a8684-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8684-159"><strong>Fonctionnalité de recherche</strong></span><span class="sxs-lookup"><span data-stu-id="a8684-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a8684-160"><strong>Remarque</strong></span><span class="sxs-lookup"><span data-stu-id="a8684-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-161">Authentification d’application uniquement</span><span class="sxs-lookup"><span data-stu-id="a8684-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="a8684-162">L’authentification d’application uniquement (accès privilégié depuis les services) n’est pas prise en charge dans la recherche Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="a8684-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8684-163">Utilisateurs invités</span><span class="sxs-lookup"><span data-stu-id="a8684-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="a8684-164">Les utilisateurs invités obtiennent uniquement les résultats de l’emplacement géographique duquel ils effectuent leur recherche.</span><span class="sxs-lookup"><span data-stu-id="a8684-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="a8684-165">Comment fonctionne la recherche dans un environnement Multi-Géo ?</span><span class="sxs-lookup"><span data-stu-id="a8684-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="a8684-166">**Tous** les clients de recherche utilisent les API REST de recherche SharePoint existantes pour interagir avec les index de recherche.</span><span class="sxs-lookup"><span data-stu-id="a8684-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="a8684-167">Un client de recherche appelle le point de terminaison REST de recherche avec la propriété de requête EnableMultiGeoSearch= true.</span><span class="sxs-lookup"><span data-stu-id="a8684-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="a8684-168">La requête est envoyée à tous les emplacements géographiques dans le client.</span><span class="sxs-lookup"><span data-stu-id="a8684-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="a8684-169">Les résultats de recherche de chaque emplacement géographique sont fusionnés et classés.</span><span class="sxs-lookup"><span data-stu-id="a8684-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="a8684-170">Le client obtient des résultats de recherche unifiés.</span><span class="sxs-lookup"><span data-stu-id="a8684-170">The client gets unified search results.</span></span>



<span data-ttu-id="a8684-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notez que nous ne fusionnons pas les résultats de recherche tant que nous n’avons pas reçu les résultats de tous les emplacements géographiques. Cela signifie que les recherches Multi-Géo ont une latence supplémentaire par rapport aux recherches effectuées dans un environnement qui ne compte qu’un seul emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a8684-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="a8684-173">Obtenir un centre de recherche pour afficher les résultats de tous les emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a8684-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="a8684-174">Chaque centre de recherche possède plusieurs secteurs verticaux et vous devez configurer chaque secteur vertical individuellement.</span><span class="sxs-lookup"><span data-stu-id="a8684-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="a8684-175">Vérifiez que vous effectuez ces étapes avec un compte doté d’autorisations pour modifier la page des résultats de la recherche et le composant WebPart Search Result.</span><span class="sxs-lookup"><span data-stu-id="a8684-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="a8684-176">Accédez à la page des résultats de la recherche (reportez-vous à la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) des pages des résultats de la recherche)</span><span class="sxs-lookup"><span data-stu-id="a8684-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="a8684-p111">Sélectionnez le secteur vertical à configurer, cliquez sur l’icône d’engrenage **Paramètres** située en haut à droite, puis cliquez sur **Modifier la page**. La page des résultats de la recherche s’ouvre en mode Édition.</span><span class="sxs-lookup"><span data-stu-id="a8684-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="a8684-p112">Dans le composant WebPart Résultats de la recherche, déplacez le pointeur vers le coin supérieur droit du composant WebPart, cliquez sur la flèche puis sur **Modifier le composant WebPart** dans le menu. Le volet des outils du composant WebPart Résultats de la recherche s’ouvre sous le ruban en haut à droite de la page. ![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="a8684-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="a8684-181">Dans le volet des outils du composant WebPart, dans la section **Paramètres**, sous **Paramètres de contrôle des résultats**, sélectionnez **Afficher les résultats multigéographiques** pour que le composant WebPart Résultats de la recherche affiche les résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="a8684-182">Cliquez sur **OK** pour enregistrer vos changements et fermer le volet des outils du composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="a8684-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="a8684-183">Vérifiez les changements que vous avez apportés au composant WebPart Résultats de la recherche en cliquant sur **Archiver** sur l’onglet Page du menu principal.</span><span class="sxs-lookup"><span data-stu-id="a8684-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="a8684-184">Publiez les changements en utilisant le lien fourni dans la note en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="a8684-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="a8684-185">Configurer des applications de recherche personnalisée pour qu’elles affichent les résultats de l’ensemble ou d’une partie des emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a8684-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="a8684-p113">Les applications de recherche personnalisée obtiennent les résultats de l’ensemble (ou d’une partie) des emplacements géographiques en spécifiant des paramètres de requête avec la demande à l’API REST de recherche SharePoint. Selon les paramètres, la requête est distribuée à tous les emplacements géographiques ou à certains emplacements géographiques. Par exemple, si vous devez seulement interroger un sous-ensemble des emplacements géographiques pour rechercher des informations pertinentes, vous pouvez contrôler la distribution ramifiée à ces derniers uniquement. Si la demande fonctionne, l’API REST de recherche SharePoint renvoie des données de réponse.</span><span class="sxs-lookup"><span data-stu-id="a8684-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="a8684-190">Paramètres de requête</span><span class="sxs-lookup"><span data-stu-id="a8684-190">Query parameters</span></span>

<span data-ttu-id="a8684-p114">EnableMultiGeoSearch : il s’agit d’une valeur booléenne qui indique si la requête doit être distribuée aux index d’autres emplacements géographiques du client Multi-Géo. Définissez-la sur **true** pour distribuer la requête et sur **false** pour ne pas la distribuer. La valeur par défaut est **false**. Si vous n’incluez pas ce paramètre, la requête n’est **pas** distribuée à d’autres emplacements géographiques. Si vous utilisez le paramètre dans un environnement qui n’est pas Multi-Géo, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="a8684-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="a8684-p115">ClientType : il s’agit une chaîne. Entrez un nom de client unique pour chaque application de recherche. Si vous n’incluez pas ce paramètre, la requête n’est **pas** distribuée à d’autres emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="a8684-p116">MultiGeoSearchConfiguration : il s’agit d’une liste facultative qui indique les emplacements géographiques dans le client Multi-Géo auxquels la requête doit être distribuée lorsque la valeur **EnableMultiGeoSearch** est définie sur **true**. Si vous n’incluez pas ce paramètre ou qu’il est vide, la requête est distribuée à tous les emplacements géographiques. Pour chaque emplacement géographique, entrez les éléments suivants, au format JSON :</span><span class="sxs-lookup"><span data-stu-id="a8684-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8684-202">Item</span><span class="sxs-lookup"><span data-stu-id="a8684-202">Item</span></span></th>
<th align="left"><span data-ttu-id="a8684-203">Description</span><span class="sxs-lookup"><span data-stu-id="a8684-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="a8684-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="a8684-205">L’emplacement géographique, par exemple NAM.</span><span class="sxs-lookup"><span data-stu-id="a8684-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8684-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="a8684-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="a8684-207">Le point de terminaison auquel se connecter, par exemple https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="a8684-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="a8684-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="a8684-209">GUID de l’origine des résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="a8684-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a8684-p117">Si vous omettez DataLocation ou EndPoint, ou si une DataLocation est dupliquée, la demande échoue. [Vous pouvez obtenir des informations sur le point de terminaison des emplacements géographiques d’un client à l’aide de Microsoft Graph](https://docs.microsoft.com/fr-FR/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="a8684-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/fr-FR/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="a8684-212">Données de réponse</span><span class="sxs-lookup"><span data-stu-id="a8684-212">Response data</span></span>

<span data-ttu-id="a8684-p118">MultiGeoSearchStatus : il s’agit d’une propriété renvoyée par l’API de recherche SharePoint en réponse à une demande. La valeur de la propriété est une chaîne et fournit les informations suivantes sur les résultats renvoyés par l’API de recherche SharePoint :</span><span class="sxs-lookup"><span data-stu-id="a8684-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8684-215">Valeur</span><span class="sxs-lookup"><span data-stu-id="a8684-215">Value</span></span></th>
<th align="left"><span data-ttu-id="a8684-216">Description</span><span class="sxs-lookup"><span data-stu-id="a8684-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-217">Complet</span><span class="sxs-lookup"><span data-stu-id="a8684-217">Full</span></span></td>
<td align="left"><span data-ttu-id="a8684-218">Résultats complets de <strong>tous</strong> les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a8684-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8684-219">Partielle</span><span class="sxs-lookup"><span data-stu-id="a8684-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="a8684-p119">Résultats partiels d’un ou plusieurs emplacements géographiques. Les résultats sont incomplets en raison d’une erreur temporaire.</span><span class="sxs-lookup"><span data-stu-id="a8684-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="a8684-222">Requête à l’aide du service REST</span><span class="sxs-lookup"><span data-stu-id="a8684-222">Query using the REST service</span></span>

<span data-ttu-id="a8684-p120">Avec une demande GET, spécifiez les paramètres de la requête dans l’URL. Avec une demande POST, vous transmettez les paramètres de la requête dans le corps au format JSON (JavaScript Object Notation).</span><span class="sxs-lookup"><span data-stu-id="a8684-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="a8684-225">En-têtes de demande</span><span class="sxs-lookup"><span data-stu-id="a8684-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8684-226">Nom</span><span class="sxs-lookup"><span data-stu-id="a8684-226">Name</span></span></th>
<th align="left"><span data-ttu-id="a8684-227">Valeur</span><span class="sxs-lookup"><span data-stu-id="a8684-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8684-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="a8684-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="a8684-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="a8684-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a8684-230">Exemple de demande GET distribuée à **tous** les emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a8684-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="a8684-231">https:// \<tenant\>/\_api/search/query?querytext=’sharepoint’&Properties=’EnableMultiGeoSearch:true’&ClientType=’my\_client\_id’</span><span class="sxs-lookup"><span data-stu-id="a8684-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="a8684-232">Exemple de demande GET à distribuer à **certains** emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a8684-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="a8684-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="a8684-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="a8684-p121">Des virgules et des points-virgules dans la liste des géo-localisations correspondants à la propriété MultiGeoSearchConfiguration précédés par le caractère**barre oblique inverse**. Ceci est dû aux demandes GET qui utilisent des points-virgules pour séparer les propriétés et des points-virgules pour séparer les arguments de propriétés. Sans barre oblique inverse comme caractère d’échappement, la propriété MultiGeoSearchConfiguration est mal interprétée.</span><span class="sxs-lookup"><span data-stu-id="a8684-p121">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a8684-237">Exemple de demande POST distribuée à **tous** les géo-localisations</span><span class="sxs-lookup"><span data-stu-id="a8684-237">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="a8684-238">Exemple de demande POST distribuée à **certains** emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a8684-238">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="a8684-239">Requête utilisant CSOM</span><span class="sxs-lookup"><span data-stu-id="a8684-239">Query using CSOM</span></span>

<span data-ttu-id="a8684-240">Voici un exemple de requête CSOM distribuée à **tous** les emplacements géographiques :</span><span class="sxs-lookup"><span data-stu-id="a8684-240">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

