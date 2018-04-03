---
title: Administration d’un environnement multi-geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenir des informations sur la façon de configurer la recherche dans un environnement multi-geo.
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="b816e-103">Configurer la recherche de OneDrive pour l’entreprise Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="b816e-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="b816e-104">Dans un environnement Multi-Geo SharePoint Online (OFS), une organisation peut avoir un locataire d’Office 365, mais stocker leur contenu SharePoint dans plusieurs régions géographiques - un emplacement central et un ou plusieurs par satellite géo emplacements.</span><span class="sxs-lookup"><span data-stu-id="b816e-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="b816e-p101">Chaque emplacement géographique a son propre index de recherche et le centre de recherche. Lorsqu’un utilisateur recherche, la requête est serveur pour tous les index, et les résultats renvoyés sont fusionnées.</span><span class="sxs-lookup"><span data-stu-id="b816e-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="b816e-p102">Par exemple, un utilisateur dans un emplacement géographique peut rechercher du contenu stocké dans un autre emplacement géographique ou de contenu sur un site SharePoint qui est limité à un emplacement géographique différent. Si l’utilisateur a accès à ce contenu, recherche affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="b816e-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="b816e-109">Qui recherche les clients dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="b816e-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="b816e-110">Ces clients peuvent renvoyer des résultats à partir de tous les emplacements de la zone géographique :</span><span class="sxs-lookup"><span data-stu-id="b816e-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="b816e-111">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="b816e-111">OneDrive for Business</span></span>

-   <span data-ttu-id="b816e-112">Delve</span><span class="sxs-lookup"><span data-stu-id="b816e-112">Delve</span></span>

-   <span data-ttu-id="b816e-113">La page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="b816e-113">The SharePoint home page</span></span>

-   <span data-ttu-id="b816e-114">Le centre de recherche</span><span class="sxs-lookup"><span data-stu-id="b816e-114">The Search Center</span></span>

-   <span data-ttu-id="b816e-115">Applications de recherche personnalisées qui utilisent l’API de recherche de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b816e-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="b816e-116">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="b816e-116">OneDrive for Business</span></span>

<span data-ttu-id="b816e-117">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans OneDrive obtenir des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="b816e-118">Delve</span><span class="sxs-lookup"><span data-stu-id="b816e-118">Delve</span></span>

<span data-ttu-id="b816e-119">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans Delve obtenir des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="b816e-p103">Le flux Delve et la Fiche profil uniquement affichent les aperçus des fichiers qui sont stockés dans l’emplacement **central** . Pour les fichiers qui sont stockés dans des emplacements satellite géo, l’icône du type de fichier est affiché.</span><span class="sxs-lookup"><span data-stu-id="b816e-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="b816e-122">La page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="b816e-122">The SharePoint home page</span></span>

<span data-ttu-id="b816e-p104">Dès que l’environnement Multi-Geo a été configuré, les utilisateurs verront news, sites récents et suivis à partir de plusieurs emplacements geo sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche sur la page d’accueil SharePoint, ils uniquement d’obtenir des résultats à partir de l’emplacement géographique SPHome index de recherche se trouve dans.</span><span class="sxs-lookup"><span data-stu-id="b816e-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use search box on the SharePoint home page, they only get results from the geo location SPHome search index is located in.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="b816e-125">Le centre de recherche</span><span class="sxs-lookup"><span data-stu-id="b816e-125">The Search Center</span></span>

<span data-ttu-id="b816e-p105">Après le Multi-Geo environnement a été configuré, chaque centre de recherche continue d’afficher uniquement les résultats à partir de leur propre emplacement géographique. Administrateurs doivent [Modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir des résultats à partir de tous les emplacements de la zone géographique. Par la suite, les utilisateurs qui recherche dans le centre de recherche affiche des résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="b816e-129">Applications de recherche personnalisées</span><span class="sxs-lookup"><span data-stu-id="b816e-129">Custom search applications</span></span>

<span data-ttu-id="b816e-p106">Comme d’habitude, les applications de recherche personnalisées interagissent avec les index de recherche à l’aide de l’API de reste de recherche SharePoint existant. Pour obtenir des résultats à partir d’emplacements de geo tout ou partie, l’application doit [appeler l’API et inclure les nouveaux paramètres de requête Multi-Geo](#_Get_custom_search) dans la demande. Cela déclenche un ventilateur de la requête à tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="b816e-133">Quelle est la différence sur la recherche dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="b816e-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="b816e-134">Vous pouvez être familiarisé avec certaines fonctions de recherche fonctionnent différemment dans un environnement Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="b816e-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b816e-135"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="b816e-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="b816e-136"><strong>Comment cela fonctionne-t-il</strong></span><span class="sxs-lookup"><span data-stu-id="b816e-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="b816e-137"><strong>Solution de contournement</strong></span><span class="sxs-lookup"><span data-stu-id="b816e-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-138">Résultats de la promotion</span><span class="sxs-lookup"><span data-stu-id="b816e-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="b816e-p107">Vous pouvez créer des règles de requête avec les résultats promus à différents niveaux : pour le locataire ensemble, pour une collection de sites ou pour un site. Dans un environnement Multi-Geo, définir des résultats promues au niveau des <strong>clients</strong> si vous souhaitez promouvoir les résultats pour les centres de recherche dans <strong>tous les</strong> emplacements de la zone géographique. Si vous <strong>seulement</strong> souhaitez promouvoir les résultats dans le centre de recherche qui se trouve dans l’emplacement géographique de la collection de sites ou un site, définir les résultats au niveau du <strong>site</strong> ou de <strong>collection de sites</strong> .</span><span class="sxs-lookup"><span data-stu-id="b816e-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="b816e-142">Si vous n’avez pas besoin des résultats différents promues par emplacement géographique, par exemple des règles différentes pour les déplacements, nous vous recommandons de définir promu les résultats au niveau du client.</span><span class="sxs-lookup"><span data-stu-id="b816e-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b816e-143">Raffineurs de recherche</span><span class="sxs-lookup"><span data-stu-id="b816e-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="b816e-p108">La recherche renvoie les raffineurs de tous les emplacements géographique d’un client et puis les agrège. L’agrégation est un maximum d’efforts, ce qui signifie que le nombre de raffineur ne peut pas précis à 100 %. La plupart des scénarios piloté par recherche, cette précision est suffisante.</span><span class="sxs-lookup"><span data-stu-id="b816e-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="b816e-147">Pour les applications pilotées par recherche dépendant de l’exhaustivité de raffineur, interroger chaque emplacement géographique indépendamment sans utiliser Multi-Geo Fanout.</span><span class="sxs-lookup"><span data-stu-id="b816e-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="b816e-148">Recherche de multi-Geo ne prend pas en charge la dynamique la création de compartiments pour les raffineurs numériques.</span><span class="sxs-lookup"><span data-stu-id="b816e-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="b816e-149">Utilisez le <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre de « Discretize »</a> pour les raffineurs numériques.</span><span class="sxs-lookup"><span data-stu-id="b816e-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b816e-150">ID de document</span><span class="sxs-lookup"><span data-stu-id="b816e-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="b816e-151">Si vous développez une application pilotée par recherche qui dépend des numéros de document, notez que les numéros de document dans un environnement Multi-Geo ne sont pas uniques dans tous les magasins de géo, ils sont uniques par les emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="b816e-p109">Nous avons ajouté une colonne qui identifie l’emplacement géographique. Utilisez cette colonne pour atteindre l’unicité. Cette colonne est nommée « GeoLocationSource ».</span><span class="sxs-lookup"><span data-stu-id="b816e-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-155">Nombre de résultats</span><span class="sxs-lookup"><span data-stu-id="b816e-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="b816e-156">La page de résultats affiche les résultats combinés à partir de l’emplacement géographique, mais il n’est pas possible de la page au-delà de 500 résultats.</span><span class="sxs-lookup"><span data-stu-id="b816e-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="b816e-157">Ce qui n’est pas pris en charge pour les recherches dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="b816e-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="b816e-158">Certaines des fonctionnalités de recherche, vous pouvez être familiarisé avec, ne sont pas pris en charge dans un environnement Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="b816e-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b816e-159"><strong>Fonctionnalité de recherche</strong></span><span class="sxs-lookup"><span data-stu-id="b816e-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="b816e-160"><strong>Remarque</strong></span><span class="sxs-lookup"><span data-stu-id="b816e-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-161">Authentification d’application uniquement</span><span class="sxs-lookup"><span data-stu-id="b816e-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="b816e-162">App uniquement l’authentification (accès privilégié à partir des services) n’est pas pris en charge dans la recherche de Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="b816e-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b816e-163">Utilisateurs invités</span><span class="sxs-lookup"><span data-stu-id="b816e-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="b816e-164">Les utilisateurs invités obtiennent uniquement des résultats à partir de l’emplacement géographique qui ils recherchent à partir de.</span><span class="sxs-lookup"><span data-stu-id="b816e-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="b816e-165">Fonctionnement de recherche de fait dans un environnement Multi-Geo ?</span><span class="sxs-lookup"><span data-stu-id="b816e-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="b816e-166">**Tous les** clients recherche utilisent les API de reste de recherche SharePoint existante pour interagir avec les index de recherche.</span><span class="sxs-lookup"><span data-stu-id="b816e-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p><span data-ttu-id="b816e-167">Figure 1 : Recherche dans un locataire avec trois emplacements geo</span><span class="sxs-lookup"><span data-stu-id="b816e-167">Figure 1: Searching across a tenant with three geo locations</span></span></p></th>
<th align="left"><p><span data-ttu-id="b816e-168">Client de recherche appelle le point de terminaison de recherche reste avec la propriété de requête EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="b816e-168">Search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span></p>
<p><span data-ttu-id="b816e-169">La requête est envoyée à tous les emplacements de geo dans le locataire.</span><span class="sxs-lookup"><span data-stu-id="b816e-169">The query is sent to all geo locations in the tenant.</span></span></p>
<p><span data-ttu-id="b816e-170">Résultats de la recherche à partir de chaque emplacement géographique sont fusionnées et classés.</span><span class="sxs-lookup"><span data-stu-id="b816e-170">Search results from each geo location are merged and ranked.</span></span></p>
<p><span data-ttu-id="b816e-171">Le client obtient des résultats de la recherche unifiée.</span><span class="sxs-lookup"><span data-stu-id="b816e-171">Client gets unified search results.</span></span></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table><span data-ttu-id="b816e-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Recherche de multi-Geo fonctionne en appelant chaque point de terminaison de recherche dans chaque géographiques. Les demandes de tôles à distance sont exécutées en parallèle, mais à la fusion pour se produire, nous attendre la jambe plus lente à répondre avant que nous puissions effectuer la fusion. Cela implique le multi-geo ajouter de latence supplémentaire à l’expérience de recherche.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
### Obtenir un centre de recherche pour afficher les résultats de tous les emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="b816e-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Multi-Geo Search works by calling each search endpoint in each geos. The requests to remote goes are performed in parallel, but to merging to happen, we wait for the slowest leg to reply before we can do the merging. This implies multi-geo add additional latency to the search experience.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
### Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="b816e-176">Chaque centre de recherche possède plusieurs secteurs, et vous devez définir individuellement chaque vertical.</span><span class="sxs-lookup"><span data-stu-id="b816e-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="b816e-177">Assurez-vous que vous effectuez ces étapes avec un compte qui dispose des autorisations nécessaires pour modifier la page de résultats de la recherche et le composant WebPart résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="b816e-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="b816e-178">Accédez à la page de résultats de la recherche (voir la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de recherche des pages de résultats)</span><span class="sxs-lookup"><span data-stu-id="b816e-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="b816e-179">Sélectionnez vertical pour définir, cliquez sur icône engrenage de **paramètres** dans l’angle supérieur droit, puis cliquez sur **Modifier la Page**.</span><span class="sxs-lookup"><span data-stu-id="b816e-179">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**.</span></span>

> ![](media/configure-search-for-multi-geo_image2.png)
>
> <span data-ttu-id="b816e-180">La page de résultats de recherche s’ouvre en mode édition.</span><span class="sxs-lookup"><span data-stu-id="b816e-180">The search results page opens in Edit mode.</span></span>

1.  <span data-ttu-id="b816e-181">Dans le composant WebPart résultats de recherche, déplacez le pointeur vers le haut, à droite du composant WebPart, cliquez sur la flèche et puis cliquez sur **Modifier des composants WebPart** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="b816e-181">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> ![](media/configure-search-for-multi-geo_image3.png)

> <span data-ttu-id="b816e-182">Le volet d’outils composant WebPart résultats de la recherche s’affiche sous le ruban dans la partie supérieure droite de la page.</span><span class="sxs-lookup"><span data-stu-id="b816e-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span>

1.  <span data-ttu-id="b816e-183">Dans le volet d’outils composant WebPart, dans la section **paramètres** , sous **paramètres de contrôle des résultats**, sélectionnez **Multi-Geo afficher les résultats** pour obtenir le composant WebPart résultats de recherche pour afficher les résultats de tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="b816e-184">Cliquez sur **OK** pour enregistrer vos modifications et fermer le volet d’outils composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="b816e-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="b816e-185">Vérifiez vos modifications dans le composant WebPart résultats de la recherche en cliquant sur **Archiver** dans l’onglet de Page du menu principal.</span><span class="sxs-lookup"><span data-stu-id="b816e-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="b816e-186">Publier les modifications en utilisant le lien fourni dans la note en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="b816e-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="b816e-187">Obtenir les applications de recherche personnalisées pour afficher les résultats de tout ou partie des emplacements geo</span><span class="sxs-lookup"><span data-stu-id="b816e-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="b816e-p111">Applications de recherche personnalisées obtenir des résultats à partir d’emplacements de geo tous ou certains, en spécifiant des paramètres de la requête avec la demande de l’API REST de recherche SharePoint. Selon les paramètres de requête, la requête est serveur à tous les emplacements de la zone géographique ou à certains emplacements de la zone géographique. Par exemple, si vous avez besoin uniquement d’interroger un sous-ensemble des emplacements geo pour rechercher des informations pertinentes, vous pouvez contrôler le facteur pyramidal de sortie uniquement ces. Si la demande réussit, l’API REST de recherche SharePoint renvoie des données de réponse.</span><span class="sxs-lookup"><span data-stu-id="b816e-p111">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="b816e-192">Paramètres de la requête</span><span class="sxs-lookup"><span data-stu-id="b816e-192">Query parameters</span></span>

<span data-ttu-id="b816e-p112">**EnableMultiGeoSearch** - il s’agit d’une valeur de type Boolean qui spécifie si la requête doit être serveur pour les index des autres emplacements géographique du locataire Multi-Geo. Affectez-lui la valeur **true** pour déployer la requête ; **false** pour ne ventilateur pas la requête. La valeur par défaut est **false**. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique. Si vous utilisez le paramètre dans un environnement qui n’est pas de Multi-Geo, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="b816e-p112">**EnableMultiGeoSearch** - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="b816e-p113">**TypeClient** - il s’agit d’une chaîne. Entrez un nom de client unique pour chaque application de recherche. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-p113">**ClientType** - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="b816e-p114">**MultiGeoSearchConfiguration** - il s’agit d’une liste facultative de la zone géographique des emplacements dans le Multi-Geo client pour déployer la requête à lorsque **EnableMultiGeoSearch** a la **valeur true**. Si vous ne spécifiez ce paramètre, ou laissez le champ vide, la requête est serveur à tous les emplacements de la zone géographique. Pour chaque emplacement géographique, entrez les éléments suivants, au format JSON :</span><span class="sxs-lookup"><span data-stu-id="b816e-p114">**MultiGeoSearchConfiguration** - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b816e-204">Élément</span><span class="sxs-lookup"><span data-stu-id="b816e-204">Item</span></span></th>
<th align="left"><span data-ttu-id="b816e-205">Description</span><span class="sxs-lookup"><span data-stu-id="b816e-205">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-206">DataLocation</span><span class="sxs-lookup"><span data-stu-id="b816e-206">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="b816e-207">L’emplacement géographique, par exemple NAM.</span><span class="sxs-lookup"><span data-stu-id="b816e-207">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b816e-208">Point de terminaison</span><span class="sxs-lookup"><span data-stu-id="b816e-208">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="b816e-209">Le point de terminaison pour se connecter à, par exemple.https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="b816e-209">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-210">SourceId</span><span class="sxs-lookup"><span data-stu-id="b816e-210">SourceId</span></span></td>
<td align="left"><span data-ttu-id="b816e-211">Le GUID de la source de résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="b816e-211">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b816e-p115">Si vous omettez de DataLocation ou point de terminaison, ou si une DataLocation est en double, la demande échoue. [Vous pouvez obtenir des informations sur le point de terminaison des emplacements de géographique d’un client à l’aide de Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="b816e-p115">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="b816e-214">Données de réponse</span><span class="sxs-lookup"><span data-stu-id="b816e-214">Response data</span></span>

<span data-ttu-id="b816e-p116">**MultiGeoSearchStatus** – il s’agit d’une propriété qui retourne de l’API de recherche de SharePoint en réponse à une demande. La valeur de la propriété est une chaîne et renvoie les informations suivantes sur les résultats qui renvoie de l’API de recherche de SharePoint :</span><span class="sxs-lookup"><span data-stu-id="b816e-p116">**MultiGeoSearchStatus** – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b816e-217">Valeur</span><span class="sxs-lookup"><span data-stu-id="b816e-217">Value</span></span></th>
<th align="left"><span data-ttu-id="b816e-218">Description</span><span class="sxs-lookup"><span data-stu-id="b816e-218">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-219">Complet</span><span class="sxs-lookup"><span data-stu-id="b816e-219">Full</span></span></td>
<td align="left"><span data-ttu-id="b816e-220">Complet à partir de <strong>tous les</strong> résultats de l’emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-220">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b816e-221">Partielle</span><span class="sxs-lookup"><span data-stu-id="b816e-221">Partial</span></span></td>
<td align="left"><span data-ttu-id="b816e-p117">Résultats partiels à partir d’un ou plusieurs emplacements de la zone géographique. Les résultats sont incomplets en raison d’une erreur temporaire.</span><span class="sxs-lookup"><span data-stu-id="b816e-p117">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-224">Aucune</span><span class="sxs-lookup"><span data-stu-id="b816e-224">None</span></span></td>
<td align="left"><span data-ttu-id="b816e-225">La requête n’était pas une requête Multi-Geo et ne était pas serveur à l’autre emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="b816e-225">The query was not a Multi-Geo query and was not fanned out to the other geo locations.</span></span></td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="b816e-226">Exécuter une requête via le service REST</span><span class="sxs-lookup"><span data-stu-id="b816e-226">Query using the REST service</span></span>

<span data-ttu-id="b816e-p118">Avec une demande GET, vous spécifiez les paramètres de requête dans l’URL. Avec une demande POST, vous transmettez les paramètres de requête dans le corps dans le format de Notation JSON (JavaScript Object).</span><span class="sxs-lookup"><span data-stu-id="b816e-p118">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="b816e-229">En-têtes de demande</span><span class="sxs-lookup"><span data-stu-id="b816e-229">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b816e-230">Nom</span><span class="sxs-lookup"><span data-stu-id="b816e-230">Name</span></span></th>
<th align="left"><span data-ttu-id="b816e-231">Valeur</span><span class="sxs-lookup"><span data-stu-id="b816e-231">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b816e-232">Content-Type</span><span class="sxs-lookup"><span data-stu-id="b816e-232">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="b816e-233">application/json ; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="b816e-233">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="b816e-234">Exemple de demande GET qui est serveur à **tous les** emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="b816e-234">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="b816e-235">https:// \<clients\>/\_api/recherche/query?querytext = « sharepoint » & propriétés = 'EnableMultiGeoSearch:true' & TypeClient =' Mes\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="b816e-235">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="b816e-236">Exemple de demande GET pouvoir déployer vers **certains** emplacements geo</span><span class="sxs-lookup"><span data-stu-id="b816e-236">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="b816e-237">https:// <tenant>/_api/search/query?querytext = 'site' & TypeClient = 'my_client_id' & propriétés ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration : [{DataLocation\:« NAM »\,point de terminaison\:« https\: contosoNAM.sharepoint.com »\,SourceId\:« B81EAB55-3140-4312-B0F4-9459D1B4FFEE »}\,{DataLocation\:« Peut »\,point de terminaison\:« https\://contosoCAN.sharepoint-df.com »}]'</span><span class="sxs-lookup"><span data-stu-id="b816e-237">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="b816e-238">Exemple de requête POST qui est serveur à **tous les** emplacements de la zone géographique</span><span class="sxs-lookup"><span data-stu-id="b816e-238">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="b816e-239">Exemple de requête POST qui est serveur à **certains** emplacements geo</span><span class="sxs-lookup"><span data-stu-id="b816e-239">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="b816e-240">Requête à l’aide de CSOM</span><span class="sxs-lookup"><span data-stu-id="b816e-240">Query using CSOM</span></span>

<span data-ttu-id="b816e-241">Voici un exemple de requête CSOM qui est serveur à **tous les** emplacements de la zone géographique :</span><span class="sxs-lookup"><span data-stu-id="b816e-241">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;