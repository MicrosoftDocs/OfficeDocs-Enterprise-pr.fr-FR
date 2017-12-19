---
title: "Déplacement des données de transaction historiques dans le cloud"
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
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "Résumé : Comment Contoso a implémenté SQL Server Stretch Database pour réduire ses besoins en matière de stockage de données locales et ses dépenses quotidiennes de fonctionnement."
ms.openlocfilehash: f1a44a14da49c394974755f7c557013717c4ccef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="87a53-103">Déplacement des données de transaction historiques dans le cloud</span><span class="sxs-lookup"><span data-stu-id="87a53-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="87a53-104">**Résumé :** Comment Contoso a implémenté SQL Server Stretch Database pour réduire ses besoins en matière de stockage de données locales et ses dépenses quotidiennes de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="87a53-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="87a53-p101">Le système de stockage d'entreprise de Contoso stocke une grande quantité de données de transaction historiques pour garantir le respect des exigences réglementaires et réaliser des études marketing et analyses décisionnelles sur les tendances des dépenses. Contoso doit également restaurer les données archivées sur des bandes magnétiques, ce qui prend beaucoup de temps. La date de fin de vie utile du matériel utilisé dans le système de stockage d'entreprise de Contoso approchait, et son remplacement aurait eu un coût important.</span><span class="sxs-lookup"><span data-stu-id="87a53-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="87a53-p102">Dans la mesure où l'entreprise avait besoin de réduire la taille de ses centres de données locales, Contoso a choisi de procéder à la mise à niveau vers SQL Server 2016 en raison de la fonction hybride de Stretch Database et de son intégration transparente avec Azure. Stretch Database permet à Contoso de déplacer les données froides de ses tables depuis son emplacement de stockage local vers le cloud, pour libérer de l'espace disque local et réduire la maintenance. Les données froides et chaudes se trouvent dans les mêmes tables, peuvent toujours être utilisées par les applications et leurs utilisateurs, et restent disponibles pour les opérations de maintenance, telles que les sauvegardes et les restaurations. La figure 1 présente Stretch Database.</span><span class="sxs-lookup"><span data-stu-id="87a53-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="87a53-112">**Figure 1 : SQL Server Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="87a53-112">**Figure 1: SQL Server Stretch Database**</span></span>

![Stretch Database avec SQL Server comme solution de données hybride](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="87a53-114">La figure 1 montre comment un client SQL envoie des requêtes T-SQL sur un serveur qui exécute SQL Server 2016, lequel les transfère vers Azure SQL Stretch Database dans Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="87a53-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="87a53-115">Pour plus d'informations, voir [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="87a53-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="87a53-116">Contoso a suivi les étapes suivantes pour déplacer ses données historiques vers le cloud :</span><span class="sxs-lookup"><span data-stu-id="87a53-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="87a53-117">Analyse des bases de données</span><span class="sxs-lookup"><span data-stu-id="87a53-117">Analyze databases</span></span>
    
    <span data-ttu-id="87a53-p103">A analysé les tables situées dans les bases de données qu'il prévoyait de transférer vers le cloud et a résolu tous les problèmes. Le nouveau gestionnaire de Stretch Database leur a présenté les fonctionnalités de SQL Server 2016, y compris les tables qui contiennent des données froides extensibles.</span><span class="sxs-lookup"><span data-stu-id="87a53-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="87a53-120">Mise à niveau</span><span class="sxs-lookup"><span data-stu-id="87a53-120">Upgrade</span></span>
    
    <span data-ttu-id="87a53-121">A mis à niveau les serveurs SQL existants du centre de données de son siège social parisien vers SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="87a53-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="87a53-122">Migration des données froides vers le cloud</span><span class="sxs-lookup"><span data-stu-id="87a53-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="87a53-p104">A identifié les bases de données à étendre et les tables à migrer vers des instances de Stretch Database dans Azure, à l'aide de SQL Management Studio. En arrière-plan, SQL Server 2016 a progressivement déplacé les données historiques vers Stretch Database dans Azure.</span><span class="sxs-lookup"><span data-stu-id="87a53-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="87a53-125">Voici la configuration finale d’un serveur exécutant SQL Server 2016 au siège social parisien.</span><span class="sxs-lookup"><span data-stu-id="87a53-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="87a53-126">**Figure 2 : Utilisation de Stretch Database pour un serveur situé dans le centre de données de Contoso**</span><span class="sxs-lookup"><span data-stu-id="87a53-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![Configuration de Contoso pour Stretch Database avec SQL Server pour un ordinateur unique exécutant SQL Server](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="87a53-128">La figure 2 montre comment les requêtes d’utilisateurs envoyées sur un serveur d’applications du centre de données de Contoso deviennent des requêtes SQL transmises à Azure SQL Stretch Database dans Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="87a53-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="87a53-p105">Les utilisateurs ont accès aux données via les requêtes et les applications existantes. Les stratégies d'accès ne sont pas modifiées. Contoso n'aura plus besoin d'effectuer des sauvegardes sur bande par la suite. Les opérations de maintenance consisteront uniquement en la sauvegarde et la restauration des données chaudes.</span><span class="sxs-lookup"><span data-stu-id="87a53-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="87a53-133">Après l’implémentation de Stretch Database, Contoso a :</span><span class="sxs-lookup"><span data-stu-id="87a53-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="87a53-134">réduit de 85 % ses besoins en matière de stockage de données locales ;</span><span class="sxs-lookup"><span data-stu-id="87a53-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="87a53-135">mis à jour le système de stockage d’entreprise et a supprimé l’archivage des données sur bande magnétique ;</span><span class="sxs-lookup"><span data-stu-id="87a53-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="87a53-136">réalisé d’importantes économies sur ses dépenses quotidiennes de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="87a53-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="87a53-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87a53-137">See Also</span></span>

[<span data-ttu-id="87a53-138">Scénarios d'entreprise pour la société Contoso</span><span class="sxs-lookup"><span data-stu-id="87a53-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="87a53-139">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="87a53-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="87a53-140">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="87a53-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="87a53-141">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="87a53-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="87a53-142">Feuille de route de Microsoft Enterprise Cloud : Ressources pour les décideurs informatiques</span><span class="sxs-lookup"><span data-stu-id="87a53-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




