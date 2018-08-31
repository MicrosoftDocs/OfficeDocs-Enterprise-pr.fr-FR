---
title: Options de navigation pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Cet article explique comment améliorer le temps de chargement des pages pour SharePoint Online à l’aide de la navigation gérée ou la navigation par recherche lors de la publication classique.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540592"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="df2f3-103">Options de navigation pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df2f3-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="df2f3-104">Cet article explique comment améliorer le temps de chargement des pages pour SharePoint Online à l’aide de la navigation gérée ou la navigation par recherche lors de la publication classique.</span><span class="sxs-lookup"><span data-stu-id="df2f3-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="df2f3-105">SharePoint Online avec publication classique activée a deux zones de navigation ; Navigation globale et Navigation actuelle.</span><span class="sxs-lookup"><span data-stu-id="df2f3-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="df2f3-106">Navigation globale est le menu de navigation supérieure pendant la Navigation actuelle est le côté ou la navigation de gauche/droite en contexte dépende de la configuration de la langue et de la page maître utilisée.</span><span class="sxs-lookup"><span data-stu-id="df2f3-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="df2f3-107">Navigation affecte les performances pour le portail entier tel qu’il est souvent configuré pour une utilisation au niveau du portail et en tant que telles est un élément important d’un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="df2f3-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="df2f3-108">Navigation structurelle n’est pas l’option de navigation recommandées dans SharePoint Online, comme il a été conçu pour une topologie sur site avec filtrage de sécurité et ce modèle entraîne des appels excessive du serveur et a un impact sur les performances lorsqu’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="df2f3-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="df2f3-p101">Que la conception a changé avec l’introduction des sites SharePoint moderne où moderne a une hiérarchie de site aplati simplifiée. Cette opération a simplifiée navigation avec une hiérarchie simplifiée qui a résolu les problèmes de performances liés à la navigation.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="df2f3-p102">Il existe deux options principales out-of-the-box navigation dans SharePoint ainsi qu’une troisième, approche personnalisée, pilotés par la recherche. Également une quatrième et option assez courante consiste à créer un fournisseur de Navigation personnalisé. Examinez [les solutions de Navigation pour les portails SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) pour obtenir des instructions sur un fournisseur de navigation personnalisé.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="df2f3-114">Chaque option présente des avantages et inconvénients, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="df2f3-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="df2f3-115">**Navigation structurelle**</span><span class="sxs-lookup"><span data-stu-id="df2f3-115">**Structural navigation**</span></span>|<span data-ttu-id="df2f3-116">**Navigation gérée**</span><span class="sxs-lookup"><span data-stu-id="df2f3-116">**Managed navigation**</span></span>|<span data-ttu-id="df2f3-117">**Navigation par recherche**</span><span class="sxs-lookup"><span data-stu-id="df2f3-117">**Search-driven navigation**</span></span>||<span data-ttu-id="df2f3-118">**Fournisseur de Navigation personnalisé**</span><span class="sxs-lookup"><span data-stu-id="df2f3-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="df2f3-119">Avantages :</span><span class="sxs-lookup"><span data-stu-id="df2f3-119">Pros:</span></span>  <br/>  <span data-ttu-id="df2f3-120">Facilité de configuration</span><span class="sxs-lookup"><span data-stu-id="df2f3-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="df2f3-121">Découpage à des fins de sécurité</span><span class="sxs-lookup"><span data-stu-id="df2f3-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="df2f3-122">Mise à jour automatique lorsque des sites sont ajoutés</span><span class="sxs-lookup"><span data-stu-id="df2f3-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="df2f3-123">Avantages :</span><span class="sxs-lookup"><span data-stu-id="df2f3-123">Pros:</span></span>  <br/>  <span data-ttu-id="df2f3-124">Facilité de maintenance</span><span class="sxs-lookup"><span data-stu-id="df2f3-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="df2f3-125">Option recommandée</span><span class="sxs-lookup"><span data-stu-id="df2f3-125">Recommended option</span></span>  <br/> | <span data-ttu-id="df2f3-126">Avantages :</span><span class="sxs-lookup"><span data-stu-id="df2f3-126">Pros:</span></span>  <br/>  <span data-ttu-id="df2f3-127">Découpage à des fins de sécurité</span><span class="sxs-lookup"><span data-stu-id="df2f3-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="df2f3-128">Mise à jour automatique lorsque des sites sont ajoutés</span><span class="sxs-lookup"><span data-stu-id="df2f3-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="df2f3-129">Rapidité de chargement et structure de navigation mise en cache localement</span><span class="sxs-lookup"><span data-stu-id="df2f3-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="df2f3-130">Avantages :</span><span class="sxs-lookup"><span data-stu-id="df2f3-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="df2f3-131">Choix plus large / options disponibles</span><span class="sxs-lookup"><span data-stu-id="df2f3-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="df2f3-132">Chargement rapide lors de la mise en cache est utilisé correctement</span><span class="sxs-lookup"><span data-stu-id="df2f3-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="df2f3-133">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="df2f3-133">Cons:</span></span>  <br/> <span data-ttu-id="df2f3-134">**Non recommandé**</span><span class="sxs-lookup"><span data-stu-id="df2f3-134">**Not recommended**</span></span> <br/> <span data-ttu-id="df2f3-135">**Affecte les performances**</span><span class="sxs-lookup"><span data-stu-id="df2f3-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="df2f3-136">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="df2f3-136">Cons:</span></span>  <br/>  <span data-ttu-id="df2f3-137">Pas de mises à jour automatiques lorsque des sites sont ajoutés</span><span class="sxs-lookup"><span data-stu-id="df2f3-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="df2f3-138">Affecte les performances si la suppression de la sécurité est activée.</span><span class="sxs-lookup"><span data-stu-id="df2f3-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="df2f3-139">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="df2f3-139">Cons:</span></span>  <br/>  <span data-ttu-id="df2f3-140">Aucune possibilité de classer facilement les sites</span><span class="sxs-lookup"><span data-stu-id="df2f3-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="df2f3-141">Nécessite une personnalisation de la page maître (compétences techniques requises)</span><span class="sxs-lookup"><span data-stu-id="df2f3-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="df2f3-142">Inconvénients :</span><span class="sxs-lookup"><span data-stu-id="df2f3-142">Cons:</span></span>  <br/>  <span data-ttu-id="df2f3-143">Développement personnalisé est requis</span><span class="sxs-lookup"><span data-stu-id="df2f3-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="df2f3-144">Source de données externe / cache stocké est nécessaire, par exemple Azure</span><span class="sxs-lookup"><span data-stu-id="df2f3-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="df2f3-p103">L’option la plus appropriée pour votre site dépendent des besoins de votre site et de vos capacités techniques. Si vous êtes habitué à utiliser une page maître personnalisée et avez une fonctionnalité dans l’organisation pour gérer les modifications qui peuvent se produire dans la page maître par défaut pour SharePoint Online, l’option de recherche produira la meilleure expérience utilisateur. Si vous souhaitez milieu simple entre la navigation structurelle out-of-the-box et de la recherche, la navigation gérée est une très bonne option. L’option de navigation gérée peut être gérée par le biais de la configuration, n’implique pas les fichiers de personnalisation de code, et il est beaucoup plus rapide que la navigation structurelle out-of-the-box.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="df2f3-p104">Simplification de la structure globale de votre portail classique comme moderne, aide également à l’échelle et les performances globales. Cela signifie qu’au lieu d’avoir une seule Collection de sites avec des centaines / des milliers de sites (sous-sites), une meilleure approche consiste à détenir de nombreuses collections de sites avec des sous-sites minime (sous-sites).</span><span class="sxs-lookup"><span data-stu-id="df2f3-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="df2f3-151">Cela fournit des options supplémentaires de mise à l’échelle dans le service, évite de placer tout le contenu dans une base de données volumineux et finalement une plus grande souplesse pour la navigation et de plus de sécurité.</span><span class="sxs-lookup"><span data-stu-id="df2f3-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="df2f3-152">Utilisation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df2f3-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="df2f3-p105">Le volet de navigation out-of-the-box utilisé par défaut et est la solution la plus simple mais possède un compromis concernant les performances coûteux. Toute personnalisation n’est pas nécessaire et un utilisateur technique peut aussi facilement ajouter des éléments, masquer les éléments et de gérer la navigation dans la page Paramètres. Il s’agit toutefois également la valeur true pour la Navigation gérée afin qu’il est recommandé d’utiliser Navigation gérée en tant que qui peuvent également être facilement gérés et contrôlés ainsi.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="df2f3-156">Activation de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df2f3-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="df2f3-p106">Pour illustrer la façon dont les performances dans une solution SharePoint Online standard avec navigation structurelle et afficher des sous-sites option activée. Vous trouverez ci-dessous est un capture d’écran paramètres contenus dans la page **Paramètres du Site** \> **Navigation**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Capture d’écran montrant des sous-sites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="df2f3-160">Analyse des performances de la navigation structurelle dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df2f3-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="df2f3-161">Pour analyser les performances d’une page SharePoint, utilisez l’onglet **Réseau** des outils de développement F12 dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="df2f3-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Capture d’écran montrant l’onglet Réseau des Outils de développement F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="df2f3-163">Sur l’onglet **Réseau**, cliquez sur la page .aspx en cours de chargement, puis sur l’onglet **Détails**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Capture d’écran montrant l’onglet Détails](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="df2f3-165">Cliquez sur **En-têtes de réponse**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-165">Click **Response headers**.</span></span>
  
![Capture d’écran de l’onglet Détails](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="df2f3-p107">SharePoint renvoie des informations de diagnostics utiles dans les en-têtes de réponse. Un des plus utiles est l’en-tête **SPRequestDuration**, qui indique la durée, en millisecondes, du traitement d’une demande sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="df2f3-p108">Dans l’écran suivant **Afficher les sous-sites** est désactivée pour la navigation structurelle. Cela signifie qu’il existe uniquement le lien de collection de sites dans le volet de navigation globale :</span><span class="sxs-lookup"><span data-stu-id="df2f3-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Capture d’écran montrant le temps de chargement en tant que durée de la demande](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="df2f3-p109">La touche **SPRequestDuration** a une valeur de 245 millisecondes. Cela représente la durée que nécessaire pour renvoyer la demande. Étant donné qu’un seul élément de navigation sur le site, il s’agit d’une moyenne pour le fonctionnement de SharePoint Online sans navigation épais. La capture d’écran suivante montre comment ajouter dans les sous-sites affecte cette clé.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Capture d’écran montrant une durée de demande de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="df2f3-177">L’ajout des sous-sites a augmenté de façon importante le temps nécessaire pour renvoyer la demande de page.</span><span class="sxs-lookup"><span data-stu-id="df2f3-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="df2f3-178">Les avantages de l’utilisation de la navigation structurée régulière est que vous pouvez facilement organiser l’ordre, masquer les sites, ajouter des pages, les résultats sont limités à la sécurité, et vous ne sont pas qui s’écartent des pages maîtres pris en charge utilisés dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="df2f3-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="df2f3-179">Utilisation de la navigation gérée et des métadonnées gérées dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df2f3-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="df2f3-180">La navigation gérée est une autre option standard que vous pouvez utiliser pour recréer le même type de fonctionnalité que la navigation structurelle.</span><span class="sxs-lookup"><span data-stu-id="df2f3-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="df2f3-p110">L’avantage de l’utilisation de métadonnées gérées est qu’il est beaucoup plus rapide pour récupérer les données à l’aide du contenu par requête pour créer la navigation de site. Bien qu’il soit que beaucoup plus rapidement il n’existe aucun moyen de découpage de sécurité les résultats donc si un utilisateur n’a pas accès à un site donné, le lien affiche toujours mais entraîne un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="df2f3-183">**Implémentation de la navigation gérée et des résultats**</span><span class="sxs-lookup"><span data-stu-id="df2f3-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="df2f3-184">Il existe plusieurs articles sur TechNet sur les détails de la navigation gérée, par exemple, voir [vue d’ensemble de la navigation gérée dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="df2f3-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="df2f3-p111">Pour implémenter la navigation gérée, vous devez disposer des autorisations d’administrateur du magasin de termes. En configurant des termes avec des URL qui correspondent à la structure d’une collection de sites, la navigation gérée peut être utilisée pour remplacer la navigation structurelle. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="df2f3-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Capture d’écran de l’exemple Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="df2f3-189">L’exemple suivant montre les performances d’une navigation complexe utilisant la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="df2f3-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Capture d’écran de l’exemple SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="df2f3-191">L’utilisation de la navigation gérée améliore sensiblement les performances par rapport à la navigation structurelle par requête sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="df2f3-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="df2f3-192">Utilisation de scripts côté client basés sur la recherche</span><span class="sxs-lookup"><span data-stu-id="df2f3-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="df2f3-p112">En utilisant la recherche, vous pouvez tirer parti des index créés en arrière-plan à l’aide de l’analyse continue. Cela signifie qu’aucune requête de contenu lourde n’est exécutée. Les résultats de recherche sont extraits de l’index de recherche et les résultats sont découpés à des fins de sécurité. Cette procédure est plus rapide que l’utilisation de requêtes de contenu standard. L’utilisation de la recherche pour la navigation structurelle va considérablement accélérer le temps de chargement des pages, surtout si vous disposez d’une structure de site complexe. Grâce à cette navigation gérée, vous bénéficiez du découpage à des fins de sécurité ; il s’agit du principal avantage de cette approche.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="df2f3-p113">Celle-ci implique la création d’une page maître personnalisée et le remplacement du code de navigation standard par du code HTML personnalisé. Suivez cette procédure pour remplacer le code de navigation dans le fichier seattle.html.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="df2f3-201">Dans cet exemple, vous ouvrez le fichier seattle.html et remplacez l’élément entier **id = « DeltaTopNavigation »** avec le code HTML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="df2f3-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="df2f3-202">**Exemple : remplacement du code de navigation standard dans une page maître**</span><span class="sxs-lookup"><span data-stu-id="df2f3-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="df2f3-203">Accédez à la page **Paramètres du site**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="df2f3-204">Ouvrez la galerie de pages maîtres en cliquant sur **Pages maîtres**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="df2f3-205">Vous pouvez alors parcourir la bibliothèque et téléchargez le fichier **seattle.master**.</span><span class="sxs-lookup"><span data-stu-id="df2f3-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="df2f3-206">Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code qui apparaît dans la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="df2f3-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Capture d’écran du code DeltaTopNavigation à supprimer](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="df2f3-208">Supprimer le code entre la \<SharePoint:AjaxDelta id = « DeltaTopNavigation »\> et \<\SharePoint:AjaxDelta\> balises et remplacez-la par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="df2f3-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="df2f3-p114">Remplacez l’URL dans la charge de balise d’ancrage au début, avec un lien vers une image dans votre collection de sites de chargement de l’image. Après avoir apporté les modifications, renommez le fichier et puis le télécharger vers la galerie de pages maîtres. Cette opération génère un nouveau fichier .master.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="df2f3-p115">Ce code HTML est le balisage de base qui est rempli par les résultats de recherche à partir du code JavaScript. Vous devez modifier le code suivant pour modifier la valeur pour le `var root = "site collection URL"` comme illustré dans l’extrait suivant :</span><span class="sxs-lookup"><span data-stu-id="df2f3-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="df2f3-214">L’intégralité du fichier JavaScript se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="df2f3-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="df2f3-215">$("li.level1").mouseover (fonction () {</span><span class="sxs-lookup"><span data-stu-id="df2f3-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="df2f3-216">position var = $(this).position() ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="df2f3-217">.find("ul.level2").css $(this) ({largeur : 100, gauche : position.left + 10, top : 50}) ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="df2f3-218">.MOUSEOUT (fonction () {</span><span class="sxs-lookup"><span data-stu-id="df2f3-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="df2f3-219">.find("ul.level2").css $(this) ({gauche :-99999, supérieur : 0}) ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="df2f3-220">});</span><span class="sxs-lookup"><span data-stu-id="df2f3-220"></span></span>
  
<span data-ttu-id="df2f3-221">$("li.level2").mouseover (fonction () {</span><span class="sxs-lookup"><span data-stu-id="df2f3-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="df2f3-222">position var = $(this).position() ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="df2f3-223">console.log(JSON.stringify(position)) ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="df2f3-224">.find("ul.level3").css $(this) ({largeur : 100, gauche : position.left + 95, top : position.top}) ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="df2f3-225">.MOUSEOUT (fonction () {</span><span class="sxs-lookup"><span data-stu-id="df2f3-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="df2f3-226">.find("ul.level3").css $(this) ({gauche :-99999, supérieur : 0}) ;</span><span class="sxs-lookup"><span data-stu-id="df2f3-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="df2f3-227">});</span><span class="sxs-lookup"><span data-stu-id="df2f3-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="df2f3-p116">Ensuite, les résultats sont affectés au tableau **[self.nodes]** et une hiérarchie repose sur les objets à l’aide de linq.js affectation la sortie à un tableau **[self.heirarchy]**. Ce tableau est l’objet qui est lié à l’élément HTML. Cela s’effectue dans la fonction **[toggleView()]** en passant l’objet automatique à la fonction **[ko.applyBinding()]** . Cela entraîne ensuite le tableau de hiérarchie doit être lié le code HTML suivant :</span><span class="sxs-lookup"><span data-stu-id="df2f3-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="df2f3-232">Enfin, les gestionnaires d’événements pour **[mouseenter]** et **[souris quitter]** sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants sous-site qui s’effectue dans la fonction **[addEventsToElements()]** .</span><span class="sxs-lookup"><span data-stu-id="df2f3-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="df2f3-233">Les résultats de la barre de navigation peuvent être affichées dans la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="df2f3-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Capture d’écran des résultats de la navigation](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="df2f3-235">Dans notre exemple de navigation complexe, le chargement d’une nouvelle page sans la mise en cache locale montre que le temps passé sur le serveur a été largement réduit par rapport à la navigation structurelle de référence et les résultats obtenus sont semblables à ceux obtenus pour la navigation gérée.</span><span class="sxs-lookup"><span data-stu-id="df2f3-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Capture d’écran de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="df2f3-237">Un des principaux avantages de cette approche est qu’en utilisant le stockage local HTML5, la navigation est stockée localement pour l’utilisateur en prévision du prochain chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="df2f3-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="df2f3-p117">Grâce à l’utilisation de l’API de recherche pour la navigation structurelle, les performances sont considérablement améliorées. Toutefois, des connaissances techniques sont requises pour exécuter et personnaliser cette fonctionnalité. Dans l’exemple d’implémentation, les sites sont classés de la même manière que dans la navigation structurelle standard, à savoir par ordre alphabétique. Si vous souhaitez classer les sites autrement, le développement et la maintenance s’avéreraient plus complexes. En outre, cette approche vous obligerait à utiliser d’autres pages maîtres que celles prises en charge. Si la page maître personnalisée n’est pas conservée, votre site ne pourra pas bénéficier des mises à jour et des améliorations que Microsoft apporte aux pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="df2f3-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="df2f3-243">Le code ci-dessus comporte les dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="df2f3-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="df2f3-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="df2f3-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="df2f3-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="df2f3-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="df2f3-246">LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), ou [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="df2f3-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="df2f3-p118">La version actuelle de LinqJS ne contient-elle pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompra le code de navigation. Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq.js avant la ligne « écraser : fonction () ».</span><span class="sxs-lookup"><span data-stu-id="df2f3-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


