---
title: "Créer de A à Z"
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Résumé : Obtenir les détails sur l’ensemble du nuage des blocs de construction de stockage que vous pouvez utiliser pour créer votre propre service de stockage ou de la solution."
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="2a5f8-103">Créer de A à Z</span><span class="sxs-lookup"><span data-stu-id="2a5f8-103">Build from the ground up</span></span>

 <span data-ttu-id="2a5f8-104">**Résumé :** Obtenir les détails sur l’ensemble du nuage des blocs de construction de stockage que vous pouvez utiliser pour créer votre propre service de stockage ou de la solution.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="2a5f8-105">Les solutions de stockage à « créer de toutes pièces » :</span><span class="sxs-lookup"><span data-stu-id="2a5f8-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="2a5f8-106">Permettent de créer votre propre solution de stockage à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="2a5f8-107">Nécessite la programmation à l’aide de l’API de reste.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="2a5f8-108">Offrir le nec plus ultra de la flexibilité et de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="2a5f8-109">Les sections suivantes décrivent les détails de chaque option de stockage à « créer de toutes pièces ».</span><span class="sxs-lookup"><span data-stu-id="2a5f8-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="2a5f8-110">Stockage Azure (fichiers)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="2a5f8-111">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="2a5f8-111">Features</span></span>

- <span data-ttu-id="2a5f8-112">Facilite le déplacement d’applications héritées vers le cloud</span><span class="sxs-lookup"><span data-stu-id="2a5f8-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="2a5f8-113">Stockage d’objets blob préféré pour de nouvelles applications</span><span class="sxs-lookup"><span data-stu-id="2a5f8-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="2a5f8-114">Montage possible à partir de toute machine virtuelle Azure</span><span class="sxs-lookup"><span data-stu-id="2a5f8-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="2a5f8-115">Montage possible en local avec SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="2a5f8-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="2a5f8-116">Fonctionne avec Linux et Windows</span><span class="sxs-lookup"><span data-stu-id="2a5f8-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="2a5f8-117">Ne prend pas en charge l’authentification AD Azure ou ACL (clés de stockage Azure compte fournissent une authentification et un accès autorisé au partage de fichiers)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2a5f8-118">Utilisations courantes</span><span class="sxs-lookup"><span data-stu-id="2a5f8-118">Common uses</span></span>

- <span data-ttu-id="2a5f8-119">Migration vers le cloud d’applications héritées qui dépendent de partages de fichiers</span><span class="sxs-lookup"><span data-stu-id="2a5f8-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="2a5f8-120">Partager des outils de développement et de test</span><span class="sxs-lookup"><span data-stu-id="2a5f8-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="2a5f8-121">Des applications distribuées peuvent stocker des journaux, des données de diagnostic et des vidages sur incident</span><span class="sxs-lookup"><span data-stu-id="2a5f8-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2a5f8-122">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="2a5f8-122">Key storage scenarios</span></span>

- <span data-ttu-id="2a5f8-123">Sauvegarder des fichiers</span><span class="sxs-lookup"><span data-stu-id="2a5f8-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="2a5f8-124">Ressources</span><span class="sxs-lookup"><span data-stu-id="2a5f8-124">Resources</span></span>

<span data-ttu-id="2a5f8-125">Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="2a5f8-126">Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="2a5f8-127">Stockage Azure (blobs)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="2a5f8-128">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="2a5f8-128">Features</span></span>

- <span data-ttu-id="2a5f8-129">Chaque compte de stockage peut contenir jusqu'à 500 To (un abonnement peut avoir plusieurs comptes de stockage)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="2a5f8-130">Les comptes de stockage sont organisés en conteneurs auxquels une sécurité peut être appliquée et qui peuvent contenir des objets blob</span><span class="sxs-lookup"><span data-stu-id="2a5f8-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="2a5f8-131">Les objets blob de blocs sont optimisés pour la diffusion en continu et le stockage d’objets jusqu’à 200 Go</span><span class="sxs-lookup"><span data-stu-id="2a5f8-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="2a5f8-132">Les objets blob de pages sont optimisés pour représenter des disques PaaS et prendre en charge les écritures aléatoires jusqu’à une taille de 1 To</span><span class="sxs-lookup"><span data-stu-id="2a5f8-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="2a5f8-133">Les objets blob d’ajout sont optimisés pour ajouter des opérations jusqu’à 195 Go</span><span class="sxs-lookup"><span data-stu-id="2a5f8-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="2a5f8-134">Un stockage Premium offre un débit d’E/S plus rapide grâce au stockage SSD</span><span class="sxs-lookup"><span data-stu-id="2a5f8-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2a5f8-135">Utilisations courantes</span><span class="sxs-lookup"><span data-stu-id="2a5f8-135">Common uses</span></span>

- <span data-ttu-id="2a5f8-136">Sauvegardes de fichiers, des ordinateurs, des bases de données et des périphériques des Images et du texte pour les applications web</span><span class="sxs-lookup"><span data-stu-id="2a5f8-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="2a5f8-137">Données de configuration pour les applications cloud</span><span class="sxs-lookup"><span data-stu-id="2a5f8-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="2a5f8-138">Big Data, par exemple, journaux et autres jeux de données volumineux</span><span class="sxs-lookup"><span data-stu-id="2a5f8-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="2a5f8-139">Azure utilise Stockage Blob pour ses propres services, tels HDInsight et les disques de machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2a5f8-140">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="2a5f8-140">Key storage scenarios</span></span>

- <span data-ttu-id="2a5f8-141">Gérer des données</span><span class="sxs-lookup"><span data-stu-id="2a5f8-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="2a5f8-142">Ressources</span><span class="sxs-lookup"><span data-stu-id="2a5f8-142">Resources</span></span>

<span data-ttu-id="2a5f8-143">Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="2a5f8-144">Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="2a5f8-145">Stockage Azure (files d’attente)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="2a5f8-146">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="2a5f8-146">Features</span></span>

- <span data-ttu-id="2a5f8-147">Un compte de stockage peut contenir un nombre quelconque de files d’attente</span><span class="sxs-lookup"><span data-stu-id="2a5f8-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="2a5f8-148">Une file d’attente peut contenir un nombre quelconque de messages (jusqu’à ce que le compte de stockage soit rempli)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="2a5f8-149">Les messages en file d’attente sont automatiquement supprimés après sept jours si aucune application ne les récupère et ne les supprime</span><span class="sxs-lookup"><span data-stu-id="2a5f8-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="2a5f8-150">La taille des messages peut atteindre 64 Ko</span><span class="sxs-lookup"><span data-stu-id="2a5f8-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="2a5f8-151">Sécurisé au niveau du compte de stockage</span><span class="sxs-lookup"><span data-stu-id="2a5f8-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="2a5f8-152">Les files d’attente sont conçues pour transmettre des messages de contrôle, pas des données brutes</span><span class="sxs-lookup"><span data-stu-id="2a5f8-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2a5f8-153">Utilisations courantes</span><span class="sxs-lookup"><span data-stu-id="2a5f8-153">Common uses</span></span>

- <span data-ttu-id="2a5f8-154">Créer un backlog à traiter de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="2a5f8-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="2a5f8-155">Traitement des messages du journal</span><span class="sxs-lookup"><span data-stu-id="2a5f8-155">Processing log messages</span></span>
    
- <span data-ttu-id="2a5f8-156">Dissocier les applications</span><span class="sxs-lookup"><span data-stu-id="2a5f8-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2a5f8-157">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="2a5f8-157">Key storage scenarios</span></span>

- <span data-ttu-id="2a5f8-158">Distribuer des événements</span><span class="sxs-lookup"><span data-stu-id="2a5f8-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="2a5f8-159">Ressources</span><span class="sxs-lookup"><span data-stu-id="2a5f8-159">Resources</span></span>

<span data-ttu-id="2a5f8-160">Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="2a5f8-161">Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="2a5f8-162">Stockage Azure (tables)</span><span class="sxs-lookup"><span data-stu-id="2a5f8-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="2a5f8-163">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="2a5f8-163">Features</span></span>

- <span data-ttu-id="2a5f8-164">Idéal pour les jeux de données semi-structurés</span><span class="sxs-lookup"><span data-stu-id="2a5f8-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="2a5f8-165">Généralement plus économique qu’un SQL traditionnel</span><span class="sxs-lookup"><span data-stu-id="2a5f8-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="2a5f8-166">Très rapide si l’interrogation de la clé, ralentir si une recherche de valeur</span><span class="sxs-lookup"><span data-stu-id="2a5f8-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="2a5f8-167">Très extensible : n’importe quelle quantité de tables dans les limites du compte de stockage</span><span class="sxs-lookup"><span data-stu-id="2a5f8-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="2a5f8-168">Accessible via API REST, protocole oData limité, .NET</span><span class="sxs-lookup"><span data-stu-id="2a5f8-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="2a5f8-169">Les valeurs doivent être sérialisées</span><span class="sxs-lookup"><span data-stu-id="2a5f8-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2a5f8-170">Utilisations courantes</span><span class="sxs-lookup"><span data-stu-id="2a5f8-170">Common uses</span></span>

- <span data-ttu-id="2a5f8-171">Données utilisateur pour applications web</span><span class="sxs-lookup"><span data-stu-id="2a5f8-171">User data for web applications</span></span>
    
- <span data-ttu-id="2a5f8-172">Carnets d’adresses</span><span class="sxs-lookup"><span data-stu-id="2a5f8-172">Address books</span></span>
    
- <span data-ttu-id="2a5f8-173">Informations sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="2a5f8-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2a5f8-174">Scénarios de stockage de clés</span><span class="sxs-lookup"><span data-stu-id="2a5f8-174">Key storage scenarios</span></span>

- <span data-ttu-id="2a5f8-175">Gérer des données</span><span class="sxs-lookup"><span data-stu-id="2a5f8-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="2a5f8-176">Ressources</span><span class="sxs-lookup"><span data-stu-id="2a5f8-176">Resources</span></span>

<span data-ttu-id="2a5f8-177">Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="2a5f8-178">Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="2a5f8-179">Recommandations concernant le Stockage Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2a5f8-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="2a5f8-180">Lorsque vous concevez votre solution de stockage personnalisé avec le Stockage Microsoft Azure, gardez les points suivants à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="2a5f8-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="2a5f8-181">Tirez parti de plusieurs comptes de stockage pour une flexibilité accrue, soit via une augmentation de taille (> 100 To), soit via un débit plus important (> 5 000 opérations par seconde).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="2a5f8-182">Concevez la capacité d’ajout de comptes d’espace de stockage comme un changement de configuration, non un changement de code.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="2a5f8-183">Sélectionnez avec soin les fonctions de partitionnement pour le stockage Table, pour permettre la mise à l’échelle souhaitée en termes de performances d’insertion et de requête.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="2a5f8-184">Choisissez des noms de colonne courts pour les propriétés de table, car les métadonnées (noms de propriété) sont stockées dans la bande (les noms de colonne sont également inclus dans la taille maximale de ligne de 1 Mo).</span><span class="sxs-lookup"><span data-stu-id="2a5f8-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="2a5f8-185">Autant que possible, groupez les opérations par lots dans l’espace de stockage.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="2a5f8-186">Placez systématiquement les informations de la base de données de configuration dans un cache distribué.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="2a5f8-187">Si les performances ou la fiabilité d’une application dépendent de la disponibilité d’un certain segment de données dans le cache, votre application doit refuser les demandes entrantes jusqu’à ce que le cache soit prérempli.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="2a5f8-188">Partitionnez les données verticalement (dans une table) ou horizontalement (en segmentant la table sur plusieurs partitions) pour répartir la charge sur plusieurs bases de données.</span><span class="sxs-lookup"><span data-stu-id="2a5f8-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2a5f8-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a5f8-189">See Also</span></span>

[<span data-ttu-id="2a5f8-190">Stockage cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="2a5f8-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="2a5f8-191">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="2a5f8-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="2a5f8-192">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="2a5f8-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



