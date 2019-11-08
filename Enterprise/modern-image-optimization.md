---
title: Optimiser les images dans les pages de sites modernes SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Découvrez comment optimiser les images dans les pages de sites modernes SharePoint Online.
ms.openlocfilehash: dafa31f95babfe0389fd77bf4a25b5a346cf3474
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032269"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optimiser les images dans les pages de sites modernes SharePoint Online

Cet article vous aidera à comprendre comment optimiser les images dans les pages de sites modernes SharePoint Online.

Pour plus d’informations sur l’optimisation des images dans les sites de publication classiques, consultez [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Pour plus d’informations sur les performances dans les portails modernes SharePoint Online, consultez [Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Utiliser l’outil Diagnostic de page pour SharePoint pour analyser l’optimisation des images

L’outil **Diagnostic de page pour SharePoint** est une extension de navigateur pour Chrome et [Microsoft Edge version 77 ou ultérieure](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que vous pouvez utiliser pour analyser les pages de sites de publication modernes et classiques SharePoint. L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](page-diagnostics-for-spo.md).

Lorsque vous analysez une page de site moderne SharePoint avec l’outil Diagnostic de page pour SharePoint, vous pouvez voir des informations sur les images de grande taille dans le volet Tests de diagnostic.

Les résultats possibles sont les suivants :

- **Attention requise** (rouge) : la page contient **une ou plusieurs** images dont la taille est supérieure à 300 Ko
- **Aucune action requise** (vert) : la page ne contient pas d’images dont la taille est supérieure à 300 Ko

Si le résultat **Images de grande taille détectées** apparaît dans la section des résultats **Attention requise**, vous pouvez cliquer sur le résultat pour afficher les détails supplémentaires.

![Résultats de l’outil Diagnostic de page](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Résoudre les problèmes liés aux images de grande taille

Si une page contient des images dont la taille est supérieure à 300 Ko, sélectionnez le résultat **Images de grande taille détectées** pour voir les images trop volumineuses. Dans les pages modernes SharePoint Online, les rendus d’images sont automatiquement fournis et dimensionnés en fonction de la taille de la fenêtre du navigateur et de la résolution du moniteur client. Vous devez toujours optimiser les images pour une utilisation sur le Web avant de les télécharger sur SharePoint Online. Les images de très grand taille sont automatiquement réduites en taille et en résolution, ce qui peut entraîner des caractéristiques de rendu inattendues.

Avant d’apporter des révisions de page pour résoudre les problèmes de performances, notez le temps de chargement des pages dans les résultats de l’analyse. Exécutez à nouveau l’outil après votre révision pour déterminer si le nouveau résultat est inclus dans la norme de référence et vérifier le nouveau temps de chargement des pages pour voir s’il y a eu une amélioration.

![Résultats du temps de chargement des pages](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Le temps de chargement des pages peut varier en fonction de nombreux facteurs tels que la charge réseau, l’heure de la journée et d’autres conditions transitoires. Vous devez tester le temps de chargement des pages plusieurs fois avant et après avoir apporté des modifications pour vous aider à faire la moyenne des résultats.

## <a name="related-topics"></a>Voir aussi

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-office-365-cdn-with-spo.md)
