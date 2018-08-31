---
title: Minimisation et regroupement dans SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Cet article décrit comment utiliser la réduction et les techniques de Web Essentials pour réduire le nombre de demandes HTTP et de réduire le temps que nécessaire pour charger des pages dans SharePoint Online.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540311"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="c6ad6-103">Minimisation et regroupement dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c6ad6-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="c6ad6-104">Cet article décrit comment utiliser la réduction et les techniques de Web Essentials pour réduire le nombre de demandes HTTP et de réduire le temps que nécessaire pour charger des pages dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="c6ad6-p101">Lorsque vous personnalisez votre site web, vous pouvez finir par devoir ajouter un grand nombre de fichiers supplémentaires sur le serveur pour prendre en charge la personnalisation. Le fait d’ajouter des fichiers JavaScript, des fichiers CSS et des images supplémentaires entraîne l’augmentation du nombre de requêtes HTTP envoyées au serveur, ce qui augmente par conséquent le temps nécessaire pour afficher une page web. Si vous disposez de plusieurs fichiers du même type, vous pouvez regrouper ces fichiers pour accélérer leur téléchargement.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="c6ad6-108">Pour les fichiers CSS et JavaScript, vous pouvez également utiliser une approche appelée réduction, où vous réduisez la taille totale des fichiers en supprimant les espaces blancs et autres caractères qui ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="c6ad6-109">Minimisation et regroupement de fichiers JavaScript et CSS avec Web Essentials</span><span class="sxs-lookup"><span data-stu-id="c6ad6-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="c6ad6-110">Vous pouvez utiliser un logiciel tiers, tel que Web Essentials pour regrouper les fichiers CSS et JavaScript.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="c6ad6-p102">Web Essentials est un projet de fournisseur tiers, open source, en fonction de la Communauté. Le logiciel est une extension de Visual Studio 2012 et Visual Studio 2013 et n’est pas pris en charge par Microsoft. Pour télécharger Web Essentials, visitez le site Web à [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="c6ad6-114">Web Essentials offre deux types de regroupement :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="c6ad6-115">.bundle : pour les fichiers CSS et JavaScript</span><span class="sxs-lookup"><span data-stu-id="c6ad6-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="c6ad6-116">.sprite : pour les images (uniquement disponible dans Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="c6ad6-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="c6ad6-117">Vous pouvez utiliser Web Essentials si vous disposez d’une fonctionnalité existante avec quelques éléments de personnalisation référencés dans une page maître personnalisée, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Capture d’écran de l’élément de marque sur la page maître personnalisée](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="c6ad6-119">**Pour créer un groupement TE000127218 et CSS dans Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="c6ad6-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="c6ad6-120">Dans Visual Studio, dans l’explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le regroupement.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="c6ad6-p103">Avec le bouton droit de la sélection de fichiers, puis sélectionnez **Web Essentials** \> **fichier JavaScript créer** dans le menu contextuel. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Capture d’écran montrant les options de menu Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="c6ad6-124">Affichage des résultats de regroupement des fichiers JavaScript et CSS</span><span class="sxs-lookup"><span data-stu-id="c6ad6-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="c6ad6-125">Lorsque vous créez un regroupement CSS et JavaScript, Web Essentials crée un fichier XML appelé fichier de recette qui identifie les fichiers JavaScript et CSS, ainsi que d’autres informations de configuration :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Capture d’écran du fichier de recette CSS et JavaScript](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="c6ad6-p104">En outre, si l’indicateur minify est défini sur true dans le fichier de recette de regroupement, la taille des fichiers est réduite et les fichiers sont regroupés. Les nouvelles versions minimisées des fichiers JavaScript sont alors créées et vous pouvez les référencer dans votre page maître.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Capture d’écran de l’indicateur minify défini sur True](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="c6ad6-130">Lorsque vous chargez une page à partir de votre site web, vous pouvez utiliser les outils de développement de votre navigateur web, comme Internet Explorer 11, pour voir le nombre de demandes envoyées au serveur et la durée de chargement de chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="c6ad6-131">L’illustration suivante présente le résultat du chargement des fichiers JavaScript et CSS avant minimisation.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Capture d’écran montrant 80 éléments en cours de téléchargement](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="c6ad6-133">Après avoir regroupé les fichiers CSS et JavaScript, le nombre de demandes a chuté à 74 et le téléchargement de chaque fichier n’a pris qu’un tout petit peu plus de temps que pour les fichiers d’origine, individuellement :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Capture d’écran montrant 74 éléments en cours de téléchargement](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="c6ad6-135">Une fois le regroupement effectué, la taille du fichier de regroupement JavaScript a été sensiblement réduite, passant de 815 ko à 365 ko :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Capture d’écran montrant une taille de téléchargement réduite](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="c6ad6-137">Regroupement d’images par la création d’une image-objet</span><span class="sxs-lookup"><span data-stu-id="c6ad6-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="c6ad6-p105">Semblable à la façon dont vous regroupez les fichiers CSS et JavaScript, vous pouvez combiner des nombreuses petites icônes et autres images courantes dans une feuille sprite plus grande, puis utiliser CSS pour afficher les images individuelles. Au lieu de télécharger chaque image, navigateur web de l’utilisateur télécharge la feuille sprite qu’une seule fois et il met en cache sur l’ordinateur local. Cela améliore les performances de chargement de page en réduisant le nombre de téléchargements et des allers-retours vers le serveur web.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="c6ad6-141">**Création d’une image-objet d’images dans Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="c6ad6-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="c6ad6-142">Dans Visual Studio, dans l’explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le regroupement.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="c6ad6-p106">Avec le bouton droit de la sélection de fichiers, puis sélectionnez **Web Essentials** \> **sprite d’image créer** dans le menu contextuel. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![Capture d’écran montrant comment créer une image-objet](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="c6ad6-p107">Choisissez un emplacement pour enregistrer le fichier d’image-objet. Le fichier .sprite est un fichier XML qui décrit les paramètres et les fichiers de l’image-objet. Les illustrations suivantes présentent l’exemple d’un fichier d’image-objet PNG et son fichier XML .sprite correspondant.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Capture d’écran d’un fichier d’image-objet](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Capture d’écran d’un fichier XML d’image-objet](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

