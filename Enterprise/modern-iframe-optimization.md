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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Découvrez comment optimiser les performances des IFrames dans les pages de sites de publication modernes et classiques SharePoint Online.
ms.openlocfilehash: 4e6695b4afcf5e2f8dc7bd8ccee3d92bbea7e124
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031299"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="42c0e-103">Optimiser les IFrames dans les pages de sites de publication modernes et classiques SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="42c0e-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="42c0e-104">Les IFrames peuvent s’avérer utiles pour afficher un aperçu d’un contenu riche, par exemple, des vidéos ou d’autres éléments multimédias.</span><span class="sxs-lookup"><span data-stu-id="42c0e-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="42c0e-105">Toutefois, étant donné que les IFrames chargent une page distincte dans la page du site SharePoint, le contenu chargé dans l’IFrame peut contenir des images, des vidéos ou d’autres éléments volumineux pouvant contribuer au temps de chargement général de la page et que vous ne pouvez pas contrôler sur la page.</span><span class="sxs-lookup"><span data-stu-id="42c0e-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="42c0e-106">Cet article vous permet de comprendre comment déterminer la façon dont les IFrames présentes dans vos pages affectent la latence perçue par l’utilisateur et comment résoudre les problèmes courants.</span><span class="sxs-lookup"><span data-stu-id="42c0e-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="42c0e-107">Pour plus d’informations sur les performances dans les sites modernes SharePoint Online, consultez [Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="42c0e-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="42c0e-108">Utiliser l’outil Diagnostic de page pour SharePoint pour analyser les composants WebPart utilisant les IFrames</span><span class="sxs-lookup"><span data-stu-id="42c0e-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="42c0e-109">L’outil **Diagnostic de page pour SharePoint** est une extension de navigateur pour Chrome et [Microsoft Edge version 77 ou ultérieure](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que vous pouvez utiliser pour analyser les pages de sites de publication modernes et classiques SharePoint.</span><span class="sxs-lookup"><span data-stu-id="42c0e-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="42c0e-110">L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance.</span><span class="sxs-lookup"><span data-stu-id="42c0e-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="42c0e-111">Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="42c0e-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="42c0e-112">Lorsque vous analysez une page de site SharePoint avec l’outil Diagnostic de page pour SharePoint, vous pouvez voir des informations sur les composants WebPart contenant des IFrames dans le volet _Tests de diagnostic_.</span><span class="sxs-lookup"><span data-stu-id="42c0e-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="42c0e-113">La métrique de référence est identique pour les pages classiques et modernes.</span><span class="sxs-lookup"><span data-stu-id="42c0e-113">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="42c0e-114">Les résultats possibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="42c0e-114">Possible results include:</span></span>

- <span data-ttu-id="42c0e-115">**Attention requise** (rouge) : la page contient **trois composants WebPart ou plus** utilisant des IFrames</span><span class="sxs-lookup"><span data-stu-id="42c0e-115">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="42c0e-116">**Possibilités d’amélioration** (jaune) : la page contient **un ou deux** composants WebPart utilisant des IFrames</span><span class="sxs-lookup"><span data-stu-id="42c0e-116">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="42c0e-117">**Aucune action requise** (vert) : la page ne contient pas de composants WebPart utilisant des IFrames</span><span class="sxs-lookup"><span data-stu-id="42c0e-117">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="42c0e-118">Si le résultat **Composants WebPart détectés utilisant des IFrames** apparaît dans la section des résultats **Possibilités d’amélioration** ou **Attention requise**, vous pouvez cliquer sur le résultat pour afficher les composants WebPart qui contiennent des IFrames.</span><span class="sxs-lookup"><span data-stu-id="42c0e-118">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![Résultats de l’outil Diagnostic de page](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="42c0e-120">Résoudre les problèmes de performance liées aux IFrames</span><span class="sxs-lookup"><span data-stu-id="42c0e-120">Remediate iFrame performance issues</span></span>

<span data-ttu-id="42c0e-121">Utilisez le résultat **Composants WebPart détectés utilisant des IFrames** dans l’outil Diagnostic de page pour identifier les composants WebPart qui contiennent des IFrames et qui peuvent contribuer au chargement lent des pages.</span><span class="sxs-lookup"><span data-stu-id="42c0e-121">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="42c0e-122">les IFrames sont lents par nature, car ils chargent une page externe distincte incluant tout le contenu associé (par exemple, JavaScript, CSS et les éléments d’infrastructure), augmentant ainsi la surcharge de la page du site par un facteur de deux ou plus.</span><span class="sxs-lookup"><span data-stu-id="42c0e-122">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="42c0e-123">Suivez les instructions ci-dessous pour optimiser l’utilisation des IFrames.</span><span class="sxs-lookup"><span data-stu-id="42c0e-123">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="42c0e-124">Dans la mesure du possible, utilisez des images au lieu d’IFrames si l’aperçu est initialement petit ou non interactif.</span><span class="sxs-lookup"><span data-stu-id="42c0e-124">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="42c0e-125">Si vous devez utiliser des IFrames, réduisez-en le nombre et/ou éloignez-les de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="42c0e-125">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="42c0e-126">Les fichiers Office incorporés tels que Word, Excel et PowerPoint sont interactifs, mais leur chargement est lent.</span><span class="sxs-lookup"><span data-stu-id="42c0e-126">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="42c0e-127">Les miniatures d’images contenant un lien vers le document complet fonctionnent souvent mieux.</span><span class="sxs-lookup"><span data-stu-id="42c0e-127">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="42c0e-128">Les vidéos YouTube incorporées et les flux Twitter sont généralement plus performants dans des IFrames, mais utilisez judicieusement ce type d’éléments incorporés.</span><span class="sxs-lookup"><span data-stu-id="42c0e-128">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="42c0e-129">Les composants WebPart isolés sont une exception raisonnable, mais réduisez leur nombre et leur insertion dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="42c0e-129">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="42c0e-130">Si un IFrame est placé hors de la fenêtre d’affichage, songez à utiliser une fonction _IntersectionObserver_ pour retarder le rendu de l’IFrame jusqu’à ce qu’il s’affiche.</span><span class="sxs-lookup"><span data-stu-id="42c0e-130">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="42c0e-131">Avant d’apporter des révisions de page pour résoudre les problèmes de performances, notez le temps de chargement des pages dans les résultats de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="42c0e-131">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="42c0e-132">Exécutez à nouveau l’outil après votre révision pour déterminer si le nouveau résultat est inclus dans la norme de référence et vérifier le nouveau temps de chargement des pages pour voir s’il y a eu une amélioration.</span><span class="sxs-lookup"><span data-stu-id="42c0e-132">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Résultats du temps de chargement des pages](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="42c0e-134">Le temps de chargement des pages peut varier en fonction de nombreux facteurs tels que la charge réseau, l’heure de la journée et d’autres conditions transitoires.</span><span class="sxs-lookup"><span data-stu-id="42c0e-134">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="42c0e-135">Vous devez tester le temps de chargement des pages plusieurs fois avant et après avoir apporté des modifications pour vous aider à faire la moyenne des résultats.</span><span class="sxs-lookup"><span data-stu-id="42c0e-135">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="42c0e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42c0e-136">Related topics</span></span>

[<span data-ttu-id="42c0e-137">Optimisation des performances SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="42c0e-137">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="42c0e-138">Optimisation des performances Office 365</span><span class="sxs-lookup"><span data-stu-id="42c0e-138">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="42c0e-139">Performances offertes par l’expérience moderne de SharePoint</span><span class="sxs-lookup"><span data-stu-id="42c0e-139">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)
