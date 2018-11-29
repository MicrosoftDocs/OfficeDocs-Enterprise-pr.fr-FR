---
title: Conception de réseau pour Microsoft Azure PaaS
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Résumé : Comprenez comment optimiser votre réseau pour accéder à Microsoft Azure PaaS.'
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872235"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="55c78-103">Conception de réseau pour Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="55c78-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="55c78-104">**Résumé :** Comprenez comment optimiser votre réseau pour accéder à Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="55c78-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="55c78-105">L’optimisation du réseau pour les applications Azure PaaS requiert une bande passante Internet appropriée et peut nécessiter la distribution du trafic réseau sur plusieurs sites ou applications.</span><span class="sxs-lookup"><span data-stu-id="55c78-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="55c78-106">Étapes de planification pour l’hébergement des applications PaaS d’entreprise dans Azure</span><span class="sxs-lookup"><span data-stu-id="55c78-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="55c78-107">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="55c78-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="55c78-108">Optimisez votre bande passante Internet en suivant les étapes 2 à 4 de la **procédure de préparation de votre réseau pour les services Microsoft SaaS** fournie dans [Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="55c78-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="55c78-109">Déterminez si vous avez besoin d’une connexion ExpressRoute à Azure.</span><span class="sxs-lookup"><span data-stu-id="55c78-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="55c78-110">Pour les charges de travail basées sur Internet, déterminez si vous avez besoin d’Azure Application Gateway.</span><span class="sxs-lookup"><span data-stu-id="55c78-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="55c78-111">Pour distribuer le trafic sur différents points de terminaison dans divers centres de données, déterminez si vous avez besoin d’Azure Traffic Manager.</span><span class="sxs-lookup"><span data-stu-id="55c78-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="55c78-112">Bande passante Internet pour les applications PaaS d’entreprise</span><span class="sxs-lookup"><span data-stu-id="55c78-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="55c78-p101">Les applications d’entreprise hébergées dans Azure PaaS nécessitent une bande passante Internet pour les utilisateurs de l’intranet. Il existe deux options :</span><span class="sxs-lookup"><span data-stu-id="55c78-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="55c78-p102">**Option 1 :** utilisez votre canal existant, optimisé pour le trafic Internet avec la capacité à gérer les charges de pointe. Voir[Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md) pour le périmètre Internet, l'utilisation client et les considérations relatives aux opérations informatiques.</span><span class="sxs-lookup"><span data-stu-id="55c78-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="55c78-117">**Option 2 :** pour une bande passante élevée ou des besoins de latence faible, utilisez une connexion ExpressRoute à Azure.</span><span class="sxs-lookup"><span data-stu-id="55c78-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="55c78-118">**Figure 1 : Options de connexion pour les services Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="55c78-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figure 1 : options de connexion pour les services PaaS Azure](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="55c78-120">La figure 1 montre une connexion du réseau local aux services Azure PaaS via un canal Internet ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="55c78-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="55c78-121">Azure Application Gateway</span><span class="sxs-lookup"><span data-stu-id="55c78-121">Azure Application Gateway</span></span>

<span data-ttu-id="55c78-122">Routage au niveau des applications et services d’équilibrage de charge vous permettant de générer un site web frontal évolutif et hautement disponible dans Azure pour les applications web, les services cloud et les machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="55c78-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="55c78-123">**Figure 2 : Azure Application Gateway**</span><span class="sxs-lookup"><span data-stu-id="55c78-123">**Figure 2: Azure Application Gateway**</span></span>

![Figure 2 : service Application Gateway d’Azure](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="55c78-125">La figure 2 présente Azure Application Gateway et indique comment les demandes utilisateur provenant d’Internet peuvent être acheminées vers les applications web Azure, les services cloud ou les machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="55c78-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="55c78-126">Application Gateway prend actuellement en charge la remise d’application de couche 7 pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="55c78-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="55c78-127">Équilibrage de charge HTTP</span><span class="sxs-lookup"><span data-stu-id="55c78-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="55c78-128">Affinité de session basée sur les cookies</span><span class="sxs-lookup"><span data-stu-id="55c78-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="55c78-129">Déchargement SSL</span><span class="sxs-lookup"><span data-stu-id="55c78-129">SSL offload</span></span>
    
<span data-ttu-id="55c78-130">Pour plus d'informations, voir [Vue d'ensemble d'Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="55c78-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="55c78-131">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="55c78-131">Azure Traffic Manager</span></span>

<span data-ttu-id="55c78-132">Distribution du trafic sur différents points de terminaison qui peuvent inclure des services cloud ou des applications web Azure situés dans différents centres de données ou points de terminaison externes.</span><span class="sxs-lookup"><span data-stu-id="55c78-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="55c78-133">Traffic Manager utilise les méthodes de routage suivantes :</span><span class="sxs-lookup"><span data-stu-id="55c78-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="55c78-134">**Basculement :** les points de terminaison sont dans un ou plusieurs centres de données Azure et vous souhaitez utiliser un point de terminaison principal pour tout le trafic, mais vous fournissez des sauvegardes au cas où les points de terminaison de sauvegarde ou principal ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="55c78-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="55c78-135">**Tourniquet (round robin) :** vous souhaitez répartir la charge sur un ensemble de points de terminaison dans le même centre de données ou entre différents centres de données.</span><span class="sxs-lookup"><span data-stu-id="55c78-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="55c78-136">**Performances :** vous avez des points de terminaison dans différentes zones géographiques et vous souhaitez demander aux clients d'utiliser le point de terminaison « le plus proche » pour la latence la plus faible.</span><span class="sxs-lookup"><span data-stu-id="55c78-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="55c78-137">Voici un exemple de trois applications web dispersées géographiquement.</span><span class="sxs-lookup"><span data-stu-id="55c78-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="55c78-138">**Figure 3 : Azure Traffic Manager**</span><span class="sxs-lookup"><span data-stu-id="55c78-138">**Figure 3: Azure Traffic Manager**</span></span>

![Figure 3 : Azure Traffic Manager](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="55c78-p103">La figure 3 indique le processus simple utilisé par Traffic Manager pour acheminer les requêtes vers trois applications web Azure différentes aux États-Unis, en Europe et en Asie. Dans l’exemple :</span><span class="sxs-lookup"><span data-stu-id="55c78-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="55c78-142">Une requête DNS utilisateur pour une URL de site web est dirigée vers Azure Traffic Manager, qui renvoie le nom d’une application web régionale, selon la méthode de routage de performances.</span><span class="sxs-lookup"><span data-stu-id="55c78-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="55c78-143">L’utilisateur lance le trafic avec l’application web régionale en Europe.</span><span class="sxs-lookup"><span data-stu-id="55c78-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="55c78-144">Pour plus d’informations, consultez la rubrique [Vue d’ensemble de Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)</span><span class="sxs-lookup"><span data-stu-id="55c78-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="55c78-145">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="55c78-145">Next step</span></span>

[<span data-ttu-id="55c78-146">Conception de réseaux pour Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="55c78-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="55c78-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c78-147">See also</span></span>

[<span data-ttu-id="55c78-148">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="55c78-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="55c78-149">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="55c78-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

