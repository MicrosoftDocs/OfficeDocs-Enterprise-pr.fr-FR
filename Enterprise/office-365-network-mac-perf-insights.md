---
title: Informations sur le réseau Office 365 (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Informations sur le réseau Office 365 (aperçu)
ms.openlocfilehash: 5064c45ffa552381ccdb6042d5e9d6f072f564aa
ms.sourcegitcommit: 44a0e9a134373eb0d1292761089a6557b01ac327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "43081706"
---
# <a name="office-365-network-insights-preview"></a><span data-ttu-id="f88ff-103">Informations sur le réseau Office 365 (aperçu)</span><span class="sxs-lookup"><span data-stu-id="f88ff-103">Office 365 Network Insights (preview)</span></span>

<span data-ttu-id="f88ff-104">Les informations sur le **réseau** sont des mesures de performances en direct collectées à partir de votre client Office 365 et disponibles uniquement par les utilisateurs administratifs de votre client.</span><span class="sxs-lookup"><span data-stu-id="f88ff-104">**Network insights** are live performance metrics collected from your Office 365 tenant, and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="f88ff-105">Les informations s’affichent dans le centre d’administration Microsoft 365 <https://portal.microsoft.com/adminportal/home#/networkperformance>à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="f88ff-105">Insights are displayed in the Microsoft 365 Admin Center at <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span></span>

<span data-ttu-id="f88ff-106">Les informations sont destinées à vous aider à concevoir des périmètres réseau pour vos emplacements de bureau.</span><span class="sxs-lookup"><span data-stu-id="f88ff-106">Insights are intended to help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="f88ff-107">Chaque vue fournit des informations détaillées sur les caractéristiques de performances d’un problème commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client.</span><span class="sxs-lookup"><span data-stu-id="f88ff-107">Each insight provides live details about the performance characteristics for a specific common issue for each geographic location where users are accessing your tenant.</span></span>

<span data-ttu-id="f88ff-108">Cinq aspects spécifiques du réseau peuvent être affichés pour chaque emplacement de bureau :</span><span class="sxs-lookup"><span data-stu-id="f88ff-108">There are five specific network insights that may be shown for each office location:</span></span>

- [<span data-ttu-id="f88ff-109">Sortie réseau retractée</span><span class="sxs-lookup"><span data-stu-id="f88ff-109">Backhauled network egress</span></span>](#backhauled-network-egress)
- [<span data-ttu-id="f88ff-110">Meilleures performances détectées pour les clients proches de vous</span><span class="sxs-lookup"><span data-stu-id="f88ff-110">Better performance detected for customers near you</span></span>](#better-performance-detected-for-customers-near-you)
- [<span data-ttu-id="f88ff-111">Utilisation d’un service frontal Exchange Online non optimal</span><span class="sxs-lookup"><span data-stu-id="f88ff-111">Use of a non-optimal Exchange Online service front door</span></span>](#use-of-a-non-optimal-exchange-online-service-front-door)
- [<span data-ttu-id="f88ff-112">Utilisation d’un service SharePoint Online non optimal</span><span class="sxs-lookup"><span data-stu-id="f88ff-112">Use of a non-optimal SharePoint Online service front door</span></span>](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [<span data-ttu-id="f88ff-113">Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint</span><span class="sxs-lookup"><span data-stu-id="f88ff-113">Low download speed from SharePoint front door</span></span>](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
><span data-ttu-id="f88ff-114">Les informations relatives au réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f88ff-114">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="f88ff-115">Sortie réseau retractée</span><span class="sxs-lookup"><span data-stu-id="f88ff-115">Backhauled network egress</span></span>

<span data-ttu-id="f88ff-116">Cette vue s’affiche si le service réseau Insights détecte que la distance entre un emplacement utilisateur donné et la sortie réseau est supérieure à 500 milles (800 kilomètres), ce qui indique que le trafic Office 365 est replacé vers un périphérique ou un proxy Internet Edge commun.</span><span class="sxs-lookup"><span data-stu-id="f88ff-116">This insight will be displayed if the network insights service detects that the distance from a given user location to the network egress is greater than 500 miles (800 kilometers), indicating that Office 365 traffic is being backhauled to a common Internet edge device or proxy.</span></span>

<span data-ttu-id="f88ff-117">Cette vue est abrégée en « sortie » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="f88ff-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

![Sortie réseau retractée](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-119">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-119">What does this mean?</span></span>

<span data-ttu-id="f88ff-120">Cela indique que la distance entre l’emplacement du bureau et la sortie du réseau est supérieure à 500 kilomètres (800 kilomètres).</span><span class="sxs-lookup"><span data-stu-id="f88ff-120">This identifies that the distance between the office location and the network egress is more than 500 miles (800 kilometers).</span></span> <span data-ttu-id="f88ff-121">L’emplacement du Bureau est identifié par un emplacement de l’ordinateur client masqué et l’emplacement de sortie du réseau est identifié à l’aide de l’adresse IP inverse pour les bases de données d’emplacement.</span><span class="sxs-lookup"><span data-stu-id="f88ff-121">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="f88ff-122">L’emplacement du Bureau peut être inexact si les services d’emplacement Windows sont désactivés sur les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f88ff-122">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="f88ff-123">L’emplacement de sortie réseau peut être inexact si les informations de la base de données d’adresses IP inversées sont inexactes.</span><span class="sxs-lookup"><span data-stu-id="f88ff-123">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="f88ff-124">Les détails de cette analyse incluent l’emplacement du bureau, le pourcentage estimé du nombre total d’utilisateurs clients à l’emplacement, l’emplacement de sortie du réseau actuel, la pertinence de l’emplacement de sortie, la distance entre l’emplacement et le point de sortie actuel, la date du premier détection de la condition et la date à laquelle la condition a été résolue.</span><span class="sxs-lookup"><span data-stu-id="f88ff-124">Details for this insight include the office location, estimated percentage of total tenant user at the location, the current network egress location, relevance of the egress location, the distance between the location and the current egress point, the date the condition was first detected, and the date the condition was resolved.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-125">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-125">What should I do?</span></span>

<span data-ttu-id="f88ff-126">Pour cette vue d’ensemble, nous recommandons un accès réseau plus proche de l’emplacement du bureau afin que la connectivité puisse acheminer de façon optimale le réseau mondial de Microsoft et le service Office 365.</span><span class="sxs-lookup"><span data-stu-id="f88ff-126">For this insight, we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's global network and to the nearest Office 365 service front door.</span></span> <span data-ttu-id="f88ff-127">Une sortie étroite du réseau vers les bureaux des utilisateurs permet également d’améliorer les performances à l’avenir à mesure que Microsoft étend à la fois les points de présence réseau et les portes frontales du service Office 365.</span><span class="sxs-lookup"><span data-stu-id="f88ff-127">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="f88ff-128">Pour plus d’informations sur la façon de résoudre ce problème, reportez-vous à la rubrique [sortie locale des connexions réseau](office-365-network-connectivity-principles.md#egress-network-connections-locally) dans [Office 365 principes de connectivité réseau](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="f88ff-128">For more information about how to resolve this issue, see [Egress network connections locally](office-365-network-connectivity-principles.md#egress-network-connections-locally) in [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="f88ff-129">Meilleures performances détectées pour les clients proches de vous</span><span class="sxs-lookup"><span data-stu-id="f88ff-129">Better performance detected for customers near you</span></span>

<span data-ttu-id="f88ff-130">Cette vue s’affiche si le service réseau Insights détecte qu’un nombre important de clients dans votre zone de métro offre de meilleures performances que les utilisateurs de votre organisation à cet emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="f88ff-130">This insight will be displayed if the network insights service detects that a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="f88ff-131">Cette vue est abrégée en « pairs » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="f88ff-131">This insight is abbreviated as "Peers" in some summary views.</span></span>

![Performances réseau relatives](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-133">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-133">What does this mean?</span></span>

<span data-ttu-id="f88ff-134">Cette vue d’ensemble examine les performances totales des clients Office 365 dans la même ville que cet emplacement de bureau.</span><span class="sxs-lookup"><span data-stu-id="f88ff-134">This insight examines the aggregate performance of Office 365 customers in the same city as this office location.</span></span> <span data-ttu-id="f88ff-135">Cette vue s’affiche si la latence moyenne de vos utilisateurs est supérieure de 10% à la latence moyenne des clients voisins.</span><span class="sxs-lookup"><span data-stu-id="f88ff-135">This insight is displayed if the average latency of your users is 10% greater than the average latency of neighboring tenants.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-136">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-136">What should I do?</span></span>

<span data-ttu-id="f88ff-137">Il peut y avoir plusieurs raisons à cette condition, notamment la latence de votre réseau d’entreprise ou de votre fournisseur de services Internet, des goulots d’étranglement ou des problèmes de conception de l’architecture.</span><span class="sxs-lookup"><span data-stu-id="f88ff-137">There could be many reasons for this condition, including latency in your corporate network or ISP, bottlenecks, or architecture design issues.</span></span> <span data-ttu-id="f88ff-138">Examinez la latence entre chaque tronçon de l’itinéraire entre votre réseau d’entreprise et le volet frontal Office 365 actuel.</span><span class="sxs-lookup"><span data-stu-id="f88ff-138">Examine the latency between each hop in the route between your office network and the current Office 365 front door.</span></span> <span data-ttu-id="f88ff-139">Pour plus d’informations, consultez la rubrique [Office 365 Network Connectivity principes](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="f88ff-139">For more information, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="f88ff-140">Utilisation d’un service frontal Exchange Online non optimal</span><span class="sxs-lookup"><span data-stu-id="f88ff-140">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="f88ff-141">Cette vue s’affiche si le service réseau Insights détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas à un service frontal Exchange Online optimal.</span><span class="sxs-lookup"><span data-stu-id="f88ff-141">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to an optimal Exchange Online service front door.</span></span>

<span data-ttu-id="f88ff-142">Cette vue est abrégée en « routage » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="f88ff-142">This insight is abbreviated as "Routing" in some summary views.</span></span>

![Porte de façade non optimale](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-144">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-144">What does this mean?</span></span>

<span data-ttu-id="f88ff-145">Nous répertorions les portes frontales du service Exchange Online qui peuvent être utilisées à partir de la ville de l’emplacement du bureau avec de bonnes performances.</span><span class="sxs-lookup"><span data-stu-id="f88ff-145">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="f88ff-146">Si le test actuel indique l’utilisation d’un service frontal Exchange Online qui ne figurent pas sur cette liste, nous appelons cette recommandation.</span><span class="sxs-lookup"><span data-stu-id="f88ff-146">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-147">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-147">What should I do?</span></span>

<span data-ttu-id="f88ff-148">L’utilisation d’une trappe frontal non optimale d’un service Exchange Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct.</span><span class="sxs-lookup"><span data-stu-id="f88ff-148">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="f88ff-149">Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.</span><span class="sxs-lookup"><span data-stu-id="f88ff-149">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="f88ff-150">Utilisation d’un service SharePoint Online non optimal</span><span class="sxs-lookup"><span data-stu-id="f88ff-150">Use of a non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="f88ff-151">Cette vue s’affiche si le service réseau Insights détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas au porte-tout du service SharePoint Online le plus proche.</span><span class="sxs-lookup"><span data-stu-id="f88ff-151">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to the closest SharePoint Online service front door.</span></span>

<span data-ttu-id="f88ff-152">Cette vue est abrégée sous la forme « AFD » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="f88ff-152">This insight is abbreviated as "Afd" in some summary views.</span></span>

![Porte de façade non optimale](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-154">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-154">What does this mean?</span></span>

<span data-ttu-id="f88ff-155">Nous allons identifier la porte d’écran du service SharePoint Online à laquelle le client de test se connecte.</span><span class="sxs-lookup"><span data-stu-id="f88ff-155">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="f88ff-156">Ensuite, pour la ville de l’emplacement du bureau, nous comparons cette ville avec le service SharePoint Online attendu pour cette ville.</span><span class="sxs-lookup"><span data-stu-id="f88ff-156">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="f88ff-157">S’il ne correspond pas, nous en faisons la recommandation.</span><span class="sxs-lookup"><span data-stu-id="f88ff-157">If it doesn't match, then we make this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-158">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-158">What should I do?</span></span>

<span data-ttu-id="f88ff-159">L’utilisation d’une trappe frontal non optimale de service SharePoint Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct.</span><span class="sxs-lookup"><span data-stu-id="f88ff-159">Use of a non-optimal SharePoint Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="f88ff-160">Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.</span><span class="sxs-lookup"><span data-stu-id="f88ff-160">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="f88ff-161">Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint</span><span class="sxs-lookup"><span data-stu-id="f88ff-161">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="f88ff-162">Cette vue s’affiche si le service réseau Insights détecte que la bande passante entre l’emplacement de bureau spécifique et SharePoint Online est inférieure à 1 MBps.</span><span class="sxs-lookup"><span data-stu-id="f88ff-162">This insight will be displayed if the network insights service detects that bandwidth between the specific office location and SharePoint Online is less than 1 MBps.</span></span>

<span data-ttu-id="f88ff-163">Cette vue est abrégée en « débit » dans certains affichages de résumés.</span><span class="sxs-lookup"><span data-stu-id="f88ff-163">This insight is abbreviated as "Throughput" in some summary views.</span></span>

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-164">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-164">What does this mean?</span></span>

<span data-ttu-id="f88ff-165">La vitesse de téléchargement qu’un utilisateur peut obtenir à partir de SharePoint Online et des portes frontales du service OneDrive entreprise est exprimée en mégaoctets par seconde (Mbits/s).</span><span class="sxs-lookup"><span data-stu-id="f88ff-165">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="f88ff-166">Si cette valeur est inférieure à 1 MBps, nous fournissons cette vue.</span><span class="sxs-lookup"><span data-stu-id="f88ff-166">If this value is less than 1 MBps then we provide this insight.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-167">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-167">What should I do?</span></span>

<span data-ttu-id="f88ff-168">Pour améliorer la vitesse de téléchargement, vous devrez peut-être augmenter la bande passante.</span><span class="sxs-lookup"><span data-stu-id="f88ff-168">To improve download speeds, bandwidth may need to be increased.</span></span> <span data-ttu-id="f88ff-169">Par ailleurs, il peut y avoir une congestion réseau entre les ordinateurs des utilisateurs à l’emplacement du bureau et le capot frontal du service SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f88ff-169">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="f88ff-170">Cette opération est parfois appelée perte de congestion et limite la vitesse de téléchargement disponible aux utilisateurs, même si la bande passante disponible est suffisante.</span><span class="sxs-lookup"><span data-stu-id="f88ff-170">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

## <a name="china-user-optimal-network-egress"></a><span data-ttu-id="f88ff-171">Sortie du réseau chinois utilisateur optimal</span><span class="sxs-lookup"><span data-stu-id="f88ff-171">China user optimal network egress</span></span>

<span data-ttu-id="f88ff-172">Cette vue s’affiche si votre organisation a des utilisateurs en Chine se connectent à votre client Office 365 dans d’autres emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="f88ff-172">This insight will be displayed if your organization has users in China connecting to your Office 365 tenant in other geographic locations.</span></span> 

### <a name="what-does-this-mean"></a><span data-ttu-id="f88ff-173">Scénario</span><span class="sxs-lookup"><span data-stu-id="f88ff-173">What does this mean?</span></span>

<span data-ttu-id="f88ff-174">Si votre organisation possède une connectivité WAN privée, nous vous recommandons de configurer un circuit WAN réseau à partir de vos emplacements de bureau en Chine qui dispose de la sortie réseau vers Internet dans l’un des emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="f88ff-174">If your organization has private WAN connectivity, we recommend configuring a network WAN circuit from your office locations in China that has network egress to the Internet in any of the following locations:</span></span>

- <span data-ttu-id="f88ff-175">Hong Kong (R.A.S.)</span><span class="sxs-lookup"><span data-stu-id="f88ff-175">Hong Kong</span></span>
- <span data-ttu-id="f88ff-176">Japon</span><span class="sxs-lookup"><span data-stu-id="f88ff-176">Japan</span></span>
- <span data-ttu-id="f88ff-177">Taïwan</span><span class="sxs-lookup"><span data-stu-id="f88ff-177">Taiwan</span></span>
- <span data-ttu-id="f88ff-178">Corée du Sud</span><span class="sxs-lookup"><span data-stu-id="f88ff-178">South Korea</span></span>
- <span data-ttu-id="f88ff-179">Singapour</span><span class="sxs-lookup"><span data-stu-id="f88ff-179">Singapore</span></span>
- <span data-ttu-id="f88ff-180">Malaisie</span><span class="sxs-lookup"><span data-stu-id="f88ff-180">Malaysia</span></span>

<span data-ttu-id="f88ff-181">Une sortie Internet plus éloignée des utilisateurs que ces emplacements réduira les performances, et la sortie en Chine peut entraîner des problèmes de latence et de connectivité élevés en raison d’une congestion transfrontalière.</span><span class="sxs-lookup"><span data-stu-id="f88ff-181">Internet egress further away from users than these locations will reduce performance, and egress in China may cause high latency and connectivity issues due to cross-border congestion.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="f88ff-182">Que dois-je faire ?</span><span class="sxs-lookup"><span data-stu-id="f88ff-182">What should I do?</span></span>

<span data-ttu-id="f88ff-183">Pour plus d’informations sur la façon d’atténuer les problèmes de performances liés à cette vue, consultez la rubrique [Office 365 global client Optimization for China Users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span><span class="sxs-lookup"><span data-stu-id="f88ff-183">For more information about how to mitigate performance issues related to this insight, see [Office 365 global tenant performance optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span></span>

## <a name="related-topics"></a><span data-ttu-id="f88ff-184">Sujets associés</span><span class="sxs-lookup"><span data-stu-id="f88ff-184">Related topics</span></span>

[<span data-ttu-id="f88ff-185">Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="f88ff-185">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="f88ff-186">Évaluation du réseau Office 365 (préversion)</span><span class="sxs-lookup"><span data-stu-id="f88ff-186">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="f88ff-187">Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="f88ff-187">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="f88ff-188">Services d’emplacement de connectivité réseau Office 365 (préversion)</span><span class="sxs-lookup"><span data-stu-id="f88ff-188">Office 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
