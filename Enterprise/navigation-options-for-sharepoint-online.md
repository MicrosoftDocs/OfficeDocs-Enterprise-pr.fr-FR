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
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547176"
---
# <a name="navigation-options-for-sharepoint-online"></a>Options de navigation pour SharePoint Online

Cet article décrit les sites des options de navigation avec publication SharePoint activé dans SharePoint Online. Le choix et la configuration de la navigation affecte considérablement les performances et l’évolutivité de sites dans SharePoint Online.

## <a name="overview"></a>Vue d'ensemble

Configuration du fournisseur de navigation peut affecter considérablement les performances pour l’intégralité du site, et une attention particulière doit être prise pour sélectionner un fournisseur de navigation et la configuration qui met en œuvre efficacement pour la configuration requise d’un site SharePoint. Il existe deux fournisseurs de navigation out-of-the-box, ainsi que les implémentations de navigation personnalisé.

La première option, la [**navigation gérée (métadonnées)**](#using-managed-navigation-and-metadata-in-sharepoint-online), est recommandée et est une des options par défaut dans SharePoint Online ; Toutefois, nous recommandons que le filtrage de sécurité être désactivé sauf indication contraire. Ajustement de la sécurité est activé comme un paramètre d’informations sécurisé par défaut pour ce fournisseur de navigation ; Toutefois, le nombre de sites ne nécessite pas de la charge de découpage de sécurité dans la mesure où les éléments de navigation sont souvent cohérentes pour tous les utilisateurs du site. Avec la configuration recommandée pour désactiver le filtrage de sécurité, ce fournisseur de navigation ne nécessite pas de l’énumération de la structure du site et est hautement évolutif avec des performances acceptables.

La deuxième option, [**navigation structurelle**](#using-structural-navigation-in-sharepoint-online), **n’est pas une option de navigation recommandées dans SharePoint Online**. Ce fournisseur de navigation a été conçu pour une topologie locale est limitée à la prise en charge dans SharePoint Online. Il fournit un ensemble de fonctionnalités par rapport à d’autres options de navigation supplémentaire, ces fonctionnalités, notamment le filtrage de sécurité et énumération de structure de site, a un coût d’appels excessive du serveur et les performances et évolutivité des impacts lorsqu’elle est utilisée. Sites à l’aide de la navigation structed qui consomment trop de ressources peuvent être soumis à la limitation.

Outre les fournisseurs de navigation out-of-the-box, de nombreux clients ont réussi implémentations autre navigation personnalisée. Une classe commune des implémentations de navigation personnalisé s’appuie sur les modèles de conception de rendu de client qui stockent un cache local des nœuds de navigation. (Voir **[recherche script côté client](#using-search-driven-client-side-scripting)** dans cet article).

Ces fournisseurs de navigation ont deux principaux avantages : 
- En règle générale, ils fonctionnent également avec les modèles de page vite.
- Ils sont très évolutives et performante, car ils peuvent restituer sans coût de la ressource (et les actualiser en arrière-plan après un délai d’expiration). 
- Ces fournisseurs de navigation peuvent récupérer des données de navigation à l’aide de diverses stratégies, allant de configurations statiques simples à différents fournisseurs de données dynamique. 

Un exemple d’un fournisseur de données consiste à utiliser une **navigation axée sur la recherche**, qui permet la flexibilité de l’énumération des nœuds de navigation et de gérer efficacement de filtrage de sécurité. 

Il existe d’autres options populaires pour créer des **fournisseurs de navigation personnalisé**. Examinez [les solutions de Navigation pour les portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) pour obtenir des instructions sur la création d’un fournisseur de navigation personnalisé.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Options de navigation des avantages et inconvénients de SharePoint Online

Le tableau suivant récapitule les avantages et inconvénients de chaque option. 


|Navigation gérée  |Navigation structurelle  |Navigation basée sur la recherche  |Fournisseur de navigation personnalisé  |
|---------|---------|---------|---------|
|Avantages :<br/><br/>Facilité de maintenance<br/>Option recommandée<br/>     |Avantages :<br/><br/>Facilité de configuration<br/>Limités de sécurité<br/>Met à jour automatiquement lorsque le contenu est ajouté.<br/>|Avantages :<br/><br/>Limités de sécurité<br/>Mise à jour automatique lorsque des sites sont ajoutés<br/>Rapidité de chargement et structure de navigation mise en cache localement<br/>|Avantages :<br/><br/>Élargir le choix des options disponibles<br/>Chargement rapide lors de la mise en cache est utilisé correctement<br/>Nombreuses options fonctionnent correctement avec la conception des pages réactif<br/>|
|Inconvénients :<br/><br/>Pas de mises à jour automatiques lorsque des sites sont ajoutés<br/>Affecte les performances si la suppression de la sécurité est activée.<br/>|Inconvénients :<br/><br/>**Non recommandé**<br/>**Impacts sur les performances et évolutivité**<br/>**Soumis à la limitation**<br/>|Inconvénients :<br/><br/>Aucune possibilité de classer facilement les sites<br/>Nécessite une personnalisation de la page maître (compétences techniques requises)<br/>|Inconvénients :<br/><br/>Développement personnalisé est requis<br/>Source de données externe / cache stocké est nécessaire, par exemple Azure<br/>|

L’option la plus appropriée pour votre site dépendent des besoins de votre site et de vos capacités techniques. Si vous souhaitez un fournisseur de navigation d’out-of-the-box évolutive, navigation gérée avec filtrage de sécurité désactivé est une très bonne option. 

L’option de navigation gérée peut être gérée par le biais de la configuration, n’implique pas les fichiers de personnalisation de code, et il est beaucoup plus rapide que la navigation structurelle. Si vous nécessitent le filtrage de sécurité et sentez à l’aise avec une page maître personnalisée et certaines fonctions dans l’organisation pour gérer les modifications qui peuvent se produire dans la page maître par défaut pour SharePoint Online, l’option de recherche peut produire une meilleure expérience utilisateur. Si vous avez des exigences plus complexes, un fournisseur de navigation personnalisé peut être le bon choix. Navigation structurelle n’est pas recommandée.

Enfin, il est important de noter que SharePoint est Ajout de fournisseurs de navigation supplémentaires et des fonctionnalités pour les architectures de site SharePoint exploitant une hiérarchie de site plus aplatie et un modèle « hub and spoke » avec les sites hub de SharePoint. Cela permet de nombreux scénarios à atteindre qui ne nécessitent pas l’utilisation de la fonctionnalité publication SharePoint, et ces configurations de navigation sont optimisées pour l’évolutivité et la latence dans SharePoint Online. Notez que l’application du même principe - simplification de la structure globale de votre site de publication SharePoint vers une structure plus simple, souvent une aide les performances globales et faire évoluer également. Cela signifie qu’au lieu d’avoir une seule Collection de sites avec des centaines de sites (sous-sites), il est préférable d’avoir plusieurs collections de sites avec des sous-sites minime (sous-sites).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>À l’aide de la navigation gérée et métadonnées dans SharePoint Online

Navigation gérée est une autre option out-of-the-box que vous pouvez utiliser pour recréer la plupart de la même fonctionnalité que la navigation structurelle. Métadonnées gérées peuvent être configurée pour que le filtrage de sécurité activées ou désactivées. Configurés avec filtrage de sécurité désactivée, lors de la navigation gérée est assez efficace tandis qu’il charge tous les liens de navigation avec un nombre constant d’appels du serveur. Évite d’activation du filtrage de sécurité, toutefois, certains des avantages de la navigation gérée et les clients peuvent choisir d’Explorer une des solutions de navigation personnalisé pour optimiser les performances et évolutivité.

Le nombre de sites ne nécessite pas de filtrage de sécurité, comme la structure de navigation est souvent cohérente pour tous les utilisateurs du site. Si le filtrage de sécurité est désactivé, un lien est ajouté à la navigation pas tous les utilisateurs ont accès à la liaison affiche toujours mais entraînera un message accès refusé. Il n’existe aucun risque d’accès par inadvertance dans le contenu.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Implémentation de la navigation gérée et des résultats

Il existe plusieurs articles sur Docs.Microsoft.com sur les détails de la navigation gérée, par exemple, voir [vue d’ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Afin d’implémenter la navigation gérée, vous configurer termes avec l’URL correspondant à la structure de navigation du site. Navigation gérée permettre même être curated manuellement pour remplacer la navigation structurelle dans de nombreux cas. Par exemple :

![Structure du site SharePoint Online](media/SPONavOptionsListOfSites.png)

L’exemple suivant montre les performances d’une navigation complexe utilisant la navigation gérée.

![Performances de navigation complexe à l’aide de la navigation gérée](media/SPONavOptionsComplexNavPerf.png)

L’utilisation de navigation gérée cohérente améliore les performances par rapport à l’approche de la structure de navigation.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilisation de la navigation structurelle dans SharePoint Online

Le volet de navigation out-of-the-box utilisé par défaut et est la solution la plus simple mais possède un compromis concernant les performances coûteux. Toute personnalisation n’est pas nécessaire et un utilisateur technique peut aussi facilement ajouter des éléments, masquer les éléments et de gérer la navigation dans la page Paramètres. Il s’agit toutefois également la valeur true pour la Navigation gérée afin qu’il est recommandé d’utiliser la Navigation gérée en tant que peut également être facilement gérée et contrôlée ainsi avec des performances améliorées.

![Navigation structurelle avec des sous-sites afficher sélectionné](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Activation de la navigation structurelle dans SharePoint Online

Pour illustrer la façon dont les performances dans une solution SharePoint Online standard avec navigation structurelle et afficher des sous-sites option activée. Voici une capture d’écran des paramètres qui se trouvent dans la page **Paramètres du Site** \> **Navigation**.
  
![Capture d’écran montrant des sous-sites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analyse des performances de la navigation structurelle dans SharePoint Online

Pour analyser les performances d’une page SharePoint, utilisez l’onglet **réseau** des outils de développement F12 dans Internet Explorer. 
  
![Capture d’écran montrant l’onglet Réseau des Outils de développement F12](media/SPONavOptionsNetworks.png)
  
1. Sur l’onglet **Réseau**, cliquez sur la page .aspx en cours de chargement, puis sur l’onglet **Détails**.<br/> ![Capture d’écran montrant l’onglet Détails](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Cliquez sur **En-têtes de réponse**. <br/>![Capture d’écran de l’onglet Détails](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint renvoie des informations de diagnostics utiles dans les en-têtes de réponse. 
3. Les éléments d’information plus utiles est **SPRequestDuration** , qui est la valeur, en millisecondes, de la durée au processus sur le serveur d’une demande. Dans la capture d’écran suivante **affiche les sous-sites** est désactivée pour la navigation structurelle. Cela signifie qu’il existe uniquement le lien de collection de sites dans le volet de navigation globale :<br/>![Capture d’écran montrant le temps de chargement en tant que durée de la demande](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. La touche **SPRequestDuration** a une valeur de 245 millisecondes. Cela représente la durée que nécessaire pour renvoyer la demande. Étant donné qu’un seul élément de navigation sur le site, il s’agit d’une moyenne pour le fonctionnement de SharePoint Online sans navigation épais. La capture d’écran suivante montre comment ajouter dans les sous-sites affecte cette clé.<br/>![Capture d’écran montrant une durée de demande de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Ajout de sous-sites a augmenté sensiblement le temps que nécessaire pour renvoyer la demande de page pour ce site exemple relativement simple. Hiérarchies de site complexe, y compris les pages dans le volet de navigation, configuration et autres options de topologie peuvent augmenter considérablement cet impact encore.

## <a name="using-search-driven-client-side-scripting"></a>Utilisation de scripts côté client basés sur la recherche

Utilisation de la recherche, vous pouvez exploiter les index sont créés en arrière-plan à l’aide de l’analyse continue. Les résultats de recherche sont extraites de l’index de recherche et les résultats sont limités à la sécurité. Il s’agit généralement plus rapide que les fournisseurs de navigation out-of-the-box lors de la suppression de la sécurité est nécessaire. Utilisation de la recherche pour la navigation structurelle, en particulier si vous avez une structure de site complexe, accélère considérablement les temps de chargement de page. Le principal avantage de cette navigation gérée est que vous pouvez bénéficier de filtrage de sécurité.

Cette approche implique la création d’une page maître personnalisée et en remplaçant le code de navigation out-of-the-box avec du code HTML personnalisé. Suivez cette procédure décrite dans l’exemple suivant pour remplacer le code de navigation dans le fichier `seattle.html`. Dans cet exemple, vous devez ouvrir le `seattle.html` de fichiers et remplacez l’élément entier `id=”DeltaTopNavigation”` avec du code HTML personnalisé.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Exemple : Remplacez le code de navigation out-of-the-box dans une page maître

1.  Accédez à la page Paramètres du site.
2.  Ouvrez la galerie de pages maîtres en cliquant sur **Pages maîtres**.
3.  À partir de là, vous pouvez naviguer dans la bibliothèque et téléchargez le fichier `seattle.master`.
4.  Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code qui apparaît dans la capture d’écran suivante.<br/>![Supprimer le bloc de code indiqué](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Supprimer le code entre la `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` et `<\SharePoint:AjaxDelta>` balises et remplacez-la par l’extrait de code suivant :<br/>

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
6. Remplacez l’URL dans la charge de balise d’ancrage au début, avec un lien vers une image dans votre collection de sites de chargement de l’image. Après avoir apporté les modifications, renommez le fichier et puis le télécharger vers la galerie de pages maîtres. Cette opération génère un nouveau fichier .master.<br/>
7. Ce code HTML est le balisage de base qui est rempli par les résultats de recherche à partir du code JavaScript. Vous devez modifier le code pour modifier la valeur de la racine var = « URL de la collection de sites » comme illustré dans l’extrait suivant :<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Les résultats sont affectés au tableau self.nodes et une hiérarchie repose sur des objets à l’aide de linq.js affectation la sortie à un tableau self.hierarchy. Ce tableau est l’objet qui est lié à l’élément HTML. Cela s’effectue dans la fonction toggleView() en passant l’objet automatique à la fonction ko.applyBinding().<br/>Cela entraîne ensuite le tableau de hiérarchie doit être lié le code HTML suivant :<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Les gestionnaires d’événements pour `mouseenter` et `mouseexit` sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants sous-site qui s’effectue dans le `addEventsToElements()` fonction.

Dans notre exemple de navigation complexes, une page vierge chargez sans l’affiche de la mise en cache local le temps passé sur le serveur a été supprimée vers le bas de la navigation structurelles banc d’essai pour obtenir un résultat similaire à l’approche de la navigation gérée.

### <a name="about-the-javascript-file"></a>À propos du fichier JavaScript...

L’intégralité du fichier JavaScript se présente comme suit :

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

Pour résumer le code ci-dessus dans le `jQuery $(document).ready` fonction est un `viewModel object` créé, puis le `loadNavigationNodes()` fonction de cet objet est appelée. Cette fonction charge soit la hiérarchie de navigation générée précédemment stockée dans le stockage local HTML5 du navigateur client ou il appelle la fonction `queryRemoteInterface()`.

`QueryRemoteInterface()`génère une demande à l’aide de la `getRequest()` fonctionne avec le paramètre de requête défini précédemment dans le script et renvoie ensuite les données à partir du serveur. Ces données sont essentiellement un tableau de tous les sites de la collection représentée en tant qu’objets de transfert de données avec différentes propriétés. 

Ces données sont ensuite analysées dans précédemment défini `SPO.Models.NavigationNode` objets qui utilisent `Knockout.js` pour créer des propriétés visible pour une utilisation par les valeurs de liaison dans le code HTML que nous avons défini précédemment de données. 

Les objets sont ensuite placées dans un tableau de résultats. Ce tableau est analysé dans JSON grâce à Knockout et stocké dans le stockage de navigateur local pour améliorer les performances sur les charges de page future.

### <a name="benefits-of-this-approach"></a>Avantages de cette approche

Un avantage majeur de [cette approche](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) est qu’à l’aide de stockage local HTML5, le volet de navigation est stockée localement pour l’utilisateur lors du prochain que chargement de la page. Nous obtenons principales améliorations de l’utilisation de l’API de recherche pour la navigation structurelle ; Toutefois, il faut des capacités techniques pour exécuter et personnaliser cette fonctionnalité. 

Dans l' [exemple d’implémentation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), les sites sont classés dans la même façon que la navigation structurelle out-of-the-box ; ordre alphabétique. Si vous souhaitez s’écartent de cette commande, il est plus complexe de développer et de mettre à jour. En outre, cette approche nécessite que vous écarter les pages maîtres pris en charge. Si la page maître personnalisée n’est pas conservée, votre site sera manquez améliorations par Microsoft pour les pages maîtres et mises à jour.

[code au-dessus de](#about-the-javascript-file) comporte les dépendances suivantes :

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- LINQ.js - http://linqjs.codeplex.com/, ou github.com/neuecc/linq.js

La version actuelle de LinqJS ne contient-elle pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompra le code de navigation. Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq.js avant la ligne `Flatten: function ()`.

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
  
## <a name="related-topics"></a>Voir aussi

[Vue d'ensemble de la navigation gérée dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

