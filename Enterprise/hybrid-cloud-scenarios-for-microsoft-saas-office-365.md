---
title: "Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Résumé : Comprendre les scénarios et l’architecture de hybride pour Microsoft de base SaaS (Office 365) les offres en nuage."
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="b3a31-103">Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b3a31-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="b3a31-104">**Résumé :** Comprendre les scénarios et l’architecture de hybride pour Microsoft de base SaaS (Office 365) les offres en nuage.</span><span class="sxs-lookup"><span data-stu-id="b3a31-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="b3a31-105">Combinez des déploiements locaux d’Exchange, de SharePoint ou de Skype Entreprise à leur équivalent dans Office 365 dans le cadre d’une migration cloud ou d’une stratégie d’intégration à long terme.</span><span class="sxs-lookup"><span data-stu-id="b3a31-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="b3a31-106">Architecture de scénario hybride pour les services SaaS Microsoft</span><span class="sxs-lookup"><span data-stu-id="b3a31-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="b3a31-107">La figure 1 présente l’architecture des scénarios hybrides SaaS de Microsoft pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="b3a31-108">**Figure 1 : Scénarios de hybride SaaS Microsoft pour Office 365**</span><span class="sxs-lookup"><span data-stu-id="b3a31-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Scénarios hybrides Microsoft SaaS pour Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="b3a31-110">Pour chaque couche de l’architecture :</span><span class="sxs-lookup"><span data-stu-id="b3a31-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="b3a31-111">Applications et scénarios</span><span class="sxs-lookup"><span data-stu-id="b3a31-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="b3a31-112">Il existe plusieurs scénarios hybrides SaaS au niveau des produits serveur Office et de leur équivalent dans Office 365 :</span><span class="sxs-lookup"><span data-stu-id="b3a31-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="b3a31-113">Exchange Server combiné à Exchange Online (Exchange Server hybride)</span><span class="sxs-lookup"><span data-stu-id="b3a31-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="b3a31-114">Skype Entreprise Server combiné à Skype Entreprise Online et aux nouveaux scénarios PBX cloud et édition Cloud Connector</span><span class="sxs-lookup"><span data-stu-id="b3a31-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="b3a31-115">SharePoint Server 2016 ou SharePoint Server 2013 combiné à SharePoint Online (plusieurs scénarios)</span><span class="sxs-lookup"><span data-stu-id="b3a31-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="b3a31-116">Vous pouvez également mettre en place Exchange Online avec Skype Entreprise Server en local (scénario hybride de produit croisé).</span><span class="sxs-lookup"><span data-stu-id="b3a31-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="b3a31-117">Identity</span><span class="sxs-lookup"><span data-stu-id="b3a31-117">Identity</span></span>
    
    <span data-ttu-id="b3a31-p101">Peut inclure la synchronisation d’annuaires avec votre Windows Server AD local. Enfin, vous pouvez configurer Azure AD pour la fédération avec un fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="b3a31-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="b3a31-120">Réseau</span><span class="sxs-lookup"><span data-stu-id="b3a31-120">Network</span></span>
    
    <span data-ttu-id="b3a31-121">Se compose de votre canal Internet existant ou d’une connexion ExpressRoute avec homologation Microsoft pour Office 365 ou Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="b3a31-122">Sur site</span><span class="sxs-lookup"><span data-stu-id="b3a31-122">On-premises</span></span>
    
    <span data-ttu-id="b3a31-p102">Peut être composé de serveurs existants pour Exchange, SharePoint et Skype Entreprise, qui doivent être mis à jour vers la dernière version disponible. Vous pouvez les combiner à leurs équivalents Office 365 pour des scénarios hybrides.</span><span class="sxs-lookup"><span data-stu-id="b3a31-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="b3a31-125">Configurer votre propre [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b3a31-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="b3a31-126">Skype Entreprise 2015 hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="b3a31-p103">Skype pour entreprise 2015 hybride vous permet de combiner un déploiement sur site existant avec Skype pour l’activité en ligne. Certains utilisateurs sont hébergées sur site et certains utilisateurs sont hébergées en ligne, mais les utilisateurs partagent le même domaine de Session Initiation Protocol (SIP), par exemple, contoso.com. Cette configuration hybride permet de migrer sur site vers Office 365 au fil du temps, selon la planification. Skype pour entreprise 2015 peut également être intégré avec Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="b3a31-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="b3a31-130">**Figure 2 : Le Skype pour la configuration de Business 2015 hybride**</span><span class="sxs-lookup"><span data-stu-id="b3a31-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Configuration hybride Skype Entreprise 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="b3a31-132">La figure 2 illustre la Skype pour configuration hybride de Business 2015, consistant en un Skype sur site pour le pool de front-end d’entreprise 2015 et edge server communique avec Skype pour Business Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="b3a31-133">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b3a31-133">For more information, see:</span></span>
  
- [<span data-ttu-id="b3a31-134">Planification de la connectivité d’hybride entre Skype pour Business Server et Skype pour professionnels en ligne</span><span class="sxs-lookup"><span data-stu-id="b3a31-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="b3a31-135">Configurations prises en charge hybride Skype pour Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="b3a31-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="b3a31-136">Skype pour entreprise hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="b3a31-137">PBX cloud avec Skype Entreprise Server</span><span class="sxs-lookup"><span data-stu-id="b3a31-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="b3a31-138">PBX cloud avec Skype Entreprise Server vous permet de convertir un déploiement local de Skype Entreprise Server en une topologie avec une connectivité RTC (réseau téléphonique commuté) locale. </span><span class="sxs-lookup"><span data-stu-id="b3a31-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="b3a31-139">**Figure 3 : Nuage PBX avec Skype pour Business Server**</span><span class="sxs-lookup"><span data-stu-id="b3a31-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![PBX cloud avec Skype Entreprise Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="b3a31-141">La figure 3 illustre le PBX nuage avec Skype pour la configuration de serveur d’entreprise, consistant en un local PBX existant ou passerelle de télécommunications, un Skype pour Business Server et le RTPC connecté au PBX de nuage de Microsoft dans Office 365, notamment Skype pour les entreprises En ligne.</span><span class="sxs-lookup"><span data-stu-id="b3a31-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="b3a31-142">Les utilisateurs au sein de l’organisation qui sont hébergés dans le cloud peuvent recevoir des services PBX (Private Branch Exchange) du cloud Microsoft qui incluent la signalisation et la messagerie vocale, mais la connectivité RTC (tonalité) est fournie via la fonctionnalité Voix Entreprise de votre déploiement Skype Entreprise Server local.</span><span class="sxs-lookup"><span data-stu-id="b3a31-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="b3a31-p104">Il s’agit d’un bon exemple de configuration hybride qui vous permet de migrer progressivement vers un service informatique. Vous pouvez conserver les fonctionnalités vocales de vos utilisateurs lorsque vous commencez à les déplacer vers Skype Entreprise Online. Vous pouvez déplacer vos utilisateurs comme vous le souhaitez, sachant que leurs fonctionnalités vocales continueront, indépendamment de l’endroit où elles sont hébergées. </span><span class="sxs-lookup"><span data-stu-id="b3a31-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="b3a31-146">Pour plus d’informations, reportez-vous à la section [planification de la connectivité d’hybride entre Skype pour Business Server et Skype pour Business Online ou Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span><span class="sxs-lookup"><span data-stu-id="b3a31-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="b3a31-147">Si vous n’avez pas encore mis en place un déploiement Lync Server ou Skype Entreprise Server, vous pouvez utiliser l’édition Cloud Connector de Skype Entreprise. Il s’agit d’un ensemble complet d’ordinateurs virtuels qui implémentent une connectivité RTC locale avec la fonctionnalité PBX cloud.</span><span class="sxs-lookup"><span data-stu-id="b3a31-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="b3a31-148">Pour plus d’informations, reportez-vous à la section [planifier Skype pour connecteur de Cloud Business Edition](https://technet.microsoft.com/library/mt605227.aspx).</span><span class="sxs-lookup"><span data-stu-id="b3a31-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="b3a31-149">Environnement hybride SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3a31-149">SharePoint Hybrid</span></span>

<span data-ttu-id="b3a31-150">SharePoint hybride combine SharePoint Online dans Office 365 à votre batterie SharePoint locale. Vous pouvez ainsi profiter des avantages des deux environnements au travers d’une expérience connectée.</span><span class="sxs-lookup"><span data-stu-id="b3a31-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="b3a31-151">**Figure 4 : Configuration hybride de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="b3a31-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Configuration hybride SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="b3a31-153">La figure 4 illustre la configuration hybride de SharePoint, consistant en une batterie de serveurs SharePoint locaux communiquent avec SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="b3a31-154">Scénarios SharePoint hybrides</span><span class="sxs-lookup"><span data-stu-id="b3a31-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="b3a31-155">OneDrive hybride pour entreprise</span><span class="sxs-lookup"><span data-stu-id="b3a31-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="b3a31-156">Sites d’équipe hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="b3a31-157">B2B d’Extranet hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="b3a31-158">Recherche de hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="b3a31-159">Profils de hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="b3a31-160">Sélecteur de hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="b3a31-161">La mise en œuvre de scénarios hybrides est un jeu d’enfant à l’aide des Assistants, car ils permettent d’automatiser la configuration hybride. Ces derniers sont disponibles dans le Centre d’administration SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="b3a31-162">Lanceur d’applications hybrides extensible</span><span class="sxs-lookup"><span data-stu-id="b3a31-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="b3a31-163">Cette fonctionnalité permet aux utilisateurs d’afficher et d’utiliser les applications Office 365 Video et Delve ainsi que des expériences dans les pages de leur batterie SharePoint locale.</span><span class="sxs-lookup"><span data-stu-id="b3a31-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="b3a31-164">Tous ces scénarios SharePoint hybrides, à l’exception du lanceur d’applications hybride extensible, sont disponibles pour les utilisateurs de SharePoint 2016 et SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="b3a31-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="b3a31-165">Pour plus d’informations, consultez [Hybride de SharePoint](http://hybrid.office.com/sharepoint/).</span><span class="sxs-lookup"><span data-stu-id="b3a31-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="b3a31-166">Exchange Server 2016 hybride</span><span class="sxs-lookup"><span data-stu-id="b3a31-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="b3a31-167">Avec Exchange Server 2016 hybride, vous pouvez tirer parti du potentiel d’Exchange Online dans Office 365 pour les utilisateurs en ligne tandis que les utilisateurs locaux continueront à utiliser l’infrastructure Exchange Server existante. </span><span class="sxs-lookup"><span data-stu-id="b3a31-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="b3a31-168">**Figure 5 : Configuration Exchange 2016 hybride**</span><span class="sxs-lookup"><span data-stu-id="b3a31-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Configuration hybride Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="b3a31-170">La figure 5 illustre la configuration Exchange 2016 hybride, qui se compose de serveurs de boîtes aux lettres Exchange local communique avec Exchange Online Protection et boîtes aux lettres dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="b3a31-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="b3a31-171">Certains utilisateurs ont recours à un serveur de messagerie local tandis que d’autres utilisent Exchange Online, mais ils partagent tous le même espace d’adressage de messagerie. </span><span class="sxs-lookup"><span data-stu-id="b3a31-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="b3a31-172">Cette configuration hybride :</span><span class="sxs-lookup"><span data-stu-id="b3a31-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="b3a31-173">Tire parti de votre infrastructure Exchange Server pendant la migration vers Exchange Online dans le temps, sur vos prévisions.</span><span class="sxs-lookup"><span data-stu-id="b3a31-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="b3a31-174">vous permet de prendre en charge les sites distants sans investir dans une infrastructure de succursale ;</span><span class="sxs-lookup"><span data-stu-id="b3a31-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="b3a31-175">vous permet d’acheminer le courrier électronique Internet entrant via Exchange Online Protection dans Office 365 ;</span><span class="sxs-lookup"><span data-stu-id="b3a31-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="b3a31-176">répond aux besoins des sociétés multinationales possédant des filiales qui exigent que les données soient hébergées sur site.</span><span class="sxs-lookup"><span data-stu-id="b3a31-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="b3a31-177">Vous pouvez également intégrer cette configuration hybride à d’autres applications Microsoft Office 365, notamment Skype Entreprise Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b3a31-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="b3a31-178">Pour plus d’informations, consultez [Déploiement d’Exchange Server hybride](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) et [Exchange hybride](http://hybrid.office.com/exchange/).</span><span class="sxs-lookup"><span data-stu-id="b3a31-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b3a31-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3a31-179">See Also</span></span>

[<span data-ttu-id="b3a31-180">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="b3a31-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="b3a31-181">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b3a31-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b3a31-182">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="b3a31-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



