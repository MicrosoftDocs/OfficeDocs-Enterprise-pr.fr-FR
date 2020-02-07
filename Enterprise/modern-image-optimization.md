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
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Découvrez comment optimiser les images dans les pages de sites modernes SharePoint Online.
ms.openlocfilehash: b1bb8bab7ee9d5f0972a476e37c35e8c14748bfb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843745"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="36d86-103">Optimiser les images dans les pages de sites modernes SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36d86-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="36d86-104">Cet article vous aidera à comprendre comment optimiser les images dans les pages de sites modernes SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36d86-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="36d86-105">Pour plus d’informations sur l’optimisation des images dans les sites de publication classiques, consultez [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="36d86-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="36d86-106">Pour plus d’informations sur les performances dans les portails modernes SharePoint Online, consultez [Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="36d86-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="36d86-107">Utiliser l’outil Diagnostic de page pour SharePoint pour analyser l’optimisation des images</span><span class="sxs-lookup"><span data-stu-id="36d86-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="36d86-108">L’outil **Diagnostic de page pour SharePoint** est une extension de navigateur pour Chrome et [Microsoft Edge version 77 ou ultérieure](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que vous pouvez utiliser pour analyser les pages de sites de publication modernes et classiques SharePoint.</span><span class="sxs-lookup"><span data-stu-id="36d86-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="36d86-109">L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance.</span><span class="sxs-lookup"><span data-stu-id="36d86-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="36d86-110">Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="36d86-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="36d86-111">Lorsque vous analysez une page de site moderne SharePoint avec l’outil Diagnostic de page pour SharePoint, vous pouvez voir des informations sur les images de grande taille dans le volet Tests de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="36d86-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="36d86-112">Les résultats possibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="36d86-112">Possible results include:</span></span>

- <span data-ttu-id="36d86-113">**Attention requise** (rouge) : la page contient **une ou plusieurs** images dont la taille est supérieure à 300 Ko</span><span class="sxs-lookup"><span data-stu-id="36d86-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="36d86-114">**Aucune action requise** (vert) : la page ne contient pas d’images dont la taille est supérieure à 300 Ko</span><span class="sxs-lookup"><span data-stu-id="36d86-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="36d86-115">Si le résultat **Images de grande taille détectées** apparaît dans la section des résultats **Attention requise**, vous pouvez cliquer sur le résultat pour afficher les détails supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="36d86-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Résultats de l’outil Diagnostic de page](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="36d86-117">Résoudre les problèmes liés aux images de grande taille</span><span class="sxs-lookup"><span data-stu-id="36d86-117">Remediate large image issues</span></span>

<span data-ttu-id="36d86-118">Si une page contient des images dont la taille est supérieure à 300 Ko, sélectionnez le résultat **Images de grande taille détectées** pour voir les images trop volumineuses.</span><span class="sxs-lookup"><span data-stu-id="36d86-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="36d86-119">Dans les pages modernes SharePoint Online, les rendus d’images sont automatiquement fournis et dimensionnés en fonction de la taille de la fenêtre du navigateur et de la résolution du moniteur client.</span><span class="sxs-lookup"><span data-stu-id="36d86-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="36d86-120">Vous devez toujours optimiser les images pour une utilisation sur le Web avant de les télécharger sur SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36d86-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="36d86-121">Les images de très grand taille sont automatiquement réduites en taille et en résolution, ce qui peut entraîner des caractéristiques de rendu inattendues.</span><span class="sxs-lookup"><span data-stu-id="36d86-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="36d86-122">Avant d’apporter des révisions de page pour résoudre les problèmes de performances, notez le temps de chargement des pages dans les résultats de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="36d86-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="36d86-123">Exécutez à nouveau l’outil après votre révision pour déterminer si le nouveau résultat est inclus dans la norme de référence et vérifier le nouveau temps de chargement des pages pour voir s’il y a eu une amélioration.</span><span class="sxs-lookup"><span data-stu-id="36d86-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Résultats du temps de chargement des pages](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="36d86-125">Le temps de chargement des pages peut varier en fonction de nombreux facteurs tels que la charge réseau, l’heure de la journée et d’autres conditions transitoires.</span><span class="sxs-lookup"><span data-stu-id="36d86-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="36d86-126">Vous devez tester le temps de chargement des pages plusieurs fois avant et après avoir apporté des modifications pour vous aider à faire la moyenne des résultats.</span><span class="sxs-lookup"><span data-stu-id="36d86-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="36d86-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36d86-127">Related topics</span></span>

[<span data-ttu-id="36d86-128">Optimisation des performances SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36d86-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="36d86-129">Optimisation des performances Office 365</span><span class="sxs-lookup"><span data-stu-id="36d86-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="36d86-130">Performances offertes par l’expérience moderne de SharePoint</span><span class="sxs-lookup"><span data-stu-id="36d86-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="36d86-131">Réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="36d86-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="36d86-132">Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36d86-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
