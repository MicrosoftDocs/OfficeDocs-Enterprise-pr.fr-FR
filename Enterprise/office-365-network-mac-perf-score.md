---
title: Évaluation du réseau Office 365 (préversion)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Évaluation du réseau Office 365 (préversion)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106304"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="9ecf6-103">Évaluation du réseau Office 365 (préversion)</span><span class="sxs-lookup"><span data-stu-id="9ecf6-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="9ecf6-104">L’évaluation du réseau Office 365 indique l’impact de l’expérience utilisateur relative à partir de la connectivité du réseau client.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="9ecf6-105">L’impact de toute connectivité réseau appartenant à Microsoft est exclu de cette façon pour permettre aux clients d’optimiser les conceptions réseau dont ils sont responsables.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="9ecf6-106">Elle est calculée à partir de mesures qui influent sur l’expérience utilisateur dans les charges de travail Office 365 principales et affichées sous la forme d’un pourcentage d’une plage comprise entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="9ecf6-107">Un score réseau très faible suggère que les clients Office 365 auront des problèmes importants de connexion ou de réactivité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="9ecf6-108">Un score de 80% représente une connectivité réseau où vous ne devriez pas vous attendre à recevoir des plaintes des utilisateurs concernant votre expérience utilisateur Office 365 en raison des performances de votre réseau.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="9ecf6-109">À mesure que les améliorations de connectivité réseau sont apportées, ce score augmentera en même temps que l’expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9ecf6-110">Les recommandations en matière de performances réseau, les informations et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="9ecf6-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9ecf6-111">Exchange Online</span></span>

<span data-ttu-id="9ecf6-112">Pour Exchange Online, la latence TCP entre l’ordinateur client et le serveur frontal Exchange est mesurée.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="9ecf6-113">Cela peut être influencé par la distance que le réseau traverse sur le réseau local et le réseau étendu du client.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="9ecf6-114">Elle peut également être affectée par les appareils ou services intermédiaires réseau qui retardent la connectivité ou provoquent le renvoi des paquets.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="9ecf6-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9ecf6-115">SharePoint Online</span></span>

<span data-ttu-id="9ecf6-116">Pour SharePoint Online, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document est mesurée.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="9ecf6-117">Cela peut être influencé par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="9ecf6-118">Il est également souvent influencé par la congestion du réseau qui se trouve dans des périphériques réseau complexes ou dans des zones de non-fidélité de mauvaise qualité.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="9ecf6-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9ecf6-119">Microsoft Teams</span></span>

<span data-ttu-id="9ecf6-120">Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="9ecf6-121">UDP est utilisé pour la connectivité audio et vidéo d’appel et de conférence pour Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="9ecf6-122">Cela peut être influencé par les mêmes facteurs que pour la latence et la vitesse de téléchargement en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau étant donné que le protocole UDP est configuré séparément pour le protocole TCP le plus courant.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="9ecf6-123">Score réseau du client et score réseau de l’emplacement du Bureau</span><span class="sxs-lookup"><span data-stu-id="9ecf6-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="9ecf6-124">Un score réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="9ecf6-125">Les améliorations apportées au périmètre réseau sont les meilleures à chaque emplacement de bureau, ou lorsque la connectivité réseau est agrégée, il peut y avoir des améliorations qui ont un impact sur plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="9ecf6-126">Nous affichons un score réseau pour l’ensemble du client Office 365 sur la page de vue d’ensemble des performances réseau et un score réseau spécifique pour chaque emplacement de bureau détecté sur la page de résumé de cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="9ecf6-127">Panneau de score réseau</span><span class="sxs-lookup"><span data-stu-id="9ecf6-127">Network score panel</span></span>

<span data-ttu-id="9ecf6-128">Chaque score réseau indique si le client ou un emplacement de bureau spécifique affiche un panneau avec des détails sur le score.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="9ecf6-129">Ce panneau affiche un graphique à barres du score à la fois sous forme de pourcentage et de total pour chaque charge de travail de composant, y compris les charges de travail où les données de mesure ont été reçues.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="9ecf6-130">Pour un score réseau d’un emplacement de bureau, nous affichons également un test qui est la médiane de tous les clients Office 365 qui ont signalé des données dans la même ville que votre emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="9ecf6-131">La décomposition du score dans le panneau indique le score de chacune des charges de travail des composants.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="9ecf6-132">L’historique des scores indique les 30 derniers jours de la note et le benchmark.</span><span class="sxs-lookup"><span data-stu-id="9ecf6-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9ecf6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ecf6-133">Related topics</span></span>

[<span data-ttu-id="9ecf6-134">Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="9ecf6-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="9ecf6-135">Informations sur les performances du réseau Office 365 (aperçu)</span><span class="sxs-lookup"><span data-stu-id="9ecf6-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="9ecf6-136">Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="9ecf6-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
