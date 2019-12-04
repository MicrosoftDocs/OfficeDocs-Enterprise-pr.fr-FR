---
title: Optimiser les IFrames dans les pages de sites de publication modernes et classiques SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Découvrez comment optimiser les performances des IFrames dans les pages de sites de publication modernes et classiques SharePoint Online.
ms.openlocfilehash: f4b28ad9e59e41ddb8a4b96b532a49811e722874
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814232"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optimiser les IFrames dans les pages de sites de publication modernes et classiques SharePoint Online

Les IFrames peuvent s’avérer utiles pour afficher un aperçu d’un contenu riche, par exemple, des vidéos ou d’autres éléments multimédias. Toutefois, étant donné que les IFrames chargent une page distincte dans la page du site SharePoint, le contenu chargé dans l’IFrame peut contenir des images, des vidéos ou d’autres éléments volumineux pouvant contribuer au temps de chargement général de la page et que vous ne pouvez pas contrôler sur la page. Cet article vous permet de comprendre comment déterminer la façon dont les IFrames présentes dans vos pages affectent la latence perçue par l’utilisateur et comment résoudre les problèmes courants.

>[!NOTE]
>Pour plus d’informations sur les performances dans les sites modernes SharePoint Online, consultez [Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>Utiliser l’outil Diagnostic de page pour SharePoint pour analyser les composants WebPart utilisant les IFrames

L’outil **Diagnostic de page pour SharePoint** est une extension de navigateur pour Chrome et [Microsoft Edge version 77 ou ultérieure](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que vous pouvez utiliser pour analyser les pages de sites de publication modernes et classiques SharePoint. L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](page-diagnostics-for-spo.md).

Lorsque vous analysez une page de site SharePoint avec l’outil Diagnostic de page pour SharePoint, vous pouvez voir des informations sur les composants WebPart contenant des IFrames dans le volet _Tests de diagnostic_. La métrique de référence est identique pour les pages classiques et modernes.

Les résultats possibles sont les suivants :

- **Attention requise** (rouge) : la page contient **trois composants WebPart ou plus** utilisant des IFrames
- **Possibilités d’amélioration** (jaune) : la page contient **un ou deux** composants WebPart utilisant des IFrames
- **Aucune action requise** (vert) : la page ne contient pas de composants WebPart utilisant des IFrames

Si le résultat **Composants WebPart détectés utilisant des IFrames** apparaît dans la section des résultats **Possibilités d’amélioration** ou **Attention requise**, vous pouvez cliquer sur le résultat pour afficher les composants WebPart qui contiennent des IFrames.

![Résultats de l’outil Diagnostic de page](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>Résoudre les problèmes de performance liées aux IFrames

Utilisez le résultat **Composants WebPart détectés utilisant des IFrames** dans l’outil Diagnostic de page pour identifier les composants WebPart qui contiennent des IFrames et qui peuvent contribuer au chargement lent des pages.

les IFrames sont lents par nature, car ils chargent une page externe distincte incluant tout le contenu associé (par exemple, JavaScript, CSS et les éléments d’infrastructure), augmentant ainsi la surcharge de la page du site par un facteur de deux ou plus.

Suivez les instructions ci-dessous pour optimiser l’utilisation des IFrames.

- Dans la mesure du possible, utilisez des images au lieu d’IFrames si l’aperçu est initialement petit ou non interactif.
- Si vous devez utiliser des IFrames, réduisez-en le nombre et/ou éloignez-les de la fenêtre d’affichage.
- Les fichiers Office incorporés tels que Word, Excel et PowerPoint sont interactifs, mais leur chargement est lent. Les miniatures d’images contenant un lien vers le document complet fonctionnent souvent mieux.
- Les vidéos YouTube incorporées et les flux Twitter sont généralement plus performants dans des IFrames, mais utilisez judicieusement ce type d’éléments incorporés.
- Les composants WebPart isolés sont une exception raisonnable, mais réduisez leur nombre et leur insertion dans la fenêtre d’affichage.
- Si un IFrame est placé hors de la fenêtre d’affichage, songez à utiliser une fonction _IntersectionObserver_ pour retarder le rendu de l’IFrame jusqu’à ce qu’il s’affiche.

Avant d’apporter des révisions de page pour résoudre les problèmes de performances, notez le temps de chargement des pages dans les résultats de l’analyse. Exécutez à nouveau l’outil après votre révision pour déterminer si le nouveau résultat est inclus dans la norme de référence et vérifier le nouveau temps de chargement des pages pour voir s’il y a eu une amélioration.

![Résultats du temps de chargement des pages](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Le temps de chargement des pages peut varier en fonction de nombreux facteurs tels que la charge réseau, l’heure de la journée et d’autres conditions transitoires. Vous devez tester le temps de chargement des pages plusieurs fois avant et après avoir apporté des modifications pour vous aider à faire la moyenne des résultats.

## <a name="related-topics"></a>Voir aussi

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)
