---
title: Différer le chargement des images et des éléments JavaScript dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Cet article explique comment réduire le temps de chargement des pages SharePoint Online en utilisant JavaScript pour différer le chargement des images et en attendant de charger le code JavaScript non essentiel jusqu’à ce que la page se charge.
ms.openlocfilehash: 9069fb395465cd9d087c018cc2ae782759ddcb0d
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616786"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Différer le chargement des images et des éléments JavaScript dans SharePoint Online

Cet article explique comment réduire le temps de chargement des pages SharePoint Online en utilisant JavaScript pour différer le chargement des images et en attendant de charger le code JavaScript non essentiel jusqu’à ce que la page se charge.
  
Les images peuvent avoir une incidence négative sur la vitesse de chargement des pages sur SharePoint Online. Par défaut, la plupart des navigateurs Internet modernes extraient les images lors du chargement d’une page HTML. Cela peut entraîner un chargement insuffisant de la page si les images ne sont pas visibles à l’écran jusqu’à ce que l’utilisateur fasse défiler vers le bas. Les images peuvent empêcher le navigateur de charger la partie visible de la page. Pour contourner ce problème, vous pouvez utiliser JavaScript pour ignorer d’abord le chargement des images. De plus, le chargement de JavaScript non essentiels peut ralentir le temps de chargement de vos pages SharePoint. Cette rubrique décrit certaines méthodes que vous pouvez utiliser pour améliorer les temps de chargement des pages avec JavaScript dans SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Améliorer les temps de chargement des pages en retardant le chargement de l’image dans les pages SharePoint Online à l’aide de JavaScript

Vous pouvez utiliser JavaScript pour empêcher un navigateur Web de récupérer des images. Cela accélère le rendu de document global. Pour ce faire, supprimez la valeur de l’attribut SRC de \<la\> balise IMG et remplacez-la par le chemin d’accès à un fichier dans un attribut Data tel que: Data-SRC. Par exemple:
  
```txt
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

À l’aide de cette méthode, le navigateur ne télécharge pas les images immédiatement. Si l’image est déjà dans la fenêtre d’affichage, JavaScript indique au navigateur d’extraire l’URL à partir de l’attribut Data et de l’insérer en tant que valeur de l’attribut SRC. L’image ne se charge que lorsque l’utilisateur fait défiler et qu’elle apparaît.
  
Pour tout faire, vous devez utiliser JavaScript.
  
Dans un fichier texte, définissez la fonction **isElementInViewport ()** pour vérifier si un élément est dans la partie du navigateur visible par l’utilisateur. 
  
```txt
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

Ensuite, utilisez **isElementInViewport ()** dans la fonction **loadItemsInView ()** . La fonction **loadItemsInView ()** charge toutes les images ayant une valeur pour l’attribut Data-SRC si elles sont dans la partie du navigateur visible par l’utilisateur. Ajoutez la fonction suivante au fichier texte: 
  
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

Enfin, appelez **loadItemsInView ()** à partir de **Window. OnScroll ()** comme indiqué dans l’exemple suivant. Cela garantit que toutes les images qui sont dans la fenêtre d’affichage sont chargées lorsque l’utilisateur en a besoin, mais pas avant. Ajoutez les éléments suivants au fichier texte: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Pour SharePoint Online, vous devez attacher la fonction suivante à l’événement scroll sur la balise div \<\> #s4-Workspace. Cela est dû au fait que les événements de fenêtre sont remplacés afin de s’assurer que le ruban reste attaché au haut de la page.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Enregistrez le fichier texte sous la forme d’un fichier JavaScript avec l’extension. js, par exemple delayLoadImages. js.
  
Une fois que vous avez terminé d’écrire delayLoadImages. js, vous pouvez ajouter le contenu du fichier à une page maître dans SharePoint Online. Pour ce faire, vous ajoutez un lien de script à l’en-tête de la page maître. Une fois qu’il se trouve dans une page maître, le code JavaScript est appliqué à toutes les pages de votre site SharePoint Online qui utilisent cette mise en page de page maître. Par ailleurs, si vous avez l’intention de l’utiliser sur une seule page de votre site, utilisez le composant WebPart éditeur de script pour incorporer le code JavaScript dans la page. Pour plus d’informations, consultez les rubriques suivantes:
  
- [Comment appliquer une page maître à un site dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Procédure : Créer une mise en page dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Exemple: référencement du fichier JavaScript delayLoadImages. js à partir d’une page maître dans SharePoint Online**
  
Pour que cela fonctionne, vous devez également référencer jQuery dans la page maître. Dans l’exemple suivant, vous pouvez voir dans le chargement de la page initiale qu’il n’y a qu’une seule image chargée, mais il y a plusieurs autres éléments sur la page.
  
![Capture d’écran montrant une seule image chargée sur une page](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
La capture d’écran suivante montre le reste des images qui sont téléchargées une fois qu’elles ont fait défiler vers la vue.
  
![Capture d’écran montrant plusieurs images chargées sur une page](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Le retardement du chargement d’image à l’aide de JavaScript peut être une technique efficace pour améliorer les performances; Toutefois, si la technique est appliquée sur un site Web public, les moteurs de recherche ne peuvent pas analyser les images de la même manière qu’elles analysent une image formée régulièrement. Cela peut affecter les classements sur les moteurs de recherche, car les métadonnées de l’image proprement dite ne sont pas vraiment là avant le chargement de la page. Les robots d’indexation de moteur de recherche ne lisent que le code HTML et, par conséquent, ne verront pas les images en tant que contenu sur la page. Les images sont l’un des facteurs utilisés pour classer les pages dans les résultats de la recherche. Pour contourner ce processus, vous pouvez utiliser un texte d’introduction pour vos images.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Exemple de code GitHub: injection de code JavaScript pour améliorer les performances

Ne manquez pas l’article et l’exemple de code sur l' [injection JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) fournis sur GitHub. 
  
## <a name="see-also"></a>Voir aussi

[Navigateurs pris en charge dans Office 2013 et Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Comment appliquer une page maître à un site dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Procédure : Créer une mise en page dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

