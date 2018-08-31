---
title: Architecture des scénarios de cloud hybride Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Résumé : Comprendre l'architecture d'offres de cloud hybride Microsoft."
ms.openlocfilehash: 8a0c5c37c2e0dfd0c6641128b1cee89c89e16441
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914919"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="5ebb7-103">Architecture des scénarios de cloud hybride Microsoft</span><span class="sxs-lookup"><span data-stu-id="5ebb7-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="5ebb7-104">**Résumé :** Comprendre l'architecture d'offres de cloud hybride Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="5ebb7-105">Utilisez une approche orientée architecture pour planifier et implémenter des scénarios de cloud hybride avec des services et plateformes de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="5ebb7-106">**Figure 1 : Pile du cloud hybride Microsoft**</span><span class="sxs-lookup"><span data-stu-id="5ebb7-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Pile du cloud hybride Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="5ebb7-108">La Figure 1 présente la pile du cloud hybride Microsoft et sa couche, qui incluent les applications et scénarios d’identité, réseau et locaux et la catégorie de service de cloud (SaaS Microsoft, Azure SaaS et Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="5ebb7-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="5ebb7-p101">La couche d’applications et de scénarios contient les scénarios de cloud hybride spécifiques qui sont détaillés dans les autres articles de ce modèle. Les couches locales, d’identité et réseau peuvent être communes aux catégories de service de cloud (SaaS, PaaS ou IaaS).</span><span class="sxs-lookup"><span data-stu-id="5ebb7-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="5ebb7-111">Sur site</span><span class="sxs-lookup"><span data-stu-id="5ebb7-111">On-premises</span></span>
    
    <span data-ttu-id="5ebb7-p102">L’infrastructure locale pour les scénarios hybrides peut inclure des serveurs pour SharePoint, Exchange, Skype Entreprise et des applications métier. Elle peut également inclure des banques de données (bases de données, listes, fichiers). Sans connexions ExpressRoute, l’accès à la banque de données stockées locale doit être autorisé via un proxy inverse ou en rendant le serveur ou les données accessibles sur votre zone DMZ ou extranet.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="5ebb7-115">Réseau</span><span class="sxs-lookup"><span data-stu-id="5ebb7-115">Network</span></span>
    
    <span data-ttu-id="5ebb7-p103">Il existe deux possibilités pour la connectivité à plateformes en nuage de Microsoft et des services : les ExpressRoute canal Internet existant. Utiliser une connexion ExpressRoute si des performances prévisibles sont important. Vous pouvez utiliser une connexion ExpressRoute pour vous connecter directement à des services Azure IaaS, PaaS Azure services et services Microsoft SaaS (Office 365 et Dynamics 365).</span><span class="sxs-lookup"><span data-stu-id="5ebb7-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="5ebb7-119">Identité</span><span class="sxs-lookup"><span data-stu-id="5ebb7-119">Identity</span></span>
    
    <span data-ttu-id="5ebb7-p104">Pour l’infrastructure d’identité de cloud, il y a deux façons de procéder, en fonction de la plateforme de cloud Microsoft. Pour SaaS et Azure PaaS, intégrez votre infrastructure d’identité locale avec Azure AD ou effectuez une fédération avec vos fournisseurs d’identité tiers ou d’infrastructure d’identité locale. Pour les ordinateurs virtuels exécutés dans Azure, vous pouvez étendre votre infrastructure d’identité locale, telle que Windows Server AD, aux réseaux virtuels où résident vos ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="5ebb7-123">Scénarios de cloud hybride pour le processus d’adoption du cloud en trois phases</span><span class="sxs-lookup"><span data-stu-id="5ebb7-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="5ebb7-p105">De nombreuses entreprises, y compris celles détenues par Microsoft, utilisent une approche à trois phases pour adopter le cloud. Les scénarios de cloud hybride peuvent jouer un rôle dans chaque phase.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="5ebb7-126">Déplacement des charges de travail de productivité vers les services SaaS</span><span class="sxs-lookup"><span data-stu-id="5ebb7-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="5ebb7-127">Pour les charges de travail de productivité qui se trouvent actuellement en local ou qui doivent y demeurer, les scénarios hybrides permettent de les intégrer à leur équivalent dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="5ebb7-128">Développement de nouvelles applications modernes dans les services PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="5ebb7-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="5ebb7-129">Les applications hybrides PaaS Azure peuvent tirer parti en toute sécurité des ressources de serveur ou de stockage locales.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="5ebb7-130">Déplacement d’applications existantes vers les services IaaS Azure</span><span class="sxs-lookup"><span data-stu-id="5ebb7-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="5ebb7-131">Pour les scénarios de réplication dans le cloud (« lift-and-shift ») et de refonte orientée cloud (« build-in-the-cloud »), les applications serveur exécutées sur des ordinateurs virtuels Azure offrent des possibilités de configuration et de mise à l’échelle faciles à mettre en œuvre.</span><span class="sxs-lookup"><span data-stu-id="5ebb7-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5ebb7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ebb7-132">See Also</span></span>

[<span data-ttu-id="5ebb7-133">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="5ebb7-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="5ebb7-134">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5ebb7-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="5ebb7-135">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="5ebb7-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



