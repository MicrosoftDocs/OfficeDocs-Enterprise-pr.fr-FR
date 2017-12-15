---
title: Exemple de conception accessible diagramme - sites Internet de Microsoft Azure pour SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Cet article est une version texte accessible du diagramme nommé Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013"
ms.openlocfilehash: 1d84900a931bf9a01cd2e757a5fc671455e076f5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="47e67-103">Diagramme accessible : Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="47e67-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="47e67-104">**Résumé :** Cet article est une version texte accessible du diagramme exemple de conception : sites Internet de Microsoft Azure pour SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="47e67-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="47e67-105">Utilisez cet exemple de conception comme point de départ pour un site Internet orienté dans Azure à l’aide de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="47e67-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="47e67-106">Cet affichage montre un exemple de la façon de concevoir les aspects suivants de SharePoint 2013 :</span><span class="sxs-lookup"><span data-stu-id="47e67-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="47e67-107">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="47e67-107">Users</span></span>
    
- <span data-ttu-id="47e67-108">Zones et authentification</span><span class="sxs-lookup"><span data-stu-id="47e67-108">Zones and authentication</span></span>
    
- <span data-ttu-id="47e67-109">Batterie de serveurs</span><span class="sxs-lookup"><span data-stu-id="47e67-109">Server farm</span></span>
    
- <span data-ttu-id="47e67-110">Site d’administration</span><span class="sxs-lookup"><span data-stu-id="47e67-110">Administration site</span></span>
    
- <span data-ttu-id="47e67-111">Services</span><span class="sxs-lookup"><span data-stu-id="47e67-111">Services</span></span>
    
- <span data-ttu-id="47e67-112">Pools d’applications et applications web</span><span class="sxs-lookup"><span data-stu-id="47e67-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="47e67-113">Collections de sites</span><span class="sxs-lookup"><span data-stu-id="47e67-113">Site collections</span></span>
    
- <span data-ttu-id="47e67-114">Sites</span><span class="sxs-lookup"><span data-stu-id="47e67-114">Sites</span></span>
    
- <span data-ttu-id="47e67-115">Bases de données de contenu</span><span class="sxs-lookup"><span data-stu-id="47e67-115">Content databases</span></span>
    
- <span data-ttu-id="47e67-116">Zones et URL</span><span class="sxs-lookup"><span data-stu-id="47e67-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="47e67-117">Utilisateurs, zones et authentification</span><span class="sxs-lookup"><span data-stu-id="47e67-117">Users, zones and authentication</span></span>

<span data-ttu-id="47e67-p101">Il existe quatre types de comptes utilisateur dans cette conception. Chaque type de compte est associé à un site d’accès et à une zone qui utilise un type spécifique d’authentification. </span><span class="sxs-lookup"><span data-stu-id="47e67-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="47e67-120">Les clients anonymes, les clients anonymes ont accès à un site par exemple http://www.contoso.com. La zone qu’ils utilisent est la « zone Internet / anonyme », qui utilise l’authentification anonyme.</span><span class="sxs-lookup"><span data-stu-id="47e67-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="47e67-121">Authentification des clients : les clients authentifiés ont accès à un site par exemple https://secure.contoso.com. La zone qu’ils utilisent est la « zone Extranet / SAML », qui utilise Azure Active Directory avec l’authentification SAML.</span><span class="sxs-lookup"><span data-stu-id="47e67-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="47e67-p102">Les auteurs et les développeurs de site, les auteurs de Site et les développeurs ont accès à des sites tels que http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. La zone qu’ils utilisent est la « zone par défaut / Windows intégrée », qui utilise les Services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="47e67-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="47e67-p103">Recherche un compte d’analyse — Le compte d’analyse recherche a accès via les sites tels que http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. La zone qu’il utilise est la « zone par défaut / Windows intégrée », qui utilise les services AD DS avec une authentification Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="47e67-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="47e67-126">Batterie de serveurs</span><span class="sxs-lookup"><span data-stu-id="47e67-126">Server farm</span></span>

<span data-ttu-id="47e67-p104">Les utilisateurs accèdent à la batterie de serveurs via Azure. La batterie de serveurs contient un ou plusieurs serveurs web.</span><span class="sxs-lookup"><span data-stu-id="47e67-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="47e67-129">Site d’administration</span><span class="sxs-lookup"><span data-stu-id="47e67-129">Administration site</span></span>

<span data-ttu-id="47e67-p105">Le site d’administration contient plusieurs serveurs d’applications, qui communiquent avec un pool d’applications (Pool d’applications 1 dans l’exemple) qui utilise l’application web Central Administration Site. L’application Central Administration Site permet d’accéder aux collections de sites au sein de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="47e67-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="47e67-132">Le site d’administration contient également des serveurs de base de données SQL, qui sont des serveurs de base de données sur lesquels SQL Server est installé et configuré pour prendre en charge le clustering, la mise en miroir ou la disponibilité AlwaysOn de SQL (AlwaysOn s’applique à SQL Server 2012 uniquement).</span><span class="sxs-lookup"><span data-stu-id="47e67-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="47e67-133">Services</span><span class="sxs-lookup"><span data-stu-id="47e67-133">Services</span></span>

<span data-ttu-id="47e67-p106">L’exemple de conception présente un site web de Services Internet (IIS), Services web SharePoint. Le site Services web SharePoint contient un pool d’applications (pools d’applications 2) avec trois services : profil utilisateur, recherche et métadonnées gérées.</span><span class="sxs-lookup"><span data-stu-id="47e67-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="47e67-136">Remarques sur les Services pour les sites Internet :</span><span class="sxs-lookup"><span data-stu-id="47e67-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="47e67-137">Métadonnées gérées — Veillez à sélectionner **cette application de service est l’emplacement de stockage par défaut pour les ensembles de termes spécifiques des colonnes**.</span><span class="sxs-lookup"><span data-stu-id="47e67-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="47e67-138">Gestion des applications — Nous ne recommandons pas d’utiliser des applications dans un site Internet destiné au public dans Azure.</span><span class="sxs-lookup"><span data-stu-id="47e67-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="47e67-139">Pools d’applications et applications web</span><span class="sxs-lookup"><span data-stu-id="47e67-139">Application pools and web applications</span></span>

<span data-ttu-id="47e67-p107">Le groupe par défaut dans Azure montre le pool d’applications 3, qui contient une application web nommée Contoso Sites. Cette collection de sites basés sur des chemins d’accès est disponible à l’adresse http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="47e67-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="47e67-142">Collections de site et sites</span><span class="sxs-lookup"><span data-stu-id="47e67-142">Site collections and sites</span></span>

<span data-ttu-id="47e67-143">Les collections de sites contenues dans le pool d’applications sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e67-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="47e67-144">Collection de sites nommée par l’hôte 1 pour l’analyse (emplacement de l’exemple http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="47e67-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="47e67-145">Collection de sites nommée par l’hôte 2 pour les requêtes (emplacement des exemples http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="47e67-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="47e67-146">Collection de sites nommée par l’hôte 3 pour les requêtes (emplacement des exemples http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="47e67-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="47e67-147">Bases de données de contenu</span><span class="sxs-lookup"><span data-stu-id="47e67-147">Content databases</span></span>

<span data-ttu-id="47e67-p108">L’exemple montre deux bases de données de contenu. L’une correspond à la collection de sites 1 utilisée pour l’analyse (http://authoring.contoso.com:8000). L’autre correspond aux deux collections de sites 2 et 3 utilisées pour les requêtes (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 ou http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="47e67-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="47e67-151">Zones et URL</span><span class="sxs-lookup"><span data-stu-id="47e67-151">Zones and URLs</span></span>

<span data-ttu-id="47e67-152">L’exemple montre les trois zones avec les URL à charge équilibrée associées qui sont utilisées par différents comptes utilisateurs. </span><span class="sxs-lookup"><span data-stu-id="47e67-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="47e67-153">La première liste de zones et d’URL est liée à la collection de sites 1 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e67-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="47e67-154">Utilisateurs - les auteurs de Site</span><span class="sxs-lookup"><span data-stu-id="47e67-154">Users - Site authors</span></span>
    
- <span data-ttu-id="47e67-155">Zone - par défaut</span><span class="sxs-lookup"><span data-stu-id="47e67-155">Zone - Default</span></span>
    
- <span data-ttu-id="47e67-156">URL avec équilibrage de charge - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="47e67-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="47e67-p109">La seconde liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 2 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e67-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="47e67-159">Première zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-159">First zone:</span></span>
  
- <span data-ttu-id="47e67-160">Utilisateurs - les auteurs de Site</span><span class="sxs-lookup"><span data-stu-id="47e67-160">Users - Site authors</span></span>
    
- <span data-ttu-id="47e67-161">Zone - par défaut</span><span class="sxs-lookup"><span data-stu-id="47e67-161">Zone - Default</span></span>
    
- <span data-ttu-id="47e67-162">URL avec équilibrage de charge - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="47e67-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="47e67-163">Deuxième zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-163">Second zone:</span></span>
  
- <span data-ttu-id="47e67-164">Utilisateurs - clients anonymes</span><span class="sxs-lookup"><span data-stu-id="47e67-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="47e67-165">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="47e67-165">Zone - Internet</span></span>
    
- <span data-ttu-id="47e67-166">URL - à charge équilibrée http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="47e67-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="47e67-167">Troisième zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-167">Third zone:</span></span>
  
- <span data-ttu-id="47e67-168">Utilisateurs - clients authentifiés</span><span class="sxs-lookup"><span data-stu-id="47e67-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="47e67-169">Zone - Extranet</span><span class="sxs-lookup"><span data-stu-id="47e67-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="47e67-170">Équilibrage de charge URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="47e67-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="47e67-p110">La troisième liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 3 et elle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e67-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="47e67-173">Première zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-173">First zone:</span></span>
  
- <span data-ttu-id="47e67-174">Utilisateurs - les auteurs de Site</span><span class="sxs-lookup"><span data-stu-id="47e67-174">Users - Site authors</span></span>
    
- <span data-ttu-id="47e67-175">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="47e67-175">Zone - Internet</span></span>
    
- <span data-ttu-id="47e67-176">URL avec équilibrage de charge - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="47e67-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="47e67-177">Deuxième zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-177">Second zone:</span></span>
  
- <span data-ttu-id="47e67-178">Utilisateurs - clients anonymes</span><span class="sxs-lookup"><span data-stu-id="47e67-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="47e67-179">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="47e67-179">Zone - Internet</span></span>
    
- <span data-ttu-id="47e67-180">Équilibrage de charge URL - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="47e67-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="47e67-181">Troisième zone :</span><span class="sxs-lookup"><span data-stu-id="47e67-181">Third zone:</span></span>
  
- <span data-ttu-id="47e67-182">Utilisateurs - clients authentifiés</span><span class="sxs-lookup"><span data-stu-id="47e67-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="47e67-183">Zone - Extranet</span><span class="sxs-lookup"><span data-stu-id="47e67-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="47e67-184">Équilibrage de charge URL - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="47e67-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

