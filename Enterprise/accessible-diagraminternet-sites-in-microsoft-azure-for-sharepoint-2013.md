---
title: "Diagramme accessible : sites Internet dans Microsoft Azure pour SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: "Cet article est une version texte accessible du diagramme Sites Internet dans Microsoft Azure pour SharePoint 2013."
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="fd936-103">Diagramme accessible : sites Internet dans Microsoft Azure pour SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fd936-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="fd936-104">**Résumé :** Cet article est une version texte accessible du diagramme nommé des sites Internet de Microsoft Azure pour SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="fd936-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="fd936-p101">Cette affiche décrit et illustre la façon dont les sites Internet publics bénéficient de la flexibilité du cloud et d’Azure AD pour les comptes clients. Il existe six différents scénarios qui décrivent comment les sites Internet bénéficient d’Azure : </span><span class="sxs-lookup"><span data-stu-id="fd936-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="fd936-107">Conception et redimensionnement de la topologie de la batterie de serveurs. </span><span class="sxs-lookup"><span data-stu-id="fd936-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="fd936-108">Ajustement pour Azure. </span><span class="sxs-lookup"><span data-stu-id="fd936-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="fd936-109">Choix du modèle Active Directory. </span><span class="sxs-lookup"><span data-stu-id="fd936-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="fd936-110">Conception de la gestion des identités, des zones et de l’authentification. </span><span class="sxs-lookup"><span data-stu-id="fd936-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="fd936-111">Conception des sites et des URL pour la publication intersites. </span><span class="sxs-lookup"><span data-stu-id="fd936-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="fd936-112">Conception de l’environnement Azure. </span><span class="sxs-lookup"><span data-stu-id="fd936-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="fd936-113">Conception et redimensionnement de la topologie de la batterie de serveurs</span><span class="sxs-lookup"><span data-stu-id="fd936-113">Design and size the farm topology</span></span>

<span data-ttu-id="fd936-114">Utilisez le Guide de topologie, de capacité et de performances pour SharePoint 2013 sur TechNet pour la conception de la topologie de la batterie.</span><span class="sxs-lookup"><span data-stu-id="fd936-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="fd936-115">Assurez-vous que la batterie que vous concevez répond aux objectifs de capacité et de performance. </span><span class="sxs-lookup"><span data-stu-id="fd936-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="fd936-116">Exemple : Batterie de serveurs de sites Internet de taille moyenne (environ 85 pages consultées par seconde)</span><span class="sxs-lookup"><span data-stu-id="fd936-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="fd936-117">Cette batterie de serveurs fournit une topologie de batterie de serveurs de recherche SharePoint 2013 à tolérance de pannes qui est optimisée pour un corpus qui contient des 3,400,000 éléments.</span><span class="sxs-lookup"><span data-stu-id="fd936-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="fd936-118">La batterie exemple traite les documents de 100 à 200 par seconde, en fonction de la langue, et qu’il prend en charge 85 vues de page par seconde et 100 requêtes par seconde.</span><span class="sxs-lookup"><span data-stu-id="fd936-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="fd936-119">Le diagramme associé présente une batterie de serveurs de sites Internet de taille moyenne avec trois types de serveurs : </span><span class="sxs-lookup"><span data-stu-id="fd936-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="fd936-120">Serveurs web</span><span class="sxs-lookup"><span data-stu-id="fd936-120">Web servers</span></span> 
    
- <span data-ttu-id="fd936-121">Serveurs d’applications</span><span class="sxs-lookup"><span data-stu-id="fd936-121">Application servers</span></span> 
    
- <span data-ttu-id="fd936-122">Serveurs de base de données</span><span class="sxs-lookup"><span data-stu-id="fd936-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="fd936-123">Serveurs Web</span><span class="sxs-lookup"><span data-stu-id="fd936-123">Web servers</span></span>

<span data-ttu-id="fd936-p102">La section des serveurs web contient trois serveurs web : Hôte A, Hôte B et Hôte C. Chaque serveur web possède un cache distribué, des profils utilisateur, des métadonnées gérées et des capacités de traitement de requêtes. Ils possèdent également une copie de partition d’index résidant sur chaque serveur.  </span><span class="sxs-lookup"><span data-stu-id="fd936-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="fd936-126">Pour monter en charge, ajoutez un serveur web supplémentaire avec les mêmes fonctionnalités pour permettre 28 affichages de pages supplémentaires par seconde. </span><span class="sxs-lookup"><span data-stu-id="fd936-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="fd936-127">Serveurs d’applications</span><span class="sxs-lookup"><span data-stu-id="fd936-127">Application servers</span></span>

<span data-ttu-id="fd936-p103">La section des serveurs d’applications contient trois serveurs d’applications : Hôte D, Hôte E et Hôte F. L’hôte D possède les composants de traitement Analyse, Admin, Analytics et Contenu. L’hôte E possède les composants de traitement Analyse, Admin et Contenu. L’hôte F possède les composants de traitement Analyse et Contenu. </span><span class="sxs-lookup"><span data-stu-id="fd936-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="fd936-131">Pour monter en charge, procédez comme suit : ajoutez un serveur d’applications avec un composant d’analyse et un composant de traitement du contenu pour traiter 40 documents supplémentaires par seconde. </span><span class="sxs-lookup"><span data-stu-id="fd936-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="fd936-132">Serveurs de base de données</span><span class="sxs-lookup"><span data-stu-id="fd936-132">Database servers</span></span>

<span data-ttu-id="fd936-133">La section des serveurs de base de données contient deux serveurs : Hôte G et Hôte H. Les serveurs de base de données sont des hôtes jumelés pour la tolérance de panne. </span><span class="sxs-lookup"><span data-stu-id="fd936-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="fd936-p104">L’hôte G contient toutes les bases de données SharePoint, notamment la base de données d’administration de la recherche, la base de données de liens, deux bases de données d’analyse, la base de données analytique et toutes les autres bases de données SharePoint. L’hôte H contient toutes les bases de données SharePoint, notamment les copies redondantes de toutes les bases de données utilisant le clustering SQL, la mise en miroir ou SQL Server 2012 AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="fd936-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="fd936-136">Ajustement pour Azure</span><span class="sxs-lookup"><span data-stu-id="fd936-136">Fine-tune for Azure</span></span>

<span data-ttu-id="fd936-p105">La batterie de serveurs SharePoint a peut-être besoin d’être ajustée pour des groupes à haute disponibilité dans la plateforme Azure. Pour assurer la haute disponibilité de tous les composants, assurez-vous que les rôles serveur sont configurés de manière identique.   </span><span class="sxs-lookup"><span data-stu-id="fd936-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="fd936-139">Dans la topologie exemple du diagramme : </span><span class="sxs-lookup"><span data-stu-id="fd936-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="fd936-140">Les serveurs web et les serveurs de base de données sont configurés de manière identique. </span><span class="sxs-lookup"><span data-stu-id="fd936-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="fd936-p106">Les trois serveurs d’applications ne sont pas configurés de manière identique. Ces rôles serveur exigent un ajustement pour les groupes à haute disponibilité dans Azure.   </span><span class="sxs-lookup"><span data-stu-id="fd936-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="fd936-143">Avant</span><span class="sxs-lookup"><span data-stu-id="fd936-143">Before</span></span>

<span data-ttu-id="fd936-p107">La partie supérieure du diagramme représente la batterie de serveurs SharePoint avant qu’elle ait été ajustée pour des groupes à haute disponibilité dans Azure. Dans le diagramme, les trois serveurs d’applications hôtes ne sont pas configurés de manière identique. Le nombre de composants est déterminé par les objectifs de capacité et de performance établis pour la batterie de serveurs. Les trois serveurs sont configurés comme suit : </span><span class="sxs-lookup"><span data-stu-id="fd936-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="fd936-148">Le serveur d’applications Hôte D est configuré avec les rôles Analyse, Admin, Analytics et Traitement du contenu. </span><span class="sxs-lookup"><span data-stu-id="fd936-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="fd936-149">Le serveur d’applications Hôte E est configuré avec les rôles Analyse, Admin et Traitement du contenu. </span><span class="sxs-lookup"><span data-stu-id="fd936-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="fd936-150">Le serveur d’applications Hôte F est configuré avec les rôles Analyse et Traitement du contenu. </span><span class="sxs-lookup"><span data-stu-id="fd936-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="fd936-151">Après</span><span class="sxs-lookup"><span data-stu-id="fd936-151">After</span></span>

<span data-ttu-id="fd936-p108">Cette partie du diagramme montre la batterie de serveurs SharePoint après que qu’il a été optimisé pour une disponibilité définit dans Azure. Pour adapter cette architecture pour Azure, nous dupliquerez des quatre composants sur les trois serveurs. Cela permet d’augmenter le nombre de composants au-delà de ce qui est nécessaire pour les performances et la capacité. Le compromis est que cette conception garantit la haute disponibilité de tous les quatre composants de la plateforme Azure lorsque ces trois ordinateurs virtuels sont affectés à un ensemble de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="fd936-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="fd936-156">Les trois serveurs sont configurés pour posséder tous les rôles Analyse, Admin, Analytics et Traitement du contenu. </span><span class="sxs-lookup"><span data-stu-id="fd936-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="fd936-157">Choix du modèle Active Directory</span><span class="sxs-lookup"><span data-stu-id="fd936-157">Choose the Active Directory model</span></span>

<span data-ttu-id="fd936-p109">Toutes les solutions SharePoint nécessitent les services de domaine Active Directory. À ce stade, il existe deux options pour les solutions SharePoint dans Azure.  </span><span class="sxs-lookup"><span data-stu-id="fd936-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="fd936-p110">Option 1 : Les domaine dédié, vous pouvez déployer un domaine dédié et isolé sur Azure pour prendre en charge d’une batterie de serveurs SharePoint. Il s’agit d’un bon choix pour les sites Internet accessible au public.</span><span class="sxs-lookup"><span data-stu-id="fd936-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="fd936-p111">Option 2 : Étendre le domaine local via une connexion VPN de site à site. Lorsque vous étendez le domaine local via une connexion VPN de site à site, les utilisateurs accéder à la batterie de serveurs SharePoint comme si elle était hébergée sur site. Vous pouvez profiter de vos implémentations DNS et Active Directory existantes.</span><span class="sxs-lookup"><span data-stu-id="fd936-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="fd936-165">Conception de la gestion des identités, des zones et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="fd936-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="fd936-166">Conception des comptes et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="fd936-166">Design for accounts and authentication</span></span>

<span data-ttu-id="fd936-167">Déterminez de quelle façon les comptes seront gérés et le type d’authentification qui sera utilisé. </span><span class="sxs-lookup"><span data-stu-id="fd936-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="fd936-168">Comptes pour développeurs et auteurs de sites</span><span class="sxs-lookup"><span data-stu-id="fd936-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="fd936-169">Ajoutez des comptes au domaine dans Azure. </span><span class="sxs-lookup"><span data-stu-id="fd936-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="fd936-170">Utilisez les services ADFS (Active Directory Federation Services)  localement pour fédérer les comptes internes dans le domaine sur Azure. </span><span class="sxs-lookup"><span data-stu-id="fd936-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="fd936-171">Si la conception comprend une connexion VPN de site à site, utilisez les comptes internes. </span><span class="sxs-lookup"><span data-stu-id="fd936-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="fd936-172">Comptes pour les clients</span><span class="sxs-lookup"><span data-stu-id="fd936-172">Accounts for customers</span></span>

- <span data-ttu-id="fd936-173">Utilisez Azure Active Directory. </span><span class="sxs-lookup"><span data-stu-id="fd936-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="fd936-174">Utilisez un autre fournisseur SAML. </span><span class="sxs-lookup"><span data-stu-id="fd936-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="fd936-175">Conception de zones</span><span class="sxs-lookup"><span data-stu-id="fd936-175">Design for zones</span></span>

<span data-ttu-id="fd936-176">Dans SharePoint 2013, la gestion des identités est prise en compte dans la configuration des zones et de l’authentification. </span><span class="sxs-lookup"><span data-stu-id="fd936-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="fd936-177">Cette conception fournit une séparation claire entre les comptes clients et tous les autres comptes. </span><span class="sxs-lookup"><span data-stu-id="fd936-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="fd936-178">Utilisez cette conception si vous souhaitez que les comptes clients soient traités de manière entièrement différente des comptes internes pour les auteurs et les développeurs de sites. </span><span class="sxs-lookup"><span data-stu-id="fd936-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="fd936-179">Grâce à cette conception, vous pouvez utiliser des stratégies de zones pour limiter les actions des utilisateurs dans une application web. </span><span class="sxs-lookup"><span data-stu-id="fd936-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="fd936-180">Cette conception se traduit par une URL différente pour les comptes client et interne. </span><span class="sxs-lookup"><span data-stu-id="fd936-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="fd936-181">Dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="fd936-181">In this example:</span></span> 
  
- <span data-ttu-id="fd936-182">Configurez la zone par défaut pour vos comptes internes. </span><span class="sxs-lookup"><span data-stu-id="fd936-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="fd936-p112">Configurez la zone extranet pour l’accès client authentifié. Utilisez Azure Active Directory (AD) pour les comptes clients ou utilisez un autre fournisseur SAML. </span><span class="sxs-lookup"><span data-stu-id="fd936-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="fd936-185">Configurez la zone Internet pour un accès anonyme.  </span><span class="sxs-lookup"><span data-stu-id="fd936-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="fd936-186">N’utilisez pas une création de deux zones dans lequel tous les utilisateurs authentifiés sont configurés pour utiliser la zone par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd936-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="fd936-187">Le diagramme associé représente une conception en trois zones dans laquelle les comptes internes et clients sont séparés.  </span><span class="sxs-lookup"><span data-stu-id="fd936-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="fd936-p113">Les visiteurs et clients accéder les clients AD Azure dans la batterie de serveurs SharePoint 2013 grâce à des applications web dans une des deux zones. Les deux zones sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd936-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="fd936-190">Zone : Internet pour les utilisateurs anonymes </span><span class="sxs-lookup"><span data-stu-id="fd936-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="fd936-191">Zone : Extranet pour les utilisateurs authentifiés </span><span class="sxs-lookup"><span data-stu-id="fd936-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="fd936-p114">Les utilisateurs disposant de comptes internes accèdent au locataire Azure Active Directory à partir de AD DS et AD FS dans l’environnement local via le tunnel VPN vers Azure AD. La zone par défaut fournit l’authentification Windows (NTLM). </span><span class="sxs-lookup"><span data-stu-id="fd936-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="fd936-194">Conception de connexion à Azure AD</span><span class="sxs-lookup"><span data-stu-id="fd936-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="fd936-p115">Azure AD offre des fonctionnalités de gestion des identités et de contrôle d’accès pour les services dans le nuage. Les fonctionnalités comprennent un magasin cloud pour les données d’annuaire et un ensemble principal de services d’identité, incluant des processus d’ouverture de session, des services d’authentification et des services AD FS. Les services d’identité qui sont inclus avec Azure AD s’intègrent facilement à vos déploiements AD DS locaux et prennent entièrement en charge les fournisseurs d’identité tiers. </span><span class="sxs-lookup"><span data-stu-id="fd936-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="fd936-198">Le diagramme associé présente le scénario suivant : </span><span class="sxs-lookup"><span data-stu-id="fd936-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="fd936-199">Lors de l’intégration SharePoint 2013 avec Azure Active Directory, un Azure Access Control Service (ACS) a deux objectifs :</span><span class="sxs-lookup"><span data-stu-id="fd936-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="fd936-p116"> Azure AD utilise SAML 2.0 et SharePoint fonctionne uniquement avec SAML 1.1. ACS comprend les deux formats et fait office d’intermédiaire pour transformer les formats de jeton entre SharePoint et Azure AD.   </span><span class="sxs-lookup"><span data-stu-id="fd936-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="fd936-202">ACS remplace la nécessité d’un service de jeton de sécurité du fournisseur d’identité (IP-STS) pour ce scénario SAML. </span><span class="sxs-lookup"><span data-stu-id="fd936-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="fd936-203">Pour plus d’informations, voir la rubrique Configuration de Azure Active Directory avec SharePoint 2013 disponible dans la bibliothèque TechNet. </span><span class="sxs-lookup"><span data-stu-id="fd936-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="fd936-204">Conception des sites et des URL pour la publication intersites</span><span class="sxs-lookup"><span data-stu-id="fd936-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="fd936-205">Une conception à une application web est recommandée pour les scénarios de publication. </span><span class="sxs-lookup"><span data-stu-id="fd936-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="fd936-206">Les sites de création et de publication se trouvent dans la même application web. </span><span class="sxs-lookup"><span data-stu-id="fd936-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="fd936-207">La publication intersites permet de publier des ressources. </span><span class="sxs-lookup"><span data-stu-id="fd936-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="fd936-208">Utilisez des collections de sites basées sur le chemin d’accès et nommées par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fd936-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="fd936-p117">L’utilisation d’une collection de site racine est une condition requise. Créez ce site en tant que site basé sur le chemin d’accès. </span><span class="sxs-lookup"><span data-stu-id="fd936-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="fd936-211">Créez toutes les autres collections de site en tant que collections de sites nommées par l’hôte. </span><span class="sxs-lookup"><span data-stu-id="fd936-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="fd936-212">URL d’application web et de site racine </span><span class="sxs-lookup"><span data-stu-id="fd936-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="fd936-p118">Utilisez un nom interne pour l’URL d’application web. SharePoint utilise le nom de la machine locale comme nom par défaut, sauf si un nom différent est spécifié. Vous pouvez utiliser un nom de domaine qui est réservé pour l’environnement réseau interne.  </span><span class="sxs-lookup"><span data-stu-id="fd936-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="fd936-p119">SharePoint affecte un numéro de port non standard lors de la création de l’application web. Utilisez ce numéro de port au lieu du port 80 ou du port 443. Vous pouvez utiliser un autre port à condition qu’il ne soit pas standard. </span><span class="sxs-lookup"><span data-stu-id="fd936-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="fd936-219">Utilisez les mêmes nom et numéro de port pour la collection de sites racine, qui est une collection de sites basée sur des chemins d’accès. </span><span class="sxs-lookup"><span data-stu-id="fd936-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="fd936-p120">Le diagramme associé représente des services de pool d’applications telles que la recherche interagissant avec les collections de sites à l’aide des applications web. Les collections de sites affichées sont les suivantes : </span><span class="sxs-lookup"><span data-stu-id="fd936-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="fd936-222">Collection de sites basée sur des chemins d’accès, disponible à l’adresse http://internal:8000 (site racine). </span><span class="sxs-lookup"><span data-stu-id="fd936-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="fd936-223">Analyse : Collections de sites nommées par l’hôte situées à une adresse du type https://authoring.contoso.com:8000. </span><span class="sxs-lookup"><span data-stu-id="fd936-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="fd936-224">Requêtes : 2 collections de sites distinctes nommées par l’hôte et situées à des adresses telles que les suivantes : </span><span class="sxs-lookup"><span data-stu-id="fd936-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="fd936-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fd936-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="fd936-226">https://Secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fd936-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="fd936-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="fd936-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="fd936-228">http://Assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fd936-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="fd936-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fd936-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="fd936-230">http://Assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="fd936-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="fd936-231">Conception de l’environnement Azure</span><span class="sxs-lookup"><span data-stu-id="fd936-231">Design the Azure environment</span></span>

<span data-ttu-id="fd936-232">Cet exemple d’architecture inclut les éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="fd936-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="fd936-233">Une connexion VPN de site à site est facultative et étend l’environnement local DNS et AD DS de Windows au réseau virtuel dans Azure. </span><span class="sxs-lookup"><span data-stu-id="fd936-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="fd936-234">Le cas échéant, utilisez un domaine dédié dans Azure pour prendre en charge la batterie de serveurs SharePoint. </span><span class="sxs-lookup"><span data-stu-id="fd936-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="fd936-235">Les serveurs sont répartis entre les services cloud d’Azure selon leur rôle. </span><span class="sxs-lookup"><span data-stu-id="fd936-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="fd936-236">Les groupes à haute disponibilité assurent la haute disponibilité de rôles serveur configurés de manière identique.  </span><span class="sxs-lookup"><span data-stu-id="fd936-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="fd936-237">Pour plus d’informations, voir l’article suivant sur TechNet : Architectures Microsoft Azure pour solutions SharePoint </span><span class="sxs-lookup"><span data-stu-id="fd936-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="fd936-238">Le diagramme associé représente un exemple d’environnement local qui se connecte à un réseau virtuel Azure.   </span><span class="sxs-lookup"><span data-stu-id="fd936-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="fd936-239">L’environnement local, qui est un élément facultatif de l’environnement Azure, comporte les éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="fd936-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="fd936-240">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="fd936-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="fd936-241">AD DS ;</span><span class="sxs-lookup"><span data-stu-id="fd936-241">AD DS</span></span> 
    
- <span data-ttu-id="fd936-242">Passerelle VPN entre Windows Server et AD DS, d’un côté, et le sous-réseau de passerelle VPN actif, de l’autre </span><span class="sxs-lookup"><span data-stu-id="fd936-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="fd936-243">L’environnement de réseau virtuel Azure comporte les éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="fd936-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="fd936-244">Sous-réseau de passerelle VPN actif (à cheval sur l’environnement local, le cas échéant) </span><span class="sxs-lookup"><span data-stu-id="fd936-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="fd936-245">Service cloud incluant le groupe à haute disponibilité AD DS et DNS (deux serveurs) </span><span class="sxs-lookup"><span data-stu-id="fd936-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="fd936-246">Service cloud incluant le groupe à haute disponibilité du serveur frontal (trois serveurs SharePoint) et le groupe à haute disponibilité du serveur d’applications (trois serveurs SharePoint) </span><span class="sxs-lookup"><span data-stu-id="fd936-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="fd936-247">Service cloud contenant deux groupes à haute disponibilité de base de données </span><span class="sxs-lookup"><span data-stu-id="fd936-247">Cloud service that contains two database availability sets</span></span> 
    

