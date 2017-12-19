---
title: "Scénarios de cloud hybride pour les services PaaS Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Résumé : Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure."
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="f2d0a-103">Scénarios de cloud hybride pour les services PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="f2d0a-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="f2d0a-104">**Résumé :** Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="f2d0a-105">Combinez des données locales ou des ressources de calcul à des applications nouvelles ou converties exécutées dans les services PaaS Azure. Vous pouvez ainsi tirer parti des performances, de la fiabilité et de la dimension du cloud tout en offrant une prise en charge optimale aux utilisateurs mobiles.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="f2d0a-106">Architecture de scénario hybride pour les services PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="f2d0a-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="f2d0a-107">La Figure 1 présente l’architecture des scénarios hybrides PaaS de Microsoft dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="f2d0a-108">**Figure 1 : Scénarios hybrides Microsoft PaaS dans Azure**</span><span class="sxs-lookup"><span data-stu-id="f2d0a-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Scénarios hybrides Microsoft PaaS dans Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="f2d0a-110">Pour chaque couche de l’architecture :</span><span class="sxs-lookup"><span data-stu-id="f2d0a-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="f2d0a-111">Applications et scénarios</span><span class="sxs-lookup"><span data-stu-id="f2d0a-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="f2d0a-112">Une application PaaS hybride est exécutée dans Azure et utilise les ressources de calcul ou de stockage locales.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="f2d0a-113">Identity</span><span class="sxs-lookup"><span data-stu-id="f2d0a-113">Identity</span></span>
    
    <span data-ttu-id="f2d0a-114">Se compose de la synchronisation d’annuaires ou de la fédération avec un fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="f2d0a-115">Réseau</span><span class="sxs-lookup"><span data-stu-id="f2d0a-115">Network</span></span>
    
    <span data-ttu-id="f2d0a-p101">Se compose de votre canal Internet existant ou d'une connexion ExpressRoute avec homologation publique pour Azure PaaS. Vous devez inclure un moyen pour l'application Azure PaaS d'accéder à la ressource de calcul ou de stockage locale.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="f2d0a-118">Sur site</span><span class="sxs-lookup"><span data-stu-id="f2d0a-118">On-premises</span></span>
    
    <span data-ttu-id="f2d0a-119">Se compose d’une infrastructure d’identité et de sécurité et d’applications métier ou de serveurs de bases de données existants auxquels une application Azure PaaS peut accéder en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="f2d0a-120">Application hybride Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="f2d0a-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="f2d0a-121">La Figure 2 illustre la configuration d’une application hybride exécutée dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="f2d0a-122">**Figure 2 : Application hybride Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="f2d0a-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Application hybride Azure PaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="f2d0a-p102">Dans la Figure 2, un réseau local héberge le stockage ou des applications sur des serveurs et une zone DMZ contenant un serveur proxy. Il est connecté à des services Azure PaaS via Internet ou avec une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="f2d0a-126">Une organisation peut mettre ses ressources de calcul ou de stockage à disposition de l’application Azure PaaS hybride :</span><span class="sxs-lookup"><span data-stu-id="f2d0a-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="f2d0a-127">en hébergeant les ressources sur des serveurs dans la zone DMZ ;</span><span class="sxs-lookup"><span data-stu-id="f2d0a-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="f2d0a-128">en hébergeant un serveur proxy inverse dans la zone DMZ, ce qui permet d’envoyer des requêtes HTTPS entrantes et authentifiées à la ressource locale.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="f2d0a-129">L’application Azure peut utiliser les informations d’identification des sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2d0a-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="f2d0a-130">Azure AD. Elles peuvent alors être synchronisées avec votre fournisseur d’identité local, tel que Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="f2d0a-131">Fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="f2d0a-132">Exemple d’application Azure PaaS hybride</span><span class="sxs-lookup"><span data-stu-id="f2d0a-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="f2d0a-133">La Figure 3 illustre un exemple d’application hybride exécutée dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="f2d0a-134">**Figure 3 : Exemple d'application hybride Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="f2d0a-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Exemple d’application hybride Azure PaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="f2d0a-p103">Dans la Figure 3, un réseau local héberge une application métier. Azure PaaS héberge une application mobile personnalisée. Un smartphone sur Internet accède à l'application mobile personnalisée dans Azure, qui envoie des demandes de données à l'application métier locale.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="f2d0a-p104">Cet exemple d'application Azure PaaS hybride est une application mobile personnalisée qui propose des informations de contact à jour concernant les employés. Le scénario hybride de bout en bout se compose de :</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="f2d0a-141">Un application pour smartphone qui, pour fonctionner, nécessite des informations d’identification locales et validées.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="f2d0a-142">Une application mobile personnalisée exécutée dans les services PaaS Azure, qui demande des informations concernant des employés spécifiques en fonction de requêtes envoyées par l'application pour smartphone d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="f2d0a-143">Un serveur proxy inverse dans la zone DMZ qui valide l’application mobile personnalisée et transfère la requête.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="f2d0a-144">Une batterie de serveurs d'applications métier qui gère la requête de contact. Elle est soumise aux autorisations du compte de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="f2d0a-145">Étant donné que le fournisseur d'identité local a été synchronisé avec Azure AD, l'application mobile personnalisée et l'application métier peuvent valider le nom du compte de l'utilisateur qui envoie la requête.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="f2d0a-146">Stretch Database avec SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="f2d0a-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="f2d0a-147">Stretch Database est une fonctionnalité de SQL Server 2016 qui vous permet de déplacer des données froides de façon transparente et sécurisée, telles que des données d’entreprise fermées dans une table volumineuse qui contient des informations sur les commandes client, vers une base de données SQL Stretch dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="f2d0a-p105">Dans le cadre d’une extension, le contenu d’une instance SQL Server, d’une base de données ou d’une table unique est la combinaison de données locales stockées sur un serveur SQL Server 2016 à des données distantes dans Azure. Les données qui deviennent éligibles à une extension sont automatiquement déplacées vers Azure par SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="f2d0a-150">La Figure 4 illustre Stretch Database avec SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="f2d0a-151">**Figure 4 : Stretch Database avec SQL Server 2016**</span><span class="sxs-lookup"><span data-stu-id="f2d0a-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![Stretch Database avec SQL Server 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="f2d0a-p106">Dans la Figure 4, un réseau local héberge un serveur exécutant SQL Server 2016 avec une petite base de données locale. Azure PaaS héberge une instance d'Azure SQL Server Stretch Database avec la partie étendue de la base de données. Les requêtes T-SQL provenant d'un utilisateur local envoyées à SQL Server local sont transférées en toute sécurité à Azure SQL Stretch Database, qui renvoie les résultats à l'utilisateur étant à l'origine de la requête.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="f2d0a-p107"> 

Les requêtes de l’utilisateur qui incluent les données historiques sont transférés en toute transparence à Azure SQL Stretch Database. Les requêtes ne doivent pas être réécrites, même si la table fait l’objet d’une extension. 

</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="f2d0a-p108">Stretch Database est une solution rentable qui offre un stockage à long terme et un accès transparent aux données historiques. Elle résout également les problèmes de performances et de disponibilité qui peuvent survenir lorsque les tables deviennent très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="f2d0a-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="f2d0a-160">Pour plus d'informations, voir [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="f2d0a-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2d0a-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2d0a-161">See Also</span></span>

[<span data-ttu-id="f2d0a-162">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="f2d0a-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="f2d0a-163">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="f2d0a-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f2d0a-164">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="f2d0a-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



