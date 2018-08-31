---
title: Différer le chargement des images et des éléments JavaScript dans SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Cet article explique comment vous pouvez réduire le temps de chargement des pages SharePoint Online à l’aide de JavaScript à retarder le chargement des images et également en charge non essentiels JavaScript jusqu'à après le chargement de la page en attente.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540561"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Différer le chargement des images et des éléments JavaScript dans SharePoint Online

Cet article explique comment vous pouvez réduire le temps de chargement des pages SharePoint Online à l’aide de JavaScript à retarder le chargement des images et également en charge non essentiels JavaScript jusqu'à après le chargement de la page en attente. 
  
Les images peuvent réduire la vitesse de chargement des pages sur SharePoint Online. Par défaut, la plupart des navigateurs Internet modernes extraient à l’avance des images lors du chargement d’une page HTML. Cela peut entraîner un ralentissement inutile du chargement de la page, notamment si les images ne sont pas visibles à l’écran tant que l’utilisateur ne fait pas défiler vers le bas. Les images peuvent empêcher le navigateur de charger la partie visible de la page. Pour contourner ce problème, vous pouvez vous servir de JavaScript pour ignorer le chargement préalable des images. En outre, le chargement d’éléments JavaScript superflus peut ralentir le chargement de vos pages SharePoint également. Cette rubrique décrit quelques-unes des méthodes que vous pouvez utiliser pour améliorer le temps de chargement des pages avec JavaScript dans SharePoint Online. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Réduire le temps de chargement des pages en différant le chargement des images dans les pages SharePoint Online à l’aide de JavaScript

Vous pouvez utiliser JavaScript pour empêcher un navigateur web à partir d’images lisant au préalable. Cela accélère l’ensemble du rendu document. Pour ce faire, vous supprimez la valeur de l’attribut src de le \<img\> tag et remplacez-la par le chemin d’accès à un fichier dans un attribut de données, telles que : données-src. Par exemple :
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

À l’aide de cette méthode, le navigateur ne télécharger immédiatement les images. Si l’image est déjà dans la fenêtre d’affichage, JavaScript indique au navigateur pour récupérer l’URL de l’attribut de données et l’insérer en tant que la valeur de l’attribut src. L’image charge uniquement en tant que l’utilisateur défile et il est fourni dans la vue.
  
Pour faire tout cela se produit, vous devrez utiliser JavaScript.
  
Dans un fichier texte, définissez la fonction **isElementInViewport()** afin qu’elle vérifie si un élément se trouve ou non dans la partie du navigateur que l’utilisateur peut voir. 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

Ensuite, utilisez **isElementInViewport()** dans la fonction **loadItemsInView()**. La fonction **loadItemsInView()** charge toutes les images possédant une valeur pour l’attribut data-src si elles se trouvent dans la partie du navigateur que l’utilisateur peut voir. Dans le fichier texte, ajoutez la fonction suivante : 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

Enfin, appelez **loadItemsInView()** depuis **window.onscroll()** comme indiqué dans l’exemple suivant. Cette procédure garantit que toutes les images qui se trouvent dans la fenêtre d’affichage sont chargées lorsque l’utilisateur a besoin, mais pas avant. Ajoutez le code suivant au fichier texte : 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Pour SharePoint Online, vous devez lier la fonction suivante à l’événement de défilement sur le s4-workspace # \<div\> balise. Il s’agit, car les événements de fenêtre sont remplacées pour garantir que le ruban reste attaché au haut de la page.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Enregistrez le fichier texte en tant que fichier JavaScript avec l’extension .js, par exemple delayLoadImages.js.
  
Une fois que vous avez terminé d’écrire delayLoadImages.js, vous pouvez ajouter le contenu du fichier à une page maître dans SharePoint Online. Pour cela, en ajoutant un lien de script à l’en-tête de la page maître. Une fois qu’il se trouve dans une page maître, le code JavaScript sera appliqué à toutes les pages de votre site SharePoint Online qui utilisent cette mise en page maître. Autrement, si vous envisagez d’utiliser uniquement sur une page de votre site, utilisez le composant WebPart Éditeur de script pour incorporer le code JavaScript dans la page. Voir les rubriques suivantes pour plus d’informations :
  
- [Procédure : appliquer une page maître à un site dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Comment : créer une mise en page dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Exemple : référencement du fichier JavaScript delayLoadImages.js à partir d’une page maître dans SharePoint Online**
  
Pour ce faire, vous devez également référencer jQuery dans la page maître. Dans l’exemple suivant, vous pouvez voir que dans le chargement initial de la page, une seule image est chargée, mais qu’il en existe plusieurs sur la page.
  
![Capture d’écran montrant une seule image chargée sur une page](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
La capture d’écran suivante montre le reste des images qui sont téléchargées lorsqu’elles apparaissent, à mesure du défilement de la page.
  
![Capture d’écran montrant plusieurs images chargées sur une page](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Le fait de différer le chargement des images à l’aide de JavaScript peut permettre d’augmenter efficacement les performances ; toutefois, si cette technique est appliquée sur un site web public, les moteurs de recherche ne pourront pas analyser les images de la même manière que pour une image normalement formée. Cette méthode peut avoir un impact négatif sur les classements des moteurs de recherche, car les métadonnées de l’image ne sont pas vraiment présentes tant que la page n’est pas chargée. Les robots de recherche de lecture ne font que lire le code HTML et ne considéreront donc pas les images comme du contenu de la page. Les images font partie des facteurs utilisés pour classer les pages dans les résultats de recherche. Pour contourner ce problème, vous pouvez insérer un texte d’introduction pour vos images.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Exemple de code GitHub : injection de code JavaScript pour améliorer les performances

Ne manquez pas l’article et exemple de code sur [injection de code JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) fourni dans les référentiels. 
  
## <a name="see-also"></a>Voir aussi

[Navigateurs pris en charge dans Office 2013 et Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Procédure : appliquer une page maître à un site dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Comment : créer une mise en page dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

