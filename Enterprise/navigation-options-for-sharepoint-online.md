---
title: Options de navigation pour SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online. Le choix et la configuration de la navigation ont un impact significatif sur les performances et l’extensibilité des sites dans SharePoint Online. Cet article ne s’applique pas aux sites d’équipe classiques.
ms.openlocfilehash: c651530284889d2808c8fa415b72836eb6d14aea
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004759"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="134cb-105">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="134cb-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="134cb-106">Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="134cb-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="134cb-107">Le choix et la configuration de la navigation ont un impact significatif sur les performances et l’extensibilité des sites dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="134cb-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span> <span data-ttu-id="134cb-108">Le modèle de site de publication SharePoint doit être utilisé uniquement si cela est nécessaire pour un portail centralisé et la fonctionnalité de publication doit être activée uniquement sur des sites spécifiques et uniquement lorsque cela est absolument nécessaire, car cela peut avoir un impact sur les performances lorsqu’il est utilisé de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="134cb-108">The SharePoint Publishing site template should only be used if required for a centralized portal and the publishing feature should only be enabled on specific sites and only when absolutely required as it can impact performance when used incorrectly.</span></span>

>[!NOTE]
><span data-ttu-id="134cb-109">Si vous utilisez des options de navigation modernes SharePoint comme le menu Mega, la navigation en cascade ou la navigation par concentrateur, cet article ne s’applique pas à votre site.</span><span class="sxs-lookup"><span data-stu-id="134cb-109">If you're using modern SharePoint navigation options like mega menu, cascading navigation, or hub navigation, this article does not apply to your site.</span></span> <span data-ttu-id="134cb-110">Les architectures de sites SharePoint modernes exploitent une hiérarchie de sites plus aplatie et un modèle Hub-and-Spoke.</span><span class="sxs-lookup"><span data-stu-id="134cb-110">Modern SharePoint site architectures leverage a more flattened site hierarchy and a hub-and-spoke model.</span></span> <span data-ttu-id="134cb-111">Cela permet de réaliser de nombreux scénarios qui ne nécessitent pas l’utilisation de la fonctionnalité de publication SharePoint.</span><span class="sxs-lookup"><span data-stu-id="134cb-111">This allows many scenarios to be achieved that do NOT require use of the SharePoint Publishing feature.</span></span>

## <a name="overview"></a><span data-ttu-id="134cb-112">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="134cb-112">Overview</span></span>

<span data-ttu-id="134cb-113">La configuration du fournisseur de navigation peut avoir un impact significatif sur les performances de l’ensemble du site, et vous devez tenir compte de la sélection d’un fournisseur de navigation et d’une configuration qui évoluent efficacement pour les besoins d’un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="134cb-113">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="134cb-114">Il existe deux fournisseurs de navigation prédéfinis, ainsi que des implémentations de navigation personnalisées.</span><span class="sxs-lookup"><span data-stu-id="134cb-114">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="134cb-115">La première option, [**navigation structurelle**](#using-structural-navigation-in-sharepoint-online), est l’option de navigation recommandée dans SharePoint Online pour les sites SharePoint classiques **si vous activez la mise en cache de la navigation structurelle pour votre site**.</span><span class="sxs-lookup"><span data-stu-id="134cb-115">The first option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), is the recommended navigation option in SharePoint Online for classic Sharepoint sites, **if you turn on structural navigation caching for your site**.</span></span> <span data-ttu-id="134cb-116">Ce fournisseur de navigation affiche les éléments de navigation sous le site actuel, et éventuellement le site actuel et ses frères.</span><span class="sxs-lookup"><span data-stu-id="134cb-116">This navigation provider displays the navigation items below the current site, and optionally the current site and its siblings.</span></span> <span data-ttu-id="134cb-117">Elle fournit des fonctionnalités supplémentaires, telles que le filtrage de sécurité et l’énumération de la structure de site.</span><span class="sxs-lookup"><span data-stu-id="134cb-117">It provides additional capabilities such as security trimming and site structure enumeration.</span></span> <span data-ttu-id="134cb-118">Si la mise en cache est désactivée, cela a un impact négatif sur les performances et l’extensibilité, et peut être soumis à la limitation.</span><span class="sxs-lookup"><span data-stu-id="134cb-118">If caching is disabled, this will negatively impact performance and scalability, and may be subject to throttling.</span></span>

<span data-ttu-id="134cb-119">La deuxième option, [**navigation gérée (métadonnées)**](#using-managed-navigation-and-metadata-in-sharepoint-online), représente les éléments de navigation à l’aide d’un ensemble de termes de métadonnées gérées.</span><span class="sxs-lookup"><span data-stu-id="134cb-119">The second option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), represents navigation items using a Managed Metadata term set.</span></span> <span data-ttu-id="134cb-120">Nous vous recommandons de désactiver le filtrage de sécurité, sauf en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="134cb-120">We recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="134cb-121">Le filtrage de sécurité est activé comme paramètre sécurisé par défaut pour ce fournisseur de navigation ; Toutefois, de nombreux sites n’ont pas besoin de la charge de filtrage de sécurité, car les éléments de navigation sont souvent cohérents pour tous les utilisateurs du site.</span><span class="sxs-lookup"><span data-stu-id="134cb-121">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="134cb-122">Avec la configuration recommandée pour désactiver le filtrage de sécurité, ce fournisseur de navigation ne requiert pas l’énumération de la structure du site et est hautement évolutif avec un impact acceptable sur les performances.</span><span class="sxs-lookup"><span data-stu-id="134cb-122">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="134cb-123">En plus des fournisseurs de navigation prédéfinis, de nombreux clients ont implémenté les autres implémentations de navigation personnalisées.</span><span class="sxs-lookup"><span data-stu-id="134cb-123">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="134cb-124">Consultez la rubrique [script côté client basé](#using-search-driven-client-side-scripting) sur la recherche dans cet article.</span><span class="sxs-lookup"><span data-stu-id="134cb-124">See [Search-driven client-side scripting](#using-search-driven-client-side-scripting) in this article.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="134cb-125">Avantages et inconvénients des options de navigation SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="134cb-125">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="134cb-126">Le tableau suivant récapitule les avantages et les inconvénients de chaque option.</span><span class="sxs-lookup"><span data-stu-id="134cb-126">The following table summarizes the pros and cons of each option.</span></span>

|<span data-ttu-id="134cb-127">Navigation structurelle</span><span class="sxs-lookup"><span data-stu-id="134cb-127">Structural navigation</span></span>  |<span data-ttu-id="134cb-128">Navigation gérée</span><span class="sxs-lookup"><span data-stu-id="134cb-128">Managed navigation</span></span>  |<span data-ttu-id="134cb-129">Navigation basée sur la recherche</span><span class="sxs-lookup"><span data-stu-id="134cb-129">Search-driven navigation</span></span>  |<span data-ttu-id="134cb-130">Fournisseur de navigation personnalisée</span><span class="sxs-lookup"><span data-stu-id="134cb-130">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="134cb-131">Avantages</span><span class="sxs-lookup"><span data-stu-id="134cb-131">Pros:</span></span><br/><br/><span data-ttu-id="134cb-132">Facilité de maintenance</span><span class="sxs-lookup"><span data-stu-id="134cb-132">Easy to maintain</span></span><br/><span data-ttu-id="134cb-133">Sécurité découpée</span><span class="sxs-lookup"><span data-stu-id="134cb-133">Security trimmed</span></span><br/><span data-ttu-id="134cb-134">Mises à jour automatiques dans les 24 heures après la modification du contenu</span><span class="sxs-lookup"><span data-stu-id="134cb-134">Automatically updates within 24 hours when content is changed</span></span><br/>     |<span data-ttu-id="134cb-135">Avantages</span><span class="sxs-lookup"><span data-stu-id="134cb-135">Pros:</span></span><br/><br/><span data-ttu-id="134cb-136">Facilité de maintenance</span><span class="sxs-lookup"><span data-stu-id="134cb-136">Easy to maintain</span></span><br/>|<span data-ttu-id="134cb-137">Avantages</span><span class="sxs-lookup"><span data-stu-id="134cb-137">Pros:</span></span><br/><br/><span data-ttu-id="134cb-138">Sécurité découpée</span><span class="sxs-lookup"><span data-stu-id="134cb-138">Security trimmed</span></span><br/><span data-ttu-id="134cb-139">Mises à jour automatiques lors de l’ajout de sites</span><span class="sxs-lookup"><span data-stu-id="134cb-139">Automatically updates as sites are added</span></span><br/><span data-ttu-id="134cb-140">Temps de chargement rapide et structure de navigation mise en cache locale</span><span class="sxs-lookup"><span data-stu-id="134cb-140">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="134cb-141">Avantages</span><span class="sxs-lookup"><span data-stu-id="134cb-141">Pros:</span></span><br/><br/><span data-ttu-id="134cb-142">Choix plus large d’options disponibles</span><span class="sxs-lookup"><span data-stu-id="134cb-142">Wider choice of options available</span></span><br/><span data-ttu-id="134cb-143">Chargement rapide lorsque la mise en cache est utilisée correctement</span><span class="sxs-lookup"><span data-stu-id="134cb-143">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="134cb-144">De nombreuses options fonctionnent bien avec la conception de pages réactives</span><span class="sxs-lookup"><span data-stu-id="134cb-144">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="134cb-145">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="134cb-145">Cons:</span></span><br/><br/><span data-ttu-id="134cb-146">**Impact sur les performances en cas de désactivation de la mise en cache**</span><span class="sxs-lookup"><span data-stu-id="134cb-146">**Impacts performance if caching is disabled**</span></span><br/><span data-ttu-id="134cb-147">Soumis à la limitation</span><span class="sxs-lookup"><span data-stu-id="134cb-147">Subject to throttling</span></span><br/>|<span data-ttu-id="134cb-148">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="134cb-148">Cons:</span></span><br/><br/><span data-ttu-id="134cb-149">Mise à jour non automatique pour refléter la structure du site</span><span class="sxs-lookup"><span data-stu-id="134cb-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="134cb-150">**Impact sur les performances si le filtrage de sécurité est activé** ou si la structure de navigation est complexe</span><span class="sxs-lookup"><span data-stu-id="134cb-150">**Impacts performance if security trimming is enabled** or when navigation structure is complex</span></span><br/>|<span data-ttu-id="134cb-151">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="134cb-151">Cons:</span></span><br/><br/><span data-ttu-id="134cb-152">Aucune possibilité de classer facilement les sites</span><span class="sxs-lookup"><span data-stu-id="134cb-152">No ability to easily order sites</span></span><br/><span data-ttu-id="134cb-153">Nécessite une personnalisation de la page maître (compétences techniques requises)</span><span class="sxs-lookup"><span data-stu-id="134cb-153">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="134cb-154">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="134cb-154">Cons:</span></span><br/><br/><span data-ttu-id="134cb-155">Un développement personnalisé est requis</span><span class="sxs-lookup"><span data-stu-id="134cb-155">Custom development is required</span></span><br/><span data-ttu-id="134cb-156">La source de données externe/le cache stocké est nécessaire par exemple, Azure</span><span class="sxs-lookup"><span data-stu-id="134cb-156">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="134cb-157">L’option la plus appropriée pour votre site dépend de vos besoins en matière de site et de vos capacités techniques.</span><span class="sxs-lookup"><span data-stu-id="134cb-157">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="134cb-158">Si vous souhaitez un fournisseur de navigation facile à configurer qui se met à jour automatiquement lorsque le contenu est modifié, la navigation structurelle [avec mise en cache activée](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) est une excellente option.</span><span class="sxs-lookup"><span data-stu-id="134cb-158">If you want an easy-to-configure navigation provider that automatically updates when content is changed, then structural navigation [with caching enabled](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) is a good option.</span></span>

>[!NOTE]
><span data-ttu-id="134cb-159">Appliquer le même principe que les sites SharePoint modernes en simplifiant la structure globale du site en une structure non hiérarchique simplifiée améliore les performances et simplifie le passage aux sites SharePoint modernes.</span><span class="sxs-lookup"><span data-stu-id="134cb-159">Applying the same principle as modern SharePoint sites by simplifying the overall site structure to a flatter, non-hierarchical structure improves performance and simplifies moving to modern SharePoint sites.</span></span> <span data-ttu-id="134cb-160">Cela signifie qu’au lieu d’avoir une seule collection de sites avec des centaines de sites (sous-sites Web), une meilleure approche consiste à avoir de nombreuses collections de sites avec très peu de sous-sites (sous-sites Web).</span><span class="sxs-lookup"><span data-stu-id="134cb-160">What this means is that instead of having a single site collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="134cb-161">Analyse des performances de navigation dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="134cb-161">Analyzing navigation performance in SharePoint Online</span></span>

<span data-ttu-id="134cb-162">L' [outil Diagnostics de la page pour SharePoint](https://aka.ms/perftool) est une extension de navigateur pour les navigateurs Microsoft Edge et chrome qui analyse à la fois les pages du portail moderne SharePoint Online et du site de publication classique.</span><span class="sxs-lookup"><span data-stu-id="134cb-162">The [Page Diagnostics for SharePoint tool](https://aka.ms/perftool) is a browser extension for Microsoft Edge and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="134cb-163">Cet outil fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.</span><span class="sxs-lookup"><span data-stu-id="134cb-163">This tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="134cb-164">L’outil génère un rapport pour chaque page analysée affichant le mode d’exécution de la page par rapport à un ensemble prédéfini de règles et affiche des informations détaillées lorsque les résultats d’un test se situent hors de la valeur de la ligne de base.</span><span class="sxs-lookup"><span data-stu-id="134cb-164">The tool generates a report for each analyzed page showing how the page performs against a pre-defined set of rules and displays detailed information when results for a test fall outside the baseline value.</span></span> <span data-ttu-id="134cb-165">Les administrateurs et les concepteurs SharePoint Online peuvent utiliser l’outil pour résoudre les problèmes de performances afin de s’assurer que les nouvelles pages sont optimisées avant la publication.</span><span class="sxs-lookup"><span data-stu-id="134cb-165">SharePoint Online administrators and designers can use the tool to troubleshoot performance issues to ensure that new pages are optimized prior to publishing.</span></span>

<span data-ttu-id="134cb-166">**SPRequestDuration** en particulier est le temps nécessaire au traitement de la page par SharePoint.</span><span class="sxs-lookup"><span data-stu-id="134cb-166">**SPRequestDuration** in particular is the time it takes for SharePoint to process the page.</span></span> <span data-ttu-id="134cb-167">La navigation intensive (comme les pages dans le volet de navigation), les hiérarchies de sites complexes, ainsi que d’autres options de configuration et de topologie, peuvent contribuer considérablement à des durées plus longues.</span><span class="sxs-lookup"><span data-stu-id="134cb-167">Heavy navigation (like including pages in navigation), complex site hierarchies, and other configuration and topology options can all dramatically contribute to longer durations.</span></span>

## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="134cb-168">Utilisation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="134cb-168">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="134cb-169">Il s’agit de la navigation prédéfinie utilisée par défaut et est la solution la plus simple.</span><span class="sxs-lookup"><span data-stu-id="134cb-169">This is the out-of-the-box navigation used by default and is the most straightforward solution.</span></span> <span data-ttu-id="134cb-170">Il ne nécessite aucune personnalisation et un utilisateur non-technique peut également facilement ajouter des éléments, masquer des éléments et gérer la navigation dans la page Paramètres.</span><span class="sxs-lookup"><span data-stu-id="134cb-170">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="134cb-171">Nous vous recommandons d' [activer la mise en cache](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), sinon il y a un compromis entre performances onéreux.</span><span class="sxs-lookup"><span data-stu-id="134cb-171">We recommend [enabling caching](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), otherwise there is an expensive performance trade-off.</span></span>

### <a name="how-to-implement-structural-navigation-caching"></a><span data-ttu-id="134cb-172">Implémentation de la mise en cache de la navigation structurelle</span><span class="sxs-lookup"><span data-stu-id="134cb-172">How to implement structural navigation caching</span></span>

<span data-ttu-id="134cb-173">Sous **paramètres** > du site**Présentation** > **de la navigation, vous**pouvez valider si la navigation structurelle est sélectionnée pour la navigation globale ou la navigation actuelle.</span><span class="sxs-lookup"><span data-stu-id="134cb-173">Under **Site Settings** > **Look and Feel** > **Navigation**, you can validate if structural navigation is selected for either global navigation or current navigation.</span></span> <span data-ttu-id="134cb-174">La sélection de **afficher les pages** aura un impact négatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="134cb-174">Selecting **Show pages** will have negative impact on performance.</span></span>

![Navigation structurelle avec afficher les sous-sites sélectionnés](media/SPONavOptionsStructuredShowSubsites.png)

<span data-ttu-id="134cb-176">La mise en cache peut être activée ou désactivée au niveau de la collection de sites et au niveau du site, et est activée par défaut pour les deux.</span><span class="sxs-lookup"><span data-stu-id="134cb-176">Caching can be enabled or disabled at the site collection level and at the site level, and is enabled for both by default.</span></span> <span data-ttu-id="134cb-177">Pour activer au niveau de la collection de sites, sous **paramètres** > du site,**collection** > de sites administration de la**collection de sites, activez**la case à cocher **activer la mise en cache**.</span><span class="sxs-lookup"><span data-stu-id="134cb-177">To enable at the site collection level, under **Site Settings** > **Site Collection Administration** > **Site Collection Navigation**, check the box for **Enable caching**.</span></span>

![Activer la mise en cache au niveau du site](media/structural-nav/structural-nav-caching-site-coll.png)

<span data-ttu-id="134cb-179">Pour activer au niveau du site, sous **Site Settings** > **navigation**des paramètres de site, activez la case à cocher **activer la mise en cache**.</span><span class="sxs-lookup"><span data-stu-id="134cb-179">To enable at the site level, under **Site Settings** > **Navigation**, check the box for **Enable caching**.</span></span>

![Activer la mise en cache au niveau du site](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="134cb-181">Utilisation de la navigation gérée et des métadonnées dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="134cb-181">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="134cb-182">La navigation gérée est une autre option prédéfinie que vous pouvez utiliser pour recréer la plupart des fonctionnalités de navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="134cb-182">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="134cb-183">Les métadonnées gérées peuvent être configurées de façon à activer ou désactiver le filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="134cb-183">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="134cb-184">Lorsqu’elle est configurée avec filtrage de sécurité désactivé, la navigation gérée est assez efficace car elle charge tous les liens de navigation avec un nombre constant d’appels serveur.</span><span class="sxs-lookup"><span data-stu-id="134cb-184">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="134cb-185">Toutefois, l’activation du filtrage de sécurité annule certains des avantages de la navigation gérée en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="134cb-185">Enabling security trimming, however, negates some of the performance advantages of managed navigation.</span></span>

<span data-ttu-id="134cb-186">Si vous devez activer le filtrage de sécurité, il est recommandé de procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="134cb-186">If you need to enable security trimming, we recommend that you:</span></span>

- <span data-ttu-id="134cb-187">Mettre à jour tous les liens d’URL conviviaux vers des liens simples</span><span class="sxs-lookup"><span data-stu-id="134cb-187">Update all friendly URL links to simple links</span></span>
- <span data-ttu-id="134cb-188">Ajouter les nœuds de filtrage de sécurité requis en tant qu’URL conviviales</span><span class="sxs-lookup"><span data-stu-id="134cb-188">Add required security trimming nodes as friendly URLs</span></span>
- <span data-ttu-id="134cb-189">Limiter le nombre d’éléments de navigation à un maximum de 100 et un maximum de 3 niveaux</span><span class="sxs-lookup"><span data-stu-id="134cb-189">Limit the number of navigation items to no more than 100 and no more than 3 levels deep</span></span>

<span data-ttu-id="134cb-190">De nombreux sites n’ont pas besoin d’un filtrage de sécurité, car la structure de navigation est souvent cohérente pour tous les utilisateurs du site.</span><span class="sxs-lookup"><span data-stu-id="134cb-190">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="134cb-191">Si le filtrage de sécurité est désactivé et qu’un lien est ajouté à la navigation et que tous les utilisateurs n’ont pas accès à, le lien continuera de s’afficher mais entraînera un message de refus d’accès.</span><span class="sxs-lookup"><span data-stu-id="134cb-191">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="134cb-192">Il n’y a aucun risque d’accès involontaire au contenu.</span><span class="sxs-lookup"><span data-stu-id="134cb-192">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="134cb-193">Comment implémenter la navigation gérée et les résultats</span><span class="sxs-lookup"><span data-stu-id="134cb-193">How to implement managed navigation and the results</span></span>

<span data-ttu-id="134cb-194">Il existe plusieurs articles sur docs.microsoft.com concernant les détails de la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="134cb-194">There are several articles on docs.microsoft.com about the details of managed navigation.</span></span> <span data-ttu-id="134cb-195">Par exemple, reportez-vous à la rubrique [vue d’ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="134cb-195">For example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="134cb-196">Pour implémenter la navigation gérée, vous configurez des termes avec des URL correspondant à la structure de navigation du site.</span><span class="sxs-lookup"><span data-stu-id="134cb-196">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of the site.</span></span> <span data-ttu-id="134cb-197">La navigation gérée peut même être organisée manuellement pour remplacer la navigation structurelle dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="134cb-197">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="134cb-198">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="134cb-198">For example:</span></span>

![Structure de site SharePoint Online](media/SPONavOptionsListOfSites.png)<span data-ttu-id="134cb-200">)</span><span class="sxs-lookup"><span data-stu-id="134cb-200">)</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="134cb-201">Utilisation de scripts côté client basés sur la recherche</span><span class="sxs-lookup"><span data-stu-id="134cb-201">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="134cb-202">Une classe commune de mises en œuvre de navigation personnalisée comporte des modèles de conception affichés par le client qui stockent un cache local de nœuds de navigation.</span><span class="sxs-lookup"><span data-stu-id="134cb-202">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span>

<span data-ttu-id="134cb-203">Ces fournisseurs de navigation présentent quelques avantages clés :</span><span class="sxs-lookup"><span data-stu-id="134cb-203">These navigation providers have a couple of key advantages:</span></span>

- <span data-ttu-id="134cb-204">Elles fonctionnent généralement bien avec des conceptions de pages réactives.</span><span class="sxs-lookup"><span data-stu-id="134cb-204">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="134cb-205">Elles sont extrêmement évolutives et performantes, car elles peuvent être rendues sans coût de ressource (et actualiser en arrière-plan après un délai d’expiration).</span><span class="sxs-lookup"><span data-stu-id="134cb-205">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span>
- <span data-ttu-id="134cb-206">Ces fournisseurs de navigation peuvent extraire des données de navigation à l’aide de différentes stratégies, allant de simples configurations statiques à différents fournisseurs de données dynamiques.</span><span class="sxs-lookup"><span data-stu-id="134cb-206">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span>

<span data-ttu-id="134cb-207">Un exemple de fournisseur de données consiste à utiliser une **navigation**basée sur la recherche, ce qui vous permet d’énumérer les nœuds de navigation et de gérer efficacement le filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="134cb-207">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span>

<span data-ttu-id="134cb-208">Il existe d’autres options populaires pour créer des **fournisseurs de navigation personnalisés**.</span><span class="sxs-lookup"><span data-stu-id="134cb-208">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="134cb-209">Pour plus d’informations sur la création d’un fournisseur de navigation personnalisé, consultez [les solutions de navigation pour les portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .</span><span class="sxs-lookup"><span data-stu-id="134cb-209">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>

<span data-ttu-id="134cb-210">À l’aide de la recherche, vous pouvez tirer parti des index créés en arrière-plan à l’aide de l’analyse continue.</span><span class="sxs-lookup"><span data-stu-id="134cb-210">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="134cb-211">Les résultats de la recherche sont extraits de l’index de recherche et les résultats sont découpés en sécurité.</span><span class="sxs-lookup"><span data-stu-id="134cb-211">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="134cb-212">Cette règle est généralement plus rapide que les fournisseurs de navigation out-of-Box lorsque le filtrage de sécurité est requis.</span><span class="sxs-lookup"><span data-stu-id="134cb-212">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="134cb-213">L’utilisation de la recherche pour la navigation structurelle, en particulier si vous avez une structure de site complexe, accélère considérablement le temps de chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="134cb-213">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="134cb-214">Le principal avantage de cette barre de navigation gérée est que vous bénéficiez du filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="134cb-214">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="134cb-215">Cette approche implique la création d’une page maître personnalisée et le remplacement du code de navigation par des éléments HTML personnalisés.</span><span class="sxs-lookup"><span data-stu-id="134cb-215">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="134cb-216">Suivez cette procédure décrite dans l’exemple suivant pour remplacer le code de navigation dans le `seattle.html`fichier.</span><span class="sxs-lookup"><span data-stu-id="134cb-216">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="134cb-217">Dans cet exemple, vous ouvrez le `seattle.html` fichier et remplacez l’intégralité de l' `id="DeltaTopNavigation"` élément par du code HTML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="134cb-217">In this example, you will open the `seattle.html` file and replace the whole element `id="DeltaTopNavigation"` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="134cb-218">Exemple : remplacer le code de navigation prédéfinie dans une page maître</span><span class="sxs-lookup"><span data-stu-id="134cb-218">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1. <span data-ttu-id="134cb-219">Accédez à la page Paramètres du site.</span><span class="sxs-lookup"><span data-stu-id="134cb-219">Navigate to the Site Settings page.</span></span>
2. <span data-ttu-id="134cb-220">Ouvrez la Galerie de pages maîtres en cliquant sur **pages maîtres**.</span><span class="sxs-lookup"><span data-stu-id="134cb-220">Open the master page gallery by clicking **Master Pages**.</span></span>
3. <span data-ttu-id="134cb-221">À partir de là, vous pouvez naviguer dans la bibliothèque et `seattle.master`Télécharger le fichier.</span><span class="sxs-lookup"><span data-stu-id="134cb-221">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4. <span data-ttu-id="134cb-222">Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code dans la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="134cb-222">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Supprimer le bloc de code affiché](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="134cb-224">Supprimez le code entre `<SharePoint:AjaxDelta id="DeltaTopNavigation">` les `<\SharePoint:AjaxDelta>` balises et remplacez-le par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="134cb-224">Remove the code between the `<SharePoint:AjaxDelta id="DeltaTopNavigation">` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. <span data-ttu-id="134cb-225">Remplacez l’URL de la balise d’ancrage de l’image de chargement au début, par un lien vers une image de chargement dans votre collection de sites.</span><span class="sxs-lookup"><span data-stu-id="134cb-225">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="134cb-226">Une fois les modifications apportées, renommez le fichier, puis téléchargez-le dans la Galerie de pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="134cb-226">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="134cb-227">Cela génère un nouveau fichier. Master.</span><span class="sxs-lookup"><span data-stu-id="134cb-227">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="134cb-228">Ce code HTML est le balisage de base qui sera rempli par les résultats de recherche renvoyés par le code JavaScript.</span><span class="sxs-lookup"><span data-stu-id="134cb-228">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="134cb-229">Vous devrez modifier le code pour modifier la valeur de var root = "URL de la collection de sites", comme illustré dans l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="134cb-229">You will need to edit the code to change the value for var root = "site collection URL" as demonstrated in the following snippet:</span></span><br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. <span data-ttu-id="134cb-230">Les résultats sont attribués au tableau self. Nodes et une hiérarchie est créée à partir des objets à l’aide de Linq. js assignant la sortie à un tableau self. Hierarchy.</span><span class="sxs-lookup"><span data-stu-id="134cb-230">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="134cb-231">Ce tableau est l’objet lié au code HTML.</span><span class="sxs-lookup"><span data-stu-id="134cb-231">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="134cb-232">Cette opération est exécutée dans la fonction toggleView () en transmettant l’objet Self à la fonction Ko. applyBinding ().</span><span class="sxs-lookup"><span data-stu-id="134cb-232">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="134cb-233">Ainsi, le tableau de hiérarchie est lié au code HTML suivant :</span><span class="sxs-lookup"><span data-stu-id="134cb-233">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

<span data-ttu-id="134cb-234">Les gestionnaires d’événements pour `mouseenter` et `mouseexit` sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants de sous-site qui sont exécutés dans la `addEventsToElements()` fonction.</span><span class="sxs-lookup"><span data-stu-id="134cb-234">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="134cb-235">Dans notre exemple de navigation complexe, un chargement de page récent sans mise en cache locale indique que le temps passé sur le serveur a été réduit à partir de la navigation structurelle de référence pour obtenir un résultat similaire à l’approche de navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="134cb-235">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="134cb-236">À propos du fichier JavaScript...</span><span class="sxs-lookup"><span data-stu-id="134cb-236">About the JavaScript file...</span></span>

>[!NOTE]
><span data-ttu-id="134cb-237">Si vous utilisez JavaScript personnalisé, vérifiez que le CDN public est activé et que le fichier se trouve à un emplacement CDN.</span><span class="sxs-lookup"><span data-stu-id="134cb-237">If using custom JavaScript, ensure that public CDN is enabled and the file is in a CDN location.</span></span>

<span data-ttu-id="134cb-238">L’intégralité du fichier JavaScript se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="134cb-238">The entire JavaScript file is as follows:</span></span>

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

<span data-ttu-id="134cb-239">Pour résumer le code indiqué ci-dessus `jQuery $(document).ready` dans la fonction, `viewModel object` une fonction est créée `loadNavigationNodes()` , puis la fonction sur cet objet est appelée.</span><span class="sxs-lookup"><span data-stu-id="134cb-239">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="134cb-240">Cette fonction charge la hiérarchie de navigation précédemment créée stockée dans le stockage local HTML5 du navigateur client ou appelle la fonction `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="134cb-240">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="134cb-241">`QueryRemoteInterface()`génère une demande à l' `getRequest()` aide de la fonction avec le paramètre de requête défini précédemment dans le script, puis retourne des données à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="134cb-241">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="134cb-242">Ces données sont essentiellement un tableau de tous les sites de la collection de sites, représentés par des objets de transfert de données, avec différentes propriétés.</span><span class="sxs-lookup"><span data-stu-id="134cb-242">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span>

<span data-ttu-id="134cb-243">Ces données sont ensuite analysées dans les objets définis `SPO.Models.NavigationNode` précédemment qui utilisent `Knockout.js` pour créer des propriétés observables utilisées par la liaison de données des valeurs dans le code HTML que nous avons défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="134cb-243">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span>

<span data-ttu-id="134cb-244">Les objets sont ensuite placés dans un tableau de résultats.</span><span class="sxs-lookup"><span data-stu-id="134cb-244">The objects are then put into a results array.</span></span> <span data-ttu-id="134cb-245">Ce tableau est analysé dans JSON à l’aide du masquage et stocké dans le stockage du navigateur local pour de meilleures performances lors des prochains chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="134cb-245">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="134cb-246">Avantages de cette approche</span><span class="sxs-lookup"><span data-stu-id="134cb-246">Benefits of this approach</span></span>

<span data-ttu-id="134cb-247">L’un des principaux avantages de [cette approche](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) est qu’en utilisant le stockage local HTML5, la navigation est stockée localement pour l’utilisateur lors du prochain chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="134cb-247">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="134cb-248">Nous obtenons des améliorations majeures en matière de performances à l’aide de l’API de recherche pour la navigation structurelle ; Toutefois, il prend certaines capacités techniques pour exécuter et personnaliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="134cb-248">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span>

<span data-ttu-id="134cb-249">Dans l' [exemple d’implémentation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), les sites sont triés de la même manière que la navigation structurelle prédéfinie ; ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="134cb-249">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="134cb-250">Si vous souhaitez vous en écarter, il serait plus compliqué de développer et de gérer.</span><span class="sxs-lookup"><span data-stu-id="134cb-250">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="134cb-251">Cette approche nécessite également de s’écarter des pages maîtres prises en charge.</span><span class="sxs-lookup"><span data-stu-id="134cb-251">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="134cb-252">Si la page maître personnalisée n’est pas conservée, votre site se déplacera sur les mises à jour et les améliorations que Microsoft apporte aux pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="134cb-252">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="134cb-253">Le [code ci-dessus](#about-the-javascript-file) présente les dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="134cb-253">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="134cb-254">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="134cb-254">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="134cb-255">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="134cb-255">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="134cb-256">Linq. js- https://linqjs.codeplex.com/ou github.com/neuecc/Linq.js</span><span class="sxs-lookup"><span data-stu-id="134cb-256">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="134cb-257">La version actuelle de LinqJS ne contient pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompt le code de navigation.</span><span class="sxs-lookup"><span data-stu-id="134cb-257">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="134cb-258">Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq. js avant la ligne `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="134cb-258">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="134cb-259">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="134cb-259">Related topics</span></span>

[<span data-ttu-id="134cb-260">Vue d'ensemble de la navigation gérée dans SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="134cb-260">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[<span data-ttu-id="134cb-261">Mise en cache et performances de la navigation structurelle</span><span class="sxs-lookup"><span data-stu-id="134cb-261">Structural navigation caching and performance</span></span>](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
