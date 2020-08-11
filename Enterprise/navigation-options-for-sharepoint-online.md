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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online.
ms.openlocfilehash: dd11775c35f9eb7d2b6bccc38023b6f8bce8efc4
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606760"
---
# <a name="navigation-options-for-sharepoint-online"></a>Options de navigation pour SharePoint Online

Cet article décrit les options de navigation sites avec la publication SharePoint activée dans SharePoint Online. Le choix et la configuration de la navigation ont un impact significatif sur les performances et l’extensibilité des sites dans SharePoint Online. Le modèle de site de publication SharePoint doit être utilisé uniquement si cela est nécessaire pour un portail centralisé et la fonctionnalité de publication doit être activée uniquement sur des sites spécifiques et uniquement lorsque cela est absolument nécessaire, car cela peut avoir un impact sur les performances lorsqu’il est utilisé de manière incorrecte.

>[!NOTE]
>Si vous utilisez des options de navigation modernes SharePoint comme le menu Mega, la navigation en cascade ou la navigation par concentrateur, cet article ne s’applique pas à votre site. Les architectures de sites SharePoint modernes exploitent une hiérarchie de sites plus aplatie et un modèle Hub-and-Spoke. Cela permet de réaliser de nombreux scénarios qui ne nécessitent pas l’utilisation de la fonctionnalité de publication SharePoint.

## <a name="overview-of-navigation-options"></a>Vue d’ensemble des options de navigation

La configuration du fournisseur de navigation peut avoir un impact significatif sur les performances de l’ensemble du site, et vous devez tenir compte de la sélection d’un fournisseur de navigation et d’une configuration qui évoluent efficacement pour les besoins d’un site SharePoint. Il existe deux fournisseurs de navigation prédéfinis, ainsi que des implémentations de navigation personnalisées.

La première option, [**navigation structurelle**](#using-structural-navigation-in-sharepoint-online), est l’option de navigation recommandée dans SharePoint Online pour les sites SharePoint classiques **si vous activez la mise en cache de la navigation structurelle pour votre site**. Ce fournisseur de navigation affiche les éléments de navigation sous le site actuel, et éventuellement le site actuel et ses frères. Elle fournit des fonctionnalités supplémentaires, telles que le filtrage de sécurité et l’énumération de la structure de site. Si la mise en cache est désactivée, cela a un impact négatif sur les performances et l’extensibilité, et peut être soumis à la limitation.

La deuxième option, [**navigation gérée (métadonnées)**](#using-managed-navigation-and-metadata-in-sharepoint-online), représente les éléments de navigation à l’aide d’un ensemble de termes de métadonnées gérées. Nous vous recommandons de désactiver le filtrage de sécurité, sauf en cas de nécessité. Le filtrage de sécurité est activé comme paramètre sécurisé par défaut pour ce fournisseur de navigation ; Toutefois, de nombreux sites n’ont pas besoin de la charge de filtrage de sécurité, car les éléments de navigation sont souvent cohérents pour tous les utilisateurs du site. Avec la configuration recommandée pour désactiver le filtrage de sécurité, ce fournisseur de navigation ne requiert pas l’énumération de la structure du site et est hautement évolutif avec un impact acceptable sur les performances.

En plus des fournisseurs de navigation prédéfinis, de nombreux clients ont implémenté les autres implémentations de navigation personnalisées. Consultez la rubrique [script côté client basé](#using-search-driven-client-side-scripting) sur la recherche dans cet article.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Avantages et inconvénients des options de navigation SharePoint Online

Le tableau suivant récapitule les avantages et les inconvénients de chaque option.

|Navigation structurelle  |Navigation gérée  |Navigation basée sur la recherche  |Fournisseur de navigation personnalisée  |
|---------|---------|---------|---------|
|Avantages<br/><br/>Facilité de maintenance<br/>Sécurité découpée<br/>Mises à jour automatiques dans les 24 heures après la modification du contenu<br/>     |Avantages<br/><br/>Facilité de maintenance<br/>|Avantages<br/><br/>Sécurité découpée<br/>Mises à jour automatiques lors de l’ajout de sites<br/>Temps de chargement rapide et structure de navigation mise en cache locale<br/>|Avantages<br/><br/>Choix plus large d’options disponibles<br/>Chargement rapide lorsque la mise en cache est utilisée correctement<br/>De nombreuses options fonctionnent bien avec la conception de pages réactives<br/>|
|Inconvénients<br/><br/>**Impact sur les performances en cas de désactivation de la mise en cache**<br/>Soumis à la limitation<br/>|Inconvénients<br/><br/>Mise à jour non automatique pour refléter la structure du site<br/>**Impact sur les performances si le filtrage de sécurité est activé** ou si la structure de navigation est complexe<br/>|Inconvénients<br/><br/>Aucune possibilité de classer facilement les sites<br/>Nécessite une personnalisation de la page maître (compétences techniques requises)<br/>|Inconvénients<br/><br/>Un développement personnalisé est requis<br/>La source de données externe/le cache stocké est nécessaire par exemple, Azure<br/>|

L’option la plus appropriée pour votre site dépend de vos besoins en matière de site et de vos capacités techniques. Si vous souhaitez un fournisseur de navigation facile à configurer qui se met à jour automatiquement lorsque le contenu est modifié, la navigation structurelle [avec mise en cache activée](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) est une excellente option.

>[!NOTE]
>Appliquer le même principe que les sites SharePoint modernes en simplifiant la structure globale du site en une structure non hiérarchique simplifiée améliore les performances et simplifie le passage aux sites SharePoint modernes. Cela signifie qu’au lieu d’avoir une seule collection de sites avec des centaines de sites (sous-sites Web), une meilleure approche consiste à avoir de nombreuses collections de sites avec très peu de sous-sites (sous-sites Web).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analyse des performances de navigation dans SharePoint Online

L' [outil Diagnostics de la page pour SharePoint](https://aka.ms/perftool) est une extension de navigateur pour les navigateurs Microsoft Edge et chrome qui analyse à la fois les pages du portail moderne SharePoint Online et du site de publication classique. Cet outil fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

L’outil génère un rapport pour chaque page analysée affichant le mode d’exécution de la page par rapport à un ensemble prédéfini de règles et affiche des informations détaillées lorsque les résultats d’un test se situent hors de la valeur de la ligne de base. Les administrateurs et les concepteurs SharePoint Online peuvent utiliser l’outil pour résoudre les problèmes de performances afin de s’assurer que les nouvelles pages sont optimisées avant la publication.

**SPRequestDuration** en particulier est le temps nécessaire au traitement de la page par SharePoint. La navigation intensive (comme les pages dans le volet de navigation), les hiérarchies de sites complexes, ainsi que d’autres options de configuration et de topologie, peuvent contribuer considérablement à des durées plus longues.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilisation de la navigation structurelle dans SharePoint Online

Il s’agit de la navigation prédéfinie utilisée par défaut et est la solution la plus simple. Il ne nécessite aucune personnalisation et un utilisateur non-technique peut également facilement ajouter des éléments, masquer des éléments et gérer la navigation dans la page Paramètres. Nous vous recommandons d' [activer la mise en cache](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), sinon il y a un compromis entre performances onéreux.

### <a name="how-to-implement-structural-navigation-caching"></a>Implémentation de la mise en cache de la navigation structurelle

Sous **paramètres du site**  >  **Présentation**  >  de**la navigation**, vous pouvez valider si la navigation structurelle est sélectionnée pour la navigation globale ou la navigation actuelle. La sélection de **afficher les pages** aura un impact négatif sur les performances.

![Navigation structurelle avec afficher les sous-sites sélectionnés](media/SPONavOptionsStructuredShowSubsites.png)

La mise en cache peut être activée ou désactivée au niveau de la collection de sites et au niveau du site, et est activée par défaut pour les deux. Pour activer au niveau de la collection de sites, sous **paramètres du site**,  >  **collection**  >  de sites administration de la collection de**sites**, activez la case à cocher Activer la **mise en cache**.

![Activer la mise en cache au niveau du site](media/structural-nav/structural-nav-caching-site-coll.png)

Pour activer au niveau du site, sous **Site Settings**  >  **navigation**des paramètres de site, activez la case à cocher **activer la mise en cache**.

![Activer la mise en cache au niveau du site](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Utilisation de la navigation gérée et des métadonnées dans SharePoint Online

La navigation gérée est une autre option prédéfinie que vous pouvez utiliser pour recréer la plupart des fonctionnalités de navigation structurelle. Les métadonnées gérées peuvent être configurées de façon à activer ou désactiver le filtrage de sécurité. Lorsqu’elle est configurée avec filtrage de sécurité désactivé, la navigation gérée est assez efficace car elle charge tous les liens de navigation avec un nombre constant d’appels serveur. Toutefois, l’activation du filtrage de sécurité annule certains des avantages de la navigation gérée en matière de performances.

Si vous devez activer le filtrage de sécurité, il est recommandé de procéder comme suit :

- Mettre à jour tous les liens d’URL conviviaux vers des liens simples
- Ajouter les nœuds de filtrage de sécurité requis en tant qu’URL conviviales
- Limiter le nombre d’éléments de navigation à un maximum de 100 et un maximum de 3 niveaux

De nombreux sites n’ont pas besoin d’un filtrage de sécurité, car la structure de navigation est souvent cohérente pour tous les utilisateurs du site. Si le filtrage de sécurité est désactivé et qu’un lien est ajouté à la navigation et que tous les utilisateurs n’ont pas accès à, le lien continuera de s’afficher mais entraînera un message de refus d’accès. Il n’y a aucun risque d’accès involontaire au contenu.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Comment implémenter la navigation gérée et les résultats

Il existe plusieurs articles sur docs.microsoft.com concernant les détails de la navigation gérée. Par exemple, reportez-vous à la rubrique [vue d’ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Pour implémenter la navigation gérée, vous configurez des termes avec des URL correspondant à la structure de navigation du site. La navigation gérée peut même être organisée manuellement pour remplacer la navigation structurelle dans de nombreux cas. Par exemple :

![Structure de site SharePoint Online](media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Utilisation de scripts côté client basés sur la recherche

Une classe commune de mises en œuvre de navigation personnalisée comporte des modèles de conception affichés par le client qui stockent un cache local de nœuds de navigation.

Ces fournisseurs de navigation présentent quelques avantages clés :

- Elles fonctionnent généralement bien avec des conceptions de pages réactives.
- Elles sont extrêmement évolutives et performantes, car elles peuvent être rendues sans coût de ressource (et actualiser en arrière-plan après un délai d’expiration).
- Ces fournisseurs de navigation peuvent extraire des données de navigation à l’aide de différentes stratégies, allant de simples configurations statiques à différents fournisseurs de données dynamiques.

Un exemple de fournisseur de données consiste à utiliser une **navigation**basée sur la recherche, ce qui vous permet d’énumérer les nœuds de navigation et de gérer efficacement le filtrage de sécurité.

Il existe d’autres options populaires pour créer des **fournisseurs de navigation personnalisés**. Pour plus d’informations sur la création d’un fournisseur de navigation personnalisé, consultez [les solutions de navigation pour les portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .

À l’aide de la recherche, vous pouvez tirer parti des index créés en arrière-plan à l’aide de l’analyse continue. Les résultats de la recherche sont extraits de l’index de recherche et les résultats sont découpés en sécurité. Cette règle est généralement plus rapide que les fournisseurs de navigation out-of-Box lorsque le filtrage de sécurité est requis. L’utilisation de la recherche pour la navigation structurelle, en particulier si vous avez une structure de site complexe, accélère considérablement le temps de chargement de la page. Le principal avantage de cette barre de navigation gérée est que vous bénéficiez du filtrage de sécurité.

Cette approche implique la création d’une page maître personnalisée et le remplacement du code de navigation par des éléments HTML personnalisés. Suivez cette procédure décrite dans l’exemple suivant pour remplacer le code de navigation dans le fichier `seattle.html` . Dans cet exemple, vous ouvrez le `seattle.html` fichier et remplacez l’intégralité de l’élément `id="DeltaTopNavigation"` par du code HTML personnalisé.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Exemple : remplacer le code de navigation prédéfinie dans une page maître

1. Accédez à la page Paramètres du site.
2. Ouvrez la Galerie de pages maîtres en cliquant sur **pages maîtres**.
3. À partir de là, vous pouvez naviguer dans la bibliothèque et télécharger le fichier `seattle.master` .
4. Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code dans la capture d’écran suivante.<br/>![Supprimer le bloc de code affiché](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Supprimez le code entre `<SharePoint:AjaxDelta id="DeltaTopNavigation">` les `<\SharePoint:AjaxDelta>` balises et remplacez-le par l’extrait de code suivant :<br/>

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
6. Remplacez l’URL de la balise d’ancrage de l’image de chargement au début, par un lien vers une image de chargement dans votre collection de sites. Une fois les modifications apportées, renommez le fichier, puis téléchargez-le dans la Galerie de pages maîtres. Cela génère un nouveau fichier. Master.<br/>
7. Ce code HTML est le balisage de base qui sera rempli par les résultats de recherche renvoyés par le code JavaScript. Vous devrez modifier le code pour modifier la valeur de var root = "URL de la collection de sites", comme illustré dans l’extrait de code suivant :<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Les résultats sont attribués au tableau self. Nodes et une hiérarchie est construite à partir des objets à l’aide de linq.js l’assignation de la sortie à un tableau self. Hierarchy. Ce tableau est l’objet lié au code HTML. Cette opération est exécutée dans la fonction toggleView () en transmettant l’objet Self à la fonction Ko. applyBinding ().<br/>Ainsi, le tableau de hiérarchie est lié au code HTML suivant :<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Les gestionnaires d’événements pour `mouseenter` et `mouseexit` sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants de sous-site qui sont exécutés dans la `addEventsToElements()` fonction.

Dans notre exemple de navigation complexe, un chargement de page récent sans mise en cache locale indique que le temps passé sur le serveur a été réduit à partir de la navigation structurelle de référence pour obtenir un résultat similaire à l’approche de navigation gérée.

### <a name="about-the-javascript-file"></a>À propos du fichier JavaScript...

>[!NOTE]
>Si vous utilisez JavaScript personnalisé, vérifiez que le CDN public est activé et que le fichier se trouve à un emplacement CDN.

L’intégralité du fichier JavaScript se présente comme suit :

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

Pour résumer le code indiqué ci-dessus dans la `jQuery $(document).ready` fonction, une fonction est `viewModel object` créée, puis la `loadNavigationNodes()` fonction sur cet objet est appelée. Cette fonction charge la hiérarchie de navigation précédemment créée stockée dans le stockage local HTML5 du navigateur client ou appelle la fonction `queryRemoteInterface()` .

`QueryRemoteInterface()`génère une demande à l’aide de la `getRequest()` fonction avec le paramètre de requête défini précédemment dans le script, puis retourne des données à partir du serveur. Ces données sont essentiellement un tableau de tous les sites de la collection de sites, représentés par des objets de transfert de données, avec différentes propriétés.

Ces données sont ensuite analysées dans les objets définis précédemment `SPO.Models.NavigationNode` qui utilisent `Knockout.js` pour créer des propriétés observables utilisées par la liaison de données des valeurs dans le code HTML que nous avons défini précédemment.

Les objets sont ensuite placés dans un tableau de résultats. Ce tableau est analysé dans JSON à l’aide du masquage et stocké dans le stockage du navigateur local pour de meilleures performances lors des prochains chargement de la page.

### <a name="benefits-of-this-approach"></a>Avantages de cette approche

L’un des principaux avantages de [cette approche](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) est qu’en utilisant le stockage local HTML5, la navigation est stockée localement pour l’utilisateur lors du prochain chargement de la page. Nous obtenons des améliorations majeures en matière de performances à l’aide de l’API de recherche pour la navigation structurelle ; Toutefois, il prend certaines capacités techniques pour exécuter et personnaliser cette fonctionnalité.

Dans l' [exemple d’implémentation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), les sites sont triés de la même manière que la navigation structurelle prédéfinie ; ordre alphabétique. Si vous souhaitez vous en écarter, il serait plus compliqué de développer et de gérer. Cette approche nécessite également de s’écarter des pages maîtres prises en charge. Si la page maître personnalisée n’est pas conservée, votre site se déplacera sur les mises à jour et les améliorations que Microsoft apporte aux pages maîtres.

Le [code ci-dessus](#about-the-javascript-file) présente les dépendances suivantes :

- jQueryhttps://jquery.com/
- KnockoutJS -https://knockoutjs.com/
- Linq.js- https://linqjs.codeplex.com/ ou github.com/neuecc/linq.js

La version actuelle de LinqJS ne contient pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompt le code de navigation. Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq.js avant la ligne `Flatten: function ()` .

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
  
## <a name="related-topics"></a>Voir aussi

[Vue d'ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[Mise en cache et performances de la navigation structurelle](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
