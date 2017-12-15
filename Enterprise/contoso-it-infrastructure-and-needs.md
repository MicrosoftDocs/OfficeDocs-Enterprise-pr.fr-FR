---
title: Infrastructure et besoins informatiques de Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Résumé : Comprendre la structure de base de l'infrastructure informatique locale de Contoso et les besoins pouvant être satisfaits par les offres cloud de Microsoft."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="684e8-103">Infrastructure et besoins informatiques de Contoso</span><span class="sxs-lookup"><span data-stu-id="684e8-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="684e8-104">**Résumé :** Comprendre la structure de base de l'infrastructure informatique locale de Contoso et les besoins pouvant être satisfaits par les offres cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="684e8-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="684e8-105">Contoso passe actuellement d'une infrastructure informatique centralisée locale à une infrastructure cloud incluant des charges de travail de productivité et des applications basées sur le cloud, ainsi que des scénarios hybrides.</span><span class="sxs-lookup"><span data-stu-id="684e8-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="684e8-106">Infrastructure informatique existante de Contoso</span><span class="sxs-lookup"><span data-stu-id="684e8-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="684e8-107">Contoso utilise une infrastructure informatique locale centralisée avec des centres de données situés au siège social parisien.</span><span class="sxs-lookup"><span data-stu-id="684e8-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="684e8-108">**Figure 1 : infrastructure informatique existante de Contoso**</span><span class="sxs-lookup"><span data-stu-id="684e8-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Infrastructure informatique existante de Contoso](images/Contoso_Poster/Existing_IT.png)
  
<span data-ttu-id="684e8-110">La Figure 1 présente le siège social avec les centres de données d'applications, un DMZ et Internet.</span><span class="sxs-lookup"><span data-stu-id="684e8-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="684e8-111">Dans le DMZ de Contoso, les différents groupes de serveurs fournissent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="684e8-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="684e8-112">Accès à distance à l'intranet et au proxy web de Contoso pour les collaborateurs présents au siège social parisien.</span><span class="sxs-lookup"><span data-stu-id="684e8-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="684e8-113">Hébergement du site web public de Contoso à partir duquel les clients peuvent commander des produits, des composants ou des fournitures.</span><span class="sxs-lookup"><span data-stu-id="684e8-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="684e8-114">Hébergement de l'extranet des partenaires de Contoso pour la collaboration et la communication avec les partenaires.</span><span class="sxs-lookup"><span data-stu-id="684e8-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="684e8-115">Besoins de Contoso</span><span class="sxs-lookup"><span data-stu-id="684e8-115">Contoso's business needs</span></span>

<span data-ttu-id="684e8-116">Voici les besoins de Contoso par ordre de priorité :</span><span class="sxs-lookup"><span data-stu-id="684e8-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="684e8-117">Respecter les exigences réglementaires locales</span><span class="sxs-lookup"><span data-stu-id="684e8-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="684e8-118">Pour éviter les amendes et entretenir de bonnes relations avec les autorités locales, Contoso doit respecter les réglementations en matière de stockage et de chiffrement des données.</span><span class="sxs-lookup"><span data-stu-id="684e8-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="684e8-119">Améliorer la gestion des partenaires et des fournisseurs</span><span class="sxs-lookup"><span data-stu-id="684e8-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="684e8-p101">L'extranet des partenaires est obsolescent et coûteux à mettre à jour. Contoso souhaite le remplacer par une solution cloud qui utilise l'authentification fédérée.</span><span class="sxs-lookup"><span data-stu-id="684e8-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="684e8-122">Améliorer la productivité des collaborateurs mobiles, la gestion et les accès des appareils</span><span class="sxs-lookup"><span data-stu-id="684e8-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="684e8-123">Étant donné le nombre croissant de collaborateurs mobiles chez Contoso, une stratégie efficace de gestion des périphériques doit être mise en œuvre pour garantir la protection de la propriété intellectuelle et un meilleur accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="684e8-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="684e8-124">Réduire l'infrastructure d'accès distant</span><span class="sxs-lookup"><span data-stu-id="684e8-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="684e8-125">En plaçant dans le cloud les ressources couramment utilisées par les collaborateurs distants, Contoso réalisera des économies sur les coûts destinés à la maintenance et l'assistance de leur solution d'accès distant.</span><span class="sxs-lookup"><span data-stu-id="684e8-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="684e8-126">Réduire la taille des centres de données locaux</span><span class="sxs-lookup"><span data-stu-id="684e8-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="684e8-127">Les centres de données Contoso possèdent des centaines de serveurs, certains d'entre eux exécutent des fonctions héritées ou d'archivage qui empêchent le service informatique de gérer des charges de travail à haute valeur ajoutée.</span><span class="sxs-lookup"><span data-stu-id="684e8-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="684e8-128">Augmenter les ressources de calcul et de stockage pour le traitement de fin de trimestre</span><span class="sxs-lookup"><span data-stu-id="684e8-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="684e8-129">La comptabilité financière et le traitement des projections de fin de trimestre ainsi que la gestion des stocks nécessitent une augmentation ponctuelle des charges de stockage et des charges serveur.</span><span class="sxs-lookup"><span data-stu-id="684e8-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="684e8-130">Mappage des besoins commerciaux de Contoso aux offres cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="684e8-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="684e8-131">Après analyse des offres cloud de Microsoft, le service informatique de Contoso a établi le mappage suivant :</span><span class="sxs-lookup"><span data-stu-id="684e8-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="684e8-132">**Software as a Service (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="684e8-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="684e8-133">**Platform as a Service (Azure PaaS )**</span><span class="sxs-lookup"><span data-stu-id="684e8-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="684e8-134">**Infrastructure as a Service (Azure IaaS )**</span><span class="sxs-lookup"><span data-stu-id="684e8-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="684e8-135">**Office 365 :** Applications principales de productivité personnelle et de groupe dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="684e8-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="684e8-136">Besoins commerciaux : 1 3 5</span><span class="sxs-lookup"><span data-stu-id="684e8-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="684e8-137">Héberger les documents des services des ventes et du support technique ainsi que les systèmes d'informations à l'aide d'applications cloud.</span><span class="sxs-lookup"><span data-stu-id="684e8-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="684e8-138">Besoin commercial : 3</span><span class="sxs-lookup"><span data-stu-id="684e8-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="684e8-139">Déplacer les systèmes d'archivage et hérités vers les serveurs cloud.</span><span class="sxs-lookup"><span data-stu-id="684e8-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="684e8-140">Besoin commercial : 5</span><span class="sxs-lookup"><span data-stu-id="684e8-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="684e8-p102">**Dynamics 365 :** Utiliser la gestion des clients et des fournisseurs sur le cloud. Supprimer un partenaire extranet dans DMZ.</span><span class="sxs-lookup"><span data-stu-id="684e8-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="684e8-143">Besoin commercial : 2</span><span class="sxs-lookup"><span data-stu-id="684e8-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="684e8-144">Les applications mobiles sont dans le cloud, et pas dans le centre de données parisien.</span><span class="sxs-lookup"><span data-stu-id="684e8-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="684e8-145">Besoins commerciaux : 3 4</span><span class="sxs-lookup"><span data-stu-id="684e8-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="684e8-146">Migrer les applications et les données peu utilisées en dehors des centres de données locaux.</span><span class="sxs-lookup"><span data-stu-id="684e8-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="684e8-147">Besoin commercial : 5</span><span class="sxs-lookup"><span data-stu-id="684e8-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="684e8-148">**Intune/EMS :** Gérer les appareils iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="684e8-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="684e8-149">Besoin commercial : 3</span><span class="sxs-lookup"><span data-stu-id="684e8-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="684e8-150">Ajouter des serveurs et de l'espace de stockage temporaires pour les besoins de traitement de fin de trimestre.</span><span class="sxs-lookup"><span data-stu-id="684e8-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="684e8-151">Besoin commercial : 6</span><span class="sxs-lookup"><span data-stu-id="684e8-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="684e8-152">See Also</span><span class="sxs-lookup"><span data-stu-id="684e8-152">See Also</span></span>

[<span data-ttu-id="684e8-153">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="684e8-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="684e8-154">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="684e8-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="684e8-155">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="684e8-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


