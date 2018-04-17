---
title: Configurer la recherche de OneDrive pour l’entreprise Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur la façon de configurer la recherche dans un environnement multi-geo.
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="7b676-103">Configurer la recherche de OneDrive pour l’entreprise Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="7b676-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="7b676-104">Dans un environnement Multi-Geo SharePoint Online (OFS), une organisation peut avoir un locataire d’Office 365, mais stocker leur contenu SharePoint dans plusieurs régions géographiques - un emplacement central et un ou plusieurs par satellite géo emplacements.</span><span class="sxs-lookup"><span data-stu-id="7b676-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="7b676-p101">Chaque emplacement géographique a son propre index de recherche et le centre de recherche. Lorsqu’un utilisateur recherche, la requête est serveur pour tous les index, et les résultats renvoyés sont fusionnées.</span><span class="sxs-lookup"><span data-stu-id="7b676-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="7b676-p102">Par exemple, un utilisateur dans un emplacement géographique peut rechercher du contenu stocké dans un autre emplacement géographique ou de contenu sur un site SharePoint qui est limité à un emplacement géographique différent. Si l’utilisateur a accès à ce contenu, recherche affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="7b676-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="7b676-109">Qui recherche les clients dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="7b676-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="7b676-110">Ces clients peuvent renvoyer des résultats à partir de tous les emplacements de la zone géographique :</span><span class="sxs-lookup"><span data-stu-id="7b676-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="7b676-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7b676-111">OneDrive for Business</span></span>

-   <span data-ttu-id="7b676-112">Delve</span><span class="sxs-lookup"><span data-stu-id="7b676-112">Delve</span></span>

-   <span data-ttu-id="7b676-113">La page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="7b676-113">The SharePoint home page</span></span>

-   <span data-ttu-id="7b676-114">Le centre de recherche</span><span class="sxs-lookup"><span data-stu-id="7b676-114">The Search Center</span></span>

-   <span data-ttu-id="7b676-115">Applications de recherche personnalisées qui utilisent l’API de recherche de SharePoint</span><span class="sxs-lookup"><span data-stu-id="7b676-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="7b676-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7b676-116">OneDrive for Business</span></span>

<span data-ttu-id="7b676-117">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans OneDrive obtenir des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="7b676-118">Delve</span><span class="sxs-lookup"><span data-stu-id="7b676-118">Delve</span></span>

<span data-ttu-id="7b676-119">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans Delve obtenir des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="7b676-p103">Le flux Delve et la Fiche profil uniquement affichent les aperçus des fichiers qui sont stockés dans l’emplacement **central** . Pour les fichiers qui sont stockés dans des emplacements satellite géo, l’icône du type de fichier est affiché.</span><span class="sxs-lookup"><span data-stu-id="7b676-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="7b676-122">La page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="7b676-122">The SharePoint home page</span></span>

<span data-ttu-id="7b676-p104">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs verront news, sites récents et suivis à partir de plusieurs emplacements geo sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche sur la page d’accueil SharePoint, ils obtiendrez des résultats fusionnés à partir de plusieurs emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="7b676-125">Le centre de recherche</span><span class="sxs-lookup"><span data-stu-id="7b676-125">The Search Center</span></span>

<span data-ttu-id="7b676-p105">Après le Multi-Geo environnement a été configuré, chaque centre de recherche continue d’afficher uniquement les résultats à partir de leur propre emplacement géographique. Administrateurs doivent [Modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir des résultats à partir de tous les emplacements de la zone géographique. Par la suite, les utilisateurs qui recherche dans le centre de recherche affiche des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="7b676-129">Applications de recherche personnalisées</span><span class="sxs-lookup"><span data-stu-id="7b676-129">Custom search applications</span></span>

<span data-ttu-id="7b676-p106">Comme d’habitude, les applications de recherche personnalisées interagissent avec les index de recherche à l’aide de l’API de reste de recherche SharePoint existant. Pour obtenir des résultats à partir d’emplacements de geo tout ou partie, l’application doit [appeler l’API et inclure les nouveaux paramètres de requête Multi-Geo](#_Get_custom_search) dans la demande. Cela déclenche un ventilateur de la requête à tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="7b676-133">Quelle est la différence sur la recherche dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="7b676-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="7b676-134">Vous pouvez être familiarisé avec certaines fonctions de recherche fonctionnent différemment dans un environnement Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="7b676-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7b676-135"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="7b676-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="7b676-136"><strong>Comment cela fonctionne-t-il</strong></span><span class="sxs-lookup"><span data-stu-id="7b676-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="7b676-137"><strong>Solution de contournement</strong></span><span class="sxs-lookup"><span data-stu-id="7b676-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-138">Résultats de la promotion</span><span class="sxs-lookup"><span data-stu-id="7b676-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="7b676-p107">Vous pouvez créer des règles de requête avec les résultats promus à différents niveaux : pour le locataire ensemble, pour une collection de sites ou pour un site. Dans un environnement Multi-Geo, définir des résultats promues au niveau des <strong>clients</strong> si vous souhaitez promouvoir les résultats pour les centres de recherche dans <strong>tous les</strong> emplacements de la zone géographique. Si vous <strong>seulement</strong> souhaitez promouvoir les résultats dans le centre de recherche qui se trouve dans l’emplacement géographique de la collection de sites ou un site, définir les résultats au niveau du <strong>site</strong> ou de <strong>collection de sites</strong> .</span><span class="sxs-lookup"><span data-stu-id="7b676-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="7b676-142">Si vous n’avez pas besoin des résultats différents promues par emplacement géographique, par exemple des règles différentes pour les déplacements, nous vous recommandons de définir promu les résultats au niveau du client.</span><span class="sxs-lookup"><span data-stu-id="7b676-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7b676-143">Raffineurs de recherche</span><span class="sxs-lookup"><span data-stu-id="7b676-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="7b676-p108">La recherche renvoie les raffineurs de tous les emplacements géographique d’un client et puis les agrège. L’agrégation est un maximum d’efforts, ce qui signifie que le nombre de raffineur ne peut pas précis à 100 %. La plupart des scénarios piloté par recherche, cette précision est suffisante.</span><span class="sxs-lookup"><span data-stu-id="7b676-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="7b676-147">Pour les applications pilotées par recherche dépendant de l’exhaustivité de raffineur, interroger chaque emplacement géographique indépendamment sans utiliser Multi-Geo Fanout.</span><span class="sxs-lookup"><span data-stu-id="7b676-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="7b676-148">Recherche de multi-Geo ne prend pas en charge la dynamique la création de compartiments pour les raffineurs numériques.</span><span class="sxs-lookup"><span data-stu-id="7b676-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="7b676-149">Utilisez le <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre de « Discretize »</a> pour les raffineurs numériques.</span><span class="sxs-lookup"><span data-stu-id="7b676-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7b676-150">ID de document</span><span class="sxs-lookup"><span data-stu-id="7b676-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="7b676-151">Si vous développez une application pilotée par recherche qui dépend des numéros de document, notez que les numéros de document dans un environnement Multi-Geo ne sont pas uniques dans tous les magasins de géo, ils sont uniques par les emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="7b676-p109">Nous avons ajouté une colonne qui identifie l’emplacement géographique. Utilisez cette colonne pour atteindre l’unicité. Cette colonne est nommée « GeoLocationSource ».</span><span class="sxs-lookup"><span data-stu-id="7b676-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-155">Nombre de résultats</span><span class="sxs-lookup"><span data-stu-id="7b676-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="7b676-156">La page de résultats affiche les résultats combinés à partir de l’emplacement géographique, mais il n’est pas possible de la page au-delà de 500 résultats.</span><span class="sxs-lookup"><span data-stu-id="7b676-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="7b676-157">Ce qui n’est pas pris en charge pour les recherches dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="7b676-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="7b676-158">Certaines des fonctionnalités de recherche, vous pouvez être familiarisé avec, ne sont pas pris en charge dans un environnement Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="7b676-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7b676-159"><strong>Fonctionnalité de recherche</strong></span><span class="sxs-lookup"><span data-stu-id="7b676-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="7b676-160"><strong>Remarque</strong></span><span class="sxs-lookup"><span data-stu-id="7b676-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-161">Authentification d’application uniquement</span><span class="sxs-lookup"><span data-stu-id="7b676-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="7b676-162">App uniquement l’authentification (accès privilégié à partir des services) n’est pas pris en charge dans la recherche de Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="7b676-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7b676-163">Utilisateurs invités</span><span class="sxs-lookup"><span data-stu-id="7b676-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="7b676-164">Les utilisateurs invités obtiennent uniquement des résultats à partir de l’emplacement géographique qui ils recherchent à partir de.</span><span class="sxs-lookup"><span data-stu-id="7b676-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="7b676-165">Fonctionnement de recherche de fait dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="7b676-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="7b676-166">**Tous les** clients recherche utilisent les API de reste de recherche SharePoint existante pour interagir avec les index de recherche.</span><span class="sxs-lookup"><span data-stu-id="7b676-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="7b676-167">Un client recherche appelle le point de terminaison de recherche reste avec la propriété de requête EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="7b676-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="7b676-168">La requête est envoyée à tous les emplacements de geo dans le locataire.</span><span class="sxs-lookup"><span data-stu-id="7b676-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="7b676-169">Résultats de la recherche à partir de chaque emplacement géographique sont fusionnées et classés.</span><span class="sxs-lookup"><span data-stu-id="7b676-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="7b676-170">Le client obtient des résultats de la recherche unifiée.</span><span class="sxs-lookup"><span data-stu-id="7b676-170">The client gets unified search results.</span></span>



<span data-ttu-id="7b676-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notez que nous ne pas fusionner les résultats de recherche jusqu'à ce que nous avons reçu les résultats à partir de tous les emplacements de la zone géographique. Cela signifie que les recherches Multi-Geo ont latence supplémentaire par rapport aux recherches dans un environnement avec geo qu’un seul emplacement.</span><span class="sxs-lookup"><span data-stu-id="7b676-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="7b676-173">Obtenir un centre de recherche pour afficher les résultats de tous les emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="7b676-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="7b676-174">Chaque centre de recherche possède plusieurs secteurs, et vous devez définir individuellement chaque vertical.</span><span class="sxs-lookup"><span data-stu-id="7b676-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="7b676-175">Assurez-vous que vous effectuez ces étapes avec un compte qui dispose des autorisations nécessaires pour modifier la page de résultats de la recherche et le composant WebPart résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="7b676-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="7b676-176">Accédez à la page de résultats de la recherche (voir la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de recherche des pages de résultats)</span><span class="sxs-lookup"><span data-stu-id="7b676-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="7b676-p111">Sélectionnez vertical pour définir, cliquez sur icône engrenage de **paramètres** dans l’angle supérieur droit, puis cliquez sur **Modifier la Page**. La page de résultats de recherche s’ouvre en mode édition.</span><span class="sxs-lookup"><span data-stu-id="7b676-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="7b676-p112">Dans le composant WebPart résultats de recherche, déplacez le pointeur vers le haut, à droite du composant WebPart, cliquez sur la flèche et puis cliquez sur **Modifier des composants WebPart** dans le menu. Le volet d’outils composant WebPart résultats de la recherche s’affiche sous le ruban dans la partie supérieure droite de la page.![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="7b676-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="7b676-181">Dans le volet d’outils composant WebPart, dans la section **paramètres** , sous **paramètres de contrôle des résultats**, sélectionnez **Multi-Geo afficher les résultats** pour obtenir le composant WebPart résultats de recherche pour afficher les résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="7b676-182">Cliquez sur **OK** pour enregistrer vos modifications et fermer le volet d’outils composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="7b676-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="7b676-183">Vérifiez vos modifications dans le composant WebPart résultats de la recherche en cliquant sur **Archiver** dans l’onglet de Page du menu principal.</span><span class="sxs-lookup"><span data-stu-id="7b676-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="7b676-184">Publier les modifications en utilisant le lien fourni dans la note en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="7b676-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="7b676-185">Obtenir les applications de recherche personnalisées pour afficher les résultats de tout ou partie des emplacements geo</span><span class="sxs-lookup"><span data-stu-id="7b676-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="7b676-p113">Applications de recherche personnalisées obtenir des résultats à partir d’emplacements de geo tous ou certains, en spécifiant des paramètres de la requête avec la demande de l’API REST de recherche SharePoint. Selon les paramètres de requête, la requête est serveur à tous les emplacements de la zone géographique ou à certains emplacements de la zone géographique. Par exemple, si vous avez besoin uniquement d’interroger un sous-ensemble des emplacements geo pour rechercher des informations pertinentes, vous pouvez contrôler le facteur pyramidal de sortie uniquement ces. Si la demande réussit, l’API REST de recherche SharePoint renvoie des données de réponse.</span><span class="sxs-lookup"><span data-stu-id="7b676-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="7b676-190">Paramètres de la requête</span><span class="sxs-lookup"><span data-stu-id="7b676-190">Query parameters</span></span>

<span data-ttu-id="7b676-p114">EnableMultiGeoSearch - il s’agit d’une valeur de type Boolean qui spécifie si la requête doit être serveur pour les index des autres emplacements géographique du locataire Multi-Geo. Affectez-lui la valeur **true** pour déployer la requête ; **false** pour ne ventilateur pas la requête. La valeur par défaut est **false**. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique. Si vous utilisez le paramètre dans un environnement qui n’est pas de Multi-Geo, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7b676-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="7b676-p115">TypeClient - il s’agit d’une chaîne. Entrez un nom de client unique pour chaque application de recherche. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="7b676-p116">MultiGeoSearchConfiguration - il s’agit d’une liste facultative de la zone géographique des emplacements dans le Multi-Geo client pour déployer la requête à lorsque **EnableMultiGeoSearch** a la **valeur true**. Si vous ne spécifiez ce paramètre, ou laissez le champ vide, la requête est serveur à tous les emplacements de la zone géographique. Pour chaque emplacement géographique, entrez les éléments suivants, au format JSON :</span><span class="sxs-lookup"><span data-stu-id="7b676-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7b676-202">Élément</span><span class="sxs-lookup"><span data-stu-id="7b676-202">Item</span></span></th>
<th align="left"><span data-ttu-id="7b676-203">Description</span><span class="sxs-lookup"><span data-stu-id="7b676-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="7b676-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="7b676-205">L’emplacement géographique, par exemple NAM.</span><span class="sxs-lookup"><span data-stu-id="7b676-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7b676-206">Point de terminaison</span><span class="sxs-lookup"><span data-stu-id="7b676-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="7b676-207">Le point de terminaison pour se connecter à, par exemple.https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="7b676-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="7b676-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="7b676-209">Le GUID de la source de résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="7b676-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="7b676-p117">Si vous omettez de DataLocation ou point de terminaison, ou si une DataLocation est en double, la demande échoue. [Vous pouvez obtenir des informations sur le point de terminaison des emplacements de géographique d’un client à l’aide de Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="7b676-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="7b676-212">Données de réponse</span><span class="sxs-lookup"><span data-stu-id="7b676-212">Response data</span></span>

<span data-ttu-id="7b676-p118">MultiGeoSearchStatus – il s’agit d’une propriété qui retourne de l’API de recherche de SharePoint en réponse à une demande. La valeur de la propriété est une chaîne et renvoie les informations suivantes sur les résultats qui renvoie de l’API de recherche de SharePoint :</span><span class="sxs-lookup"><span data-stu-id="7b676-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7b676-215">Valeur</span><span class="sxs-lookup"><span data-stu-id="7b676-215">Value</span></span></th>
<th align="left"><span data-ttu-id="7b676-216">Description</span><span class="sxs-lookup"><span data-stu-id="7b676-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-217">Complet</span><span class="sxs-lookup"><span data-stu-id="7b676-217">Full</span></span></td>
<td align="left"><span data-ttu-id="7b676-218">Complet à partir de <strong>tous les</strong> résultats de l’emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="7b676-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7b676-219">Partielle</span><span class="sxs-lookup"><span data-stu-id="7b676-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="7b676-p119">Résultats partiels à partir d’un ou plusieurs emplacements de la zone géographique. Les résultats sont incomplets en raison d’une erreur temporaire.</span><span class="sxs-lookup"><span data-stu-id="7b676-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="7b676-222">Exécuter une requête via le service REST</span><span class="sxs-lookup"><span data-stu-id="7b676-222">Query using the REST service</span></span>

<span data-ttu-id="7b676-p120">Avec une demande GET, vous spécifiez les paramètres de requête dans l’URL. Avec une demande POST, vous transmettez les paramètres de requête dans le corps dans le format de Notation JSON (JavaScript Object).</span><span class="sxs-lookup"><span data-stu-id="7b676-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="7b676-225">En-têtes de demande</span><span class="sxs-lookup"><span data-stu-id="7b676-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7b676-226">Nom</span><span class="sxs-lookup"><span data-stu-id="7b676-226">Name</span></span></th>
<th align="left"><span data-ttu-id="7b676-227">Valeur</span><span class="sxs-lookup"><span data-stu-id="7b676-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7b676-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="7b676-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="7b676-229">application/json ; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="7b676-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="7b676-230">Exemple de demande GET qui est serveur à **tous les** emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="7b676-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="7b676-231">https:// \<clients\>/\_api/recherche/query?querytext = « sharepoint » & propriétés = 'EnableMultiGeoSearch:true' & TypeClient =' Mes\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="7b676-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="7b676-232">Exemple de demande GET pouvoir déployer vers **certains** emplacements geo</span><span class="sxs-lookup"><span data-stu-id="7b676-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="7b676-233">https:// <tenant>/_api/search/query?querytext = 'site' & TypeClient = 'my_client_id' & propriétés ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration : [{DataLocation\:« NAM »\,point de terminaison\:« https\: contosoNAM.sharepoint.com »\,SourceId\:« B81EAB55-3140-4312-B0F4-9459D1B4FFEE »}\,{DataLocation\:« Peut »\,point de terminaison\:« https\://contosoCAN.sharepoint-df.com »}]'</span><span class="sxs-lookup"><span data-stu-id="7b676-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="7b676-234">Exemple de requête POST qui est serveur à **tous les** emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="7b676-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="7b676-235">Exemple de requête POST qui est serveur à **certains** emplacements geo</span><span class="sxs-lookup"><span data-stu-id="7b676-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="7b676-236">Requête à l’aide de CSOM</span><span class="sxs-lookup"><span data-stu-id="7b676-236">Query using CSOM</span></span>

<span data-ttu-id="7b676-237">Voici un exemple de requête CSOM qui est serveur à **tous les** emplacements de la zone géographique :</span><span class="sxs-lookup"><span data-stu-id="7b676-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

