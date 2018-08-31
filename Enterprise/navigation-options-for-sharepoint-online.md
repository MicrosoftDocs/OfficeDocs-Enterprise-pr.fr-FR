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
# <a name="navigation-options-for-sharepoint-online"></a>Options de navigation pour SharePoint Online

Cet article explique comment améliorer le temps de chargement des pages pour SharePoint Online à l’aide de la navigation gérée ou la navigation par recherche lors de la publication classique.
  
SharePoint Online avec publication classique activée a deux zones de navigation ; Navigation globale et Navigation actuelle.
  
Navigation globale est le menu de navigation supérieure pendant la Navigation actuelle est le côté ou la navigation de gauche/droite en contexte dépende de la configuration de la langue et de la page maître utilisée.
  
Navigation affecte les performances pour le portail entier tel qu’il est souvent configuré pour une utilisation au niveau du portail et en tant que telles est un élément important d’un site SharePoint.
  
Navigation structurelle n’est pas l’option de navigation recommandées dans SharePoint Online, comme il a été conçu pour une topologie sur site avec filtrage de sécurité et ce modèle entraîne des appels excessive du serveur et a un impact sur les performances lorsqu’il est utilisé.
  
Que la conception a changé avec l’introduction des sites SharePoint moderne où moderne a une hiérarchie de site aplati simplifiée. Cette opération a simplifiée navigation avec une hiérarchie simplifiée qui a résolu les problèmes de performances liés à la navigation.
  
Il existe deux options principales out-of-the-box navigation dans SharePoint ainsi qu’une troisième, approche personnalisée, pilotés par la recherche. Également une quatrième et option assez courante consiste à créer un fournisseur de Navigation personnalisé. Examinez [les solutions de Navigation pour les portails SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) pour obtenir des instructions sur un fournisseur de navigation personnalisé. 
  
Chaque option présente des avantages et inconvénients, comme indiqué dans le tableau suivant.
  
|**Navigation structurelle**|**Navigation gérée**|**Navigation par recherche**||**Fournisseur de Navigation personnalisé**|
|:-----|:-----|:-----|:-----|:-----|
| Avantages :  <br/>  Facilité de configuration  <br/>  Découpage à des fins de sécurité  <br/>  Mise à jour automatique lorsque des sites sont ajoutés  <br/> | Avantages :  <br/>  Facilité de maintenance  <br/>  Option recommandée  <br/> | Avantages :  <br/>  Découpage à des fins de sécurité  <br/>  Mise à jour automatique lorsque des sites sont ajoutés  <br/>  Rapidité de chargement et structure de navigation mise en cache localement  <br/> || Avantages :  <br/>    <br/>  Choix plus large / options disponibles  <br/>  Chargement rapide lors de la mise en cache est utilisé correctement  <br/> |
| Inconvénients :  <br/> **Non recommandé** <br/> **Affecte les performances** <br/> | Inconvénients :  <br/>  Pas de mises à jour automatiques lorsque des sites sont ajoutés  <br/>  Affecte les performances si la suppression de la sécurité est activée.  <br/> | Inconvénients :  <br/>  Aucune possibilité de classer facilement les sites  <br/>  Nécessite une personnalisation de la page maître (compétences techniques requises)  <br/> || Inconvénients :  <br/>  Développement personnalisé est requis  <br/>  Source de données externe / cache stocké est nécessaire, par exemple Azure  <br/> |
   
L’option la plus appropriée pour votre site dépendent des besoins de votre site et de vos capacités techniques. Si vous êtes habitué à utiliser une page maître personnalisée et avez une fonctionnalité dans l’organisation pour gérer les modifications qui peuvent se produire dans la page maître par défaut pour SharePoint Online, l’option de recherche produira la meilleure expérience utilisateur. Si vous souhaitez milieu simple entre la navigation structurelle out-of-the-box et de la recherche, la navigation gérée est une très bonne option. L’option de navigation gérée peut être gérée par le biais de la configuration, n’implique pas les fichiers de personnalisation de code, et il est beaucoup plus rapide que la navigation structurelle out-of-the-box.
  
Simplification de la structure globale de votre portail classique comme moderne, aide également à l’échelle et les performances globales. Cela signifie qu’au lieu d’avoir une seule Collection de sites avec des centaines / des milliers de sites (sous-sites), une meilleure approche consiste à détenir de nombreuses collections de sites avec des sous-sites minime (sous-sites).
  
Cela fournit des options supplémentaires de mise à l’échelle dans le service, évite de placer tout le contenu dans une base de données volumineux et finalement une plus grande souplesse pour la navigation et de plus de sécurité.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilisation de la navigation structurelle dans SharePoint Online

Le volet de navigation out-of-the-box utilisé par défaut et est la solution la plus simple mais possède un compromis concernant les performances coûteux. Toute personnalisation n’est pas nécessaire et un utilisateur technique peut aussi facilement ajouter des éléments, masquer les éléments et de gérer la navigation dans la page Paramètres. Il s’agit toutefois également la valeur true pour la Navigation gérée afin qu’il est recommandé d’utiliser Navigation gérée en tant que qui peuvent également être facilement gérés et contrôlés ainsi.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Activation de la navigation structurelle dans SharePoint Online

Pour illustrer la façon dont les performances dans une solution SharePoint Online standard avec navigation structurelle et afficher des sous-sites option activée. Vous trouverez ci-dessous est un capture d’écran paramètres contenus dans la page **Paramètres du Site** \> **Navigation**.
  
![Capture d’écran montrant des sous-sites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analyse des performances de la navigation structurelle dans SharePoint Online

Pour analyser les performances d’une page SharePoint, utilisez l’onglet **Réseau** des outils de développement F12 dans Internet Explorer. 
  
![Capture d’écran montrant l’onglet Réseau des Outils de développement F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
Sur l’onglet **Réseau**, cliquez sur la page .aspx en cours de chargement, puis sur l’onglet **Détails**. 
  
![Capture d’écran montrant l’onglet Détails](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Cliquez sur **En-têtes de réponse**.
  
![Capture d’écran de l’onglet Détails](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint renvoie des informations de diagnostics utiles dans les en-têtes de réponse. Un des plus utiles est l’en-tête **SPRequestDuration**, qui indique la durée, en millisecondes, du traitement d’une demande sur le serveur. 
  
Dans l’écran suivant **Afficher les sous-sites** est désactivée pour la navigation structurelle. Cela signifie qu’il existe uniquement le lien de collection de sites dans le volet de navigation globale : 
  
![Capture d’écran montrant le temps de chargement en tant que durée de la demande](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
La touche **SPRequestDuration** a une valeur de 245 millisecondes. Cela représente la durée que nécessaire pour renvoyer la demande. Étant donné qu’un seul élément de navigation sur le site, il s’agit d’une moyenne pour le fonctionnement de SharePoint Online sans navigation épais. La capture d’écran suivante montre comment ajouter dans les sous-sites affecte cette clé. 
  
![Capture d’écran montrant une durée de demande de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
L’ajout des sous-sites a augmenté de façon importante le temps nécessaire pour renvoyer la demande de page.
  
Les avantages de l’utilisation de la navigation structurée régulière est que vous pouvez facilement organiser l’ordre, masquer les sites, ajouter des pages, les résultats sont limités à la sécurité, et vous ne sont pas qui s’écartent des pages maîtres pris en charge utilisés dans SharePoint Online.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Utilisation de la navigation gérée et des métadonnées gérées dans SharePoint Online

La navigation gérée est une autre option standard que vous pouvez utiliser pour recréer le même type de fonctionnalité que la navigation structurelle.
  
L’avantage de l’utilisation de métadonnées gérées est qu’il est beaucoup plus rapide pour récupérer les données à l’aide du contenu par requête pour créer la navigation de site. Bien qu’il soit que beaucoup plus rapidement il n’existe aucun moyen de découpage de sécurité les résultats donc si un utilisateur n’a pas accès à un site donné, le lien affiche toujours mais entraîne un message d’erreur.
  
 **Implémentation de la navigation gérée et des résultats**
  
Il existe plusieurs articles sur TechNet sur les détails de la navigation gérée, par exemple, voir [vue d’ensemble de la navigation gérée dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Pour implémenter la navigation gérée, vous devez disposer des autorisations d’administrateur du magasin de termes. En configurant des termes avec des URL qui correspondent à la structure d’une collection de sites, la navigation gérée peut être utilisée pour remplacer la navigation structurelle. Par exemple :
  
![Capture d’écran de l’exemple Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
L’exemple suivant montre les performances d’une navigation complexe utilisant la navigation gérée.
  
![Capture d’écran de l’exemple SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
L’utilisation de la navigation gérée améliore sensiblement les performances par rapport à la navigation structurelle par requête sur le contenu.
  
## <a name="using-search-driven-client-side-scripting"></a>Utilisation de scripts côté client basés sur la recherche

En utilisant la recherche, vous pouvez tirer parti des index créés en arrière-plan à l’aide de l’analyse continue. Cela signifie qu’aucune requête de contenu lourde n’est exécutée. Les résultats de recherche sont extraits de l’index de recherche et les résultats sont découpés à des fins de sécurité. Cette procédure est plus rapide que l’utilisation de requêtes de contenu standard. L’utilisation de la recherche pour la navigation structurelle va considérablement accélérer le temps de chargement des pages, surtout si vous disposez d’une structure de site complexe. Grâce à cette navigation gérée, vous bénéficiez du découpage à des fins de sécurité ; il s’agit du principal avantage de cette approche.
  
Celle-ci implique la création d’une page maître personnalisée et le remplacement du code de navigation standard par du code HTML personnalisé. Suivez cette procédure pour remplacer le code de navigation dans le fichier seattle.html.
  
Dans cet exemple, vous ouvrez le fichier seattle.html et remplacez l’élément entier **id = « DeltaTopNavigation »** avec le code HTML personnalisé. 
  
 **Exemple : remplacement du code de navigation standard dans une page maître**
  
1. Accédez à la page **Paramètres du site**. 
    
2. Ouvrez la galerie de pages maîtres en cliquant sur **Pages maîtres**.
    
3. Vous pouvez alors parcourir la bibliothèque et téléchargez le fichier **seattle.master**.
    
4. Modifiez le code à l’aide d’un éditeur de texte et supprimez le bloc de code qui apparaît dans la capture d’écran suivante.
    
    ![Capture d’écran du code DeltaTopNavigation à supprimer](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Supprimer le code entre la \<SharePoint:AjaxDelta id = « DeltaTopNavigation »\> et \<\SharePoint:AjaxDelta\> balises et remplacez-la par l’extrait de code suivant :
    
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

6. Remplacez l’URL dans la charge de balise d’ancrage au début, avec un lien vers une image dans votre collection de sites de chargement de l’image. Après avoir apporté les modifications, renommez le fichier et puis le télécharger vers la galerie de pages maîtres. Cette opération génère un nouveau fichier .master.
    
7. Ce code HTML est le balisage de base qui est rempli par les résultats de recherche à partir du code JavaScript. Vous devez modifier le code suivant pour modifier la valeur pour le `var root = "site collection URL"` comme illustré dans l’extrait suivant : 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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

     $("li.level1").mouseover (fonction () { 
  
position var = $(this).position() ;
  
.find("ul.level2").css $(this) ({largeur : 100, gauche : position.left + 10, top : 50}) ;
    
     }) 
  
.MOUSEOUT (fonction () {
  
.find("ul.level2").css $(this) ({gauche :-99999, supérieur : 0}) ;
  
});
  
$("li.level2").mouseover (fonction () {
  
position var = $(this).position() ;
  
console.log(JSON.stringify(position)) ;
  
.find("ul.level3").css $(this) ({largeur : 100, gauche : position.left + 95, top : position.top}) ;
    
     }) 
  
.MOUSEOUT (fonction () {
  
.find("ul.level3").css $(this) ({gauche :-99999, supérieur : 0}) ;
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. Ensuite, les résultats sont affectés au tableau **[self.nodes]** et une hiérarchie repose sur les objets à l’aide de linq.js affectation la sortie à un tableau **[self.heirarchy]**. Ce tableau est l’objet qui est lié à l’élément HTML. Cela s’effectue dans la fonction **[toggleView()]** en passant l’objet automatique à la fonction **[ko.applyBinding()]** . Cela entraîne ensuite le tableau de hiérarchie doit être lié le code HTML suivant : 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    Enfin, les gestionnaires d’événements pour **[mouseenter]** et **[souris quitter]** sont ajoutés à la navigation de niveau supérieur pour gérer les menus déroulants sous-site qui s’effectue dans la fonction **[addEventsToElements()]** . 
    
    Les résultats de la barre de navigation peuvent être affichées dans la capture d’écran ci-dessous :
    
    ![Capture d’écran des résultats de la navigation](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    Dans notre exemple de navigation complexe, le chargement d’une nouvelle page sans la mise en cache locale montre que le temps passé sur le serveur a été largement réduit par rapport à la navigation structurelle de référence et les résultats obtenus sont semblables à ceux obtenus pour la navigation gérée.
    
    ![Capture d’écran de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Un des principaux avantages de cette approche est qu’en utilisant le stockage local HTML5, la navigation est stockée localement pour l’utilisateur en prévision du prochain chargement de la page.
    
Grâce à l’utilisation de l’API de recherche pour la navigation structurelle, les performances sont considérablement améliorées. Toutefois, des connaissances techniques sont requises pour exécuter et personnaliser cette fonctionnalité. Dans l’exemple d’implémentation, les sites sont classés de la même manière que dans la navigation structurelle standard, à savoir par ordre alphabétique. Si vous souhaitez classer les sites autrement, le développement et la maintenance s’avéreraient plus complexes. En outre, cette approche vous obligerait à utiliser d’autres pages maîtres que celles prises en charge. Si la page maître personnalisée n’est pas conservée, votre site ne pourra pas bénéficier des mises à jour et des améliorations que Microsoft apporte aux pages maîtres.
  
Le code ci-dessus comporte les dépendances suivantes :
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), ou [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
La version actuelle de LinqJS ne contient-elle pas la méthode ByHierarchy utilisée dans le code ci-dessus et rompra le code de navigation. Pour résoudre ce problème, ajoutez la méthode suivante au fichier Linq.js avant la ligne « écraser : fonction () ».
  
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


