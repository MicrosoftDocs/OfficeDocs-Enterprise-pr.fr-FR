---
title: Options de navigation pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Cet article décrit les sites des options de navigation avec publication SharePoint activé dans SharePoint Online. Le choix et la configuration de la navigation affecte considérablement les performances et l’évolutivité de sites dans SharePoint Online.
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957449"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="8e4af-104">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="8e4af-p102">Cet article décrit les sites des options de navigation avec publication SharePoint activé dans SharePoint Online. Le choix et la configuration de la navigation affecte considérablement les performances et l’évolutivité de sites dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="8e4af-107">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8e4af-107">Overview</span></span>

<span data-ttu-id="8e4af-p103">Configuration du fournisseur de navigation peut affecter considérablement les performances pour l’intégralité du site, et une attention particulière doit être prise pour sélectionner un fournisseur de navigation et la configuration qui met en œuvre efficacement pour la configuration requise d’un site SharePoint. Il existe deux fournisseurs de navigation out-of-the-box, ainsi que les implémentations de navigation personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="8e4af-p104">La première option, la [**navigation gérée (métadonnées)**](#using-managed-navigation-and-metadata-in-sharepoint-online), est recommandée et est une des options par défaut dans SharePoint Online ; Toutefois, nous recommandons que le filtrage de sécurité être désactivé sauf indication contraire. Ajustement de la sécurité est activé comme un paramètre d’informations sécurisé par défaut pour ce fournisseur de navigation ; Toutefois, le nombre de sites ne nécessite pas de la charge de découpage de sécurité dans la mesure où les éléments de navigation sont souvent cohérentes pour tous les utilisateurs du site. Avec la configuration recommandée pour désactiver le filtrage de sécurité, ce fournisseur de navigation ne nécessite pas de l’énumération de la structure du site et est hautement évolutif avec des performances acceptables.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="8e4af-p105">La deuxième option, [**navigation structurelle**](#using-structural-navigation-in-sharepoint-online), **n’est pas une option de navigation recommandées dans SharePoint Online**. Ce fournisseur de navigation a été conçu pour une topologie locale est limitée à la prise en charge dans SharePoint Online. Il fournit un ensemble de fonctionnalités par rapport à d’autres options de navigation supplémentaire, ces fonctionnalités, notamment le filtrage de sécurité et énumération de structure de site, a un coût d’appels excessive du serveur et les performances et évolutivité des impacts lorsqu’elle est utilisée. Sites à l’aide de la navigation structed qui consomment trop de ressources peuvent être soumis à la limitation.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="8e4af-p106">Outre les fournisseurs de navigation out-of-the-box, de nombreux clients ont réussi implémentations autre navigation personnalisée. Une classe commune des implémentations de navigation personnalisé s’appuie sur les modèles de conception de rendu de client qui stockent un cache local des nœuds de navigation. (Voir **[recherche script côté client](#using-search-driven-client-side-scripting)** dans cet article).</span><span class="sxs-lookup"><span data-stu-id="8e4af-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="8e4af-120">Ces fournisseurs de navigation ont deux principaux avantages :</span><span class="sxs-lookup"><span data-stu-id="8e4af-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="8e4af-121">En règle générale, ils fonctionnent également avec les modèles de page vite.</span><span class="sxs-lookup"><span data-stu-id="8e4af-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="8e4af-122">Ils sont très évolutives et performante, car ils peuvent restituer sans coût de la ressource (et les actualiser en arrière-plan après un délai d’expiration).</span><span class="sxs-lookup"><span data-stu-id="8e4af-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="8e4af-123">Ces fournisseurs de navigation peuvent récupérer des données de navigation à l’aide de diverses stratégies, allant de configurations statiques simples à différents fournisseurs de données dynamique.</span><span class="sxs-lookup"><span data-stu-id="8e4af-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="8e4af-124">Un exemple d’un fournisseur de données consiste à utiliser une **navigation axée sur la recherche**, qui permet la flexibilité de l’énumération des nœuds de navigation et de gérer efficacement de filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8e4af-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="8e4af-p107">Il existe d’autres options populaires pour créer des **fournisseurs de navigation personnalisé**. Examinez [les solutions de Navigation pour les portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) pour obtenir des instructions sur la création d’un fournisseur de navigation personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="8e4af-127">Options de navigation des avantages et inconvénients de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="8e4af-128">Le tableau suivant récapitule les avantages et inconvénients de chaque option.</span><span class="sxs-lookup"><span data-stu-id="8e4af-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="8e4af-129">Navigation gérée</span><span class="sxs-lookup"><span data-stu-id="8e4af-129">Managed navigation</span></span>  |<span data-ttu-id="8e4af-130">Navigation structurelle</span><span class="sxs-lookup"><span data-stu-id="8e4af-130">Structural navigation</span></span>  |<span data-ttu-id="8e4af-131">Navigation basée sur la recherche</span><span class="sxs-lookup"><span data-stu-id="8e4af-131">Search-driven navigation</span></span>  |<span data-ttu-id="8e4af-132">Fournisseur de navigation personnalisé</span><span class="sxs-lookup"><span data-stu-id="8e4af-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="8e4af-133">Avantages :</span><span class="sxs-lookup"><span data-stu-id="8e4af-133">Pros:</span></span><br/><br/><span data-ttu-id="8e4af-134">Facilité de maintenance</span><span class="sxs-lookup"><span data-stu-id="8e4af-134">Easy to maintain</span></span><br/><span data-ttu-id="8e4af-135">Option recommandée</span><span class="sxs-lookup"><span data-stu-id="8e4af-135">Recommended option</span></span><br/>     |<span data-ttu-id="8e4af-136">Avantages :</span><span class="sxs-lookup"><span data-stu-id="8e4af-136">Pros:</span></span><br/><br/><span data-ttu-id="8e4af-137">Facilité de configuration</span><span class="sxs-lookup"><span data-stu-id="8e4af-137">Easy to configure</span></span><br/><span data-ttu-id="8e4af-138">Limités de sécurité</span><span class="sxs-lookup"><span data-stu-id="8e4af-138">Security trimmed</span></span><br/><span data-ttu-id="8e4af-139">Met à jour automatiquement lorsque le contenu est ajouté.</span><span class="sxs-lookup"><span data-stu-id="8e4af-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="8e4af-140">Avantages :</span><span class="sxs-lookup"><span data-stu-id="8e4af-140">Pros:</span></span><br/><br/><span data-ttu-id="8e4af-141">Limités de sécurité</span><span class="sxs-lookup"><span data-stu-id="8e4af-141">Security trimmed</span></span><br/><span data-ttu-id="8e4af-142">Mise à jour automatique lorsque des sites sont ajoutés</span><span class="sxs-lookup"><span data-stu-id="8e4af-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="8e4af-143">Rapidité de chargement et structure de navigation mise en cache localement</span><span class="sxs-lookup"><span data-stu-id="8e4af-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="8e4af-144">Avantages :</span><span class="sxs-lookup"><span data-stu-id="8e4af-144">Pros:</span></span><br/><br/><span data-ttu-id="8e4af-145">Élargir le choix des options disponibles</span><span class="sxs-lookup"><span data-stu-id="8e4af-145">Wider choice of options available</span></span><br/><span data-ttu-id="8e4af-146">Chargement rapide lors de la mise en cache est utilisé correctement</span><span class="sxs-lookup"><span data-stu-id="8e4af-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="8e4af-147">Nombreuses options fonctionnent correctement avec la conception des pages réactif</span><span class="sxs-lookup"><span data-stu-id="8e4af-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="8e4af-148">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="8e4af-148">Cons:</span></span><br/><br/><span data-ttu-id="8e4af-149">Pas de mises à jour automatiques lorsque des sites sont ajoutés</span><span class="sxs-lookup"><span data-stu-id="8e4af-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="8e4af-150">Affecte les performances si la suppression de la sécurité est activée.</span><span class="sxs-lookup"><span data-stu-id="8e4af-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="8e4af-151">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="8e4af-151">Cons:</span></span><br/><br/><span data-ttu-id="8e4af-152">**Non recommandé**</span><span class="sxs-lookup"><span data-stu-id="8e4af-152">**Not recommended**</span></span><br/><span data-ttu-id="8e4af-153">**Impacts sur les performances et évolutivité**</span><span class="sxs-lookup"><span data-stu-id="8e4af-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="8e4af-154">**Soumis à la limitation**</span><span class="sxs-lookup"><span data-stu-id="8e4af-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="8e4af-155">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="8e4af-155">Cons:</span></span><br/><br/><span data-ttu-id="8e4af-156">Aucune possibilité de classer facilement les sites</span><span class="sxs-lookup"><span data-stu-id="8e4af-156">No ability to easily order sites</span></span><br/><span data-ttu-id="8e4af-157">Nécessite une personnalisation de la page maître (compétences techniques requises)</span><span class="sxs-lookup"><span data-stu-id="8e4af-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="8e4af-158">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="8e4af-158">Cons:</span></span><br/><br/><span data-ttu-id="8e4af-159">Développement personnalisé est requis</span><span class="sxs-lookup"><span data-stu-id="8e4af-159">Custom development is required</span></span><br/><span data-ttu-id="8e4af-160">Source de données externe / cache stocké est nécessaire, par exemple Azure</span><span class="sxs-lookup"><span data-stu-id="8e4af-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="8e4af-p108">L’option la plus appropriée pour votre site dépendent des besoins de votre site et de vos capacités techniques. Si vous souhaitez un fournisseur de navigation d’out-of-the-box évolutive, navigation gérée avec filtrage de sécurité désactivé est une très bonne option.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="8e4af-p109">L’option de navigation gérée peut être gérée par le biais de la configuration, n’implique pas les fichiers de personnalisation de code, et il est beaucoup plus rapide que la navigation structurelle. Si vous nécessitent le filtrage de sécurité et sentez à l’aise avec une page maître personnalisée et certaines fonctions dans l’organisation pour gérer les modifications qui peuvent se produire dans la page maître par défaut pour SharePoint Online, l’option de recherche peut produire une meilleure expérience utilisateur. Si vous avez des exigences plus complexes, un fournisseur de navigation personnalisé peut être le bon choix. Navigation structurelle n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="8e4af-p110">Enfin, il est important de noter que SharePoint est Ajout de fournisseurs de navigation supplémentaires et des fonctionnalités pour les architectures de site SharePoint exploitant une hiérarchie de site plus aplatie et un modèle « hub and spoke » avec les sites hub de SharePoint. Cela permet de nombreux scénarios à atteindre qui ne nécessitent pas l’utilisation de la fonctionnalité publication SharePoint, et ces configurations de navigation sont optimisées pour l’évolutivité et la latence dans SharePoint Online. Notez que l’application du même principe - simplification de la structure globale de votre site de publication SharePoint vers une structure plus simple, souvent une aide les performances globales et faire évoluer également. Cela signifie qu’au lieu d’avoir une seule Collection de sites avec des centaines de sites (sous-sites), il est préférable d’avoir plusieurs collections de sites avec des sous-sites minime (sous-sites).</span><span class="sxs-lookup"><span data-stu-id="8e4af-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="8e4af-171">À l’aide de la navigation gérée et métadonnées dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="8e4af-p111">Navigation gérée est une autre option out-of-the-box que vous pouvez utiliser pour recréer la plupart de la même fonctionnalité que la navigation structurelle. Métadonnées gérées peuvent être configurée pour que le filtrage de sécurité activées ou désactivées. Configurés avec filtrage de sécurité désactivée, lors de la navigation gérée est assez efficace tandis qu’il charge tous les liens de navigation avec un nombre constant d’appels du serveur. Évite d’activation du filtrage de sécurité, toutefois, certains des avantages de la navigation gérée et les clients peuvent choisir d’Explorer une des solutions de navigation personnalisé pour optimiser les performances et évolutivité.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="8e4af-p112">Le nombre de sites ne nécessite pas de filtrage de sécurité, comme la structure de navigation est souvent cohérente pour tous les utilisateurs du site. Si le filtrage de sécurité est désactivé, un lien est ajouté à la navigation pas tous les utilisateurs ont accès à la liaison affiche toujours mais entraînera un message accès refusé. Il n’existe aucun risque d’accès par inadvertance dans le contenu.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="8e4af-179">Implémentation de la navigation gérée et des résultats</span><span class="sxs-lookup"><span data-stu-id="8e4af-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="8e4af-180">Il existe plusieurs articles sur Docs.Microsoft.com sur les détails de la navigation gérée, par exemple, voir [vue d’ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="8e4af-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="8e4af-p113">Afin d’implémenter la navigation gérée, vous configurer termes avec l’URL correspondant à la structure de navigation du site. Navigation gérée permettre même être curated manuellement pour remplacer la navigation structurelle dans de nombreux cas. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8e4af-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![Structure du site SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="8e4af-185">L’exemple suivant montre les performances d’une navigation complexe utilisant la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="8e4af-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Performances de navigation complexe à l’aide de la navigation gérée](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="8e4af-187">L’utilisation de navigation gérée cohérente améliore les performances par rapport à l’approche de la structure de navigation.</span><span class="sxs-lookup"><span data-stu-id="8e4af-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="8e4af-188">Utilisation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="8e4af-p114">Le volet de navigation out-of-the-box utilisé par défaut et est la solution la plus simple mais possède un compromis concernant les performances coûteux. Toute personnalisation n’est pas nécessaire et un utilisateur technique peut aussi facilement ajouter des éléments, masquer les éléments et de gérer la navigation dans la page Paramètres. Il s’agit toutefois également la valeur true pour la Navigation gérée afin qu’il est recommandé d’utiliser la Navigation gérée en tant que peut également être facilement gérée et contrôlée ainsi avec des performances améliorées.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Navigation structurelle avec des sous-sites afficher sélectionné](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="8e4af-193">Activation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="8e4af-p115">Pour illustrer la façon dont les performances dans une solution SharePoint Online standard avec navigation structurelle et afficher des sous-sites option activée. Voici une capture d’écran des paramètres qui se trouvent dans la page **Paramètres du Site** \> **Navigation**.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Capture d’écran montrant des sous-sites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="8e4af-197">Analyse des performances de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8e4af-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="8e4af-198">Pour analyser les performances d’une page SharePoint, utilisez l’onglet **réseau** des outils de développement F12 dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8e4af-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Capture d’écran montrant l’onglet Réseau des Outils de développement F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="8e4af-200">Sur l’onglet **Réseau**, cliquez sur la page .aspx en cours de chargement, puis sur l’onglet **Détails**.</span><span class="sxs-lookup"><span data-stu-id="8e4af-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="8e4af-201">![Capture d’écran montrant l’onglet Détails](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="8e4af-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="8e4af-202">Cliquez sur **En-têtes de réponse**.</span><span class="sxs-lookup"><span data-stu-id="8e4af-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="8e4af-203">![Capture d’écran de l’onglet Détails](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="8e4af-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="8e4af-204">SharePoint renvoie des informations de diagnostics utiles dans les en-têtes de réponse.</span><span class="sxs-lookup"><span data-stu-id="8e4af-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="8e4af-p116">Les éléments d’information plus utiles est **SPRequestDuration** , qui est la valeur, en millisecondes, de la durée au processus sur le serveur d’une demande. Dans la capture d’écran suivante **affiche les sous-sites** est désactivée pour la navigation structurelle. Cela signifie qu’il existe uniquement le lien de collection de sites dans le volet de navigation globale :</span><span class="sxs-lookup"><span data-stu-id="8e4af-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="8e4af-208">![Capture d’écran montrant le temps de chargement en tant que durée de la demande](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="8e4af-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="8e4af-p117">La touche **SPRequestDuration** a une valeur de 245 millisecondes. Cela représente la durée que nécessaire pour renvoyer la demande. Étant donné qu’un seul élément de navigation sur le site, il s’agit d’une moyenne pour le fonctionnement de SharePoint Online sans navigation épais. La capture d’écran suivante montre comment ajouter dans les sous-sites affecte cette clé.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="8e4af-213">![Capture d’écran montrant une durée de demande de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="8e4af-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="8e4af-p118">Ajout de sous-sites a augmenté sensiblement le temps que nécessaire pour renvoyer la demande de page pour ce site exemple relativement simple. Hiérarchies de site complexe, y compris les pages dans le volet de navigation, configuration et autres options de topologie peuvent augmenter considérablement cet impact encore.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="8e4af-216">Utilisation de scripts côté client basés sur la recherche</span><span class="sxs-lookup"><span data-stu-id="8e4af-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="8e4af-p119">Utilisation de la recherche, vous pouvez exploiter les index sont créés en arrière-plan à l’aide de l’analyse continue. Les résultats de recherche sont extraites de l’index de recherche et les résultats sont limités à la sécurité. Il s’agit généralement plus rapide que les fournisseurs de navigation out-of-the-box lors de la suppression de la sécurité est nécessaire. Utilisation de la recherche pour la navigation structurelle, en particulier si vous avez une structure de site complexe, accélère considérablement les temps de chargement de page. Le principal avantage de cette navigation gérée est que vous pouvez bénéficier de filtrage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="8e4af-p120">Cette approche implique la création d’une page maître personnalisée et en remplaçant le code de navigation out-of-the-box avec du code HTML personnalisé. Suivez cette procédure décrite dans l’exemple suivant pour remplacer le code de navigation dans le fichier `seattle.html`. Dans cet exemple, vous devez ouvrir le `seattle.html` de fichiers et remplacez l’élément entier `id=”DeltaTopNavigation”` avec du code HTML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="8e4af-225">Exemple : Remplacez le code de navigation out-of-the-box dans une page maître</span><span class="sxs-lookup"><span data-stu-id="8e4af-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="8e4af-226">Accédez à la page Paramètres du site.</span><span class="sxs-lookup"><span data-stu-id="8e4af-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="8e4af-227">Ouvrez la galerie de pages maîtres en cliquant sur **Pages maîtres**.</span><span class="sxs-lookup"><span data-stu-id="8e4af-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="8e4af-228">À partir de là, vous pouvez naviguer dans la bibliothèque et téléchargez le fichier `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="8e4af-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="8e4af-229">Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code qui apparaît dans la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="8e4af-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Supprimer le bloc de code indiqué](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="8e4af-231">Supprimer le code entre la `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` et `<\SharePoint:AjaxDelta>` balises et remplacez-la par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="8e4af-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="8e4af-p121">Remplacez l’URL dans la charge de balise d’ancrage au début, avec un lien vers une image dans votre collection de sites de chargement de l’image. Après avoir apporté les modifications, renommez le fichier et puis le télécharger vers la galerie de pages maîtres. Cette opération génère un nouveau fichier .master.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="8e4af-p122">Ce code HTML est le balisage de base qui est rempli par les résultats de recherche à partir du code JavaScript. Vous devez modifier le code pour modifier la valeur de la racine var = « URL de la collection de sites » comme illustré dans l’extrait suivant :</span><span class="sxs-lookup"><span data-stu-id="8e4af-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="8e4af-p123">Les résultats sont affectés au tableau self.nodes et une hiérarchie repose sur des objets à l’aide de linq.js affectation la sortie à un tableau self.heirarchy. Ce tableau est l’objet qui est lié à l’élément HTML. Cela s’effectue dans la fonction toggleView() en passant l’objet automatique à la fonction ko.applyBinding().</span><span class="sxs-lookup"><span data-stu-id="8e4af-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.heirarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="8e4af-240">Cela entraîne ensuite le tableau de hiérarchie doit être lié le code HTML suivant :</span><span class="sxs-lookup"><span data-stu-id="8e4af-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="8e4af-241">Les gestionnaires d’événements pour `mouseenter` et `mouseexit` sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants sous-site qui s’effectue dans le `addEventsToElements()` fonction.</span><span class="sxs-lookup"><span data-stu-id="8e4af-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="8e4af-242">Dans notre exemple de navigation complexes, une page vierge chargez sans l’affiche de la mise en cache local le temps passé sur le serveur a été supprimée vers le bas de la navigation structurelles banc d’essai pour obtenir un résultat similaire à l’approche de la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="8e4af-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="8e4af-243">À propos du fichier JavaScript...</span><span class="sxs-lookup"><span data-stu-id="8e4af-243">About the JavaScript file...</span></span>

<span data-ttu-id="8e4af-244">L’intégralité du fichier JavaScript se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e4af-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="8e4af-p124">Pour résumer le code ci-dessus dans le `jQuery $(document).ready` fonction est un `viewModel object` créé, puis le `loadNavigationNodes()` fonction de cet objet est appelée. Cette fonction charge soit la hiérarchie de navigation générée précédemment stockée dans le stockage local HTML5 du navigateur client ou il appelle la fonction `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="8e4af-p125">`QueryRemoteInterface()`génère une demande à l’aide de la `getRequest()` fonctionne avec le paramètre de requête défini précédemment dans le script et renvoie ensuite les données à partir du serveur. Ces données sont essentiellement un tableau de tous les sites de la collection représentée en tant qu’objets de transfert de données avec différentes propriétés.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="8e4af-249">Ces données sont ensuite analysées dans précédemment défini `SPO.Models.NavigationNode` objets qui utilisent `Knockout.js` pour créer des propriétés visible pour une utilisation par les valeurs de liaison dans le code HTML que nous avons défini précédemment de données.</span><span class="sxs-lookup"><span data-stu-id="8e4af-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="8e4af-p126">Les objets sont ensuite placées dans un tableau de résultats. Ce tableau est analysé dans JSON grâce à Knockout et stocké dans le stockage de navigateur local pour améliorer les performances sur les charges de page future.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="8e4af-252">Avantages de cette approche</span><span class="sxs-lookup"><span data-stu-id="8e4af-252">Benefits of this approach</span></span>

<span data-ttu-id="8e4af-p127">Un avantage majeur de [cette approche](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) est qu’à l’aide de stockage local HTML5, le volet de navigation est stockée localement pour l’utilisateur lors du prochain que chargement de la page. Nous obtenons principales améliorations de l’utilisation de l’API de recherche pour la navigation structurelle ; Toutefois, il faut des capacités techniques pour exécuter et personnaliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="8e4af-p128">Dans l' [exemple d’implémentation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), les sites sont classés dans la même façon que la navigation structurelle out-of-the-box ; ordre alphabétique. Si vous souhaitez s’écartent de cette commande, il est plus complexe de développer et de mettre à jour. En outre, cette approche nécessite que vous écarter les pages maîtres pris en charge. Si la page maître personnalisée n’est pas conservée, votre site sera manquez améliorations par Microsoft pour les pages maîtres et mises à jour.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="8e4af-259">[code au-dessus de](#about-the-javascript-file) comporte les dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e4af-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="8e4af-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="8e4af-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="8e4af-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="8e4af-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="8e4af-262">LINQ.js - http://linqjs.codeplex.com/, ou github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="8e4af-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="8e4af-p129">La version actuelle de LinqJS ne contient-elle pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompra le code de navigation. Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq.js avant la ligne `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="8e4af-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="8e4af-265">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e4af-265">Related topics</span></span>

[<span data-ttu-id="8e4af-266">Vue d'ensemble de la navigation gérée dans SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="8e4af-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

