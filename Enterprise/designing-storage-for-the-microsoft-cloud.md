---
title: "Conception d’espace de stockage pour le cloud de Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Résumé : Découvrez pourquoi vous avez besoin de stockage cloud et passez en revue la liste des options de stockage cloud de Microsoft et les principaux scénarios de stockage."
ms.openlocfilehash: 3501f6a39498276d02fe4178f701a06dfb6a3e93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="1f959-103">Conception d’espace de stockage pour le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1f959-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="1f959-104">**Résumé :** Découvrez pourquoi vous avez besoin de stockage cloud et passez en revue la liste des options de stockage cloud de Microsoft et les principaux scénarios de stockage.</span><span class="sxs-lookup"><span data-stu-id="1f959-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="1f959-105">L’intégration de votre espace de stockage aux services de cloud computing Microsoft permet d’accéder à un vaste éventail de services et d’options de plateforme cloud.</span><span class="sxs-lookup"><span data-stu-id="1f959-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="1f959-106">Pourquoi un stockage cloud ?</span><span class="sxs-lookup"><span data-stu-id="1f959-106">Why cloud storage?</span></span>

<span data-ttu-id="1f959-107">Il y a deux raisons principales à l’utilisation du stockage cloud.</span><span class="sxs-lookup"><span data-stu-id="1f959-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="1f959-108">Vitesse de mise sur le marché :</span><span class="sxs-lookup"><span data-stu-id="1f959-108">Speed to market:</span></span>
    
  - <span data-ttu-id="1f959-109">Configuration plus rapide pour la haute disponibilité et la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="1f959-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="1f959-110">Aucun matériel de stockage à acheter</span><span class="sxs-lookup"><span data-stu-id="1f959-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="1f959-111">Plomberie intégrée fournie par les offres cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1f959-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="1f959-112">Disponible partout dans le monde</span><span class="sxs-lookup"><span data-stu-id="1f959-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="1f959-113">Coûts de maintenance réduits :</span><span class="sxs-lookup"><span data-stu-id="1f959-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="1f959-114">Élasticité de mise à l’échelle en fonction de la demande de stockage</span><span class="sxs-lookup"><span data-stu-id="1f959-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="1f959-115">Aucun matériel de stockage dont effectuer la maintenance ou à migrer</span><span class="sxs-lookup"><span data-stu-id="1f959-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="1f959-116">Microsoft est votre plombier intégré pour la maintenance et l’amélioration de l’infrastructure</span><span class="sxs-lookup"><span data-stu-id="1f959-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="1f959-117">Meilleure sécurité de stockage du marché grâce à des améliorations continues</span><span class="sxs-lookup"><span data-stu-id="1f959-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="1f959-118">Options de stockage cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1f959-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="1f959-119">Pour vous aider à comprendre les diverses options de stockage cloud, nous utilisons une analogie de construction.</span><span class="sxs-lookup"><span data-stu-id="1f959-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="1f959-120">Solutions prêtes à installer</span><span class="sxs-lookup"><span data-stu-id="1f959-120">Move-in ready</span></span>

<span data-ttu-id="1f959-p101">Utilisez ces solutions prépackagées incluant des services existants. Soyez immédiatement opérationnel avec un minimum de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f959-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="1f959-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="1f959-123">Office 365</span></span>
    
- <span data-ttu-id="1f959-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="1f959-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="1f959-125">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="1f959-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="1f959-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1f959-126">Dynamics 365</span></span>
    
- <span data-ttu-id="1f959-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="1f959-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="1f959-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="1f959-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="1f959-129">Site de partage Yammer</span><span class="sxs-lookup"><span data-stu-id="1f959-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="1f959-130">Sauvegarde Azure</span><span class="sxs-lookup"><span data-stu-id="1f959-130">Azure Backup</span></span>
    
<span data-ttu-id="1f959-131">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Solutions prêtes à installer](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="1f959-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="1f959-132">Certains assembly requis</span><span class="sxs-lookup"><span data-stu-id="1f959-132">Some assembly required</span></span>

<span data-ttu-id="1f959-133">Utilisez ces services existants comme point de départ pour votre solution de stockage, avec une configuration ou un codage supplémentaire pour obtenir une solution personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1f959-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="1f959-134">Réseau de distribution de contenu Azure</span><span class="sxs-lookup"><span data-stu-id="1f959-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="1f959-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="1f959-135">Azure Media Services</span></span>
    
- <span data-ttu-id="1f959-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="1f959-136">HdInsight</span></span>
    
- <span data-ttu-id="1f959-137">Cache Redis Azure</span><span class="sxs-lookup"><span data-stu-id="1f959-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="1f959-138">Base de données SQL Azure</span><span class="sxs-lookup"><span data-stu-id="1f959-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="1f959-139">SQL Server sur machine virtuelle Azure</span><span class="sxs-lookup"><span data-stu-id="1f959-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="1f959-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1f959-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="1f959-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="1f959-141">StorSimple</span></span>
    
- <span data-ttu-id="1f959-142">Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="1f959-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="1f959-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="1f959-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="1f959-144">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Certains assembly requis](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="1f959-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="1f959-145">Créer de A à Z</span><span class="sxs-lookup"><span data-stu-id="1f959-145">Build from the ground up</span></span>

<span data-ttu-id="1f959-146">Utilisez ces blocs de construction de stockage, ainsi qu’un codage, pour créer votre propre solution de stockage ou des applications de A à Z.</span><span class="sxs-lookup"><span data-stu-id="1f959-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="1f959-147">Stockage Azure (fichiers)</span><span class="sxs-lookup"><span data-stu-id="1f959-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="1f959-148">Stockage Azure (blobs)</span><span class="sxs-lookup"><span data-stu-id="1f959-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="1f959-149">Stockage Azure (files d’attente)</span><span class="sxs-lookup"><span data-stu-id="1f959-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="1f959-150">Stockage Azure (tables)</span><span class="sxs-lookup"><span data-stu-id="1f959-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="1f959-151">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Créer de A à Z](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="1f959-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="1f959-152">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="1f959-152">Key storage scenarios</span></span>

<span data-ttu-id="1f959-153">Voici les principaux scénarios qui nécessitent un stockage basé sur le cloud :</span><span class="sxs-lookup"><span data-stu-id="1f959-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="1f959-154">Mettre en cache des données</span><span class="sxs-lookup"><span data-stu-id="1f959-154">Cache data</span></span>
    
    <span data-ttu-id="1f959-155">Accélérez l’accès aux données fréquemment utilisées en les stockant dans un cache à haut débit.</span><span class="sxs-lookup"><span data-stu-id="1f959-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="1f959-156">Collaborer avec les membres d’une équipe</span><span class="sxs-lookup"><span data-stu-id="1f959-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="1f959-157">Autorisez plusieurs utilisateurs à accéder aux données du stockage cloud.</span><span class="sxs-lookup"><span data-stu-id="1f959-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="1f959-158">Gérer des données</span><span class="sxs-lookup"><span data-stu-id="1f959-158">Manage data</span></span>
    
    <span data-ttu-id="1f959-159">Stockez, déplacez ou supprimez des données en bloc internes ou externes.</span><span class="sxs-lookup"><span data-stu-id="1f959-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="1f959-160">Gérer le code source</span><span class="sxs-lookup"><span data-stu-id="1f959-160">Manage source code</span></span>
    
    <span data-ttu-id="1f959-161">Chargez et exécutez des fichiers de code d’application dans le cloud, et collaborez sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="1f959-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="1f959-162">Sauvegarder des fichiers</span><span class="sxs-lookup"><span data-stu-id="1f959-162">Backup files</span></span>
    
    <span data-ttu-id="1f959-163">Stockez des copies de données internes ou externes hors site dans plusieurs emplacements du cloud.</span><span class="sxs-lookup"><span data-stu-id="1f959-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="1f959-164">Publier des communications d’entreprise</span><span class="sxs-lookup"><span data-stu-id="1f959-164">Publish company communications</span></span>
    
    <span data-ttu-id="1f959-165">Créez un point de publication unique pour les messages internes ou externes.</span><span class="sxs-lookup"><span data-stu-id="1f959-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="1f959-166">Distribuer des millions d’événements</span><span class="sxs-lookup"><span data-stu-id="1f959-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="1f959-167">Créez un espace de stockage pour l’ingestion de la télémétrie de sites web, d’applications et d’appareils.</span><span class="sxs-lookup"><span data-stu-id="1f959-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="1f959-168">Gérer et diffuser des vidéos</span><span class="sxs-lookup"><span data-stu-id="1f959-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="1f959-169">Stockez et diffusez du contenu vidéo à des clients ou à des utilisateurs au sein de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="1f959-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="1f959-170">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="1f959-170">Next step</span></span>

<span data-ttu-id="1f959-171">Consultez les options de stockage cloud décrites dans l'article [Solutions prêtes à installer](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="1f959-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1f959-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f959-172">See Also</span></span>

[<span data-ttu-id="1f959-173">Stockage cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="1f959-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="1f959-174">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="1f959-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="1f959-175">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="1f959-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


