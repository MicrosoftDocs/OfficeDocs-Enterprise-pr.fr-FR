---
title: Conception de réseaux pour Microsoft SaaS
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Résumé : Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487294"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="06114-103">Conception de réseaux pour Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="06114-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="06114-104">**Résumé :** Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="06114-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="06114-105">L’optimisation de votre réseau pour les services SaaS de Microsoft requiert la configuration des équipements de périmètre et internes pour acheminer les différentes catégories de trafic vers les services SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="06114-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="06114-106">Étapes pour préparer votre réseau aux services SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="06114-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="06114-107">Procédez comme suit pour optimiser votre réseau pour les services SaaS de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="06114-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="06114-108">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="06114-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="06114-109">Ajoutez une connexion Internet à chacun de vos bureaux.</span><span class="sxs-lookup"><span data-stu-id="06114-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="06114-110">Assurez-vous que les fournisseurs de services Internet de toutes les connexions Internet utilisent un serveur DNS avec une adresse IP locale.</span><span class="sxs-lookup"><span data-stu-id="06114-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="06114-111">Examinez votre réseau les épingles, les destinations intermédiaires, telles que les services de sécurité en nuage, et supprimez-les si possible.</span><span class="sxs-lookup"><span data-stu-id="06114-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="06114-112">ConFigurez vos périphériques Edge pour qu'ils contournent le traitement pour les catégories Optimize et allow du trafic SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="06114-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="06114-113">Optimisation du trafic vers les services SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="06114-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="06114-114">Il existe trois catégories de trafic Microsoft SaaS:</span><span class="sxs-lookup"><span data-stu-id="06114-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="06114-115">Optimiser</span><span class="sxs-lookup"><span data-stu-id="06114-115">Optimize</span></span>

  <span data-ttu-id="06114-116">Obligatoire pour la connectivité à chaque service SaaS de Microsoft et représente plus de 75% de la bande passante de Microsoft SaaS, des connexions et du volume de données.</span><span class="sxs-lookup"><span data-stu-id="06114-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="06114-117">Autoriser</span><span class="sxs-lookup"><span data-stu-id="06114-117">Allow</span></span>

  <span data-ttu-id="06114-118">Requis pour la connectivité à des services et des fonctionnalités Microsoft SaaS spécifiques, mais qui ne sont pas sensibles aux performances et à la latence du réseau comme ceux de la catégorie optimize.</span><span class="sxs-lookup"><span data-stu-id="06114-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="06114-119">Par défaut</span><span class="sxs-lookup"><span data-stu-id="06114-119">Default</span></span>

  <span data-ttu-id="06114-120">Représentent les services et dépendances Microsoft SaaS qui ne nécessitent aucune optimisation.</span><span class="sxs-lookup"><span data-stu-id="06114-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="06114-121">Vous pouvez traiter le trafic de catégorie par défaut comme le trafic Internet normal.</span><span class="sxs-lookup"><span data-stu-id="06114-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="06114-122">**Figure 1: configuration recommandée pour le trafic SaaS de Microsoft pour tous les bureaux**</span><span class="sxs-lookup"><span data-stu-id="06114-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Figure 1: configuration recommandée pour le trafic SaaS de Microsoft pour tous les bureaux](media/Network-Poster/SaaS1.png)

<span data-ttu-id="06114-124">La figure 1 présente la configuration recommandée de tous les bureaux, y compris les succursales, les succursales régionales ou centrales, dans lesquelles:</span><span class="sxs-lookup"><span data-stu-id="06114-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="06114-125">La catégorie **par défaut** et le trafic Internet général sont acheminés vers les bureaux disposant de serveurs proxy et d'autres périphériques Edge pour fournir une protection contre les risques de sécurité Internet.</span><span class="sxs-lookup"><span data-stu-id="06114-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="06114-126">**Optimiser** et **autoriser** le trafic de catégorie est transféré directement vers le serveur frontal le plus proche de l'extrémité du réseau Microsoft vers le bureau contenant l'utilisateur qui se connecte, en contournant les serveurs proxy et autres périphériques Edge.</span><span class="sxs-lookup"><span data-stu-id="06114-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="06114-127">Les périphériques SD-WAN (réseau étendu) définis par le logiciel dans les succursales séparent les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="06114-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="06114-128">La catégorie **par défaut** et le trafic Internet général sont acheminés vers un bureau central ou régional sur le réseau principal du réseau étendu.</span><span class="sxs-lookup"><span data-stu-id="06114-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="06114-129">**Optimiser** et **autoriser** le trafic de catégorie vers le fournisseur de services Internet fournissant la connexion Internet locale.</span><span class="sxs-lookup"><span data-stu-id="06114-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="06114-130">Pour plus d’informations, reportez-vous aux rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="06114-130">For more information, see:</span></span>
  
- [<span data-ttu-id="06114-131">Principes de connectivité réseau</span><span class="sxs-lookup"><span data-stu-id="06114-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="06114-132">Planification réseau et de migration pour Office 365</span><span class="sxs-lookup"><span data-stu-id="06114-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="06114-133">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="06114-133">Next step</span></span>

[<span data-ttu-id="06114-134">Conception de réseau pour Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="06114-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="06114-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06114-135">See also</span></span>

[<span data-ttu-id="06114-136">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="06114-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="06114-137">Ressources relatives à l’architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="06114-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

