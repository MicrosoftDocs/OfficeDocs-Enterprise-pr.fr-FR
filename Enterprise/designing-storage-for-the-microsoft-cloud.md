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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Résumé : Découvrez pourquoi vous avez besoin de stockage cloud et passez en revue la liste des options de stockage cloud de Microsoft et les principaux scénarios de stockage."
ms.openlocfilehash: 199e385ea0238e8fb27c04153faf177df07e1025
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="b5beb-103">Conception d’espace de stockage pour le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5beb-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="b5beb-104">**Résumé :** Découvrez pourquoi vous avez besoin de stockage cloud et passez en revue la liste des options de stockage cloud de Microsoft et les principaux scénarios de stockage.</span><span class="sxs-lookup"><span data-stu-id="b5beb-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="b5beb-105">L’intégration de votre espace de stockage aux services de cloud computing Microsoft permet d’accéder à un vaste éventail de services et d’options de plateforme cloud.</span><span class="sxs-lookup"><span data-stu-id="b5beb-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="b5beb-106">Pourquoi un stockage cloud ?</span><span class="sxs-lookup"><span data-stu-id="b5beb-106">Why cloud storage?</span></span>

<span data-ttu-id="b5beb-107">Il y a deux raisons principales à l’utilisation du stockage cloud.</span><span class="sxs-lookup"><span data-stu-id="b5beb-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="b5beb-108">Vitesse de mise sur le marché :</span><span class="sxs-lookup"><span data-stu-id="b5beb-108">Speed to market:</span></span>
    
  - <span data-ttu-id="b5beb-109">Configuration plus rapide pour la haute disponibilité et la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="b5beb-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="b5beb-110">Aucun matériel de stockage à acheter</span><span class="sxs-lookup"><span data-stu-id="b5beb-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="b5beb-111">Plomberie intégrée fournie par les offres cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5beb-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="b5beb-112">Disponible partout dans le monde</span><span class="sxs-lookup"><span data-stu-id="b5beb-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="b5beb-113">Coûts de maintenance réduits :</span><span class="sxs-lookup"><span data-stu-id="b5beb-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="b5beb-114">Élasticité de mise à l’échelle en fonction de la demande de stockage</span><span class="sxs-lookup"><span data-stu-id="b5beb-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="b5beb-115">Aucun matériel de stockage dont effectuer la maintenance ou à migrer</span><span class="sxs-lookup"><span data-stu-id="b5beb-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="b5beb-116">Microsoft est votre plombier intégré pour la maintenance et l’amélioration de l’infrastructure</span><span class="sxs-lookup"><span data-stu-id="b5beb-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="b5beb-117">Meilleure sécurité de stockage du marché grâce à des améliorations continues</span><span class="sxs-lookup"><span data-stu-id="b5beb-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="b5beb-118">Options de stockage cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5beb-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="b5beb-119">Pour vous aider à comprendre les diverses options de stockage cloud, nous utilisons une analogie de construction.</span><span class="sxs-lookup"><span data-stu-id="b5beb-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="b5beb-120">Solutions prêtes à installer</span><span class="sxs-lookup"><span data-stu-id="b5beb-120">Move-in ready</span></span>

<span data-ttu-id="b5beb-p101">Utilisez ces solutions prépackagées incluant des services existants. Soyez immédiatement opérationnel avec un minimum de configuration.</span><span class="sxs-lookup"><span data-stu-id="b5beb-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="b5beb-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="b5beb-123">Office 365</span></span>
    
- <span data-ttu-id="b5beb-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="b5beb-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="b5beb-125">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="b5beb-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="b5beb-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b5beb-126">Dynamics 365</span></span>
    
- <span data-ttu-id="b5beb-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="b5beb-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="b5beb-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="b5beb-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="b5beb-129">Site de partage Yammer</span><span class="sxs-lookup"><span data-stu-id="b5beb-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="b5beb-130">Sauvegarde Azure</span><span class="sxs-lookup"><span data-stu-id="b5beb-130">Azure Backup</span></span>
    
<span data-ttu-id="b5beb-131">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Solutions prêtes à installer](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="b5beb-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="b5beb-132">Certains assembly requis</span><span class="sxs-lookup"><span data-stu-id="b5beb-132">Some assembly required</span></span>

<span data-ttu-id="b5beb-133">Utilisez ces services existants comme point de départ pour votre solution de stockage, avec une configuration ou un codage supplémentaire pour obtenir une solution personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b5beb-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="b5beb-134">Réseau de distribution de contenu Azure</span><span class="sxs-lookup"><span data-stu-id="b5beb-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="b5beb-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="b5beb-135">Azure Media Services</span></span>
    
- <span data-ttu-id="b5beb-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="b5beb-136">HdInsight</span></span>
    
- <span data-ttu-id="b5beb-137">Cache Redis Azure</span><span class="sxs-lookup"><span data-stu-id="b5beb-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="b5beb-138">Base de données SQL Azure</span><span class="sxs-lookup"><span data-stu-id="b5beb-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="b5beb-139">SQL Server sur machine virtuelle Azure</span><span class="sxs-lookup"><span data-stu-id="b5beb-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="b5beb-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b5beb-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="b5beb-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="b5beb-141">StorSimple</span></span>
    
- <span data-ttu-id="b5beb-142">Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="b5beb-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="b5beb-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="b5beb-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="b5beb-144">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Certains assembly requis](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="b5beb-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="b5beb-145">Créer de A à Z</span><span class="sxs-lookup"><span data-stu-id="b5beb-145">Build from the ground up</span></span>

<span data-ttu-id="b5beb-146">Utilisez ces blocs de construction de stockage, ainsi qu’un codage, pour créer votre propre solution de stockage ou des applications de A à Z.</span><span class="sxs-lookup"><span data-stu-id="b5beb-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="b5beb-147">Stockage Azure (fichiers)</span><span class="sxs-lookup"><span data-stu-id="b5beb-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="b5beb-148">Stockage Azure (blobs)</span><span class="sxs-lookup"><span data-stu-id="b5beb-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="b5beb-149">Stockage Azure (files d’attente)</span><span class="sxs-lookup"><span data-stu-id="b5beb-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="b5beb-150">Stockage Azure (tables)</span><span class="sxs-lookup"><span data-stu-id="b5beb-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="b5beb-151">Pour obtenir des informations sur chacune de ces options de stockage cloud, consultez l'article [Créer de A à Z](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="b5beb-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="b5beb-152">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="b5beb-152">Key storage scenarios</span></span>

<span data-ttu-id="b5beb-153">Voici les principaux scénarios qui nécessitent un stockage basé sur le cloud :</span><span class="sxs-lookup"><span data-stu-id="b5beb-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="b5beb-154">Mettre en cache des données</span><span class="sxs-lookup"><span data-stu-id="b5beb-154">Cache data</span></span>
    
    <span data-ttu-id="b5beb-155">Accélérez l’accès aux données fréquemment utilisées en les stockant dans un cache à haut débit.</span><span class="sxs-lookup"><span data-stu-id="b5beb-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="b5beb-156">Collaborer avec les membres d’une équipe</span><span class="sxs-lookup"><span data-stu-id="b5beb-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="b5beb-157">Autorisez plusieurs utilisateurs à accéder aux données du stockage cloud.</span><span class="sxs-lookup"><span data-stu-id="b5beb-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="b5beb-158">Gérer des données</span><span class="sxs-lookup"><span data-stu-id="b5beb-158">Manage data</span></span>
    
    <span data-ttu-id="b5beb-159">Stockez, déplacez ou supprimez des données en bloc internes ou externes.</span><span class="sxs-lookup"><span data-stu-id="b5beb-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="b5beb-160">Gérer le code source</span><span class="sxs-lookup"><span data-stu-id="b5beb-160">Manage source code</span></span>
    
    <span data-ttu-id="b5beb-161">Chargez et exécutez des fichiers de code d’application dans le cloud, et collaborez sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="b5beb-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="b5beb-162">Sauvegarder des fichiers</span><span class="sxs-lookup"><span data-stu-id="b5beb-162">Backup files</span></span>
    
    <span data-ttu-id="b5beb-163">Stockez des copies de données internes ou externes hors site dans plusieurs emplacements du cloud.</span><span class="sxs-lookup"><span data-stu-id="b5beb-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="b5beb-164">Publier des communications d’entreprise</span><span class="sxs-lookup"><span data-stu-id="b5beb-164">Publish company communications</span></span>
    
    <span data-ttu-id="b5beb-165">Créez un point de publication unique pour les messages internes ou externes.</span><span class="sxs-lookup"><span data-stu-id="b5beb-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="b5beb-166">Distribuer des millions d’événements</span><span class="sxs-lookup"><span data-stu-id="b5beb-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="b5beb-167">Créez un espace de stockage pour l’ingestion de la télémétrie de sites web, d’applications et d’appareils.</span><span class="sxs-lookup"><span data-stu-id="b5beb-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="b5beb-168">Gérer et diffuser des vidéos</span><span class="sxs-lookup"><span data-stu-id="b5beb-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="b5beb-169">Stockez et diffusez du contenu vidéo à des clients ou à des utilisateurs au sein de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="b5beb-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b5beb-170">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="b5beb-170">Next step</span></span>

<span data-ttu-id="b5beb-171">Consultez les options de stockage cloud décrites dans l'article [Solutions prêtes à installer](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="b5beb-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5beb-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5beb-172">See Also</span></span>

[<span data-ttu-id="b5beb-173">Stockage cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="b5beb-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="b5beb-174">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5beb-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="b5beb-175">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="b5beb-175">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>


