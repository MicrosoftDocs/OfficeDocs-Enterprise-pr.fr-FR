---
title: Configurer votre réseau pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : consultez ces articles pour comprendre la mise en réseau pour Microsoft 365.'
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735655"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="37119-103">Configurer votre réseau pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="37119-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="37119-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="37119-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span><span class="sxs-lookup"><span data-stu-id="37119-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span></span> <span data-ttu-id="37119-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span><span class="sxs-lookup"><span data-stu-id="37119-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="37119-107">Utilisez ces articles pour comprendre les différences clés et modifier vos équipements de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances de la part de vos utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="37119-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="37119-108">Fonctionnement de la mise en réseau Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="37119-109">Consultez les articles suivants pour obtenir une vue d’ensemble de la connectivité pour Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="37119-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="37119-110">Vue d’ensemble de la connectivité réseau Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="37119-111">Principes de connectivité réseau de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="37119-112">Évaluation de la connectivité réseau Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="37119-113">Pour obtenir des conseils sur l’amélioration des performances, voir [planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="37119-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="37119-114">Prise en charge de la mise en réseau Microsoft 365 en tant que fournisseur d’équipement réseau</span><span class="sxs-lookup"><span data-stu-id="37119-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="37119-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span><span class="sxs-lookup"><span data-stu-id="37119-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span> <span data-ttu-id="37119-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span><span class="sxs-lookup"><span data-stu-id="37119-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="37119-117">Points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-117">Office 365 endpoints</span></span>

<span data-ttu-id="37119-118">Les points de terminaison sont l’ensemble des adresses IP de destination, noms de domaine DNS et URL pour le trafic sur Internet Office 365.</span><span class="sxs-lookup"><span data-stu-id="37119-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="37119-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span><span class="sxs-lookup"><span data-stu-id="37119-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span></span> <span data-ttu-id="37119-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span><span class="sxs-lookup"><span data-stu-id="37119-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="37119-121">Voir [Gestion des points de terminaison d’Office 365 ](managing-office-365-endpoints.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="37119-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="37119-122">There are currently five different Office 365 clouds.</span><span class="sxs-lookup"><span data-stu-id="37119-122">There are currently five different Office 365 clouds.</span></span> <span data-ttu-id="37119-123">This table takes you to the list of endpoints for each one.</span><span class="sxs-lookup"><span data-stu-id="37119-123">This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="37119-124">Points de terminaison internationaux</span><span class="sxs-lookup"><span data-stu-id="37119-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="37119-125">Les points de terminaison pour les abonnements Office 365 dans le monde, dont le États-Unis Government Community Cloud (GCC).</span><span class="sxs-lookup"><span data-stu-id="37119-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="37119-126">Points de terminaison DoD du gouvernement américain</span><span class="sxs-lookup"><span data-stu-id="37119-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="37119-127">Les points de terminaison pour les abonnements aux États-Unis Department of Defense (DoD).</span><span class="sxs-lookup"><span data-stu-id="37119-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="37119-128">Points de terminaison GCC High du gouvernement américain</span><span class="sxs-lookup"><span data-stu-id="37119-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="37119-129">Les points de terminaison pour les abonnements aux États-Unis pour le secteur public Communauté Cloud élevé (GCC élevé).</span><span class="sxs-lookup"><span data-stu-id="37119-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="37119-130">Office 365 géré par les points de terminaison 21Vianet</span><span class="sxs-lookup"><span data-stu-id="37119-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="37119-131">Les points de terminaison pour Office 365 géré par 21Vianet, qui est conçu pour répondre aux besoins d’Office 365 en Chine.</span><span class="sxs-lookup"><span data-stu-id="37119-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="37119-132">Points de terminaison Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="37119-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="37119-133">Les points de terminaison pour un cloud en Europe distinct, pour les clients plus régulés en Allemagne, Union européenne (UE) et l’Association européenne de libre-échange (AELE).</span><span class="sxs-lookup"><span data-stu-id="37119-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="37119-134">Pour automatiser l’obtention de la dernière liste des points de terminaison pour votre cloud Office 365, voir [Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="37119-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="37119-135">Pour plus de points de terminaison, voir les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="37119-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="37119-136">Autres points de terminaison supplémentaires non inclus dans les services web</span><span class="sxs-lookup"><span data-stu-id="37119-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="37119-137">Requêtes réseau dans Office 2016 pour Mac</span><span class="sxs-lookup"><span data-stu-id="37119-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="37119-138">Rubriques supplémentaires pour Microsoft 365 Networking</span><span class="sxs-lookup"><span data-stu-id="37119-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="37119-139">Consultez les articles suivants pour obtenir des rubriques spécialisées sur la mise en réseau Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="37119-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="37119-140">Réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="37119-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="37119-141">Prise en charge du protocole IPv6 dans les services Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="37119-142">Prise en charge de la traduction d’adresses réseau (NAT) avec Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="37119-143">ExpressRoute pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="37119-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="37119-144">Consultez les articles suivants pour plus d’informations sur l’utilisation d’ExpressRoute pour le trafic Office 365 :</span><span class="sxs-lookup"><span data-stu-id="37119-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="37119-145">Azure ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="37119-146">Implémentation d’ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="37119-147">Planification de réseau avec ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="37119-148">Routage avec ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="37119-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
