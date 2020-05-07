---
title: Configurer la recherche pour Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez la procédure de configuration de la recherche dans un environnement multigéographique.
ms.openlocfilehash: 0b84dc2eea246643e277936cfa8eeb2b9f87b614
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057670"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a><span data-ttu-id="a0c58-103">Configurer la recherche pour Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a0c58-103">Configure Search for Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="a0c58-104">Dans un environnement multigéographique, chaque emplacement géographique comporte son propre index de recherche et son centre de recherche.</span><span class="sxs-lookup"><span data-stu-id="a0c58-104">In a multi-geo environment, each geo location has its own search index and Search Center.</span></span> <span data-ttu-id="a0c58-105">Lorsqu’un utilisateur effectue une recherche, la requête est distribuée à tous les index et les résultats renvoyés sont fusionnés.</span><span class="sxs-lookup"><span data-stu-id="a0c58-105">When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="a0c58-106">Par exemple, un utilisateur d’un emplacement géographique peut rechercher du contenu stocké dans un autre emplacement géographique ou du contenu sur un site SharePoint limité à un emplacement géographique différent.</span><span class="sxs-lookup"><span data-stu-id="a0c58-106">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that's restricted to a different geo location.</span></span> <span data-ttu-id="a0c58-107">Si l’utilisateur a accès à ce contenu, la recherche affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="a0c58-107">If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="a0c58-108">Quels sont les clients de recherche qui fonctionnent dans un environnement Multi-Géo ?</span><span class="sxs-lookup"><span data-stu-id="a0c58-108">Which search clients work in a multi-geo environment?</span></span>

<span data-ttu-id="a0c58-109">Ces clients peuvent renvoyer des résultats de tous les emplacements géographiques :</span><span class="sxs-lookup"><span data-stu-id="a0c58-109">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="a0c58-110">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="a0c58-110">OneDrive for Business</span></span>

-   <span data-ttu-id="a0c58-111">Delve</span><span class="sxs-lookup"><span data-stu-id="a0c58-111">Delve</span></span>

-   <span data-ttu-id="a0c58-112">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0c58-112">The SharePoint home page</span></span>

-   <span data-ttu-id="a0c58-113">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="a0c58-113">The Search Center</span></span>

-   <span data-ttu-id="a0c58-114">Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0c58-114">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="a0c58-115">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="a0c58-115">OneDrive for Business</span></span>

<span data-ttu-id="a0c58-116">Dès que l’environnement Multi-Géo est configuré, les utilisateurs qui effectuent des recherches dans OneDrive obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-116">As soon as the multi-geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="a0c58-117">Delve</span><span class="sxs-lookup"><span data-stu-id="a0c58-117">Delve</span></span>

<span data-ttu-id="a0c58-118">Dès que l’environnement Multi-Géo est configuré, les utilisateurs qui effectuent des recherches dans Delve obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-118">As soon as the multi-geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="a0c58-119">Le flux Delve et la fiche de profil n’affichent que les aperçus de fichiers stockés dans l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="a0c58-119">The Delve feed and the profile card only show previews of files that are stored in the central location.</span></span> <span data-ttu-id="a0c58-120">Pour les fichiers stockés dans des emplacements satellites, l’icône du type de fichier apparaît à la place.</span><span class="sxs-lookup"><span data-stu-id="a0c58-120">For files that are stored in satellite locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="a0c58-121">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0c58-121">The SharePoint home page</span></span>

<span data-ttu-id="a0c58-p104">Dès que l’environnement Multi-Géo est configuré, les utilisateurs voient les actualités, les sites récents et les sites suivis de plusieurs emplacements géographiques sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche sur la page d’accueil SharePoint, ils obtiennent des résultats fusionnés provenant de plusieurs emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p104">As soon as the multi-geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="a0c58-124">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="a0c58-124">The Search Center</span></span>

<span data-ttu-id="a0c58-p105">Une fois que l’environnement Multi-Géo est configuré, chaque centre de recherche continue à afficher uniquement les résultats de son propre emplacement géographique. Les administrateurs doivent [modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir des résultats de tous les emplacements géographiques. Par la suite, les utilisateurs qui effectuent une recherche dans le centre de recherche obtiennent des résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p105">After the multi-geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="a0c58-128">Applications de recherche personnalisée</span><span class="sxs-lookup"><span data-stu-id="a0c58-128">Custom search applications</span></span>

<span data-ttu-id="a0c58-p106">Comme d’habitude, les applications de recherche personnalisée interagissent avec les index de recherche en utilisant les API REST de recherche SharePoint existantes. Pour obtenir des résultats de tous les emplacements géographiques (ou une partie), l’application doit [appeler l’API et inclure les nouveaux paramètres de requête Multi-Géo](#_Get_custom_search) dans la demande. Cela déclenche une distribution ramifiée de la requête à tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="a0c58-132">Quelles différences la recherche présente-t-elle dans un environnement multigéographique ?</span><span class="sxs-lookup"><span data-stu-id="a0c58-132">What's different about search in a multi-geo environment?</span></span>

<span data-ttu-id="a0c58-133">Certaines fonctionnalités de recherche auxquelles vous êtes habitué fonctionnent différemment dans un environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-133">Some search features you might be familiar with, work differently in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a0c58-134"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="a0c58-134"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a0c58-135"><strong>Fonctionnement</strong></span><span class="sxs-lookup"><span data-stu-id="a0c58-135"><strong>How it works</strong></span></span></th>
<th align="left"><span data-ttu-id="a0c58-136"><strong>Solution de contournement</strong></span><span class="sxs-lookup"><span data-stu-id="a0c58-136"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-137">Résultats promus</span><span class="sxs-lookup"><span data-stu-id="a0c58-137">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="a0c58-138">Vous pouvez créer des règles de requête avec des résultats promus à différents niveaux : pour le client entier, pour une collection de sites ou pour un site.</span><span class="sxs-lookup"><span data-stu-id="a0c58-138">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site.</span></span> <span data-ttu-id="a0c58-139">Dans un environnement multigéographique, définissez les résultats promus au niveau du client pour promouvoir les résultats aux centres de recherche de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-139">In a multi-geo environment, define promoted results at the tenant level to promote the results to the Search Centers in all geo locations.</span></span> <span data-ttu-id="a0c58-140">Si vous souhaitez seulement promouvoir les résultats dans le centre de recherche qui se trouve dans l’emplacement géographique de la collection de sites ou du site, définissez les résultats promus au niveau de la collection de sites ou du site.</span><span class="sxs-lookup"><span data-stu-id="a0c58-140">If you only want to promote results in the Search Center that's in the geo location of the site collection or site, define the promoted results at the site collection or site level.</span></span> <span data-ttu-id="a0c58-141">Ces résultats ne sont pas promus dans d’autres emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-141">These results are not promoted in other geo locations.</span></span></td>
<td align="left"><span data-ttu-id="a0c58-142">Si vous n’avez pas besoin d’autres résultats promus par emplacement géographique (par exemple, des règles différentes pour les déplacements), nous vous recommandons de définir les résultats promus au niveau du client.</span><span class="sxs-lookup"><span data-stu-id="a0c58-142">If you don't need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-143">Affinements de la recherche</span><span class="sxs-lookup"><span data-stu-id="a0c58-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="a0c58-p108">La recherche renvoie des affinements de tous les emplacements géographiques d’un client puis les regroupe. Le regroupement est ce qu’il y a de mieux, ce qui signifie que le nombre d’affinements peut ne pas être précis à 100 %. Pour la plupart des scénarios de recherche, cette précision est suffisante. </span><span class="sxs-lookup"><span data-stu-id="a0c58-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="a0c58-147">Pour les applications basées sur la recherche qui dépendent de l’intégralité de l’affinement, effectuez une requête indépendante sur chaque emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-147">For search-driven applications that depend on refiner completeness, query each geo location independently.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="a0c58-148">La recherche multigéographique ne prend pas en charge la création dynamique de compartiments pour les affinements numériques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-148">Multi-geo search doesn't support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="a0c58-149">Utilisez le <a href="https://docs.microsoft.com/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre « Discretize »</a> pour les affinements numériques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-149">Use the <a href="https://docs.microsoft.com/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-150">ID de document</span><span class="sxs-lookup"><span data-stu-id="a0c58-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="a0c58-151">Si vous développez une application basée sur la recherche qui dépend des ID de document, notez que les ID de document d’un environnement multigéographique ne sont pas uniques parmi les emplacements géographiques, mais le sont par emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-151">If you're developing a search-driven application that depends on document IDs, note that document IDs in a multi-geo environment aren't unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="a0c58-152">Nous avons ajouté une colonne qui identifie l’emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-152">We've added a column that identifies the geo location.</span></span> <span data-ttu-id="a0c58-153">Utilisez cette colonne pour atteindre l’unicité.</span><span class="sxs-lookup"><span data-stu-id="a0c58-153">Use this column to achieve uniqueness.</span></span> <span data-ttu-id="a0c58-154">Cette colonne s’intitule « GeoLocationSource ».</span><span class="sxs-lookup"><span data-stu-id="a0c58-154">This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-155">Nombre de résultats</span><span class="sxs-lookup"><span data-stu-id="a0c58-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="a0c58-156">La page des résultats de recherche affiche les résultats combinés des emplacements géographiques, mais il n’est pas possible d’afficher plus de 500 résultats par page.</span><span class="sxs-lookup"><span data-stu-id="a0c58-156">The search results page shows combined results from the geo locations, but it's not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-157">Recherche hybride</span><span class="sxs-lookup"><span data-stu-id="a0c58-157">Hybrid search</span></span></td>
<td align="left"><span data-ttu-id="a0c58-158">Dans un environnement SharePoint hybride avec <a href="https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">recherche hybride dans le cloud</a>, le contenu local est ajouté à l’index Microsoft 365 de l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="a0c58-158">In a hybrid SharePoint environment with <a href="https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">cloud hybrid search</a>,  on-premises content is added to the Microsoft 365 index of the central location.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="a0c58-159">Quels sont les éléments qui ne sont pas pris en charge par la recherche dans un environnement multigéographique ?</span><span class="sxs-lookup"><span data-stu-id="a0c58-159">What's not supported for search in a multi-geo environment?</span></span>

<span data-ttu-id="a0c58-160">Certaines fonctionnalités de recherche auxquelles vous êtes habitué ne sont pas prises en charge dans un environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-160">Some of the search features you might be familiar with, aren't supported in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a0c58-161"><strong>Fonctionnalité de recherche</strong></span><span class="sxs-lookup"><span data-stu-id="a0c58-161"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a0c58-162"><strong>Remarque</strong></span><span class="sxs-lookup"><span data-stu-id="a0c58-162"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-163">Authentification d’application uniquement</span><span class="sxs-lookup"><span data-stu-id="a0c58-163">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="a0c58-164">L’authentification d’application uniquement (accès privilégié depuis les services) n’est pas prise en charge dans la recherche multigéographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-164">App-only authentication (privileged access from services) isn't supported in multi-geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-165">Utilisateurs invités</span><span class="sxs-lookup"><span data-stu-id="a0c58-165">Guest users</span></span></td>
<td align="left"><span data-ttu-id="a0c58-166">Les utilisateurs invités obtiennent uniquement les résultats de l’emplacement géographique à partir duquel ils effectuent leur recherche.</span><span class="sxs-lookup"><span data-stu-id="a0c58-166">Guest users only get results from the geo location that they're searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="a0c58-167">Comment fonctionne la recherche dans un environnement multigéographique ?</span><span class="sxs-lookup"><span data-stu-id="a0c58-167">How does search work in a multi-geo environment?</span></span>

<span data-ttu-id="a0c58-168">Tous les clients de recherche utilisent les API REST de recherche SharePoint existantes pour interagir avec les index de recherche.</span><span class="sxs-lookup"><span data-stu-id="a0c58-168">All the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="a0c58-169">Un client de recherche appelle le point de terminaison REST de recherche avec la propriété de requête EnableMultiGeoSearch= true.</span><span class="sxs-lookup"><span data-stu-id="a0c58-169">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="a0c58-170">La requête est envoyée à tous les emplacements géographiques dans le client.</span><span class="sxs-lookup"><span data-stu-id="a0c58-170">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="a0c58-171">Les résultats de recherche de chaque emplacement géographique sont fusionnés et classés.</span><span class="sxs-lookup"><span data-stu-id="a0c58-171">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="a0c58-172">Le client obtient des résultats de recherche unifiés.</span><span class="sxs-lookup"><span data-stu-id="a0c58-172">The client gets unified search results.</span></span>



<span data-ttu-id="a0c58-173"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notez que nous ne fusionnons pas les résultats de recherche avant d’avoir reçu les résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-173"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don't merge the search results until we've received results from all the geo locations.</span></span> <span data-ttu-id="a0c58-174">Cela signifie que les recherches géographiques multiples souffrent d’une latence supplémentaire par rapport aux recherches dans un environnement ne comportant qu’un seul emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-174">This means that multi-geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="a0c58-175">Obtenir un centre de recherche pour afficher les résultats de tous les emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-175">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="a0c58-176">Chaque centre de recherche possède plusieurs secteurs verticaux et vous devez configurer chaque secteur vertical individuellement.</span><span class="sxs-lookup"><span data-stu-id="a0c58-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="a0c58-177">Vérifiez que vous effectuez ces étapes avec un compte doté d’autorisations pour modifier la page des résultats de la recherche et le composant WebPart Search Result.</span><span class="sxs-lookup"><span data-stu-id="a0c58-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="a0c58-178">Accédez à la page des résultats de la recherche (reportez-vous à la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) des pages des résultats de la recherche)</span><span class="sxs-lookup"><span data-stu-id="a0c58-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="a0c58-p111">Sélectionnez le secteur vertical à configurer, cliquez sur l’icône d’engrenage **Paramètres** située en haut à droite, puis cliquez sur **Modifier la page**. La page des résultats de la recherche s’ouvre en mode Édition.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="a0c58-181">Dans le composant WebPart de résultats de recherche, déplacez le pointeur vers le coin supérieur droit et cliquez sur la flèche, puis sur **Modifier le composant WebPart** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="a0c58-181">In the Search Results Web Part, move the pointer to the upper, right corner of the web part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> <span data-ttu-id="a0c58-182">Le volet des outils du composant WebPart des résultats de recherche s’ouvre sous le ruban en haut à droite de la page.</span><span class="sxs-lookup"><span data-stu-id="a0c58-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span> ![](media/configure-search-for-multi-geo-image3.png)

1.  <span data-ttu-id="a0c58-183">Dans le volet des outils du composant WebPart, dans la section **Paramètres**, sous **Paramètres de contrôle des résultats**, sélectionnez **Afficher les résultats multigéographiques** pour que le composant WebPart Résultats de la recherche affiche les résultats de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="a0c58-184">Cliquez sur **OK** pour enregistrer vos changements et fermer le volet des outils du composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="a0c58-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="a0c58-185">Vérifiez les changements que vous avez apportés au composant WebPart Résultats de la recherche en cliquant sur **Archiver** sur l’onglet Page du menu principal.</span><span class="sxs-lookup"><span data-stu-id="a0c58-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="a0c58-186">Publiez les changements en utilisant le lien fourni dans la note en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="a0c58-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="a0c58-187">Configurer des applications de recherche personnalisée pour qu’elles affichent les résultats de l’ensemble ou d’une partie des emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="a0c58-p113">Les applications de recherche personnalisée obtiennent les résultats de l’ensemble (ou d’une partie) des emplacements géographiques en spécifiant des paramètres de requête avec la demande à l’API REST de recherche SharePoint. Selon les paramètres, la requête est distribuée à tous les emplacements géographiques ou à certains emplacements géographiques. Par exemple, si vous devez seulement interroger un sous-ensemble des emplacements géographiques pour rechercher des informations pertinentes, vous pouvez contrôler la distribution ramifiée à ces derniers uniquement. Si la demande fonctionne, l’API REST de recherche SharePoint renvoie des données de réponse.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

<span data-ttu-id="a0c58-192">**Configuration requise**</span><span class="sxs-lookup"><span data-stu-id="a0c58-192">**Requirement**</span></span>

<span data-ttu-id="a0c58-193">Pour chaque emplacement géographique, vous devez vous assurer que tous les utilisateurs de l’organisation ont reçu l’autorisation de **lecture** du site web racine (par exemple contoso**APAC**.sharepoint.com/ et contoso**EU**.sharepoint.com/).</span><span class="sxs-lookup"><span data-stu-id="a0c58-193">For each geo location, you must ensure that all users in the organization have been granted the **Read** permission level for the root website (for example contoso**APAC**.sharepoint.com/ and contoso**EU**.sharepoint.com/).</span></span> <span data-ttu-id="a0c58-194">[En savoir plus sur les autorisations](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span><span class="sxs-lookup"><span data-stu-id="a0c58-194">[Learn about permissions](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span></span>

### <a name="query-parameters"></a><span data-ttu-id="a0c58-195">Paramètres de requête</span><span class="sxs-lookup"><span data-stu-id="a0c58-195">Query parameters</span></span>

<span data-ttu-id="a0c58-196">EnableMultiGeoSearch : il s’agit une valeur booléenne qui spécifie si la requête doit être étendue aux index des autres emplacements géographiques du client multigéographique.</span><span class="sxs-lookup"><span data-stu-id="a0c58-196">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the multi-geo tenant.</span></span> <span data-ttu-id="a0c58-197">Définissez-la sur **true** pour étendre la requête et sur **false** pour ne pas l’étendre.</span><span class="sxs-lookup"><span data-stu-id="a0c58-197">Set it to **true** to fan out the query; **false** to not fan out the query.</span></span> <span data-ttu-id="a0c58-198">Si vous n’incluez pas ce paramètre, la valeur par défaut est **false**, sauf lorsque vous effectuez un appel de l’API REST contre un site qui utilise le modèle Centre de recherche d’entreprise, dans ce cas, la valeur par défaut est **true**.</span><span class="sxs-lookup"><span data-stu-id="a0c58-198">If you don't include this parameter, the default value is **false**, except when making a REST API call against a site which uses the Enterprise Search Center template, in this case the default value is **true**.</span></span> <span data-ttu-id="a0c58-199">Si vous utilisez ce paramètre dans un environnement qui n’est pas multigéographique, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="a0c58-199">If you use the parameter in an environment that isn't multi-geo, the parameter is ignored.</span></span>

<span data-ttu-id="a0c58-200">TypeClient : il s’agit d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a0c58-200">ClientType - This is a string.</span></span> <span data-ttu-id="a0c58-201">Entrez un nom de client unique pour chaque application de recherche.</span><span class="sxs-lookup"><span data-stu-id="a0c58-201">Enter a unique client name for each search application.</span></span> <span data-ttu-id="a0c58-202">Si vous n’incluez pas ce paramètre, la requête n’est pas étendue à d’autres emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-202">If you don't include this parameter, the query is not fanned out to other geo locations.</span></span>

<span data-ttu-id="a0c58-203">MultiGeoSearchConfiguration : il s’agit d’une liste facultative d’emplacements géographiques dans le client multigéographique pour étendre la requête lorsque **EnableMultiGeoSearch** est défini sur **true**.</span><span class="sxs-lookup"><span data-stu-id="a0c58-203">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the multi-geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**.</span></span> <span data-ttu-id="a0c58-204">Si vous n’incluez pas ce paramètre ou que vous le laissez vide, la requête est étendue à d’autres emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-204">If you don't include this parameter, or leave it blank, the query is fanned out to all geo locations.</span></span> <span data-ttu-id="a0c58-205">Pour chaque emplacement géographique, entrez les éléments suivants au format JSON :</span><span class="sxs-lookup"><span data-stu-id="a0c58-205">For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a0c58-206">Option</span><span class="sxs-lookup"><span data-stu-id="a0c58-206">Item</span></span></th>
<th align="left"><span data-ttu-id="a0c58-207">Description</span><span class="sxs-lookup"><span data-stu-id="a0c58-207">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-208">DataLocation</span><span class="sxs-lookup"><span data-stu-id="a0c58-208">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="a0c58-209">L’emplacement géographique, par exemple NAM.</span><span class="sxs-lookup"><span data-stu-id="a0c58-209">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-210">EndPoint</span><span class="sxs-lookup"><span data-stu-id="a0c58-210">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="a0c58-211">Le point de terminaison auquel se connecter, par exemple https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="a0c58-211">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-212">SourceId</span><span class="sxs-lookup"><span data-stu-id="a0c58-212">SourceId</span></span></td>
<td align="left"><span data-ttu-id="a0c58-213">GUID de l’origine des résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="a0c58-213">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a0c58-p118">Si vous omettez DataLocation ou EndPoint, ou si une DataLocation est dupliquée, la demande échoue. [Vous pouvez obtenir des informations sur le point de terminaison des emplacements géographiques d’un client à l’aide de Microsoft Graph](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="a0c58-p118">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="a0c58-216">Données de réponse</span><span class="sxs-lookup"><span data-stu-id="a0c58-216">Response data</span></span>

<span data-ttu-id="a0c58-p119">MultiGeoSearchStatus : il s’agit d’une propriété renvoyée par l’API de recherche SharePoint en réponse à une demande. La valeur de la propriété est une chaîne et fournit les informations suivantes sur les résultats renvoyés par l’API de recherche SharePoint :</span><span class="sxs-lookup"><span data-stu-id="a0c58-p119">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a0c58-219">Valeur</span><span class="sxs-lookup"><span data-stu-id="a0c58-219">Value</span></span></th>
<th align="left"><span data-ttu-id="a0c58-220">Description</span><span class="sxs-lookup"><span data-stu-id="a0c58-220">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-221">Complet</span><span class="sxs-lookup"><span data-stu-id="a0c58-221">Full</span></span></td>
<td align="left"><span data-ttu-id="a0c58-222">Résultats complets de <strong>tous</strong> les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="a0c58-222">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a0c58-223">Partielle</span><span class="sxs-lookup"><span data-stu-id="a0c58-223">Partial</span></span></td>
<td align="left"><span data-ttu-id="a0c58-p120">Résultats partiels d’un ou plusieurs emplacements géographiques. Les résultats sont incomplets en raison d’une erreur temporaire.</span><span class="sxs-lookup"><span data-stu-id="a0c58-p120">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="a0c58-226">Requête à l’aide du service REST</span><span class="sxs-lookup"><span data-stu-id="a0c58-226">Query using the REST service</span></span>

<span data-ttu-id="a0c58-p121">Avec une demande GET, spécifiez les paramètres de la requête dans l’URL. Avec une demande POST, vous transmettez les paramètres de la requête dans le corps au format JSON (JavaScript Object Notation).</span><span class="sxs-lookup"><span data-stu-id="a0c58-p121">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="a0c58-229">En-têtes de demande</span><span class="sxs-lookup"><span data-stu-id="a0c58-229">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a0c58-230">Nom</span><span class="sxs-lookup"><span data-stu-id="a0c58-230">Name</span></span></th>
<th align="left"><span data-ttu-id="a0c58-231">Valeur</span><span class="sxs-lookup"><span data-stu-id="a0c58-231">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a0c58-232">Content-Type</span><span class="sxs-lookup"><span data-stu-id="a0c58-232">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="a0c58-233">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="a0c58-233">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a0c58-234">Exemple de demande GET étendue à **tous** les emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-234">Sample GET request that's fanned out to **all** geo locations</span></span>

<span data-ttu-id="a0c58-235">https:// \<tenant\>/\_api/search/query?querytext=’sharepoint’&Properties=’EnableMultiGeoSearch:true’&ClientType=’my\_client\_id’</span><span class="sxs-lookup"><span data-stu-id="a0c58-235">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="a0c58-236">Exemple de demande GET à distribuer à **certains** emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-236">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="a0c58-237">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="a0c58-237">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="a0c58-238">Les symboles virgule et deux-points de la liste des emplacements géographiques pour la propriété MultiGeoSearchConfiguration sont précédés par le caractère **barre oblique inverse**,</span><span class="sxs-lookup"><span data-stu-id="a0c58-238">Commas and colons in the list of geo locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character.</span></span> <span data-ttu-id="a0c58-239">car les demandes GET utilisent des syboles deux-points pour séparer les propriétés, et des virgules pour séparer les arguments des propriétés.</span><span class="sxs-lookup"><span data-stu-id="a0c58-239">This is because GET requests use colons to separate properties and commas to separate arguments of properties.</span></span> <span data-ttu-id="a0c58-240">Sans barre oblique inverse comme caractère d’échappement, la propriété MultiGeoSearchConfiguration est interprétée de façon erronée.</span><span class="sxs-lookup"><span data-stu-id="a0c58-240">Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a0c58-241">Exemple de demande POST étendue à **tous** les emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-241">Sample POST request that's fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="a0c58-242">Exemple de demande POST étendue à **certains** emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="a0c58-242">Sample POST request that's fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="a0c58-243">Requête utilisant CSOM</span><span class="sxs-lookup"><span data-stu-id="a0c58-243">Query using CSOM</span></span>

<span data-ttu-id="a0c58-244">Voici un exemple de requête CSOM étendue à **tous** les emplacements géographiques :</span><span class="sxs-lookup"><span data-stu-id="a0c58-244">Here's a sample CSOM query that's fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

