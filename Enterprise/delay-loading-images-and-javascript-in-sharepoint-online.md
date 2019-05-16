---
title: Différer le chargement des images et des éléments JavaScript dans SharePoint Online
ms.author: krowley
author: kccross
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
ms.openlocfilehash: 6b2e91ca4b8642ac7129e353f2527db60a32d75b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067980"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="9e7fa-103">Différer le chargement des images et des éléments JavaScript dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9e7fa-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="9e7fa-104">Cet article explique comment réduire le temps de chargement des pages SharePoint Online en utilisant JavaScript pour différer le chargement des images et en attendant de charger le code JavaScript non essentiel jusqu’à ce que la page se charge.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="9e7fa-105">Les images peuvent avoir une incidence négative sur la vitesse de chargement des pages sur SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-105">Images can negatively affect page load speeds on SharePoint Online.</span></span> <span data-ttu-id="9e7fa-106">Par défaut, la plupart des navigateurs Internet modernes extraient les images lors du chargement d’une page HTML.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-106">By default, most modern Internet browsers pre-fetch images when loading an HTML page.</span></span> <span data-ttu-id="9e7fa-107">Cela peut entraîner un chargement insuffisant de la page si les images ne sont pas visibles à l’écran jusqu’à ce que l’utilisateur fasse défiler vers le bas.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-107">This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down.</span></span> <span data-ttu-id="9e7fa-108">Les images peuvent empêcher le navigateur de charger la partie visible de la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-108">The images can block the browser from loading the visible part of the page.</span></span> <span data-ttu-id="9e7fa-109">Pour contourner ce problème, vous pouvez utiliser JavaScript pour ignorer d’abord le chargement des images.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-109">To work around this problem, you can use JavaScript to skip loading the images first.</span></span> <span data-ttu-id="9e7fa-110">De plus, le chargement de JavaScript non essentiels peut ralentir le temps de chargement de vos pages SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-110">Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too.</span></span> <span data-ttu-id="9e7fa-111">Cette rubrique décrit certaines méthodes que vous pouvez utiliser pour améliorer les temps de chargement des pages avec JavaScript dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-111">This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="9e7fa-112">Améliorer les temps de chargement des pages en retardant le chargement de l’image dans les pages SharePoint Online à l’aide de JavaScript</span><span class="sxs-lookup"><span data-stu-id="9e7fa-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="9e7fa-113">Vous pouvez utiliser JavaScript pour empêcher un navigateur Web de récupérer des images.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-113">You can use JavaScript to prevent a web browser from pre-fetching images.</span></span> <span data-ttu-id="9e7fa-114">Cela accélère le rendu de document global.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-114">This speeds up overall document rendering.</span></span> <span data-ttu-id="9e7fa-115">Pour ce faire, supprimez la valeur de l’attribut SRC de \<la\> balise IMG et remplacez-la par le chemin d’accès à un fichier dans un attribut Data tel que: Data-SRC. Par exemple:</span><span class="sxs-lookup"><span data-stu-id="9e7fa-115">To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="9e7fa-116">À l’aide de cette méthode, le navigateur ne télécharge pas les images immédiatement.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-116">By using this method, the browser doesn't download the images immediately.</span></span> <span data-ttu-id="9e7fa-117">Si l’image est déjà dans la fenêtre d’affichage, JavaScript indique au navigateur d’extraire l’URL à partir de l’attribut Data et de l’insérer en tant que valeur de l’attribut SRC.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-117">If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute.</span></span> <span data-ttu-id="9e7fa-118">L’image ne se charge que lorsque l’utilisateur fait défiler et qu’elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-118">The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="9e7fa-119">Pour tout faire, vous devez utiliser JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="9e7fa-120">Dans un fichier texte, définissez la fonction **isElementInViewport ()** pour vérifier si un élément est dans la partie du navigateur visible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
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

<span data-ttu-id="9e7fa-121">Ensuite, utilisez **isElementInViewport ()** dans la fonction **loadItemsInView ()** .</span><span class="sxs-lookup"><span data-stu-id="9e7fa-121">Next, use **isElementInViewport()** in the **loadItemsInView()** function.</span></span> <span data-ttu-id="9e7fa-122">La fonction **loadItemsInView ()** charge toutes les images ayant une valeur pour l’attribut Data-SRC si elles sont dans la partie du navigateur visible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-122">The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user.</span></span> <span data-ttu-id="9e7fa-123">Ajoutez la fonction suivante au fichier texte:</span><span class="sxs-lookup"><span data-stu-id="9e7fa-123">Add the following function to the text file:</span></span> 
  
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

<span data-ttu-id="9e7fa-124">Enfin, appelez **loadItemsInView ()** à partir de **Window. OnScroll ()** comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-124">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example.</span></span> <span data-ttu-id="9e7fa-125">Cela garantit que toutes les images qui sont dans la fenêtre d’affichage sont chargées lorsque l’utilisateur en a besoin, mais pas avant.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-125">This ensures that any images that are in the viewport are loaded as the user needs them, but not before.</span></span> <span data-ttu-id="9e7fa-126">Ajoutez les éléments suivants au fichier texte:</span><span class="sxs-lookup"><span data-stu-id="9e7fa-126">Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="9e7fa-127">Pour SharePoint Online, vous devez attacher la fonction suivante à l’événement scroll sur la balise div \<\> #s4-Workspace.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-127">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag.</span></span> <span data-ttu-id="9e7fa-128">Cela est dû au fait que les événements de fenêtre sont remplacés afin de s’assurer que le ruban reste attaché au haut de la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-128">This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="9e7fa-129">Enregistrez le fichier texte sous la forme d’un fichier JavaScript avec l’extension. js, par exemple delayLoadImages. js.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="9e7fa-130">Une fois que vous avez terminé d’écrire delayLoadImages. js, vous pouvez ajouter le contenu du fichier à une page maître dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-130">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online.</span></span> <span data-ttu-id="9e7fa-131">Pour ce faire, vous ajoutez un lien de script à l’en-tête de la page maître.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-131">You do this by adding a script link to the header in the master page.</span></span> <span data-ttu-id="9e7fa-132">Une fois qu’il se trouve dans une page maître, le code JavaScript est appliqué à toutes les pages de votre site SharePoint Online qui utilisent cette mise en page de page maître.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-132">Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout.</span></span> <span data-ttu-id="9e7fa-133">Par ailleurs, si vous avez l’intention de l’utiliser sur une seule page de votre site, utilisez le composant WebPart éditeur de script pour incorporer le code JavaScript dans la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-133">Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page.</span></span> <span data-ttu-id="9e7fa-134">Pour plus d’informations, consultez les rubriques suivantes:</span><span class="sxs-lookup"><span data-stu-id="9e7fa-134">See these topics for more information:</span></span>
  
- [<span data-ttu-id="9e7fa-135">Comment appliquer une page maître à un site dans SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e7fa-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="9e7fa-136">Procédure : Créer une mise en page dans SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e7fa-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="9e7fa-137">**Exemple: référencement du fichier JavaScript delayLoadImages. js à partir d’une page maître dans SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="9e7fa-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="9e7fa-138">Pour que cela fonctionne, vous devez également référencer jQuery dans la page maître.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-138">In order for this to work, you also need to reference jQuery in the master page.</span></span> <span data-ttu-id="9e7fa-139">Dans l’exemple suivant, vous pouvez voir dans le chargement de la page initiale qu’il n’y a qu’une seule image chargée, mais il y a plusieurs autres éléments sur la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-139">In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Capture d’écran montrant une seule image chargée sur une page](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="9e7fa-141">La capture d’écran suivante montre le reste des images qui sont téléchargées une fois qu’elles ont fait défiler vers la vue.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Capture d’écran montrant plusieurs images chargées sur une page](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="9e7fa-143">Le retardement du chargement d’image à l’aide de JavaScript peut être une technique efficace pour améliorer les performances; Toutefois, si la technique est appliquée sur un site Web public, les moteurs de recherche ne peuvent pas analyser les images de la même manière qu’elles analysent une image formée régulièrement.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-143">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image.</span></span> <span data-ttu-id="9e7fa-144">Cela peut affecter les classements sur les moteurs de recherche, car les métadonnées de l’image proprement dite ne sont pas vraiment là avant le chargement de la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-144">This can affect rankings on search engines because metadata on the image itself is not really there until the page loads.</span></span> <span data-ttu-id="9e7fa-145">Les robots d’indexation de moteur de recherche ne lisent que le code HTML et, par conséquent, ne verront pas les images en tant que contenu sur la page.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-145">Search engine crawlers only read the HTML and therefore will not see the images as content on the page.</span></span> <span data-ttu-id="9e7fa-146">Les images sont l’un des facteurs utilisés pour classer les pages dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-146">Images are one of the factors used to rank pages in search results.</span></span> <span data-ttu-id="9e7fa-147">Pour contourner ce processus, vous pouvez utiliser un texte d’introduction pour vos images.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-147">One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="9e7fa-148">Exemple de code GitHub: injection de code JavaScript pour améliorer les performances</span><span class="sxs-lookup"><span data-stu-id="9e7fa-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="9e7fa-149">Ne manquez pas l’article et l’exemple de code sur l' [injection JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) fournis sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9e7fa-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="9e7fa-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e7fa-150">See also</span></span>

[<span data-ttu-id="9e7fa-151">Navigateurs pris en charge dans Office 2013 et Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="9e7fa-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="9e7fa-152">Comment appliquer une page maître à un site dans SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e7fa-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="9e7fa-153">Procédure : Créer une mise en page dans SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e7fa-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

