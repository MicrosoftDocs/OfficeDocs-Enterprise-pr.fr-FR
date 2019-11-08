---
title: Diagramme accessible  Options de plateforme Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Lync 2013, qui est disponible dans la rubrique Diagrammes techniques.
ms.openlocfilehash: a62fb6d1e1ee7fbddb79b0aec4ddafea4b07b4fe
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030598"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="5bfb0-103">Diagramme accessible : Options de plateforme Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="5bfb0-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="5bfb0-104">**Résumé :** Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Lync 2013, qui est disponible dans la rubrique [Diagrammes techniques](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="5bfb0-105">Cette affiche décrit ce que les architectes et les décideurs d'entreprise (BDM) doivent savoir sur les déploiements Lync Online (Office 365) et Lync Server et inclut :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="5bfb0-106">Une comparaison de quatre options de déploiement : Lync Online (Office 365), hybride Lync Online/Server, Lync Server et Lync Server hébergé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="5bfb0-107">Deux exemples de scénarios de déploiement de Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="5bfb0-108">Une comparaison de quatre déploiements distincts pour la plateforme Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="5bfb0-109">La comparaison fournit des informations sur chaque option de déploiement dans les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="5bfb0-110">Une vue d’ensemble des différentes fonctionnalités de déploiement</span><span class="sxs-lookup"><span data-stu-id="5bfb0-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="5bfb0-111">Avantages de l'implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="5bfb0-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="5bfb0-112">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="5bfb0-112">Licensing requirements</span></span>
    
- <span data-ttu-id="5bfb0-113">Tâches architecturales requises</span><span class="sxs-lookup"><span data-stu-id="5bfb0-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="5bfb0-114">Responsabilités des professionnels informatiques pour l’implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="5bfb0-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="5bfb0-115">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="5bfb0-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="5bfb0-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="5bfb0-117">Gagnez en efficacité et optimisez les coûts avec les plans partagés au sein d'une architecture mutualisée de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="5bfb0-118">Le schéma associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de compte entre l'environnement local des services de domaine Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="5bfb0-119">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="5bfb0-120">Software as a Service (SaaS).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="5bfb0-121">L’ensemble riche de fonctionnalités est toujours à jour.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="5bfb0-122">Comprend un client Azure Active Directory pour les comptes en ligne, qui peut être utilisé avec d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="5bfb0-123">L'intégration Directory comprend la synchronisation des mots de passe et des noms de compte entre l'environnement des services de domaine Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="5bfb0-124">Si l'authentification unique (SSO) est une exigence, les services ADFS (Active Directory Federation Services) doivent être implémentés.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="5bfb0-125">La communication client sur Internet est chiffrée et authentifiée.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="5bfb0-126">La connectivité à l’équipement téléphonique hérité (réseau téléphonique commuté) est disponible par le biais de fournisseurs tiers.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="5bfb0-127">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="5bfb0-128">Vous pouvez associer les avantages d'Office 365 à un déploiement local de Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="5bfb0-p101">Le diagramme associé représente Office 365 avec Lync Online où certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne. Un serveur Edge déployé local est également représenté.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="5bfb0-131">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="5bfb0-132">Certains utilisateurs sont hébergés localement et d’autres sont hébergés en ligne, mais ils partagent tous le même domaine SIP (contoso.com, par exemple).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="5bfb0-133">Utilisez votre infrastructure Lync Server 2013 existante, notamment les connexions au réseau téléphonique commuté (RTC).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="5bfb0-134">Ajoutez de nouveaux utilisateurs Lync Online facilement lorsqu’ils n’ont pas besoin du RTC.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="5bfb0-135">Migrez progressivement de Lync en local vers Lync Online, selon votre planification.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="5bfb0-136">Intégrez d'autres applications Office 365, y compris Exchange Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="5bfb0-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-137">Lync Server</span></span>

<span data-ttu-id="5bfb0-p102">Dans ce déploiement, vous êtes propriétaire de tous les éléments. Le diagramme associé présente une infrastructure Lync Server avec un environnement local des services de domaine Active Directory dans lequel les utilisateurs sont hébergés localement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="5bfb0-140">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="5bfb0-141">Planification et dimensionnement de la capacité.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="5bfb0-142">Configuration et acquisition du serveur. </span><span class="sxs-lookup"><span data-stu-id="5bfb0-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="5bfb0-143">Déploiement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-143">Deployment.</span></span>
    
- <span data-ttu-id="5bfb0-144">Mise à l’échelle, mise à jour corrective et opérations.  </span><span class="sxs-lookup"><span data-stu-id="5bfb0-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="5bfb0-145">Sauvegarde des données.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-145">Backing up data.</span></span>
    
- <span data-ttu-id="5bfb0-146">Maintenance du basculement et de la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="5bfb0-147">Connexion de l’infrastructure Lync Server 2013 au RTC</span><span class="sxs-lookup"><span data-stu-id="5bfb0-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="5bfb0-148">Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="5bfb0-149">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="5bfb0-p103">Dans ce déploiement, votre fournisseur possède tous les éléments. Le diagramme associé représente le réseau d'un fournisseur comprenant ses serveurs et équipement avec une connexion à un environnement local.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="5bfb0-152">Description des fonctions et fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="5bfb0-153">Planification et dimensionnement de la capacité.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="5bfb0-154">Configuration et acquisition du serveur. </span><span class="sxs-lookup"><span data-stu-id="5bfb0-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="5bfb0-155">Déploiement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-155">Deployment.</span></span>
    
- <span data-ttu-id="5bfb0-156">Mise à l’échelle, mise à jour corrective et opérations.  </span><span class="sxs-lookup"><span data-stu-id="5bfb0-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="5bfb0-157">Sauvegarde des données.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-157">Backing up data.</span></span>
    
- <span data-ttu-id="5bfb0-158">Maintenance du basculement et de la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="5bfb0-159">Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="5bfb0-160">Par ailleurs, le fournisseur peut :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="5bfb0-161">Installer ses serveurs et équipements dans son propre réseau à l’aide d’une connexion à votre réseau local (trait plein).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="5bfb0-162">Installer ses serveurs sur votre réseau local (ligne en pointillés).</span><span class="sxs-lookup"><span data-stu-id="5bfb0-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="5bfb0-163">Avantages de l’implémentation de chaque option de déploiement</span><span class="sxs-lookup"><span data-stu-id="5bfb0-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="5bfb0-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="5bfb0-165">Aucune charge de fonctionnement liée aux serveurs locaux ou aux logiciels serveur.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="5bfb0-166">Fonctionnalités de communication de Lync Server 2013 en tant que service cloud.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="5bfb0-167">Fonctionnalités de présence, de messagerie instantanée, d’appels audio et vidéo, de réunions en ligne denses et de conférences sur le web.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="5bfb0-168">Utilisées pour les organisations dispersées sur le plan géographique ou dont les employés principalement mobiles.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="5bfb0-169">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="5bfb0-170">Utilisez Lync Online pour les utilisateurs distants et l’intégration avec des partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="5bfb0-171">Facilitez une migration à partir de Lync en local vers Lync Online.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="5bfb0-172">Prenez en charge des sites distants sans utiliser l’équipement d’une filiale.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="5bfb0-173">Ajoutez facilement la prise en charge de Lync dans les nouvelles acquisitions d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="5bfb0-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-174">Lync Server</span></span>

- <span data-ttu-id="5bfb0-175">Solutions de cloud privées.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="5bfb0-176">Les solutions hautement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="5bfb0-177">Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="5bfb0-178">Restrictions de confidentialité qui empêchent la synchronisation des comptes AD DS avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="5bfb0-179">Organisations qui souhaitent bénéficier du contrôle de l’ensemble de la plateforme et de la solution.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="5bfb0-180">Remplacement de PBX par Voix Entreprise de Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="5bfb0-181">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="5bfb0-182">Organisations qui veulent bénéficier des fonctionnalités de Lync Server mais qui souhaitent externaliser leur déploiement et leur maintenance.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="5bfb0-183">Solutions fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="5bfb0-184">Les solutions hautement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="5bfb0-185">Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="5bfb0-186">Remplacement de PBX par Voix Entreprise de Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="5bfb0-187">Critères de licence</span><span class="sxs-lookup"><span data-stu-id="5bfb0-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="5bfb0-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="5bfb0-189">Modèle d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="5bfb0-190">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="5bfb0-p104">Office 365  Modèle d'abonnement. Aucune licence supplémentaire nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="5bfb0-193">Local — Toutes les licences locales s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="5bfb0-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-194">Lync Server</span></span>

- <span data-ttu-id="5bfb0-195">Système d’exploitation du serveur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-195">Server Operating System</span></span>
    
- <span data-ttu-id="5bfb0-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-196">SQL Server</span></span>
    
- <span data-ttu-id="5bfb0-197">Licence de serveur Lync 2013</span><span class="sxs-lookup"><span data-stu-id="5bfb0-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="5bfb0-198">Licence d’accès au client Lync 2013</span><span class="sxs-lookup"><span data-stu-id="5bfb0-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="5bfb0-199">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="5bfb0-200">Les coûts dépendent de l’accord conclu avec votre fournisseur de la solution Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="5bfb0-201">Tâches d’architecture</span><span class="sxs-lookup"><span data-stu-id="5bfb0-201">Architecture tasks</span></span>

<span data-ttu-id="5bfb0-202">Cette section répertorie les tâches d’architecture pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="5bfb0-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="5bfb0-204">Planifier et concevoir la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="5bfb0-205">Garantir la capacité et la disponibilité du réseau grâce à des pare-feu, des serveurs proxy, des passerelles et des liaisons WAN.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="5bfb0-206">Acquérez des certificats SSL tiers pour fournir une sécurité d’entreprise pour les offres de service Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="5bfb0-207">Décider si vous souhaitez vous connecter à Office 365 en utilisant le protocole IPv6.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="5bfb0-208">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="5bfb0-209">En plus des tâches pour les environnements Office 365 et locaux :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="5bfb0-210">Déterminez les besoins en matière d’intégration de fonctionnalités avec les versions locales et en ligne d’Exchange Server et de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="5bfb0-211">Si nécessaire, déterminez le périphérique de serveur proxy à utiliser pour les demandes provenant de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="5bfb0-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-212">Lync Server</span></span>

<span data-ttu-id="5bfb0-213">Concevez l’environnement Lync dans un environnement local existant :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="5bfb0-214">Topologie Lync pour les filiales et les bureaux principaux.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="5bfb0-215">Matériel de serveur, y compris la virtualisation.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="5bfb0-216">Intégration avec les services de domaine Active Directory et le DNS.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="5bfb0-217">Équilibrage de charge pour les pools de serveurs Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="5bfb0-218">Basculement et récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="5bfb0-219">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="5bfb0-220">Pour une installation informatique, déterminez la connexion au réseau du fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="5bfb0-221">Pour une installation locale, déterminez l'emplacement des serveurs Lync du fournisseur sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="5bfb0-222">Pour les deux types d’installation, déterminez l’intégration avec AD DS et votre équipement PBX.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="5bfb0-223">Responsabilités des professionnels de l’informatique</span><span class="sxs-lookup"><span data-stu-id="5bfb0-223">IT Pro responsibilities</span></span>

<span data-ttu-id="5bfb0-224">Cette section répertorie les responsabilités des professionnels de l’informatique pour chaque option de déploiement.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="5bfb0-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="5bfb0-226">Déployez et gérez Lync Online (Office 365) :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="5bfb0-227">Implémentation du plan de synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="5bfb0-228">Planification et implémentation du routage et des enregistrements DNS internes et externes.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="5bfb0-229">Configurez le proxy ou pare-feu pour l'adresse IP Office 365 et les exigences d'URL.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="5bfb0-230">Gérez les comptes d’utilisateurs et les paramètres Lync Online.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="5bfb0-231">Déploiement hybride Lync Online/Server (domaine séparé)</span><span class="sxs-lookup"><span data-stu-id="5bfb0-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="5bfb0-232">En plus des tâches pour les environnements Office 365 et locaux :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="5bfb0-233">Configurez le périphérique de serveur proxy, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="5bfb0-234">Configurez l’intégration de fonctionnalités avec les versions locales et en ligne d’Exchange Server et de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="5bfb0-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="5bfb0-235">Lync Server</span></span>

<span data-ttu-id="5bfb0-236">Déployez et gérez Lync Server dans un environnement local :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="5bfb0-237">Configuration des serveurs.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-237">Provision the servers.</span></span>
    
- <span data-ttu-id="5bfb0-238">Déployez la topologie de Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="5bfb0-239">Mettez à jour les serveurs Lync.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="5bfb0-240">Ajoutez ou supprimez des serveurs de topologie en fonction de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="5bfb0-241">Implémentez l’environnement de basculement et de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="5bfb0-242">Lync Server hébergé par le fournisseur</span><span class="sxs-lookup"><span data-stu-id="5bfb0-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="5bfb0-243">Collaborez avec le fournisseur pour :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="5bfb0-244">Intégrer Lync Server à votre réseau.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="5bfb0-245">Intégrer Lync Server avec d’autres produits ou solutions personnalisées Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="5bfb0-246">S’assurer que le contrat de niveau de service (SLA) du fournisseur est respecté.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="5bfb0-247">Deux exemples de scénarios de déploiement de Lync 2013</span><span class="sxs-lookup"><span data-stu-id="5bfb0-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="5bfb0-248">Composants de la synchronisation d’annuaires dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5bfb0-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="5bfb0-249">Le déploiement des composants de synchronisation d'annuaires Office 365 dans Azure est plus rapide grâce à la capacité de déploiement de machines virtuelles à la demande.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="5bfb0-250">Le diagramme associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local Active Directory et le client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="5bfb0-p105">**Serveur de synchronisation d'annuaires uniquement**. Plutôt que de déployer le serveur de synchronisation d'annuaires 64 bits dans votre environnement local, mettez en service une machine virtuelle dans Azure sur Internet.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="5bfb0-p106">**Synchronisation d'annuaires + AD FS**. Cette option vous permet de prendre en charge les identités fédérées Office 365 (SSO) sans ajouter de matériel à votre infrastructure locale. Elle fournit également la résilience si l'environnement Active Directory local n'est pas disponible. Les fonctionnalités de cette option sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="5bfb0-257">Composants d'intégration d'annuaire exécutés en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="5bfb0-258">AD FS est publié sur Internet par le biais de proxies AD FS s'exécutant en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="5bfb0-259">Le trafic d'authentification du client, pour les utilisateurs qui se connectent à partir de n'importe quel endroit, est géré par les serveurs et les proxies AD FS qui sont déployés en tant que machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="5bfb0-260">Intégration de Lync avec Exchange et SharePoint dans Office 365</span><span class="sxs-lookup"><span data-stu-id="5bfb0-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="5bfb0-261">Lync Server avec Exchange Online et SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5bfb0-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="5bfb0-262">Le diagramme associé représente Office 365 avec Exchange Online et SharePoint Online connectés à une batterie de serveurs Lync Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="5bfb0-263">Ce déploiement offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="5bfb0-264">Utiliser l'intégralité des fonctionnalités de Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="5bfb0-265">Utiliser vos équipements téléphoniques existants, tels que les PBX.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="5bfb0-266">Utiliser Exchange Online pour la messagerie, l'allègement de la charge des serveurs de messagerie et de l'espace de stockage local.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="5bfb0-267">Utiliser SharePoint Online pour la collaboration, l'allègement de la charge de maintenance des serveurs SharePoint locaux.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="5bfb0-268">Utiliser les fonctionnalités intégrées de Lync, d'Exchange et de SharePoint, notamment la messagerie unifiée dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="5bfb0-269">Exchange Server avec Lync Online</span><span class="sxs-lookup"><span data-stu-id="5bfb0-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="5bfb0-270">Le diagramme associé représente Office 365 avec Lync Online connecté à une batterie de serveurs Exchange Server locale.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="5bfb0-271">Ce déploiement offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bfb0-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="5bfb0-272">Utiliser votre infrastructure Exchange existante.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="5bfb0-273">Utiliser Lync Online pour les fonctionnalités de présence, de messagerie instantanée et de conférence.</span><span class="sxs-lookup"><span data-stu-id="5bfb0-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

