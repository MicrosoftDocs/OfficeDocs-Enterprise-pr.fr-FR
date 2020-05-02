---
title: Minimisation et regroupement dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Cet article explique comment utiliser les techniques de minimisation et de regroupement avec Web Essentials pour réduire le nombre de requêtes HTTP et réduire le temps nécessaire au chargement des pages dans SharePoint Online.
ms.openlocfilehash: 44f9e6151c22c3715b56a164bd0c9cacedcf2580
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004769"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minimisation et regroupement dans SharePoint Online

Cet article explique comment utiliser les techniques de minimisation et de regroupement avec Web Essentials pour réduire le nombre de requêtes HTTP et réduire le temps nécessaire au chargement des pages dans SharePoint Online.
  
Lorsque vous personnalisez votre site Web, vous pouvez ajouter un grand nombre de fichiers supplémentaires au serveur afin de prendre en charge la personnalisation. L’ajout de code JavaScript, CSS et images supplémentaires augmente le nombre de requêtes HTTP vers le serveur, ce qui augmente en retour le temps nécessaire à l’affichage d’une page Web. Si vous avez plusieurs fichiers du même type, vous pouvez regrouper ces fichiers pour faciliter le téléchargement de ces fichiers.
  
Pour les fichiers JavaScript et CSS, vous pouvez également utiliser une approche appelée minimisation, dans laquelle vous réduisez la taille totale des fichiers en supprimant les espaces et autres caractères qui ne sont pas nécessaires.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minimisation et regroupement des fichiers JavaScript et CSS avec Web Essentials

Vous pouvez utiliser des logiciels tiers tels que Web Essentials pour regrouper les fichiers CSS et JavaScript.
  
> [!IMPORTANT]
> Web Essentials est un projet de communauté ouverte, basé sur une source tierce. Le logiciel est une extension de Visual Studio 2012 et Visual Studio 2013 et n’est pas pris en charge par Microsoft. Pour télécharger Web Essentials, visitez le site Web à [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)l’adresse. 
  
Web Essentials offre deux types de groupage :
  
- . Bundle : pour les fichiers CSS et JavaScript
    
- . Sprite : pour les images (uniquement disponible dans Visual Studio 2013)
    
Vous pouvez utiliser Web Essentials si vous disposez d’une fonctionnalité existante avec certains éléments de personnalisation qui sont référencés dans une page maître personnalisée, par exemple :
  
![Capture d’écran de l’élément de marque sur la page maître personnalisée](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Pour créer un groupement TE000127218 et CSS dans Web Essentials**
  
1. Dans Visual Studio, dans l’Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le fichier groupé.
    
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** \> **créer un fichier de package JavaScript** dans le menu contextuel. Par exemple : 
    
    ![Capture d’écran montrant les options de menu Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Affichage des résultats du regroupement de fichiers JavaScript et CSS

Lorsque vous créez un groupement JavaScript et CSS, Web Essentials crée un fichier XML appelé « fichier de recette » qui identifie les fichiers JavaScript et CSS, ainsi que d’autres informations de configuration : 
  
![Capture d’écran du fichier de recette CSS et JavaScript](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
En outre, si l’indicateur réduire est défini sur true dans la recette de regroupement, les fichiers sont réduits et regroupés. Cela signifie que de nouvelles versions réduites des fichiers JavaScript ont été créées et que vous pouvez référencer dans votre page maître.
  
![Capture d’écran de l’indicateur minify défini sur True](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Lorsque vous chargez une page à partir de votre site Web, vous pouvez utiliser les outils de développement de votre navigateur Web, tels qu’Internet Explorer 11, pour afficher le nombre de demandes envoyées au serveur et la durée de chargement de chaque fichier.
  
L’illustration suivante est le résultat du chargement des fichiers JavaScript et CSS avant la minimisation.
  
![Capture d’écran montrant 80 éléments en cours de téléchargement](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Après avoir groupé les fichiers CSS et JavaScript ensemble, le nombre de requêtes déposées vers 74 et chaque fichier prenait seulement légèrement plus longtemps que les fichiers d’origine à télécharger individuellement :
  
![Capture d’écran montrant 74 éléments en cours de téléchargement](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Après le regroupement, le fichier de package JavaScript est considérablement réduit de 815KB à 365KB :
  
![Capture d’écran montrant une taille de téléchargement réduite](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Regroupement d’images en créant un sprite d’image

De la même manière que vous regroupez les fichiers JavaScript et CSS, vous pouvez combiner de nombreuses petites icônes et d’autres images courantes dans une feuille de plus grande taille, puis utiliser CSS pour afficher les images individuelles. Au lieu de télécharger chaque image individuelle, le navigateur Web de l’utilisateur télécharge la feuille de sprite une fois, puis la met en cache sur l’ordinateur local. Cela améliore les performances de chargement des pages en réduisant le nombre de téléchargements et d’allers-retours vers le serveur Web.
  
 **Pour créer un sprite image dans Web Essentials**
  
1. Dans Visual Studio, dans l’Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le fichier groupé.
    
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** \> **créer une image sprite** dans le menu contextuel. Par exemple : 
    
    ![Capture d’écran montrant comment créer une image-objet](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Choisissez un emplacement pour enregistrer le fichier Sprite. Le fichier. Sprite est un fichier XML qui décrit les paramètres et les fichiers du sprite. Les figures suivantes illustrent un exemple de fichier PNG Sprite et son fichier XML. Sprite correspondant.
    
    ![Capture d’écran d’un fichier d’image-objet](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Capture d’écran d’un fichier XML d’image-objet](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

