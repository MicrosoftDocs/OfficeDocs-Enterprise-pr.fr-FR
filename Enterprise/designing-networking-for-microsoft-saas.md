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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872265"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="3dfcd-103">Conception de réseaux pour Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="3dfcd-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="3dfcd-104">**Résumé :** Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="3dfcd-105">Optimisation de votre réseau pour les services Microsoft SaaS requiert la configuration d’interne et les routeurs pour acheminer les différentes catégories de trafic aux services Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="3dfcd-106">Étapes pour préparer votre réseau aux services SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="3dfcd-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="3dfcd-107">Procédez comme suit pour optimiser votre réseau pour les services SaaS de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="3dfcd-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="3dfcd-108">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="3dfcd-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="3dfcd-109">Ajouter une connexion Internet à chacun de vos sites.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="3dfcd-110">Vérifiez que le fournisseur de services pour toutes les connexions Internet utilisez un serveur DNS avec une adresse IP locale.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="3dfcd-111">Examinez votre épingles à cheveux du réseau, les destinations intermédiaires tels que les services de sécurité en nuage et les éliminer la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="3dfcd-112">Configurer vos périphériques edge pour contourner le traitement de l’optimiser et autoriser des catégories de trafic SaaS Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="3dfcd-113">Optimisation du trafic aux SaaS services de Microsoft</span><span class="sxs-lookup"><span data-stu-id="3dfcd-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="3dfcd-114">Il existe trois catégories de trafic SaaS Microsoft :</span><span class="sxs-lookup"><span data-stu-id="3dfcd-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="3dfcd-115">Optimiser</span><span class="sxs-lookup"><span data-stu-id="3dfcd-115">Optimize</span></span>

  <span data-ttu-id="3dfcd-116">Requis pour la connectivité à tous les services Microsoft SaaS et représentent plus de 75 % de la bande passante Microsoft SaaS, des connexions et le volume de données.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="3dfcd-117">Autoriser</span><span class="sxs-lookup"><span data-stu-id="3dfcd-117">Allow</span></span>

  <span data-ttu-id="3dfcd-118">Requis pour la connectivité au spécifique SaaS Microsoft services et fonctionnalités mais ne sont pas soumis à des performances du réseau et la latence en tant que ceux de la catégorie d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="3dfcd-119">Par défaut</span><span class="sxs-lookup"><span data-stu-id="3dfcd-119">Default</span></span>

  <span data-ttu-id="3dfcd-p101">Représentent SaaS Microsoft services et les dépendances qui ne nécessitent pas de n’importe quel optimisation. Vous pouvez traiter le trafic de catégorie par défaut comme le trafic Internet normal.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="3dfcd-122">**La figure 1 : Configuration recommandée pour le trafic de tous les bureaux Microsoft SaaS**</span><span class="sxs-lookup"><span data-stu-id="3dfcd-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![La figure 1 : Configuration recommandée pour le trafic de tous les bureaux Microsoft SaaS](media/Network-Poster/SaaS1.png)

<span data-ttu-id="3dfcd-124">La figure 1 illustre la configuration recommandée de toutes les succursales, y compris les agences et celles qui sont locaux ou centrale, dans laquelle :</span><span class="sxs-lookup"><span data-stu-id="3dfcd-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="3dfcd-125">Catégorie **par défaut** et général le trafic Internet est routé vers des bureaux qui ont des serveurs proxy et autres périphériques edge pour assurer la protection contre les risques de sécurité basé sur Internet.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="3dfcd-126">**Optimiser** et **Autoriser** le trafic de catégorie est transféré directement vers le bord de Microsoft réseau front-end plus proche de l’office contenant l’utilisateur connecté, sans passer par les serveurs proxy et autres périphériques de périphérie.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="3dfcd-127">Défini par le logiciel à l’échelle (WAN SD) périphériques réseau dans les succursales séparent le trafic afin que :</span><span class="sxs-lookup"><span data-stu-id="3dfcd-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="3dfcd-128">Catégorie **par défaut** et général du trafic Internet accède à un bureau central ou régional via le réseau WAN principal.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="3dfcd-129">**Optimiser** et **Autoriser** le trafic de catégorie atteint le fournisseur de services fournissant la connexion Internet locale.</span><span class="sxs-lookup"><span data-stu-id="3dfcd-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="3dfcd-130">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="3dfcd-130">For more information, see:</span></span>
  
- [<span data-ttu-id="3dfcd-131">Principes de la connectivité réseau</span><span class="sxs-lookup"><span data-stu-id="3dfcd-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="3dfcd-132">Planification réseau et de migration pour Office 365</span><span class="sxs-lookup"><span data-stu-id="3dfcd-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="3dfcd-133">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="3dfcd-133">Next step</span></span>

[<span data-ttu-id="3dfcd-134">Conception de réseau pour Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="3dfcd-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="3dfcd-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dfcd-135">See also</span></span>

[<span data-ttu-id="3dfcd-136">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="3dfcd-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3dfcd-137">Ressources relatives à l’architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="3dfcd-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

