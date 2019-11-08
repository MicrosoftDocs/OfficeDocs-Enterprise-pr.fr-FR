---
title: Diagramme accessible-exemple de conception de sites Internet dans Microsoft Azure pour SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Cet article est une version texte accessible du diagramme nommé Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027628"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="810f1-103">Diagramme accessible : Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="810f1-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="810f1-104">**Résumé :** Cet article est une version texte accessible du diagramme nommé exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="810f1-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="810f1-105">Utilisez cet exemple de conception comme point de départ pour un site accessible sur Internet dans Azure à l’aide de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="810f1-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="810f1-106">Cette affiche montre un exemple de la façon de concevoir les aspects suivants de SharePoint 2013 :</span><span class="sxs-lookup"><span data-stu-id="810f1-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="810f1-107">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="810f1-107">Users</span></span>
    
- <span data-ttu-id="810f1-108">Zones et authentification</span><span class="sxs-lookup"><span data-stu-id="810f1-108">Zones and authentication</span></span>
    
- <span data-ttu-id="810f1-109">Batterie de serveurs</span><span class="sxs-lookup"><span data-stu-id="810f1-109">Server farm</span></span>
    
- <span data-ttu-id="810f1-110">Site d’administration</span><span class="sxs-lookup"><span data-stu-id="810f1-110">Administration site</span></span>
    
- <span data-ttu-id="810f1-111">Services</span><span class="sxs-lookup"><span data-stu-id="810f1-111">Services</span></span>
    
- <span data-ttu-id="810f1-112">Pools d’applications et applications web</span><span class="sxs-lookup"><span data-stu-id="810f1-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="810f1-113">Collections de sites</span><span class="sxs-lookup"><span data-stu-id="810f1-113">Site collections</span></span>
    
- <span data-ttu-id="810f1-114">Sites</span><span class="sxs-lookup"><span data-stu-id="810f1-114">Sites</span></span>
    
- <span data-ttu-id="810f1-115">Bases de données de contenu</span><span class="sxs-lookup"><span data-stu-id="810f1-115">Content databases</span></span>
    
- <span data-ttu-id="810f1-116">Zones et URL</span><span class="sxs-lookup"><span data-stu-id="810f1-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="810f1-117">Utilisateurs, zones et authentification</span><span class="sxs-lookup"><span data-stu-id="810f1-117">Users, zones and authentication</span></span>

<span data-ttu-id="810f1-p101">Il existe quatre types de comptes utilisateur dans cette conception. Chaque type de compte est associé à un site d’accès et à une zone qui utilise un type spécifique d’authentification. </span><span class="sxs-lookup"><span data-stu-id="810f1-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="810f1-120">Clients anonymes : les clients anonymes ont accès à un https://www.contoso.comsite tel que.</span><span class="sxs-lookup"><span data-stu-id="810f1-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="810f1-121">La zone utilisée est la « zone Internet/anonyme » qui utilise l’authentification anonyme.</span><span class="sxs-lookup"><span data-stu-id="810f1-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="810f1-122">Clients authentifiés : les clients authentifiés ont accès à un site tel https://secure.contoso.comque.</span><span class="sxs-lookup"><span data-stu-id="810f1-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="810f1-123">La zone utilisée est la « zone extranet/SAML » qui utilise Azure Active Directory avec l’authentification SAML.</span><span class="sxs-lookup"><span data-stu-id="810f1-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="810f1-124">Auteurs de site et développeurs : les auteurs de site et les développeurs ont accès https://authoring.contoso.com:8000 à https://www.contoso.com:8000des sites tels que ou.</span><span class="sxs-lookup"><span data-stu-id="810f1-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="810f1-125">La zone utilisée est la « zone par défaut/intégrée à Windows », qui utilise les services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="810f1-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="810f1-126">Compte d’analyse de recherche : le compte d’analyse de recherche a accès https://authoring.contoso.com:8000 par https://www.contoso.com:8000le biais de sites tels que ou.</span><span class="sxs-lookup"><span data-stu-id="810f1-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="810f1-127">La zone qu’il utilise est la « zone par défaut/intégrée à Windows », qui utilise les services AD DS avec l’authentification Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="810f1-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="810f1-128">Batterie de serveurs</span><span class="sxs-lookup"><span data-stu-id="810f1-128">Server farm</span></span>

<span data-ttu-id="810f1-p106">Les utilisateurs accèdent à la batterie de serveurs via Azure. La batterie de serveurs contient un ou plusieurs serveurs web.</span><span class="sxs-lookup"><span data-stu-id="810f1-p106">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="810f1-131">Site d’administration</span><span class="sxs-lookup"><span data-stu-id="810f1-131">Administration site</span></span>

<span data-ttu-id="810f1-p107">Le site d’administration contient plusieurs serveurs d’applications, qui communiquent avec un pool d’applications (Pool d’applications 1 dans l’exemple) qui utilise l’application web Central Administration Site. L’application Central Administration Site permet d’accéder aux collections de sites au sein de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="810f1-p107">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="810f1-134">Le site d’administration contient également des serveurs de base de données SQL, qui sont des serveurs de base de données sur lesquels SQL Server est installé et configuré pour prendre en charge le clustering, la mise en miroir ou la disponibilité AlwaysOn de SQL (AlwaysOn s’applique à SQL Server 2012 uniquement).</span><span class="sxs-lookup"><span data-stu-id="810f1-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="810f1-135">Services</span><span class="sxs-lookup"><span data-stu-id="810f1-135">Services</span></span>

<span data-ttu-id="810f1-p108">L’exemple de conception présente un site web de Services Internet (IIS), Services web SharePoint. Le site Services web SharePoint contient un pool d’applications (pools d’applications 2) avec trois services : profil utilisateur, recherche et métadonnées gérées.</span><span class="sxs-lookup"><span data-stu-id="810f1-p108">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="810f1-138">Remarques sur les Services pour les sites Internet :</span><span class="sxs-lookup"><span data-stu-id="810f1-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="810f1-139">Métadonnées gérées — Veillez à sélectionner **Cette application de service est l’emplacement de stockage par défaut pour les ensembles de termes propres aux colonnes**.</span><span class="sxs-lookup"><span data-stu-id="810f1-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="810f1-140">Gestion des applications — Nous ne recommandons pas d’utiliser des applications dans un site Internet destiné au public dans Azure.</span><span class="sxs-lookup"><span data-stu-id="810f1-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="810f1-141">Pools d’applications et applications web</span><span class="sxs-lookup"><span data-stu-id="810f1-141">Application pools and web applications</span></span>

<span data-ttu-id="810f1-142">Le groupe par défaut dans Azure montre le pool d’applications 3, qui contient une application web nommée Contoso Sites.</span><span class="sxs-lookup"><span data-stu-id="810f1-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="810f1-143">Cette collection de sites basée sur le chemin d' https://internal:8000accès se trouve à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="810f1-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="810f1-144">Collections de site et sites</span><span class="sxs-lookup"><span data-stu-id="810f1-144">Site collections and sites</span></span>

<span data-ttu-id="810f1-145">Les collections de sites contenues dans le pool d’applications sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="810f1-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="810f1-146">Collection de sites nommée par l’hôte 1 pour l’analyse (exemple d’emplacementhttps://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="810f1-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="810f1-147">Collection de sites nommée par l’hôte 2 pour les requêtes https://www.contoso.com( https://secure.contoso.comemplacements d’exemple,,https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="810f1-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="810f1-148">Collection de sites nommée par l’hôte 3 pour les requêtes https://assets.contoso.com( https://secureassets.contoso.comemplacements d’exemple,,https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="810f1-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="810f1-149">Bases de données de contenu</span><span class="sxs-lookup"><span data-stu-id="810f1-149">Content databases</span></span>

<span data-ttu-id="810f1-150">L’exemple montre deux bases de données de contenu.</span><span class="sxs-lookup"><span data-stu-id="810f1-150">The example shows two content databases.</span></span> <span data-ttu-id="810f1-151">La première concerne la collection de sites 1 utilisée pour l’analysehttps://authoring.contoso.com:8000)(.</span><span class="sxs-lookup"><span data-stu-id="810f1-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="810f1-152">L’autre est pour les deux collections de sites 2 et 3 utilisées pour leshttps://www.contoso.comrequêtes https://secure.contoso.com( https://www.contoso.com:8000,, https://assets.contoso.com, https://secureassets.contoso.comou https://assets.contoso.com:8000),,.</span><span class="sxs-lookup"><span data-stu-id="810f1-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="810f1-153">Zones et URL</span><span class="sxs-lookup"><span data-stu-id="810f1-153">Zones and URLs</span></span>

<span data-ttu-id="810f1-154">L’exemple montre les trois zones avec les URL à charge équilibrée associées qui sont utilisées par différents comptes utilisateurs. </span><span class="sxs-lookup"><span data-stu-id="810f1-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="810f1-155">La première liste de zones et d’URL est liée à la collection de sites 1 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="810f1-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="810f1-156">Utilisateurs-auteurs de site</span><span class="sxs-lookup"><span data-stu-id="810f1-156">Users - Site authors</span></span>
    
- <span data-ttu-id="810f1-157">Zone-valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="810f1-157">Zone - Default</span></span>
    
- <span data-ttu-id="810f1-158">URL à charge équilibrée-https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="810f1-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="810f1-p111">La seconde liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 2 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="810f1-p111">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="810f1-161">Première zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-161">First zone:</span></span>
  
- <span data-ttu-id="810f1-162">Utilisateurs-auteurs de site</span><span class="sxs-lookup"><span data-stu-id="810f1-162">Users - Site authors</span></span>
    
- <span data-ttu-id="810f1-163">Zone-valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="810f1-163">Zone - Default</span></span>
    
- <span data-ttu-id="810f1-164">URL à charge équilibrée-https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="810f1-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="810f1-165">Deuxième zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-165">Second zone:</span></span>
  
- <span data-ttu-id="810f1-166">Utilisateurs-clients anonymes</span><span class="sxs-lookup"><span data-stu-id="810f1-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="810f1-167">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="810f1-167">Zone - Internet</span></span>
    
- <span data-ttu-id="810f1-168">URL à charge équilibrée-https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="810f1-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="810f1-169">Troisième zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-169">Third zone:</span></span>
  
- <span data-ttu-id="810f1-170">Utilisateurs authentifiés</span><span class="sxs-lookup"><span data-stu-id="810f1-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="810f1-171">Zone-extranet</span><span class="sxs-lookup"><span data-stu-id="810f1-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="810f1-172">URL à charge équilibrée-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="810f1-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="810f1-p112">La troisième liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 3 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="810f1-p112">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="810f1-175">Première zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-175">First zone:</span></span>
  
- <span data-ttu-id="810f1-176">Utilisateurs-auteurs de site</span><span class="sxs-lookup"><span data-stu-id="810f1-176">Users - Site authors</span></span>
    
- <span data-ttu-id="810f1-177">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="810f1-177">Zone - Internet</span></span>
    
- <span data-ttu-id="810f1-178">URL à charge équilibrée-https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="810f1-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="810f1-179">Deuxième zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-179">Second zone:</span></span>
  
- <span data-ttu-id="810f1-180">Utilisateurs-clients anonymes</span><span class="sxs-lookup"><span data-stu-id="810f1-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="810f1-181">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="810f1-181">Zone - Internet</span></span>
    
- <span data-ttu-id="810f1-182">URL à charge équilibrée-https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="810f1-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="810f1-183">Troisième zone :</span><span class="sxs-lookup"><span data-stu-id="810f1-183">Third zone:</span></span>
  
- <span data-ttu-id="810f1-184">Utilisateurs authentifiés</span><span class="sxs-lookup"><span data-stu-id="810f1-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="810f1-185">Zone-extranet</span><span class="sxs-lookup"><span data-stu-id="810f1-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="810f1-186">URL à charge équilibrée-https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="810f1-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

