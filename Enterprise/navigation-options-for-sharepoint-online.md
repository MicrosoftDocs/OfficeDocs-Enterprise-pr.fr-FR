---
title: Options de navigation pour SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online. Le choix et la configuration de la navigation ont un impact significatif sur les performances et l’extensibilité des sites dans SharePoint Online. Cet article ne s’applique pas aux sites d’équipe classiques.
ms.openlocfilehash: fa180e1904ef57f28e512c6d6ff163f2f4a483ad
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031259"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="9dbf2-105">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="9dbf2-106">Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="9dbf2-107">Le choix et la configuration de la navigation ont un impact significatif sur les performances et l’extensibilité des sites dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="9dbf2-108">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9dbf2-108">Overview</span></span>

<span data-ttu-id="9dbf2-109">La configuration du fournisseur de navigation peut avoir un impact significatif sur les performances de l’ensemble du site, et vous devez tenir compte de la sélection d’un fournisseur de navigation et d’une configuration qui évoluent efficacement pour les besoins d’un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-109">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="9dbf2-110">Il existe deux fournisseurs de navigation prédéfinis, ainsi que des implémentations de navigation personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-110">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="9dbf2-111">La première option, la [**navigation gérée (métadonnées)**](#using-managed-navigation-and-metadata-in-sharepoint-online), est recommandée et est l’une des options par défaut dans SharePoint Online ; Toutefois, nous vous recommandons de désactiver le filtrage de sécurité, sauf en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-111">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="9dbf2-112">Le filtrage de sécurité est activé comme paramètre sécurisé par défaut pour ce fournisseur de navigation ; Toutefois, de nombreux sites n’ont pas besoin de la charge de filtrage de sécurité, car les éléments de navigation sont souvent cohérents pour tous les utilisateurs du site.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-112">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="9dbf2-113">Avec la configuration recommandée pour désactiver le filtrage de sécurité, ce fournisseur de navigation ne requiert pas l’énumération de la structure du site et est hautement évolutif avec un impact acceptable sur les performances.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-113">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="9dbf2-114">La deuxième option, [**navigation structurelle**](#using-structural-navigation-in-sharepoint-online), **n’est pas une option de navigation recommandée dans SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-114">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="9dbf2-115">Ce fournisseur de navigation a été conçu pour une topologie locale a une prise en charge limitée dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-115">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="9dbf2-116">Bien qu’il fournisse des fonctionnalités supplémentaires par rapport aux autres options de navigation, ces fonctionnalités, y compris le filtrage de sécurité et l’énumération de la structure de site, ont un coût d’appels serveur excessifs et ont un impact sur l’évolutivité et les performances lorsqu’elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-116">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="9dbf2-117">Les sites qui utilisent la navigation structurée qui consomment des ressources excessives peuvent être soumis à la limitation.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-117">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="9dbf2-118">En plus des fournisseurs de navigation prédéfinis, de nombreux clients ont implémenté les autres implémentations de navigation personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-118">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="9dbf2-119">Une classe commune de mises en œuvre de navigation personnalisée comporte des modèles de conception affichés par le client qui stockent un cache local de nœuds de navigation.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-119">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="9dbf2-120">(Voir **[script côté client](#using-search-driven-client-side-scripting)** basé sur la recherche dans cet article.)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-120">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="9dbf2-121">Ces fournisseurs de navigation présentent quelques avantages clés :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-121">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="9dbf2-122">Elles fonctionnent généralement bien avec des conceptions de pages réactives.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-122">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="9dbf2-123">Elles sont extrêmement évolutives et performantes, car elles peuvent être rendues sans coût de ressource (et actualiser en arrière-plan après un délai d’expiration).</span><span class="sxs-lookup"><span data-stu-id="9dbf2-123">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="9dbf2-124">Ces fournisseurs de navigation peuvent extraire des données de navigation à l’aide de différentes stratégies, allant de simples configurations statiques à différents fournisseurs de données dynamiques.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-124">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="9dbf2-125">Un exemple de fournisseur de données consiste à utiliser une **navigation**basée sur la recherche, ce qui vous permet d’énumérer les nœuds de navigation et de gérer efficacement le filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-125">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="9dbf2-126">Il existe d’autres options populaires pour créer des **fournisseurs de navigation personnalisés**.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-126">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="9dbf2-127">Pour plus d’informations sur la création d’un fournisseur de navigation personnalisé, consultez [les solutions de navigation pour les portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .</span><span class="sxs-lookup"><span data-stu-id="9dbf2-127">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="9dbf2-128">Avantages et inconvénients des options de navigation SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-128">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="9dbf2-129">Le tableau suivant récapitule les avantages et les inconvénients de chaque option.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-129">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="9dbf2-130">Navigation gérée</span><span class="sxs-lookup"><span data-stu-id="9dbf2-130">Managed navigation</span></span>  |<span data-ttu-id="9dbf2-131">Navigation structurelle</span><span class="sxs-lookup"><span data-stu-id="9dbf2-131">Structural navigation</span></span>  |<span data-ttu-id="9dbf2-132">Navigation basée sur la recherche</span><span class="sxs-lookup"><span data-stu-id="9dbf2-132">Search-driven navigation</span></span>  |<span data-ttu-id="9dbf2-133">Fournisseur de navigation personnalisée</span><span class="sxs-lookup"><span data-stu-id="9dbf2-133">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="9dbf2-134">Avantages</span><span class="sxs-lookup"><span data-stu-id="9dbf2-134">Pros:</span></span><br/><br/><span data-ttu-id="9dbf2-135">Facilité de maintenance</span><span class="sxs-lookup"><span data-stu-id="9dbf2-135">Easy to maintain</span></span><br/><span data-ttu-id="9dbf2-136">Option recommandée</span><span class="sxs-lookup"><span data-stu-id="9dbf2-136">Recommended option</span></span><br/>     |<span data-ttu-id="9dbf2-137">Avantages</span><span class="sxs-lookup"><span data-stu-id="9dbf2-137">Pros:</span></span><br/><br/><span data-ttu-id="9dbf2-138">Facile à configurer</span><span class="sxs-lookup"><span data-stu-id="9dbf2-138">Easy to configure</span></span><br/><span data-ttu-id="9dbf2-139">Sécurité découpée</span><span class="sxs-lookup"><span data-stu-id="9dbf2-139">Security trimmed</span></span><br/><span data-ttu-id="9dbf2-140">Mises à jour automatiques au fur et à mesure de l’ajout de contenu</span><span class="sxs-lookup"><span data-stu-id="9dbf2-140">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="9dbf2-141">Avantages</span><span class="sxs-lookup"><span data-stu-id="9dbf2-141">Pros:</span></span><br/><br/><span data-ttu-id="9dbf2-142">Sécurité découpée</span><span class="sxs-lookup"><span data-stu-id="9dbf2-142">Security trimmed</span></span><br/><span data-ttu-id="9dbf2-143">Mises à jour automatiques lors de l’ajout de sites</span><span class="sxs-lookup"><span data-stu-id="9dbf2-143">Automatically updates as sites are added</span></span><br/><span data-ttu-id="9dbf2-144">Temps de chargement rapide et structure de navigation mise en cache locale</span><span class="sxs-lookup"><span data-stu-id="9dbf2-144">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="9dbf2-145">Avantages</span><span class="sxs-lookup"><span data-stu-id="9dbf2-145">Pros:</span></span><br/><br/><span data-ttu-id="9dbf2-146">Choix plus large d’options disponibles</span><span class="sxs-lookup"><span data-stu-id="9dbf2-146">Wider choice of options available</span></span><br/><span data-ttu-id="9dbf2-147">Chargement rapide lorsque la mise en cache est utilisée correctement</span><span class="sxs-lookup"><span data-stu-id="9dbf2-147">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="9dbf2-148">De nombreuses options fonctionnent bien avec la conception de pages réactives</span><span class="sxs-lookup"><span data-stu-id="9dbf2-148">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="9dbf2-149">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="9dbf2-149">Cons:</span></span><br/><br/><span data-ttu-id="9dbf2-150">Mise à jour non automatique pour refléter la structure du site</span><span class="sxs-lookup"><span data-stu-id="9dbf2-150">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="9dbf2-151">Impact sur les performances si le filtrage de sécurité est activé</span><span class="sxs-lookup"><span data-stu-id="9dbf2-151">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="9dbf2-152">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="9dbf2-152">Cons:</span></span><br/><br/><span data-ttu-id="9dbf2-153">**Non recommandé**</span><span class="sxs-lookup"><span data-stu-id="9dbf2-153">**Not recommended**</span></span><br/><span data-ttu-id="9dbf2-154">**Impact sur les performances et l’extensibilité**</span><span class="sxs-lookup"><span data-stu-id="9dbf2-154">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="9dbf2-155">**Soumis à la limitation**</span><span class="sxs-lookup"><span data-stu-id="9dbf2-155">**Subject to throttling**</span></span><br/>|<span data-ttu-id="9dbf2-156">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="9dbf2-156">Cons:</span></span><br/><br/><span data-ttu-id="9dbf2-157">Aucune possibilité de classer facilement les sites</span><span class="sxs-lookup"><span data-stu-id="9dbf2-157">No ability to easily order sites</span></span><br/><span data-ttu-id="9dbf2-158">Nécessite une personnalisation de la page maître (compétences techniques requises)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-158">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="9dbf2-159">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="9dbf2-159">Cons:</span></span><br/><br/><span data-ttu-id="9dbf2-160">Un développement personnalisé est requis</span><span class="sxs-lookup"><span data-stu-id="9dbf2-160">Custom development is required</span></span><br/><span data-ttu-id="9dbf2-161">La source de données externe/le cache stocké est nécessaire par exemple, Azure</span><span class="sxs-lookup"><span data-stu-id="9dbf2-161">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="9dbf2-162">L’option la plus appropriée pour votre site dépend de vos besoins en matière de site et de vos capacités techniques.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-162">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="9dbf2-163">Si vous souhaitez un fournisseur de navigation out-of-out évolutif, la navigation gérée avec filtrage de sécurité désactivé est une très bonne option.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-163">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="9dbf2-164">L’option de navigation gérée peut être gérée par le biais de la configuration, n’implique pas de fichiers de personnalisation de code, et elle est beaucoup plus rapide que la navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-164">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="9dbf2-165">Si vous avez besoin d’un filtrage de sécurité et que vous êtes familiarisé à l’utilisation d’une page maître personnalisée et que vous disposez d’une fonctionnalité dans l’Organisation pour conserver les modifications susceptibles de se produire dans la page maître par défaut pour SharePoint Online, l’option de recherche peut produire une meilleure expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-165">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="9dbf2-166">Si vous avez des exigences plus complexes, un fournisseur de navigation personnalisé peut être le bon choix.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-166">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="9dbf2-167">La navigation structurelle n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-167">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="9dbf2-168">Enfin, il est important de noter que SharePoint ajoute des fournisseurs de navigation et des fonctionnalités supplémentaires pour les architectures de sites SharePoint modernes exploitant une hiérarchie de sites plus aplatie et un modèle Hub-and-spoke avec des sites hub SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-168">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="9dbf2-169">Cela permet de réaliser de nombreux scénarios qui ne nécessitent pas l’utilisation de la fonctionnalité de publication SharePoint, et ces configurations de navigation sont optimisées pour l’extensibilité et la latence dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-169">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="9dbf2-170">Notez que le fait d’appliquer le même principe : simplifier la structure globale de votre site de publication SharePoint en une structure plus plat, permet souvent d’obtenir des performances globales et de l’adapter.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-170">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="9dbf2-171">Cela signifie qu’au lieu d’avoir une seule collection de sites avec des centaines de sites (sous-sites Web), une meilleure approche consiste à avoir de nombreuses collections de sites avec très peu de sous-sites (sous-sites Web).</span><span class="sxs-lookup"><span data-stu-id="9dbf2-171">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="9dbf2-172">Utilisation de la navigation gérée et des métadonnées dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-172">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="9dbf2-173">La navigation gérée est une autre option prédéfinie que vous pouvez utiliser pour recréer la plupart des fonctionnalités de navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-173">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="9dbf2-174">Les métadonnées gérées peuvent être configurées de façon à activer ou désactiver le filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-174">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="9dbf2-175">Lorsqu’elle est configurée avec filtrage de sécurité désactivé, la navigation gérée est assez efficace car elle charge tous les liens de navigation avec un nombre constant d’appels serveur.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-175">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="9dbf2-176">Toutefois, l’activation du filtrage de sécurité annule certains des avantages de la navigation gérée, et les clients peuvent choisir d’explorer l’une des solutions de navigation personnalisées pour des performances et une évolutivité optimales.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-176">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="9dbf2-177">De nombreux sites n’ont pas besoin d’un filtrage de sécurité, car la structure de navigation est souvent cohérente pour tous les utilisateurs du site.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-177">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="9dbf2-178">Si le filtrage de sécurité est désactivé et qu’un lien est ajouté à la navigation et que tous les utilisateurs n’ont pas accès à, le lien continuera de s’afficher mais entraînera un message de refus d’accès.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-178">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="9dbf2-179">Il n’y a aucun risque d’accès involontaire au contenu.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-179">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="9dbf2-180">Comment implémenter la navigation gérée et les résultats</span><span class="sxs-lookup"><span data-stu-id="9dbf2-180">How to implement managed navigation and the results</span></span>

<span data-ttu-id="9dbf2-181">Il existe plusieurs articles sur Docs.Microsoft.com sur les détails de la navigation gérée, par exemple, voir [Overview of Managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="9dbf2-181">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="9dbf2-182">Pour implémenter la navigation gérée, vous configurez des termes avec des URL correspondant à la structure de navigation du site.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-182">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="9dbf2-183">La navigation gérée peut même être organisée manuellement pour remplacer la navigation structurelle dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-183">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="9dbf2-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-184">For example:</span></span>

![Structure de site SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="9dbf2-186">L’exemple suivant montre les performances de la navigation complexe à l’aide de la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-186">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Performances de la navigation complexe à l’aide de la navigation gérée](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="9dbf2-188">L’utilisation de la navigation gérée améliore de façon cohérente les performances par rapport à l’approche de navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-188">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="9dbf2-189">Utilisation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-189">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="9dbf2-190">Il s’agit de la navigation prédéfinie utilisée par défaut et est la solution la plus simple, mais elle présente un compromis entre performances onéreux.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-190">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="9dbf2-191">Il ne nécessite aucune personnalisation et un utilisateur non-technique peut également facilement ajouter des éléments, masquer des éléments et gérer la navigation dans la page Paramètres.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-191">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="9dbf2-192">Ceci est toutefois également vrai pour la navigation gérée, c’est pourquoi il est recommandé d’utiliser la navigation gérée comme cela peut également être géré et contrôlé facilement et avec de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-192">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Navigation structurelle avec afficher les sous-sites sélectionnés](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="9dbf2-194">Activation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-194">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="9dbf2-195">Montrer comment les performances d’une solution SharePoint Online standard avec navigation structurelle et l’option Afficher les sous-sites sont activées.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-195">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="9dbf2-196">Vous trouverez ci-dessous une capture d’écran des paramètres de **navigation**des **paramètres** \> de site de la page.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-196">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Capture d’écran montrant des sous-sites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="9dbf2-198">Analyse des performances de navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9dbf2-198">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="9dbf2-199">Pour analyser les performances d’une page SharePoint, utilisez l’onglet **réseau** des outils de développement F12 dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-199">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Capture d’écran montrant l’onglet Réseau des Outils de développement F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="9dbf2-201">Dans l’onglet **réseau** , cliquez sur la page. aspx en cours de chargement, puis cliquez sur l’onglet **Détails** .</span><span class="sxs-lookup"><span data-stu-id="9dbf2-201">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="9dbf2-202">![Capture d’écran montrant l’onglet Détails](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-202">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="9dbf2-203">Cliquez sur **en-têtes de réponse**.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-203">Click **Response headers**.</span></span> <br/><span data-ttu-id="9dbf2-204">![Capture d’écran de l’onglet Détails](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-204">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="9dbf2-205">SharePoint renvoie des informations de diagnostic utiles dans ses en-têtes de réponse.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-205">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="9dbf2-206">L’un des éléments d’information les plus utiles est **SPRequestDuration** , qui est la valeur, en millisecondes, de la durée de traitement d’une demande sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-206">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="9dbf2-207">Dans la capture d’écran suivante, les **sous-sites** ne sont pas vérifiés pour la navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-207">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="9dbf2-208">Cela signifie qu’il n’existe qu’un lien de collection de sites dans la navigation globale :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-208">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="9dbf2-209">![Capture d’écran montrant le temps de chargement en tant que durée de la demande](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-209">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="9dbf2-210">La valeur de la clé **SPRequestDuration** est de 245 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-210">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="9dbf2-211">Cela représente le temps nécessaire pour retourner la demande.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-211">This represents the time it took to return the request.</span></span> <span data-ttu-id="9dbf2-212">Étant donné qu’il n’existe qu’un seul élément de navigation sur le site, il s’agit d’un point de référence adapté à la façon dont SharePoint Online effectue la navigation.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-212">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="9dbf2-213">La capture d’écran suivante montre comment l’ajout dans les sous-sites affecte cette clé.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-213">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="9dbf2-214">![Capture d’écran montrant une durée de demande de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="9dbf2-214">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="9dbf2-215">L’ajout des sous-sites a considérablement augmenté le temps nécessaire pour renvoyer la demande de page pour cet exemple de site relativement simple.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-215">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="9dbf2-216">Les hiérarchies de sites complexes, y compris les pages de navigation, ainsi que d’autres options de configuration et de topologie, peuvent considérablement augmenter cet impact.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-216">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="9dbf2-217">Utilisation de scripts côté client basés sur la recherche</span><span class="sxs-lookup"><span data-stu-id="9dbf2-217">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="9dbf2-218">À l’aide de la recherche, vous pouvez tirer parti des index créés en arrière-plan à l’aide de l’analyse continue.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-218">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="9dbf2-219">Les résultats de la recherche sont extraits de l’index de recherche et les résultats sont découpés en sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-219">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="9dbf2-220">Cette règle est généralement plus rapide que les fournisseurs de navigation out-of-Box lorsque le filtrage de sécurité est requis.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-220">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="9dbf2-221">L’utilisation de la recherche pour la navigation structurelle, en particulier si vous avez une structure de site complexe, accélère considérablement le temps de chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-221">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="9dbf2-222">Le principal avantage de cette barre de navigation gérée est que vous bénéficiez du filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-222">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="9dbf2-223">Cette approche implique la création d’une page maître personnalisée et le remplacement du code de navigation par des éléments HTML personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-223">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="9dbf2-224">Suivez cette procédure décrite dans l’exemple suivant pour remplacer le code de navigation dans le `seattle.html`fichier.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-224">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="9dbf2-225">Dans cet exemple, vous ouvrez le `seattle.html` fichier et remplacez l’intégralité de l' `id=”DeltaTopNavigation”` élément par du code HTML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-225">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="9dbf2-226">Exemple : remplacer le code de navigation prédéfinie dans une page maître</span><span class="sxs-lookup"><span data-stu-id="9dbf2-226">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="9dbf2-227">Accédez à la page Paramètres du site.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-227">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="9dbf2-228">Ouvrez la Galerie de pages maîtres en cliquant sur **pages maîtres**.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-228">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="9dbf2-229">À partir de là, vous pouvez naviguer dans la bibliothèque et `seattle.master`Télécharger le fichier.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-229">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="9dbf2-230">Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code dans la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-230">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Supprimer le bloc de code affiché](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="9dbf2-232">Supprimez le code entre `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` les `<\SharePoint:AjaxDelta>` balises et remplacez-le par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-232">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
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
6. <span data-ttu-id="9dbf2-233">Remplacez l’URL de la balise d’ancrage de l’image de chargement au début, par un lien vers une image de chargement dans votre collection de sites.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-233">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="9dbf2-234">Une fois les modifications apportées, renommez le fichier, puis téléchargez-le dans la Galerie de pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-234">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="9dbf2-235">Cela génère un nouveau fichier. Master.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-235">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="9dbf2-236">Ce code HTML est le balisage de base qui sera rempli par les résultats de recherche renvoyés par le code JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-236">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="9dbf2-237">Vous devrez modifier le code pour modifier la valeur de var root = "URL de la collection de sites", comme illustré dans l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-237">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="9dbf2-238">Les résultats sont attribués au tableau self. Nodes et une hiérarchie est créée à partir des objets à l’aide de Linq. js assignant la sortie à un tableau self. Hierarchy.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-238">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="9dbf2-239">Ce tableau est l’objet lié au code HTML.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-239">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="9dbf2-240">Cette opération est exécutée dans la fonction toggleView () en transmettant l’objet Self à la fonction Ko. applyBinding ().</span><span class="sxs-lookup"><span data-stu-id="9dbf2-240">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="9dbf2-241">Ainsi, le tableau de hiérarchie est lié au code HTML suivant :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-241">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="9dbf2-242">Les gestionnaires d’événements pour `mouseenter` et `mouseexit` sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants de sous-site qui sont exécutés dans la `addEventsToElements()` fonction.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-242">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="9dbf2-243">Dans notre exemple de navigation complexe, un chargement de page récent sans mise en cache locale indique que le temps passé sur le serveur a été réduit à partir de la navigation structurelle de référence pour obtenir un résultat similaire à l’approche de navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-243">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="9dbf2-244">À propos du fichier JavaScript...</span><span class="sxs-lookup"><span data-stu-id="9dbf2-244">About the JavaScript file...</span></span>

<span data-ttu-id="9dbf2-245">L’intégralité du fichier JavaScript se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-245">The entire JavaScript file is as follows:</span></span>

```
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

    // ByHierarchy method breaks the sorting in chrome and firefix 
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

<span data-ttu-id="9dbf2-246">Pour résumer le code indiqué ci-dessus `jQuery $(document).ready` dans la fonction, `viewModel object` une fonction est créée `loadNavigationNodes()` , puis la fonction sur cet objet est appelée.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-246">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="9dbf2-247">Cette fonction charge la hiérarchie de navigation précédemment créée stockée dans le stockage local HTML5 du navigateur client ou appelle la fonction `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-247">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="9dbf2-248">`QueryRemoteInterface()`génère une demande à l' `getRequest()` aide de la fonction avec le paramètre de requête défini précédemment dans le script, puis retourne des données à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-248">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="9dbf2-249">Ces données sont essentiellement un tableau de tous les sites de la collection de sites, représentés par des objets de transfert de données, avec différentes propriétés.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-249">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="9dbf2-250">Ces données sont ensuite analysées dans les objets définis `SPO.Models.NavigationNode` précédemment qui utilisent `Knockout.js` pour créer des propriétés observables utilisées par la liaison de données des valeurs dans le code HTML que nous avons défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-250">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="9dbf2-251">Les objets sont ensuite placés dans un tableau de résultats.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-251">The objects are then put into a results array.</span></span> <span data-ttu-id="9dbf2-252">Ce tableau est analysé dans JSON à l’aide du masquage et stocké dans le stockage du navigateur local pour de meilleures performances lors des prochains chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-252">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="9dbf2-253">Avantages de cette approche</span><span class="sxs-lookup"><span data-stu-id="9dbf2-253">Benefits of this approach</span></span>

<span data-ttu-id="9dbf2-254">L’un des principaux avantages de [cette approche](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) est qu’en utilisant le stockage local HTML5, la navigation est stockée localement pour l’utilisateur lors du prochain chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-254">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="9dbf2-255">Nous obtenons des améliorations majeures en matière de performances à l’aide de l’API de recherche pour la navigation structurelle ; Toutefois, il prend certaines capacités techniques pour exécuter et personnaliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-255">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="9dbf2-256">Dans l' [exemple d’implémentation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), les sites sont triés de la même manière que la navigation structurelle prédéfinie ; ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-256">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="9dbf2-257">Si vous souhaitez vous en écarter, il serait plus compliqué de développer et de gérer.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-257">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="9dbf2-258">Cette approche nécessite également de s’écarter des pages maîtres prises en charge.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-258">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="9dbf2-259">Si la page maître personnalisée n’est pas conservée, votre site se déplacera sur les mises à jour et les améliorations que Microsoft apporte aux pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-259">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="9dbf2-260">Le [code ci-dessus](#about-the-javascript-file) présente les dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="9dbf2-260">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="9dbf2-261">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="9dbf2-261">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="9dbf2-262">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="9dbf2-262">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="9dbf2-263">Linq. js- https://linqjs.codeplex.com/ou github.com/neuecc/Linq.js</span><span class="sxs-lookup"><span data-stu-id="9dbf2-263">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="9dbf2-264">La version actuelle de LinqJS ne contient pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompt le code de navigation.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-264">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="9dbf2-265">Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq. js avant la ligne `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="9dbf2-265">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
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
  
## <a name="related-topics"></a><span data-ttu-id="9dbf2-266">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dbf2-266">Related topics</span></span>

[<span data-ttu-id="9dbf2-267">Vue d'ensemble de la navigation gérée dans SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="9dbf2-267">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

