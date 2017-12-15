---
title: Diagramme accessible  Options de plateforme Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: "Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Lync 2013, qui est disponible dans la rubrique Diagrammes techniques."
ms.openlocfilehash: 79342a30a0391980cf16304f3615f6a7e64d51ff
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="fb817-103">Diagramme accessible : Options de plateforme Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="fb817-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="fb817-104">**Résumé :** Cet article est une version texte accessible du diagramme nommé Options de plate-forme Microsoft Lync 2013, qui est disponible à l’adresse [Diagrammes techniques](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="fb817-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="fb817-105">Cette affiche décrit ce que les architectes et les décideurs d'entreprise (BDM) doivent savoir sur les déploiements Lync Online (Office 365) et Lync Server et inclut :</span><span class="sxs-lookup"><span data-stu-id="fb817-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="fb817-106">Une comparaison de quatre options de déploiement : Lync Online (Office 365), hybride Lync Online/Server, Lync Server et Lync Server hébergé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fb817-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="fb817-107">Deux exemples de scénarios de déploiement de Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="fb817-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="fb817-108">Une comparaison de quatre déploiements distincts pour la plateforme Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="fb817-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="fb817-109">La comparaison fournit des informations sur chaque option de déploiement dans les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb817-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="fb817-110">Une vue d'ensemble des différentes fonctionnalités de déploiement</span><span class="sxs-lookup"><span data-stu-id="fb817-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="fb817-111">Avantages de l'implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="fb817-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="fb817-112">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="fb817-112">Licensing requirements</span></span>
    
- <span data-ttu-id="fb817-113">Tâches architecturales requises</span><span class="sxs-lookup"><span data-stu-id="fb817-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="fb817-114">Responsabilités des professionnels informatiques pour l'implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="fb817-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="fb817-115">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="fb817-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="fb817-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fb817-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="fb817-117">Gagnez en efficacité et optimisez les coûts avec les plans partagés au sein d'une architecture mutualisée de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fb817-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="fb817-118">Le schéma associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de compte entre l'environnement local des services de domaine Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb817-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="fb817-119">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="fb817-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fb817-120">Software as a Service (SaaS).</span><span class="sxs-lookup"><span data-stu-id="fb817-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="fb817-121">L'ensemble riche de fonctionnalités est toujours à jour.</span><span class="sxs-lookup"><span data-stu-id="fb817-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="fb817-122">Comprend un client Azure Active Directory pour les comptes en ligne, qui peut être utilisé avec d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="fb817-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="fb817-123">L'intégration Directory comprend la synchronisation des mots de passe et des noms de compte entre l'environnement des services de domaine Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb817-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="fb817-124">Si l'authentification unique (SSO) est une exigence, les services ADFS (Active Directory Federation Services) doivent être implémentés.</span><span class="sxs-lookup"><span data-stu-id="fb817-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="fb817-125">La communication client sur Internet est chiffrée et authentifiée.</span><span class="sxs-lookup"><span data-stu-id="fb817-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="fb817-126">La connectivité à l'équipement téléphonique hérité (réseau téléphonique commuté) est disponible par le biais de fournisseurs tiers.</span><span class="sxs-lookup"><span data-stu-id="fb817-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="fb817-127">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="fb817-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="fb817-128">Vous pouvez associer les avantages d'Office 365 à un déploiement local de Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="fb817-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="fb817-p101">Le diagramme associé représente Office 365 avec Lync Online où certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne. Un serveur Edge déployé local est également représenté.</span><span class="sxs-lookup"><span data-stu-id="fb817-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="fb817-131">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="fb817-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fb817-132">Certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne, mais ils partagent tous le même domaine SIP (contoso.com, par exemple).</span><span class="sxs-lookup"><span data-stu-id="fb817-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="fb817-133">Utilisez votre infrastructure Lync Server 2013 existante, notamment les connexions au réseau téléphonique commuté (RTC).</span><span class="sxs-lookup"><span data-stu-id="fb817-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="fb817-134">Ajoutez de nouveaux utilisateurs Lync Online facilement lorsqu'ils n'ont pas besoin du RTC.</span><span class="sxs-lookup"><span data-stu-id="fb817-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="fb817-135">Migrez progressivement de Lync en local vers Lync Online, selon votre planification.</span><span class="sxs-lookup"><span data-stu-id="fb817-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="fb817-136">Intégrez d'autres applications Office 365, y compris Exchange Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="fb817-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="fb817-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="fb817-137">Lync Server</span></span>

<span data-ttu-id="fb817-p102">Dans ce déploiement, vous êtes propriétaire de tous les éléments. Le diagramme associé présente une infrastructure Lync Server avec un environnement local des services de domaine Active Directory dans lequel les utilisateurs sont hébergés localement.</span><span class="sxs-lookup"><span data-stu-id="fb817-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="fb817-140">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="fb817-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fb817-141">Planification et dimensionnement de la capacité.</span><span class="sxs-lookup"><span data-stu-id="fb817-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="fb817-142">Configuration et acquisition du serveur.</span><span class="sxs-lookup"><span data-stu-id="fb817-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="fb817-143">Déploiement.</span><span class="sxs-lookup"><span data-stu-id="fb817-143">Deployment.</span></span>
    
- <span data-ttu-id="fb817-144">Mise à l'échelle, mise à jour corrective et opérations.</span><span class="sxs-lookup"><span data-stu-id="fb817-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="fb817-145">Sauvegarde des données.</span><span class="sxs-lookup"><span data-stu-id="fb817-145">Backing up data.</span></span>
    
- <span data-ttu-id="fb817-146">Maintenance du basculement et de la récupération d'urgence.</span><span class="sxs-lookup"><span data-stu-id="fb817-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="fb817-147">Connexion de l'infrastructure Lync Server 2013 au RTC</span><span class="sxs-lookup"><span data-stu-id="fb817-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="fb817-148">Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).</span><span class="sxs-lookup"><span data-stu-id="fb817-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="fb817-149">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="fb817-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="fb817-p103">Dans ce déploiement, votre fournisseur possède tous les éléments. Le diagramme associé représente le réseau d'un fournisseur comprenant ses serveurs et équipement avec une connexion à un environnement local.</span><span class="sxs-lookup"><span data-stu-id="fb817-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="fb817-152">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="fb817-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fb817-153">Planification et dimensionnement de la capacité.</span><span class="sxs-lookup"><span data-stu-id="fb817-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="fb817-154">Configuration et acquisition du serveur.</span><span class="sxs-lookup"><span data-stu-id="fb817-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="fb817-155">Déploiement.</span><span class="sxs-lookup"><span data-stu-id="fb817-155">Deployment.</span></span>
    
- <span data-ttu-id="fb817-156">Mise à l'échelle, mise à jour corrective et opérations.</span><span class="sxs-lookup"><span data-stu-id="fb817-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="fb817-157">Sauvegarde des données.</span><span class="sxs-lookup"><span data-stu-id="fb817-157">Backing up data.</span></span>
    
- <span data-ttu-id="fb817-158">Maintenance du basculement et de la récupération d'urgence.</span><span class="sxs-lookup"><span data-stu-id="fb817-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="fb817-159">Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).</span><span class="sxs-lookup"><span data-stu-id="fb817-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="fb817-160">Par ailleurs, le fournisseur peut :</span><span class="sxs-lookup"><span data-stu-id="fb817-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="fb817-161">Installer ses serveurs et équipements dans son propre réseau à l'aide d'une connexion à votre réseau local (trait plein).</span><span class="sxs-lookup"><span data-stu-id="fb817-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="fb817-162">Installer ses serveurs sur votre réseau local (ligne en pointillés).</span><span class="sxs-lookup"><span data-stu-id="fb817-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="fb817-163">Avantages de l'implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="fb817-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="fb817-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fb817-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="fb817-165">Aucune charge de fonctionnement liée aux serveurs locaux ou aux logiciels serveur.</span><span class="sxs-lookup"><span data-stu-id="fb817-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="fb817-166">Fonctionnalités de communication de Lync Server 2013 en tant que service cloud.</span><span class="sxs-lookup"><span data-stu-id="fb817-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="fb817-167">Fonctionnalités de présence, de messagerie instantanée, d'appels audio et vidéo, de réunions en ligne denses et de conférences sur le web.</span><span class="sxs-lookup"><span data-stu-id="fb817-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="fb817-168">Utilisées pour les organisations dispersées sur le plan géographique ou dont les employés principalement mobiles.</span><span class="sxs-lookup"><span data-stu-id="fb817-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="fb817-169">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="fb817-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="fb817-170">Utilisez Lync Online pour les utilisateurs distants et l'intégration avec des partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="fb817-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="fb817-171">Facilitez une migration à partir de Lync en local vers Lync Online.</span><span class="sxs-lookup"><span data-stu-id="fb817-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="fb817-172">Prenez en charge des sites distants sans utiliser l'équipement d'une filiale.</span><span class="sxs-lookup"><span data-stu-id="fb817-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="fb817-173">Ajoutez facilement la prise en charge de Lync dans les nouvelles acquisitions d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="fb817-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="fb817-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="fb817-174">Lync Server</span></span>

- <span data-ttu-id="fb817-175">Solutions de cloud privées.</span><span class="sxs-lookup"><span data-stu-id="fb817-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="fb817-176">Les solutions hautement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fb817-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="fb817-177">Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.</span><span class="sxs-lookup"><span data-stu-id="fb817-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="fb817-178">Restrictions de confidentialité qui empêchent la synchronisation des comptes AD DS avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="fb817-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="fb817-179">Organisations qui souhaitent bénéficier du contrôle de l'ensemble de la plateforme et de la solution.</span><span class="sxs-lookup"><span data-stu-id="fb817-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="fb817-180">Remplacement de PBX par Voix Entreprise de Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="fb817-181">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="fb817-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="fb817-182">Organisations qui veulent bénéficier des fonctionnalités de Lync Server mais qui souhaitent externaliser leur déploiement et leur maintenance.</span><span class="sxs-lookup"><span data-stu-id="fb817-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="fb817-183">Solutions fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fb817-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="fb817-184">Les solutions hautement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fb817-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="fb817-185">Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.</span><span class="sxs-lookup"><span data-stu-id="fb817-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="fb817-186">Remplacement de PBX par Voix Entreprise de Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="fb817-187">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="fb817-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="fb817-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fb817-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="fb817-189">Modèle d'abonnement.</span><span class="sxs-lookup"><span data-stu-id="fb817-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="fb817-190">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="fb817-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="fb817-p104">Office 365  Modèle d'abonnement. Aucune licence supplémentaire nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fb817-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="fb817-193">Local  Toutes les licences locales s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="fb817-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="fb817-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="fb817-194">Lync Server</span></span>

- <span data-ttu-id="fb817-195">Système d'exploitation du serveur</span><span class="sxs-lookup"><span data-stu-id="fb817-195">Server Operating System</span></span>
    
- <span data-ttu-id="fb817-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fb817-196">SQL Server</span></span>
    
- <span data-ttu-id="fb817-197">Licence de serveur Lync 2013</span><span class="sxs-lookup"><span data-stu-id="fb817-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="fb817-198">Licence d'accès au client Lync 2013</span><span class="sxs-lookup"><span data-stu-id="fb817-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="fb817-199">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="fb817-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="fb817-200">Les coûts dépendent de l'accord conclu avec votre fournisseur de la solution Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="fb817-201">Tâches d'architecture</span><span class="sxs-lookup"><span data-stu-id="fb817-201">Architecture tasks</span></span>

<span data-ttu-id="fb817-202">Cette section répertorie les tâches d'architecture pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fb817-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="fb817-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fb817-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="fb817-204">Planifier et concevoir la synchronisation d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="fb817-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="fb817-205">Garantir la capacité et la disponibilité du réseau grâce à des pare-feu, des serveurs proxy, des passerelles et des liaisons WAN.</span><span class="sxs-lookup"><span data-stu-id="fb817-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="fb817-206">Acquérir des certificats SSL tiers pour fournir une sécurité d'entreprise pour les offres de service Office 365.</span><span class="sxs-lookup"><span data-stu-id="fb817-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="fb817-207">Décider si vous souhaitez vous connecter à Office 365 en utilisant le protocole IPv6.</span><span class="sxs-lookup"><span data-stu-id="fb817-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="fb817-208">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="fb817-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="fb817-209">En plus des tâches pour les environnements Office 365 et locaux :</span><span class="sxs-lookup"><span data-stu-id="fb817-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="fb817-210">Déterminez les besoins en matière d'intégration de fonctionnalités avec les versions locales et en ligne d'Exchange Server et de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fb817-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="fb817-211">Si nécessaire, déterminez le périphérique de serveur proxy à utiliser pour les demandes provenant de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fb817-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="fb817-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="fb817-212">Lync Server</span></span>

<span data-ttu-id="fb817-213">Concevez l'environnement Lync dans un environnement local existant :</span><span class="sxs-lookup"><span data-stu-id="fb817-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="fb817-214">Topologie Lync pour les filiales et les bureaux principaux.</span><span class="sxs-lookup"><span data-stu-id="fb817-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="fb817-215">Matériel de serveur, y compris la virtualisation.</span><span class="sxs-lookup"><span data-stu-id="fb817-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="fb817-216">Intégration avec les services de domaine Active Directory et le DNS.</span><span class="sxs-lookup"><span data-stu-id="fb817-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="fb817-217">Équilibrage de charge pour les pools de serveurs Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="fb817-218">Basculement et récupération d'urgence.</span><span class="sxs-lookup"><span data-stu-id="fb817-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="fb817-219">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="fb817-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="fb817-220">Pour une installation informatique, déterminez la connexion au réseau du fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="fb817-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="fb817-221">Pour une installation locale, déterminez l'emplacement des serveurs Lync du fournisseur sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="fb817-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="fb817-222">Pour les deux types d'installation, déterminez l'intégration avec AD DS et votre équipement PBX.</span><span class="sxs-lookup"><span data-stu-id="fb817-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="fb817-223">Responsabilités des professionnels de l'informatique</span><span class="sxs-lookup"><span data-stu-id="fb817-223">IT Pro responsibilities</span></span>

<span data-ttu-id="fb817-224">Cette section répertorie les responsabilités des professionnels de l'informatique pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fb817-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="fb817-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fb817-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="fb817-226">Déployez et gérez Lync Online (Office 365) :</span><span class="sxs-lookup"><span data-stu-id="fb817-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="fb817-227">Implémentation du plan de synchronisation d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="fb817-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="fb817-228">Planification et implémentation du routage et des enregistrements DNS internes et externes.</span><span class="sxs-lookup"><span data-stu-id="fb817-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="fb817-229">Configurez le proxy ou pare-feu pour l'adresse IP Office 365 et les exigences d'URL.</span><span class="sxs-lookup"><span data-stu-id="fb817-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="fb817-230">Gérez les comptes d'utilisateurs et les paramètres Lync Online.</span><span class="sxs-lookup"><span data-stu-id="fb817-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="fb817-231">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="fb817-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="fb817-232">En plus des tâches pour les environnements Office 365 et locaux :</span><span class="sxs-lookup"><span data-stu-id="fb817-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="fb817-233">Configurez le périphérique de serveur proxy, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fb817-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="fb817-234">Configurez l'intégration de fonctionnalités avec les versions locales et en ligne d'Exchange Server et de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fb817-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="fb817-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="fb817-235">Lync Server</span></span>

<span data-ttu-id="fb817-236">Déployez et gérez Lync Server dans un environnement local :</span><span class="sxs-lookup"><span data-stu-id="fb817-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="fb817-237">Configuration des serveurs.</span><span class="sxs-lookup"><span data-stu-id="fb817-237">Provision the servers.</span></span>
    
- <span data-ttu-id="fb817-238">Déployez la topologie de Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="fb817-239">Mettez à jour les serveurs Lync.</span><span class="sxs-lookup"><span data-stu-id="fb817-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="fb817-240">Ajoutez ou supprimez des serveurs de topologie en fonction de l'utilisation.</span><span class="sxs-lookup"><span data-stu-id="fb817-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="fb817-241">Implémentez l'environnement de basculement et de récupération d'urgence.</span><span class="sxs-lookup"><span data-stu-id="fb817-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="fb817-242">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="fb817-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="fb817-243">Collaborez avec le fournisseur pour :</span><span class="sxs-lookup"><span data-stu-id="fb817-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="fb817-244">Intégrer Lync Server à votre réseau.</span><span class="sxs-lookup"><span data-stu-id="fb817-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="fb817-245">Intégrer Lync Server avec d'autres produits ou solutions personnalisées Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fb817-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="fb817-246">S'assurer que le contrat de niveau de service (SLA) du fournisseur est respecté.</span><span class="sxs-lookup"><span data-stu-id="fb817-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="fb817-247">Deux exemples de scénarios de déploiement de Lync 2013</span><span class="sxs-lookup"><span data-stu-id="fb817-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="fb817-248">Composants de la synchronisation d'annuaires dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="fb817-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="fb817-249">Le déploiement des composants de synchronisation d'annuaires Office 365 dans Azure est plus rapide grâce à la capacité de déploiement de machines virtuelles à la demande.</span><span class="sxs-lookup"><span data-stu-id="fb817-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="fb817-250">Le diagramme associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb817-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="fb817-p105">**Serveur de synchronisation d'annuaires uniquement**. Plutôt que de déployer le serveur de synchronisation d'annuaires 64 bits dans votre environnement local, mettez en service une machine virtuelle dans Azure sur Internet.</span><span class="sxs-lookup"><span data-stu-id="fb817-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="fb817-p106">**Synchronisation d'annuaires + AD FS**. Cette option vous permet de prendre en charge les identités fédérées Office 365 (SSO) sans ajouter de matériel à votre infrastructure locale. Elle fournit également la résilience si l'environnement Active Directory local n'est pas disponible. Les fonctionnalités de cette option sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb817-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="fb817-257">Composants d'intégration d'annuaire exécutés en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="fb817-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="fb817-258">AD FS est publié sur Internet par le biais de proxies AD FS s'exécutant en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="fb817-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="fb817-259">Le trafic d'authentification du client, pour les utilisateurs qui se connectent à partir de n'importe quel endroit, est géré par les serveurs et les proxies AD FS qui sont déployés en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="fb817-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="fb817-260">Intégration de Lync avec Exchange et SharePoint dans Office 365</span><span class="sxs-lookup"><span data-stu-id="fb817-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="fb817-261">Lync Server avec Exchange Online et SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fb817-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="fb817-262">Le diagramme associé représente Office 365 avec Exchange Online et SharePoint Online connectés à une batterie de serveurs Lync Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="fb817-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="fb817-263">Ce déploiement offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb817-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="fb817-264">Utiliser l'intégralité des fonctionnalités de Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="fb817-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="fb817-265">Utiliser vos équipements téléphoniques existants, tels que les PBX.</span><span class="sxs-lookup"><span data-stu-id="fb817-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="fb817-266">Utiliser Exchange Online pour la messagerie, l'allègement de la charge des serveurs de messagerie et de l'espace de stockage local.</span><span class="sxs-lookup"><span data-stu-id="fb817-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="fb817-267">Utiliser SharePoint Online pour la collaboration, l'allègement de la charge de maintenance des serveurs SharePoint locaux.</span><span class="sxs-lookup"><span data-stu-id="fb817-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="fb817-268">Utiliser les fonctionnalités intégrées de Lync, d'Exchange et de SharePoint, notamment la messagerie unifiée dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="fb817-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="fb817-269">Exchange Server avec Lync Online</span><span class="sxs-lookup"><span data-stu-id="fb817-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="fb817-270">Le diagramme associé représente Office 365 avec Lync Online connecté à une batterie de serveurs Exchange Server locale.</span><span class="sxs-lookup"><span data-stu-id="fb817-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="fb817-271">Ce déploiement offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb817-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="fb817-272">Utiliser votre infrastructure Exchange existante.</span><span class="sxs-lookup"><span data-stu-id="fb817-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="fb817-273">Utiliser Lync Online pour les fonctionnalités de présence, de messagerie instantanée et de conférence.</span><span class="sxs-lookup"><span data-stu-id="fb817-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

