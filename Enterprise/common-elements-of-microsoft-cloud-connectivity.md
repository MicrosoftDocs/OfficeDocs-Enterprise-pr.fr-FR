---
title: Éléments courants de connectivité du cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Résumé : Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau."
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490194"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="eb4fb-103">Éléments communs de la connectivité au cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="eb4fb-104">**Résumé :** Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="eb4fb-105">L’intégration de votre réseau avec le cloud Microsoft fournit un accès optimal à une large gamme de services.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="eb4fb-106">Étapes pour préparer votre réseau pour les services cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="eb4fb-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="eb4fb-107"></span></span>

<span data-ttu-id="eb4fb-108">Pour votre réseau local, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb4fb-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="eb4fb-109">Analysez les ordinateurs de vos clients et optimisez le matériel réseau, les pilotes logiciels, les paramètres du protocole et les navigateurs Internet.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="eb4fb-110">Analysez votre réseau local pour la latence du trafic et le routage optimal vers le périphérique du périmètre Internet.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="eb4fb-111">Analysez la capacité et les performances du périphérique du périmètre Internet et optimisez les niveaux supérieurs de trafic.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="eb4fb-112">Pour votre connexion Internet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb4fb-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="eb4fb-113">Analysez la latence entre le périphérique du périmètre Internet (par exemple, votre pare-feu externe) et les emplacements régionaux du service cloud de Microsoft auquel vous vous connectez.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="eb4fb-p101">Analysez la capacité et l’utilisation de votre connexion Internet actuelle et augmentez la capacité si nécessaire. Vous pouvez également ajouter une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="eb4fb-116">Options de connectivité au cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="eb4fb-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="eb4fb-117"></span></span>

<span data-ttu-id="eb4fb-118">Utilisez votre canal Internet existant ou une connexion ExpressRoute à Office 365, Azure et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="eb4fb-119">**Figure 1 : Options pour la connectivité cloud Microsoft**</span><span class="sxs-lookup"><span data-stu-id="eb4fb-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figure 1 :  options pour la connectivité cloud Microsoft](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="eb4fb-p102">La figure 1 indique la façon dont un réseau local peut être connecté aux offres de cloud de Microsoft à l’aide de son canal Internet existant ou d’ExpressRoute. Le canal Internet représente une zone DMZ et peut avoir les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="eb4fb-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="eb4fb-p103">**Pare-feu interne :** Barrière entre votre réseau approuvé et un réseau non approuvé. Effectue le filtrage (en fonction des règles) et la surveillance du trafic.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="eb4fb-125">**Charge de travail externe :** Sites web ou autres charges de travail mis à la disposition des utilisateurs externes sur Internet.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="eb4fb-126">**Serveur proxy :** Demandes de services pour le contenu web au nom des utilisateurs de l'intranet.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="eb4fb-127">Un proxy inverse autorise les demandes entrantes non sollicitées.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="eb4fb-128">**Pare-feu externe :** Autorise le trafic sortant et le trafic entrant spécifié.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="eb4fb-129">Peut effectuer la traduction d'adresse, l'inspection de paquets, l'interruption et l'inspection de SSL, ou la protection contre la perte de données.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="eb4fb-130">**Connexion WAN à ISP :** Connexion basée sur un opérateur à un fournisseur de services Internet, qui est homologuée avec Internet pour la connectivité et le routage.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="eb4fb-131">Zones de réseau communes à tous les services cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="eb4fb-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="eb4fb-132"></span></span>

<span data-ttu-id="eb4fb-133">Vous devez prendre en considération ces zones de réseau lors de l’adoption des services cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="eb4fb-134">**Performances intranet :** Les performances des ressources basées sur Internet seront réduites si votre intranet, y compris les ordinateurs des clients, n'est pas optimisé.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="eb4fb-135">**Périphériques du périmètre :** Les périphériques dans le périmètre de votre réseau sont des points de sortie et peuvent inclure des traducteurs d'adresses réseau (NAT), des serveurs proxy (y compris les proxys inverses), des pare-feux, des périphériques de détection des intrusions ou une combinaison.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="eb4fb-p106">**Connexion à Internet :** Votre connexion WAN à votre fournisseur de services Internet et Internet doivent avoir une capacité suffisante pour gérer les charges de pointe. Vous pouvez également utiliser une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="eb4fb-p107">**Internet DNS :** A, AAAA, CNAME, MX, PTR et les autres enregistrements pour localiser le cloud de Microsoft ou les services hébergés dans le cloud. Par exemple, vous pouvez avoir besoin d’un enregistrement CNAME pour votre application hébergée dans Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="eb4fb-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="eb4fb-140">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="eb4fb-140">Next step</span></span>

[<span data-ttu-id="eb4fb-141">ExpressRoute pour la connectivité au cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="eb4fb-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb4fb-142">See also</span></span>

<span data-ttu-id="eb4fb-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="eb4fb-143"></span></span>

[<span data-ttu-id="eb4fb-144">Mise en réseau cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="eb4fb-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="eb4fb-145">Ressources relatives à l’architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb4fb-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


