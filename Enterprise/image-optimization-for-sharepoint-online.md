---
title: Optimisation des images pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Découvrez comment utiliser les formats et sprites pour améliorer les performances d’image sur vos sites Web SharePoint Online.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540346"
---
# <a name="image-optimization-for-sharepoint-online"></a>Optimisation des images pour SharePoint Online

La vitesse de chargement d’une page Web dépend de la taille combinée de tous les composants requis pour afficher la page, y compris les images, HTML, JavaScript et CSS. Les images sont idéal pour rendre votre site plus attrayant, mais leur taille peut affecter les performances. En optimisant vos images avec la compression de redimensionnement et l’utilisation de sprites, vous pouvez décaler les effets des images de très grande taille. À l’aide d’images SharePoint, vous pouvez télécharger une seule grande image et afficher des sections de l’image, ce qui lui permet d’être réutilisé plutôt que rechargé.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Utilisation d’images-objets pour accélérer le chargement d’images dans SharePoint Online

|||
|:-----|:-----|
| Un sprite image contient plusieurs images plus petites. À l’aide de CSS sélectionnez une partie de l’image composite à afficher sur un composant particulier de la page avec le positionnement absolu. En fait, vous déplacez une image autour de la page au lieu de chargement de plusieurs images et afficher une petite partie de cette image dans une fenêtre de petite taille où la partie de l’image sprite est affichée à l’utilisateur final. SharePoint Online utilise sprites pour afficher ses diverses icônes dans le spcommon.png sprite.  <br/>  Ce qui est traité ici :  <br/>  Compression d’image  <br/>  Optimisation des images  <br/>  Images SharePoint  <br/> |![Capture d’écran de spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Cela peut accroître les performances car vous téléchargez uniquement une image au lieu de plusieurs et puis mettre en cache et réutilisez cette image. Même si l’image n’est pas mis en cache, organisez une image au lieu de plusieurs images, cette méthode réduit le nombre total de demandes HTTP vers le serveur qui permet de réduire le temps de chargement de page. Il s’agit vraiment d’un formulaire de regroupement de l’image. Il s’agit très utile si les images ne changeant pas très souvent, par exemple, des icônes, comme illustré dans l’exemple ci-dessus SharePoint. Vous pouvez l’utilisation [Web Essentials](http://vswebessentials.com/), un projet de fournisseur tiers, open source, en fonction de la Communauté pour y parvenir facilement dans Microsoft Visual Studio. Pour plus d’informations, voir [réduction et regroupement dans SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Utilisation de l’optimisation et de la compression d’images pour accélérer le chargement de pages dans SharePoint

L’optimisation et la compression d’images consistent à réduire la taille des fichiers images que vous utilisez sur votre site. Bien souvent, la meilleure façon de réduire la taille d’une image est de l’ajuster aux dimensions maximales auxquelles elle sera affichée sur le site. Il est inutile de conserver les dimensions d’une image si elle ne sera affichée que dans des proportions inférieures. Pour réduire facilement et rapidement la taille de votre page, assurez-vous que les dimensions des images sont correctes à l’aide d’un éditeur d’images.
  
Une fois que les images sont la taille, l’étape suivante consiste à optimiser la compression de ces images. Il existe différents outils à utiliser pour la compression et optimisation, y compris la galerie de photos et des outils tiers. La clé sur compression consiste à réduire la taille du fichier autant que possible sans perte de la qualité visible pour les utilisateurs finaux. Veillez à que tester vos fichiers compressés sur un affichage haute définition pour s’assurer qu’ils seront toujours regarder la bonne.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Accélération du téléchargement des pages à l’aide des rendus d’image SharePoint

Rendus d’image sont une fonctionnalité dans SharePoint Online qui permet de traiter les différentes versions d’images basées sur les dimensions de l’image prédéfinies. Ceci est particulièrement important lors du contenu image générés par l’utilisateur ou les dimensions de l’image tels que la largeur et hauteur sont résolues par la CSS sur le site. Même si une image est résolue en CSS, l’image de la solution complète est encore chargée. Dans ce cas, la taille du fichier peut être réduite à l’aide de rendus d’image.
  
> [!NOTE]
> Formats associés sont disponibles pour SharePoint uniquement lorsque la publication est activée. Vous pouvez activer la publication sous paramètres \> paramètres du Site \> gérer les fonctionnalités des sites \> publication Office SharePoint Server. L’option n’apparaît pas dans le cas contraire. 
  
Le redimensionnement par rendu d’image fonctionne comme suit : à partir de la plus petite dimension que vous définissez (largeur ou hauteur), l’autre dimension est automatiquement redimensionnée selon les proportions verrouillées. Par défaut, l’image sera rognée à partir du centre selon les dimensions restantes. Par exemple, si vous définissez un rendu de 100 px de large et de 50 px de haut et que l’image d’origine fait 1 000 px de large et 800 px de haut, elle sera redimensionnée de sorte que la dimension à 800 px soit réduite à 50 px et que la dimension à 1 000 px atteigne les 62,5 px par rognage à partir du centre de l’image.
  
Les étapes sont relativement simples, mais pour que vous puissiez utiliser les rendus sur les images, les rendus doivent se trouver sur le site SharePoint avant que vous ajoutiez les images. En outre, les fonctionnalités d’infrastructure de publication de SharePoint Server (au niveau de la collection de sites) et de publication de SharePoint Server (au niveau du site) doivent être activées.
  
 **Ajouter un rendu d’image pour accélérer le chargement de la page**
  
1. Vérifiez que le compte d’utilisateur qui exécute cette procédure, au minimum, les autorisations de conception pour le site de niveau supérieur de la collection de sites, et que le site est en cours de publication vers une page Web.
    
2. Dans un navigateur web, accédez au site de niveau supérieur de la collection de sites de publication.
    
3. Cliquez sur l’icône **Paramètres**. 
    
4. Sur la page **Paramètres du site**, dans la section **Aspect**, vous verrez les rendus d’image intégrés. 
    
    Vous pouvez utiliser les rendus standard ou choisir **Rendus d’image** pour en créer un. 
    
    ![Capture d’écran de rendu d’Image](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Sur la page **Rendus d’image**, sélectionnez **Ajouter un nouvel élément**.
    
    ![Capture d’écran de l’option Ajouter un nouvel élément](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Sur la page **Nouveau rendu d’image**, dans la zone **Nom**, saisissez le nom du rendu. 
    
7. Dans les zones de texte **Largeur** et **Hauteur**, entrez la largeur et la hauteur, en pixels, du rendu, puis cliquez sur **Enregistrer**.
    
    ![Capture d’écran du nom de rendu d’image](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Rognage personnalisé avec les rendus d’image dans SharePoint

Par défaut, un rendu d’image est généré à partir du centre de l’image. Vous pouvez régler le rendu d’image pour des images individuelles par les rogner la partie de l’image que vous souhaitez utiliser. Vous pouvez rogner les images individuellement, par le rendu. Rognage les images accélère la page chargement en utilisant le cache blob de SharePoint pour créer une version de l’image pour chaque format associé. Ainsi, la charge du serveur est réduite, car l’image est redimensionnée uniquement une seule fois et est prêt à répondre aux utilisateurs finaux plusieurs fois. Pour plus d’informations sur la façon de rogner un rendu d’image, voir [Rogner un rendu d’image](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

