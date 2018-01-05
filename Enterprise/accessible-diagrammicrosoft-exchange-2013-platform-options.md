---
title: "Diagramme accessible : Options de plateforme Microsoft Exchange 2013"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Exchange 2013, qui est disponible dans la rubrique Diagrammes techniques."
ms.openlocfilehash: d81fe9947feee64d1dd75278738262d10c802ecc
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="9c1ed-103">Diagramme accessible : Options de plateforme Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="9c1ed-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="9c1ed-104">**Résumé :** Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Exchange 2013, qui est disponible dans la rubrique [Diagrammes techniques](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="9c1ed-104">This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="9c1ed-105">Cette affiche décrit ce que les architectes et les décideurs d’entreprise (BDM) doivent savoir sur les déploiements Exchange Online et Exchange Server et inclut :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="9c1ed-106">Une comparaison des quatre options de plateforme disponibles pour Exchange 2013 : Exchange Online (Office 365), Exchange hybride, Exchange Server local et Exchange hébergé par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="9c1ed-107">Des descriptions de trois fonctionnalités nouvelles ou mises à jour dans Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="9c1ed-108">Une comparaison de quatre déploiements distincts pour la plateforme Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="9c1ed-109">La comparaison fournit des informations sur chaque option de déploiement dans les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="9c1ed-110">Une vue d’ensemble des différentes fonctionnalités de déploiement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="9c1ed-111">Avantages de l’implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="9c1ed-112">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="9c1ed-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="9c1ed-113">Tâches architecturales requises</span><span class="sxs-lookup"><span data-stu-id="9c1ed-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="9c1ed-114">Responsabilités des professionnels informatiques pour l’implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="9c1ed-115">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9c1ed-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="9c1ed-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="9c1ed-117">Vous gagnez en efficacité et réduisez les coûts grâce à Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="9c1ed-p101">Le schéma associé présente Exchange Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local des services de domaine Active Directory (AD DS) et le client Azure Active Directory. Les services ADFS (Active Directory Federation Services) sont requis pour l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="9c1ed-120">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="9c1ed-121">Fonctionnement des serveurs et des logiciels de serveur géré par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="9c1ed-122">Riche ensemble de fonctionnalités d'Exchange Server 2013 en tant que service informatique.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="9c1ed-123">Toujours à jour avec les dernières fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="9c1ed-124">Exchange Online Protection (EOP) inclus pour la protection contre le courrier indésirable/contre les programmes malveillants.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="9c1ed-125">Haute disponibilité intégrée avec un contrat de niveau de service (SLA) de 99,9 %.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="9c1ed-p102">La synchronisation d'annuaires inclut les mots de passe entre les services AD DS (Active Directory Domain Services) et le client Azure Active Directory. Les services AD FS (Active Directory Federation Services) sont requis pour l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="9c1ed-128">Environnement Exchange hybride</span><span class="sxs-lookup"><span data-stu-id="9c1ed-128">Exchange Hybrid</span></span>

<span data-ttu-id="9c1ed-129">Vous pouvez tirer profit d'Office 365 tout en conservant Exchange Server en local.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="9c1ed-p103">Le diagramme associé présente un environnement Office 365 avec Exchange Online, dans lequel certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne. Il présente également un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local des services de domaine Active Directory (AD DS) et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="9c1ed-132">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="9c1ed-133">Certains utilisateurs sont hébergés localement et d’autres sont hébergés en ligne. En outre, les utilisateurs partagent le même espace d’adressage de messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="9c1ed-134">Utilisation de votre infrastructure Exchange Server existante.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="9c1ed-135">Migration à partir d’Exchange en local vers Exchange Online dans le temps, selon votre planification.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="9c1ed-136">Intégration d'autres applications Office 365, y compris Lync Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="9c1ed-137">Environnement Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="9c1ed-137">Exchange Server on-premises</span></span>

<span data-ttu-id="9c1ed-138">Vous pouvez concevoir et gérer votre propre infrastructure Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="9c1ed-139">Le diagramme associé présente une infrastructure Exchange Server avec un environnement local des services de domaine Active Directory (AD DS) dans lequel les utilisateurs sont hébergés localement.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="9c1ed-140">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="9c1ed-141">Niveau de contrôle et de personnalisation le plus élevé pour votre configuration.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="9c1ed-142">Aucune dépendance concernant la gestion de l’affinité de session au niveau de la couche d’équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="9c1ed-143">Haute disponibilité et résilience de site simples à l’aide de groupes de disponibilité de base de données (DAG).</span><span class="sxs-lookup"><span data-stu-id="9c1ed-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="9c1ed-144">Disponibilité gérée qui vous permet de conserver une très bonne expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="9c1ed-145">Utilisation de l’infrastructure de stockage et matérielle existante.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="9c1ed-146">Environnement Exchange hébergé par un fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="9c1ed-147">Vous pouvez externaliser votre charge de travail Exchange Server vers un fournisseur de solutions Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="9c1ed-148">Le diagramme associé présente un environnement Exchange Server géré et tenu à jour par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="9c1ed-149">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="9c1ed-150">Le fonctionnement des serveurs et des logiciels de serveur est géré par votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="9c1ed-151">La planification, le dimensionnement, la mise à l’échelle et la maintenance de l’infrastructure Exchange Server sont délégués à votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="9c1ed-152">La maintenance du service est gérée par votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="9c1ed-153">L’ensemble de fonctionnalités Exchange est limité à la version du logiciel déployée par votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="9c1ed-154">Avantages de l’implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="9c1ed-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="9c1ed-156">Cette option de déploiement est idéale pour :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="9c1ed-157">Les organisations qui cherchent à réduire les coûts d’exploitation pour les déploiements Exchange locaux.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="9c1ed-158">Les organisations qui prévoient de tirer profit d'autres offres Office 365, telles que SharePoint Online et Lync Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="9c1ed-159">Environnement Exchange hybride</span><span class="sxs-lookup"><span data-stu-id="9c1ed-159">Exchange Hybrid</span></span>

<span data-ttu-id="9c1ed-160">Cette option de déploiement est idéale pour :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="9c1ed-161">Faciliter une migration d’Exchange en local vers Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="9c1ed-162">Prendre en charge des sites distants sans avoir à investir dans une infrastructure de succursale.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="9c1ed-163">Les sociétés multinationales avec des filiales qui exigent que les données soient hébergées sur site.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="9c1ed-164">Environnement Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="9c1ed-164">Exchange Server on-premises</span></span>

<span data-ttu-id="9c1ed-165">Cette option de déploiement est idéale pour :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="9c1ed-166">Les solutions hautement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="9c1ed-167">Les solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="9c1ed-168">Les organisations soumises à des réglementations de gouvernance de données qui exigent que les données soient hébergées sur site.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="9c1ed-169">Les organisations qui souhaitent conserver le contrôle de l’ensemble de la plateforme et de la solution.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="9c1ed-170">Environnement Exchange hébergé par un fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="9c1ed-171">Cette option de déploiement est idéale pour :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="9c1ed-172">Les organisations qui ont besoin d’une fonctionnalité Exchange Server, mais qui souhaitent sous-traiter son déploiement et sa maintenance.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="9c1ed-173">Les organisations qui ont besoin d’options de support personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="9c1ed-174">Les solutions personnalisées et l’intégration avec des applications personnalisées proposées par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="9c1ed-175">Les solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="9c1ed-176">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="9c1ed-176">License requirements</span></span>

<span data-ttu-id="9c1ed-177">Le tableau suivant détaille les critères de licence pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="9c1ed-178">**Option de déploiement**</span><span class="sxs-lookup"><span data-stu-id="9c1ed-178">**Deployment option**</span></span>|<span data-ttu-id="9c1ed-179">**Critères de licence**</span><span class="sxs-lookup"><span data-stu-id="9c1ed-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9c1ed-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="9c1ed-181">Modèle d’abonnement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="9c1ed-182">Environnement Exchange hybride</span><span class="sxs-lookup"><span data-stu-id="9c1ed-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="9c1ed-183">Office 365 : modèle d'abonnement</span><span class="sxs-lookup"><span data-stu-id="9c1ed-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="9c1ed-184">Environnement local : toutes les licences locales s'appliquent (révision des licences pour Exchange Server en local)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="9c1ed-185">Licence de serveur hybride*</span><span class="sxs-lookup"><span data-stu-id="9c1ed-185">Hybrid server license*</span></span> <br/> |
|<span data-ttu-id="9c1ed-186">Environnement Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="9c1ed-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="9c1ed-187">Système d’exploitation du serveur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-187">Server Operating System</span></span> <br/>  <span data-ttu-id="9c1ed-188">Licence de serveur Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="9c1ed-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="9c1ed-189">Licence d’accès au client Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="9c1ed-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="9c1ed-190">Environnement Exchange hébergé par un fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="9c1ed-191">Les coûts sont déterminés en fonction de l’accord avec le fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="9c1ed-192">Tâches d’architecture</span><span class="sxs-lookup"><span data-stu-id="9c1ed-192">Architecture tasks</span></span>

<span data-ttu-id="9c1ed-193">Cette section répertorie les tâches d’architecture pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="9c1ed-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="9c1ed-195">Planifier et concevoir la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="9c1ed-196">Vérifier la connectivité et la capacité du réseau via les pare-feu, les serveurs proxy, les passerelles et sur l’ensemble des liaisons de réseau étendu (WAN).</span><span class="sxs-lookup"><span data-stu-id="9c1ed-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="9c1ed-197">Environnement Exchange hybride</span><span class="sxs-lookup"><span data-stu-id="9c1ed-197">Exchange Hybrid</span></span>

<span data-ttu-id="9c1ed-198">En plus des tâches d'architecture pour les environnements Office 365 et locaux :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="9c1ed-199">Décider de rendre disponible ou non l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="9c1ed-200">Décider d’acheminer le courrier Internet entrant via une organisation locale ou via Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="9c1ed-201">Environnement Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="9c1ed-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="9c1ed-202">Concevoir la topologie Exchange.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="9c1ed-203">Planifier la capacité du matériel de serveur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="9c1ed-204">Concevoir la topologie de routage.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="9c1ed-205">Concevoir l’équilibrage de charge pour les serveurs d’accès au client.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="9c1ed-206">Planifier la haute disponibilité à l’aide de groupes de disponibilité de base de données.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="9c1ed-207">Environnement Exchange hébergé par un fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="9c1ed-208">Assurez-vous que la capacité et la disponibilité du réseau via les pare-feu, les serveurs proxy, les passerelles et sur l’ensemble des liaisons WAN sont disponibles pour votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="9c1ed-209">Responsabilités des professionnels de l’informatique</span><span class="sxs-lookup"><span data-stu-id="9c1ed-209">IT Pro responsibilities</span></span>

<span data-ttu-id="9c1ed-210">Cette section répertorie les responsabilités des professionnels de l’informatique pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="9c1ed-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9c1ed-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="9c1ed-212">Implémentation du plan de synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="9c1ed-213">Planification et implémentation du routage et des enregistrements DNS internes et externes.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="9c1ed-214">Configuration du serveur proxy ou du pare-feu pour les exigences en matière d'URL et d'adresse IP Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="9c1ed-215">Gestion des comptes d’utilisateurs et des paramètres Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="9c1ed-216">Environnement Exchange hybride</span><span class="sxs-lookup"><span data-stu-id="9c1ed-216">Exchange Hybrid</span></span>

<span data-ttu-id="9c1ed-217">En plus des responsabilités des professionnels de l'informatique pour les environnements locaux et Office 365 :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="9c1ed-218">Configuration des services ADFS (Active Directory Federation Services) pour l’authentification unique (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="9c1ed-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="9c1ed-219">Configuration des certificats Exchange pour des communications sécurisées entre les serveurs Exchange 2013 et Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="9c1ed-220">Configuration des enregistrements DNS pour le chemin de messagerie Internet entrant souhaité.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="9c1ed-221">Environnement Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="9c1ed-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="9c1ed-222">Configuration des certificats requis pour les services Exchange.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="9c1ed-223">Configuration des serveurs.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-223">Provision the servers.</span></span>
    
- <span data-ttu-id="9c1ed-224">Implémentation de la topologie de routage de messages Exchange.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="9c1ed-225">Implémentation des groupes de disponibilité de base de données.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="9c1ed-226">Mise à jour et gestion des serveurs Exchange.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="9c1ed-227">En fonction de l’utilisation, ajout ou suppression de serveurs selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="9c1ed-228">Environnement Exchange hébergé par un fournisseur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="9c1ed-229">Les responsabilités du fournisseur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="9c1ed-230">Maintenance du service et du système.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="9c1ed-231">Déploiement des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="9c1ed-232">Protection des données et récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="9c1ed-233">Les responsabilités du personnel informatique de votre organisation incluent la création et la gestion de comptes d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="9c1ed-234">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="9c1ed-234">More information</span></span>

<span data-ttu-id="9c1ed-235">Pour en savoir plus sur Exchange Online (Office 365), consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- <span data-ttu-id="9c1ed-236">[Description du service Exchange Online](((https://aka.ms/EXO)SD))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-236">[Exchange Online service description](((https://aka.ms/EXO)SD))</span></span>
    
- <span data-ttu-id="9c1ed-237">[Bibliothèque Exchange Online sur TechNet](((https://aka.ms/EXO)TN))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-237">[Exchange Online library on TechNet](((https://aka.ms/EXO)TN))</span></span>
    
- <span data-ttu-id="9c1ed-238">[Portail Exchange Online]((https://aka.ms/EXO))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-238">[Exchange Online portal]((https://aka.ms/EXO))</span></span>
    
<span data-ttu-id="9c1ed-239">Pour plus d’informations sur l’environnement Exchange hybride, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="9c1ed-p104">[Déploiements hybrides Exchange 2013]((https://aka.ms/ExchangeHybrid)). Veuillez noter que la licence de serveur hybride est uniquement requise pour les scénarios suivants : organisation Exchange 2010 avec un serveur hybride Exchange 2013 et organisation Exchange 2007 avec un serveur hybride Exchange 2010 ou Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p104">[Exchange 2013 hybrid deployments]((https://aka.ms/ExchangeHybrid)). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- <span data-ttu-id="9c1ed-242">[Page de connexion à Office 365]((https://aka.ms/HybridKey))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-242">[Office 365 Sign in]((https://aka.ms/HybridKey))</span></span>
    
<span data-ttu-id="9c1ed-243">Pour en savoir plus sur l’environnement Exchange local, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- <span data-ttu-id="9c1ed-244">[Bibliothèque Exchange Server 2013 sur TechNet]((https://aka.ms/Ex2013TN))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-244">[Exchange Server 2013 library on TechNet]((https://aka.ms/Ex2013TN))</span></span>
    
- <span data-ttu-id="9c1ed-245">[Portail Exchange Server 2013]((https://aka.ms/Exchange2013))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-245">[Exchange Server 2013 portal]((https://aka.ms/Exchange2013))</span></span>
    
- <span data-ttu-id="9c1ed-246">[Architecture Exchange Server 2013]((https://aka.ms/Ex2013SP1ArchPoster))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-246">[Exchange Server 2013 architecture]((https://aka.ms/Ex2013SP1ArchPoster))</span></span>
    
<span data-ttu-id="9c1ed-247">Pour en savoir plus sur l’environnement Exchange hébergé par un fournisseur, consultez la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="9c1ed-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
<span data-ttu-id="9c1ed-248">[Solutions et guide d'hébergement et d'architecture mutualisée Exchange Server 2013]((https://aka.ms/Ex2013Hosting))</span><span class="sxs-lookup"><span data-stu-id="9c1ed-248">[Exchange Server 2013 hosting and multi-tenancy solutions and guidance]((https://aka.ms/Ex2013Hosting))</span></span>
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="9c1ed-249">Descriptions de trois fonctionnalités nouvelles ou mises à jour dans Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="9c1ed-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="9c1ed-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="9c1ed-250">Exchange Online Protection</span></span>

<span data-ttu-id="9c1ed-p105">Exchange Online Protection (EOP) fournit une protection contre le courrier indésirable et contre les programmes malveillants pour tout déploiement en proposant une couche de fonctionnalités de protection déployées sur un réseau mondial de centres de données. Cette protection vous permet de gérer vos environnements de messagerie plus facilement. EOP est inclus dans les abonnements Exchange Online, mais vous pouvez également l’utiliser pour les déploiements hybrides et locaux.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="9c1ed-254">Les diagrammes associés présentent les déploiements Exchange Online, Exchange hybride et Exchange local qui comprennent la couche EOP dans le réseau global.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="9c1ed-255">Assistant de déploiement Exchange Server</span><span class="sxs-lookup"><span data-stu-id="9c1ed-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="9c1ed-p106">L’Assistant de déploiement Exchange Server est un outil web qui vous pose quelques questions concernant votre environnement actuel, puis génère une liste de contrôle détaillée et personnalisée pour vous aider à déployer Exchange Server pour différents types de scénarios. Que vous migriez depuis une version antérieure d’Exchange vers Exchange 2013, vers Exchange Online ou que vous planifiiez une infrastructure hybride, l’Assistant de déploiement Exchange Server crée une liste de contrôle personnalisée pour le déploiement de votre scénario.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="9c1ed-258">La capture d’écran associée présente un exemple de liste de contrôle créée à l’aide de l’Assistant de déploiement Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="9c1ed-259">Intégration avec Lync et SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c1ed-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="9c1ed-p107">Exchange Server 2013 inclut de nombreuses fonctionnalités qui s'intègrent à Lync Server 2013 et SharePoint Server 2013. Ensemble, ces produits proposent un large éventail de fonctionnalités et améliorent la collaboration au sein de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="9c1ed-262">Un diagramme d’illustration présente l’affiche portant sur l’authentification de serveur à serveur et comprend un lien vers celle-ci.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="9c1ed-263">Archivage, mise en attente et découverte électronique</span><span class="sxs-lookup"><span data-stu-id="9c1ed-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="9c1ed-264">Boîtes aux lettres de site</span><span class="sxs-lookup"><span data-stu-id="9c1ed-264">Site mailboxes</span></span>
    
- <span data-ttu-id="9c1ed-265">Magasin de contacts unifié</span><span class="sxs-lookup"><span data-stu-id="9c1ed-265">Unified contact store</span></span>
    
- <span data-ttu-id="9c1ed-266">Photos haute résolution de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="9c1ed-267">Fonctionnalité de présence Lync dans Outlook et Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="9c1ed-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="9c1ed-268">Authentification de serveur à serveur</span><span class="sxs-lookup"><span data-stu-id="9c1ed-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="9c1ed-269">Messagerie vocale</span><span class="sxs-lookup"><span data-stu-id="9c1ed-269">Voicemail</span></span>
    
- <span data-ttu-id="9c1ed-270">Enregistrements de réunions</span><span class="sxs-lookup"><span data-stu-id="9c1ed-270">Meeting recordings</span></span>
    
- <span data-ttu-id="9c1ed-271">Synchronisation de tâches Exchange</span><span class="sxs-lookup"><span data-stu-id="9c1ed-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="9c1ed-272">Un diagramme d'illustration présente l'affiche Architecture d'Exchange Server 2013 SP1 et fournit un lien vers celle-ci.</span><span class="sxs-lookup"><span data-stu-id="9c1ed-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

