---
title: "Éléments communs de la connectivité au cloud Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Résumé : Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau."
ms.openlocfilehash: 27a83217e94d6a0f882825c57346b58ea1834443
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="26232-103">Éléments communs de la connectivité au cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="26232-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="26232-104">**Résumé :** Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau.</span><span class="sxs-lookup"><span data-stu-id="26232-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="26232-105">L’intégration de votre réseau avec le cloud Microsoft fournit un accès optimal à une large gamme de services.</span><span class="sxs-lookup"><span data-stu-id="26232-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="26232-106">Étapes pour préparer votre réseau pour les services cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="26232-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="26232-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="26232-107"><a name="steps"> </a></span></span>

<span data-ttu-id="26232-108">Pour votre réseau local, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="26232-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="26232-109">Analysez les ordinateurs de vos clients et optimisez le matériel réseau, les pilotes logiciels, les paramètres du protocole et les navigateurs Internet.</span><span class="sxs-lookup"><span data-stu-id="26232-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="26232-110">Analysez votre réseau local pour la latence du trafic et le routage optimal vers le périphérique du périmètre Internet.</span><span class="sxs-lookup"><span data-stu-id="26232-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="26232-111">Analysez la capacité et les performances du périphérique du périmètre Internet et optimisez les niveaux supérieurs de trafic.</span><span class="sxs-lookup"><span data-stu-id="26232-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="26232-112">Pour votre connexion Internet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="26232-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="26232-113">Analysez la latence entre le périphérique du périmètre Internet (par exemple, votre pare-feu externe) et les emplacements régionaux du service cloud de Microsoft auquel vous vous connectez.</span><span class="sxs-lookup"><span data-stu-id="26232-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="26232-p101">Analysez la capacité et l’utilisation de votre connexion Internet actuelle et augmentez la capacité si nécessaire. Vous pouvez également ajoutez une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="26232-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="26232-116">Options de connectivité au cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="26232-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="26232-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="26232-117"><a name="steps"> </a></span></span>

<span data-ttu-id="26232-118">Utilisez votre canal Internet existant ou une connexion ExpressRoute à Office 365, Azure et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="26232-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="26232-119">**Figure 1 : Options pour la connectivité cloud Microsoft**</span><span class="sxs-lookup"><span data-stu-id="26232-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figure 1 :  options pour la connectivité cloud Microsoft](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="26232-p102">La figure 1 indique la façon dont un réseau local peut être connecté aux offres de cloud de Microsoft à l’aide de son canal Internet existant ou d’ExpressRoute. Le canal Internet représente une zone DMZ et peut avoir les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="26232-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="26232-p103">**Pare-feu interne :** Barrière entre votre réseau approuvé et un réseau non approuvé. Effectue le filtrage (en fonction des règles) et la surveillance du trafic.</span><span class="sxs-lookup"><span data-stu-id="26232-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="26232-125">**Charge de travail externe :** Sites web ou autres charges de travail mis à la disposition des utilisateurs externes sur Internet.</span><span class="sxs-lookup"><span data-stu-id="26232-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="26232-p104">**Serveur proxy :** Demandes de services pour le contenu web au nom des utilisateurs de l'intranet. Un proxy inverse autorise les demandes entrantes non sollicitées.</span><span class="sxs-lookup"><span data-stu-id="26232-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="26232-p105">**Pare-feu externe :** Autorise le trafic sortant et le trafic entrant spécifié. Peut effectuer la traduction d'adresses.</span><span class="sxs-lookup"><span data-stu-id="26232-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="26232-130">**Connexion WAN à ISP :** Connexion basée sur un opérateur à un fournisseur de services Internet, qui est homologuée avec Internet pour la connectivité et le routage.</span><span class="sxs-lookup"><span data-stu-id="26232-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="26232-131">Zones de réseau communes à tous les services cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="26232-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="26232-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="26232-132"><a name="steps"> </a></span></span>

<span data-ttu-id="26232-133">Vous devez prendre en considération ces zones de réseau lors de l’adoption des services cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="26232-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="26232-134">**Performances intranet :** Les performances des ressources basées sur Internet seront réduites si votre intranet, y compris les ordinateurs des clients, n'est pas optimisé.</span><span class="sxs-lookup"><span data-stu-id="26232-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="26232-135">**Périphériques du périmètre :** Les périphériques dans le périmètre de votre réseau sont des points de sortie et peuvent inclure des traducteurs d'adresses réseau (NAT), des serveurs proxy (y compris les proxys inverses), des pare-feux, des périphériques de détection des intrusions ou une combinaison.</span><span class="sxs-lookup"><span data-stu-id="26232-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="26232-p106">**Connexion à Internet :** Votre connexion WAN à votre fournisseur de services Internet et Internet doivent avoir une capacité suffisante pour gérer les charges de pointe. Vous pouvez également utiliser une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="26232-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="26232-p107">**Internet DNS :** A, AAAA, CNAME, MX, PTR et les autres enregistrements pour localiser le cloud de Microsoft ou les services hébergés dans le cloud. Par exemple, vous pouvez avoir besoin d'un enregistrement CNAME pour votre application hébergée dans Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="26232-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="26232-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26232-140">See Also</span></span>

<span data-ttu-id="26232-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="26232-141"><a name="steps"> </a></span></span>

[<span data-ttu-id="26232-142">Mise en réseau cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="26232-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="26232-143">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="26232-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="26232-144">Feuille de route Enterprise Cloud de Microsoft relative aux ressources pour les décideurs en matière d'informatique</span><span class="sxs-lookup"><span data-stu-id="26232-144">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


