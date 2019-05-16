---
title: Configurer votre réseau pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Voir les articles suivants pour comprendre la mise en réseau pour Office 365.'
ms.openlocfilehash: 6fb1d4d441719f61886b9263b30cdf27cbe7eaf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070820"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="0c221-103">Configurer votre réseau pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-103">Set up your network for Office 365</span></span>

<span data-ttu-id="0c221-104">**Résumé :** voir les articles suivants pour comprendre la mise en réseau pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c221-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="0c221-p101">Une partie importante de votre intégration Office 365 est tout d’abord de vous assurer que vos connexions réseau et Internet sont définies pour optimiser l’accès. Configurer votre réseau local pour accéder à un cloud logiciel en tant que service (SaaS) distribué globalement est différent d’un réseau traditionnel optimisé pour le trafic aux centres de données locaux.</span><span class="sxs-lookup"><span data-stu-id="0c221-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="0c221-107">Utilisez ces articles pour comprendre les différences clés et modifier votre équipement de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0c221-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="0c221-108">Fonctionnement de mise en réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-108">How Office 365 networking works</span></span>

<span data-ttu-id="0c221-109">Consultez les articles suivants pour une vue d’ensemble de la connectivité pour Office 365 :</span><span class="sxs-lookup"><span data-stu-id="0c221-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="0c221-110">Vue d’ensemble de la connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="0c221-111">Principes de connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="0c221-112">Connectivité réseau à Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-112">Network connectivity to Office 365</span></span>](network-connectivity.md)

<span data-ttu-id="0c221-113">Pour obtenir des conseils sur l’amélioration des performances, voir [planification réseau et optimisation des performances pour Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="0c221-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="0c221-114">Prise en charge de la mise en réseau Office 365 comme un fournisseur d’équipement réseau</span><span class="sxs-lookup"><span data-stu-id="0c221-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="0c221-p102">Si vous êtes un fournisseur d’équipement réseau, rejoignez le[programme de partenariat mise en réseau d’Office 365](office-365-networking-partner-program.md). Inscrivez-vous au programme pour développer les principes de connectivité réseau Office 365 dans vos produits et solutions.</span><span class="sxs-lookup"><span data-stu-id="0c221-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="0c221-117">Points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-117">Office 365 endpoints</span></span>

<span data-ttu-id="0c221-118">Les points de terminaison sont l’ensemble des adresses IP de destination, noms de domaine DNS et URL pour le trafic sur Internet Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c221-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="0c221-p103">Pour optimiser les performances aux services Office 365 basés sur le cloud, ces points de terminaison nécessitent une gestion spéciale par les autres navigateurs client et les appareils dans votre réseau de périmètre. Ces appareils incluent pare-feux, SSL Break and Inspect et des appareils d’inspection des paquets, et systèmes de protection contre la perte de données.</span><span class="sxs-lookup"><span data-stu-id="0c221-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="0c221-121">Voir [Gestion des points de terminaison d’Office 365 ](managing-office-365-endpoints.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="0c221-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="0c221-p104">Il existe actuellement cinq différents clouds Office 365. Ce tableau vous permet d’accéder à la liste des points de terminaison pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="0c221-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="0c221-124">Points de terminaison internationaux</span><span class="sxs-lookup"><span data-stu-id="0c221-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="0c221-125">Les points de terminaison pour les abonnements Office 365 dans le monde, dont le États-Unis Government Community Cloud (GCC).</span><span class="sxs-lookup"><span data-stu-id="0c221-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="0c221-126">Points de terminaison DoD du gouvernement américain</span><span class="sxs-lookup"><span data-stu-id="0c221-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="0c221-127">Les points de terminaison pour les abonnements aux États-Unis Department of Defense (DoD).</span><span class="sxs-lookup"><span data-stu-id="0c221-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="0c221-128">Points de terminaison GCC High du gouvernement américain</span><span class="sxs-lookup"><span data-stu-id="0c221-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="0c221-129">Les points de terminaison pour les abonnements aux États-Unis pour le secteur public Communauté Cloud élevé (GCC élevé).</span><span class="sxs-lookup"><span data-stu-id="0c221-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="0c221-130">Office 365 géré par les points de terminaison 21Vianet</span><span class="sxs-lookup"><span data-stu-id="0c221-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="0c221-131">Les points de terminaison pour Office 365 géré par 21Vianet, qui est conçu pour répondre aux besoins d’Office 365 en Chine.</span><span class="sxs-lookup"><span data-stu-id="0c221-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="0c221-132">Points de terminaison Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="0c221-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="0c221-133">Les points de terminaison pour un cloud en Europe distinct, pour les clients plus régulés en Allemagne, Union européenne (UE) et l’Association européenne de libre-échange (AELE).</span><span class="sxs-lookup"><span data-stu-id="0c221-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="0c221-134">Pour automatiser l’obtention de la dernière liste des points de terminaison pour votre cloud Office 365, voir [Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="0c221-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="0c221-135">Pour plus de points de terminaison, voir les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="0c221-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="0c221-136">Autres points de terminaison supplémentaires non inclus dans les services web</span><span class="sxs-lookup"><span data-stu-id="0c221-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="0c221-137">Requêtes réseau dans Office 2016 pour Mac</span><span class="sxs-lookup"><span data-stu-id="0c221-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="0c221-138">Autres rubriques réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="0c221-139">Voir les articles suivants pour rubriques spécialisés dans la mise en réseau Office 365 :</span><span class="sxs-lookup"><span data-stu-id="0c221-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="0c221-140">Réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="0c221-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="0c221-141">Prise en charge du protocole IPv6 dans les services Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="0c221-142">Prise en charge de la traduction d’adresses réseau (NAT) avec Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="0c221-143">ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="0c221-144">Consultez les articles suivants pour plus d’informations sur l’utilisation d’ExpressRoute pour le trafic Office 365 :</span><span class="sxs-lookup"><span data-stu-id="0c221-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="0c221-145">Azure ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="0c221-146">Implémentation d’ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="0c221-147">Planification de réseau avec ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="0c221-148">Routage avec ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0c221-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
