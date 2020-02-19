---
title: Informations sur les performances du réseau Office 365 (aperçu)
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
description: Informations sur les performances du réseau Office 365 (aperçu)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106311"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="6ac9d-103">Informations sur les performances du réseau Office 365 (aperçu)</span><span class="sxs-lookup"><span data-stu-id="6ac9d-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="6ac9d-104">Les pages des performances du réseau du centre d’administration Microsoft 365 montrent Office 365 Network Insights, qui peut vous aider à concevoir des périmètres réseau pour vos emplacements de bureau.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="6ac9d-105">Cinq analyses de réseau spécifiques peuvent être affichées pour chaque emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6ac9d-106">Les recommandations en matière de performances réseau, les informations et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="6ac9d-107">Sortie réseau retractée</span><span class="sxs-lookup"><span data-stu-id="6ac9d-107">Backhauled network egress</span></span>

<span data-ttu-id="6ac9d-108">La distance entre l’emplacement de l’utilisateur et la sortie réseau est supérieure à 500 milles (800 kilomètres) et cela devrait avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="6ac9d-109">Une sortie locale plus proche de l’utilisateur est recommandée.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="6ac9d-110">Cela indique que la distance entre l’emplacement du bureau et la sortie du réseau est supérieure à 500 kilomètres.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="6ac9d-111">L’emplacement du Bureau est identifié par un emplacement de l’ordinateur client masqué et l’emplacement de sortie du réseau est identifié à l’aide de l’adresse IP inverse pour les bases de données d’emplacement.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="6ac9d-112">L’emplacement du Bureau peut être inexact si les services d’emplacement Windows sont désactivés sur les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="6ac9d-113">L’emplacement de sortie réseau peut être inexact si les informations de la base de données d’adresses IP inversées sont inexactes.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="6ac9d-114">Les détails de cette analyse incluent l’emplacement du bureau, l’emplacement de sortie réseau et la distance entre eux.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="6ac9d-115">Pour cette vue, nous recommandons de passer un accès réseau plus près de l’emplacement du bureau afin que la connectivité puisse acheminer le réseau de manière optimale vers le réseau de Microsoft sur Internet et sur les portes frontales du service Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="6ac9d-116">Une sortie étroite du réseau vers les bureaux des utilisateurs permet également d’améliorer les performances à l’avenir à mesure que Microsoft étend à la fois les points de présence réseau et les portes frontales du service Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="6ac9d-117">Cette vue est abrégée en « sortie » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="6ac9d-118">Meilleures performances détectées pour les clients proches de vous</span><span class="sxs-lookup"><span data-stu-id="6ac9d-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="6ac9d-119">Dans la mesure où un nombre important de clients dans votre zone de métro offre de meilleures performances que les utilisateurs de votre organisation à cet emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="6ac9d-120">Cela examine les performances totales des clients Office 365 dans la même ville que cet emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Performances réseau relatives](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="6ac9d-122">Nous calculons le pourcentage de clients Office 365 dans la même ville dans des compartiments de performance plus performants.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="6ac9d-123">Si ce nombre est supérieur à 10%, nous affichons Network Insight.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="6ac9d-124">Cette vue est abrégée en « pairs » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="6ac9d-125">Utilisation d’un service frontal Exchange Online non optimal</span><span class="sxs-lookup"><span data-stu-id="6ac9d-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="6ac9d-126">L’utilisateur ne se connecte pas à une trappe frontal de service Office 365 optimale et cela devrait avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="6ac9d-127">Nous répertorions les portes frontales du service Exchange Online qui peuvent être utilisées à partir de la ville de l’emplacement du bureau avec de bonnes performances.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="6ac9d-128">Si le test actuel indique l’utilisation d’un service frontal Exchange Online qui ne figurent pas sur cette liste, nous appelons cette recommandation.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="6ac9d-129">L’utilisation d’une trappe frontal non optimale d’un service Exchange Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="6ac9d-130">Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="6ac9d-131">Cette vue est abrégée en « routage » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="6ac9d-132">Utilisation de la porte d’appel frontale SharePoint Online non optimale</span><span class="sxs-lookup"><span data-stu-id="6ac9d-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="6ac9d-133">L’utilisateur ne se connecte pas au volet frontal du service SharePoint Online le plus proche.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="6ac9d-134">Cela peut avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="6ac9d-135">Nous allons identifier la porte d’écran du service SharePoint Online à laquelle le client de test se connecte.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="6ac9d-136">Ensuite, pour la ville de l’emplacement du bureau, nous comparons cette ville avec le service SharePoint Online attendu pour cette ville.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="6ac9d-137">S’il ne correspond pas, nous en faisons la recommandation.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="6ac9d-138">Cette vue est abrégée sous la forme « AFD » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="6ac9d-139">Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint</span><span class="sxs-lookup"><span data-stu-id="6ac9d-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="6ac9d-140">Vitesse de téléchargement du réseau sous-optimal, qui a un impact sur le temps nécessaire au chargement des documents à partir de OneDrive entreprise.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="6ac9d-141">La vitesse de téléchargement qu’un utilisateur peut obtenir à partir de SharePoint Online et des portes frontales du service OneDrive entreprise est exprimée en mégaoctets par seconde (Mbits/s).</span><span class="sxs-lookup"><span data-stu-id="6ac9d-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="6ac9d-142">Si cette valeur est inférieure à 1 MBps, nous fournissons cette vue.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="6ac9d-143">Pour améliorer la vitesse de téléchargement qu’un utilisateur peut obtenir de la bande passante, il est peut-être nécessaire de l’augmenter.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="6ac9d-144">Par ailleurs, il peut y avoir une congestion réseau entre les ordinateurs des utilisateurs à l’emplacement du bureau et le capot frontal du service SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="6ac9d-145">Cette opération est parfois appelée perte de congestion et limite la vitesse de téléchargement disponible aux utilisateurs, même si la bande passante disponible est suffisante.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="6ac9d-146">Cette vue est abrégée en « débit » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="6ac9d-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="6ac9d-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ac9d-147">Related topics</span></span>

[<span data-ttu-id="6ac9d-148">Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="6ac9d-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="6ac9d-149">Évaluation du réseau Office 365 (préversion)</span><span class="sxs-lookup"><span data-stu-id="6ac9d-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="6ac9d-150">Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="6ac9d-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
