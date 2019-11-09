---
title: Optimisation des images pour les sites de publication classiques SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Découvrez comment utiliser des rendus et des sprites pour améliorer les performances de l’image sur vos sites de publication classiques SharePoint Online.
ms.openlocfilehash: a3dbfeaa238f8c12f8ecc3afaa3a45942d665599
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077617"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Optimisation des images pour les sites de publication classiques SharePoint Online

La vitesse de chargement d’une page Web dépend de la taille combinée de tous les composants nécessaires au rendu de la page, y compris les images, HTML, JavaScript et CSS. Les images constituent un excellent moyen de rendre votre site plus attrayant, mais leur taille peut affecter les performances. En optimisant vos images avec la compression et le redimensionnement, et en utilisant des sprites, vous pouvez décaler les effets des images très volumineuses. À l’aide des rendus d’image SharePoint, vous pouvez télécharger une seule image de grande taille et afficher les sections de l’image, ce qui permet de la réutiliser au lieu de la recharger.

>[!NOTE]
>Cette rubrique s’applique aux sites de publication classiques SharePoint Online, et non aux sites portail modernes. Pour plus d’informations sur l’optimisation des images dans les sites portail modernes SharePoint Online, consultez la rubrique [optimize images in SharePoint Online Modern Portal pages](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Utilisation des sprites pour accélérer le chargement de l’image

|||
|:-----|:-----|
| Une image sprite contient de nombreuses images plus petites. À l’aide de CSS, vous sélectionnez une partie de l’image composite à afficher sur une partie particulière de la page avec un positionnement absolu. En gros, vous déplacez une image unique sur la page au lieu de charger plusieurs images, et une petite partie de cette image est visible dans une petite fenêtre où la partie requise de l’image sprite s’affiche pour l’utilisateur final. SharePoint Online utilise des sprites pour afficher ses différentes icônes dans le sprite Sprite. png.  <br/>  Ce qui est abordé ici :  <br/>  Compression d’image  <br/>  Optimisation de l’image  <br/>  Rendus d’image SharePoint  <br/> |![Capture d’écran de common](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Cela peut augmenter les performances, car vous ne téléchargez qu’une image au lieu de plusieurs, puis mettez en cache et réutilisez cette image. Même si l’image ne reste pas mise en cache, avec une seule image au lieu de plusieurs images, cette méthode réduit le nombre total de demandes HTTP vers le serveur, ce qui réduira le temps de chargement de la page. Il s’agit d’une forme de regroupement d’images. Il s’agit d’une technique très utile si les images ne changent pas très souvent, par exemple, des icônes, comme illustré dans l’exemple de code SharePoint fourni ci-dessus. Vous pouvez utiliser [Web Essentials](https://vswebessentials.com/), un projet open source tiers, basé sur la communauté pour y parvenir facilement dans Microsoft Visual Studio. Pour plus d’informations, consultez la rubrique [Minimize and Grouping in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Utilisation de la compression et de l’optimisation des images pour accélérer le chargement des pages

La compression d’image et l’optimisation permettent de réduire la taille de fichier des images que vous utilisez sur votre site. Souvent, la meilleure technique pour réduire la taille d’une image est de redimensionner l’image en fonction des dimensions maximales qu’elle sera affichée sur le site. Il n’est pas judicieux d’avoir une image plus grande qu’elle ne sera jamais affichée. S’assurer que les images sont des dimensions correctes à l’aide d’un éditeur d’images est un moyen rapide et facile de réduire la taille de votre page.
  
Une fois que les images sont de la bonne taille, l’étape suivante consiste à optimiser la compression de ces images. Il existe différents outils à utiliser pour la compression et l’optimisation, y compris la Galerie de photos et les outils tiers. La clé de compression est de réduire autant que possible la taille du fichier sans perte de qualité perceptible pour les utilisateurs finaux. Assurez-vous de tester vos fichiers compressés sur un écran haute définition pour vous assurer qu’ils seront toujours en bonne qualité.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Accélérer les téléchargements de pages à l’aide de rendus d’image SharePoint

Les rendus d’image sont une fonctionnalité de SharePoint Online qui vous permet d’utiliser des versions différentes d’images basées sur des dimensions d’image prédéfinies. Cela est particulièrement important lorsqu’il existe un contenu d’image généré par l’utilisateur ou que les dimensions de l’image telles que la largeur et la hauteur sont fixées par la feuille de style CSS sur le site. Même si une image est résolue par CSS, l’image de résolution complète est toujours chargée. Dans ce cas, il est possible de réduire la taille du fichier à l’aide de rendus d’image.
  
> [!NOTE]
> Les rendus ne sont disponibles que pour SharePoint lorsque la publication est activée. Vous pouvez activer la publication sous \> paramètres de \> site paramètres de \> gestion des fonctionnalités de site SharePoint Server Publishing. L’option n’apparaît pas dans le cas contraire.
  
Le redimensionnement de rendu d’image fonctionne en prenant la plus petite dimension que vous définissez, la largeur ou la hauteur, puis le redimensionnement de l’image de manière à ce que l’autre dimension soit automatiquement redimensionnée en fonction des proportions verrouillées. Par défaut, l’image est rognée du centre par les autres dimensions. Par exemple, si vous définissez un rendu de 100px en largeur et en hauteur de 50 pixels et que votre image d’origine est 1000px large et 800px haute, elle est redimensionnée de sorte que la dimension 800px est maintenant de 50 px et que la dimension 1000px (maintenant 62,5 PX) est rognée du centre de l’image.
  
Les étapes sont relativement simples, mais pour les images pour utiliser les rendus, les rendus doivent se trouver sur le site SharePoint avant d’ajouter les images. De plus, vous devez également avoir activé les fonctionnalités d’infrastructure de publication SharePoint Server (niveau de collection de sites) et de publication SharePoint Server.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Ajouter un rendu d’image pour accélérer le chargement des pages
  
1. Vérifiez que le compte d’utilisateur qui exécute cette procédure dispose, au minimum, des autorisations de conception sur le site de niveau supérieur de la collection de sites, et que le site est en cours de publication dans une page Web.

2. Dans un navigateur Web, accédez au site de niveau supérieur de la collection de sites de publication.

3. Choisissez l'icône **Paramètres**.

4. Dans la page **paramètres du site** , dans la section **aspect** , vous verrez les rendus d’image intégrés.

    Vous pouvez utiliser les rendus de la zone ou choisir des **rendus d’image** pour en créer un nouveau.

    ![Capture d’écran du rendu d’image](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Sur la page **Rendus d’image**, sélectionnez **Ajouter un nouvel élément**.

    ![Capture d’écran de l’option Ajouter un nouvel élément](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Sur la page **Nouveau rendu d'Image**, dans la zone **Nom**, saisissez un nom pour le rendu.

7. Dans les zones de texte **Largeur** et **Hauteur**, saisissez la largeur et la hauteur, en pixels, du rendu voulu, puis choisissez **Enregistrer**.

    ![Capture d’écran du nom de rendu d’image](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Rognage personnalisé avec rendus d’image

Par défaut, un rendu d'image est généré à partir du centre de l'image. Vous pouvez régler le rendu d'image de chaque image en détourant la partie de l'image que vous souhaitez utiliser. Vous pouvez rogner les images de manière individuelle, par format associé. Le rognage des images accélère le chargement des pages à l’aide du cache BLOB de SharePoint pour créer une version de l’image pour chaque format associé. De cette façon, la charge du serveur est réduite, car l’image n’est redimensionnée qu’une seule fois et est prête à être utilisée plusieurs fois pour les utilisateurs finaux. Pour plus d’informations sur la façon de rogner un rendu d’image, voir [rogner un rendu d’image](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

