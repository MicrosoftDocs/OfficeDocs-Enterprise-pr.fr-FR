---
title: Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Résumé : Découvrez les scénarios et l’architecture hybride pour Microsoft basée sur SaaS (Office 365) les offres de cloud.'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123411"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="c122f-103">Scénarios de cloud hybride pour Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c122f-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="c122f-104">**Résumé :** Comprendre les scénarios et l’architecture hybride pour Microsoft basée sur SaaS (Office 365) les offres de cloud.</span><span class="sxs-lookup"><span data-stu-id="c122f-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="c122f-105">Combinez des déploiements locaux d’Exchange, de SharePoint ou de Skype Entreprise à leur équivalent dans Office 365 dans le cadre d’une migration cloud ou d’une stratégie d’intégration à long terme.</span><span class="sxs-lookup"><span data-stu-id="c122f-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="c122f-106">Architecture de scénario hybride pour les services SaaS Microsoft</span><span class="sxs-lookup"><span data-stu-id="c122f-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="c122f-107">La figure 1 présente l’architecture des scénarios hybrides SaaS de Microsoft pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="c122f-108">**Figure 1 : Scénarios hybrides Microsoft SaaS pour Office 365**</span><span class="sxs-lookup"><span data-stu-id="c122f-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Scénarios hybrides Microsoft SaaS pour Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="c122f-110">Pour chaque couche de l’architecture :</span><span class="sxs-lookup"><span data-stu-id="c122f-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="c122f-111">Applications et scénarios</span><span class="sxs-lookup"><span data-stu-id="c122f-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="c122f-112">Il existe plusieurs scénarios hybrides SaaS au niveau des produits serveur Office et de leur équivalent dans Office 365 :</span><span class="sxs-lookup"><span data-stu-id="c122f-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="c122f-113">Exchange Server combiné à Exchange Online (Exchange Server hybride)</span><span class="sxs-lookup"><span data-stu-id="c122f-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="c122f-114">Skype Entreprise Server combiné à Skype Entreprise Online et aux nouveaux scénarios PBX cloud et édition Cloud Connector</span><span class="sxs-lookup"><span data-stu-id="c122f-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="c122f-115">SharePoint Server 2013, SharePoint Server 2016 ou SharePoint Server 2019 combinées avec SharePoint Online (plusieurs scénarios)</span><span class="sxs-lookup"><span data-stu-id="c122f-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="c122f-116">Vous pouvez également mettre en place Exchange Online avec Skype Entreprise Server en local (scénario hybride de produit croisé).</span><span class="sxs-lookup"><span data-stu-id="c122f-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="c122f-117">Identity</span><span class="sxs-lookup"><span data-stu-id="c122f-117">Identity</span></span>
    
    <span data-ttu-id="c122f-p101">Peut inclure la synchronisation d’annuaires avec votre Windows Server AD local. Enfin, vous pouvez configurer Azure AD pour la fédération avec un fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="c122f-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="c122f-120">Réseau</span><span class="sxs-lookup"><span data-stu-id="c122f-120">Network</span></span>
    
    <span data-ttu-id="c122f-121">Se compose de votre canal Internet existant ou d’une connexion ExpressRoute avec homologation Microsoft pour Office 365 ou Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="c122f-122">Sur site</span><span class="sxs-lookup"><span data-stu-id="c122f-122">On-premises</span></span>
    
    <span data-ttu-id="c122f-p102">Peut être composé de serveurs existants pour Exchange, SharePoint et Skype Entreprise, qui doivent être mis à jour vers la dernière version disponible. Vous pouvez les combiner à leurs équivalents Office 365 pour des scénarios hybrides.</span><span class="sxs-lookup"><span data-stu-id="c122f-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="c122f-125">Configurer votre propre environnement de développement/test Office 365, voir les [Guides de laboratoire de Test d’Office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="c122f-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="c122f-126">Skype pour Business hybride</span><span class="sxs-lookup"><span data-stu-id="c122f-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="c122f-p103">Skype pour Business hybride vous permet de combiner un déploiement local existant avec Skype pour Business Online. Certains utilisateurs sont hébergés sur un système local et certains utilisateurs sont hébergés en ligne, mais les utilisateurs partagent le même domaine de protocole SIP (Session Initiation), par exemple, contoso.com. Vous pouvez utiliser cette configuration hybride pour migrer à partir de locaux vers Office 365 au fil du temps, votre calendrier. Skype pour les entreprises peut également être intégré avec [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="c122f-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="c122f-131">**La figure 2 : Skype pour la configuration hybride d’entreprise**</span><span class="sxs-lookup"><span data-stu-id="c122f-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Le Skype pour la configuration hybride d’entreprise](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="c122f-133">La figure 2 illustre la Skype pour la configuration hybride d’entreprise, comprenant un Skype locale pour Business le pool frontal et edge server communique avec Skype pour Business Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="c122f-134">Pour plus d’informations, voir [planification de la connectivité hybride entre Skype pour Business Server et Skype pour Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="c122f-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="c122f-135">PBX cloud avec Skype Entreprise Server</span><span class="sxs-lookup"><span data-stu-id="c122f-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="c122f-136">Nuage PBX avec Skype pour Business Server vous permet de passer un Skype pour le déploiement local de Business Server à une topologie existante avec une connectivité sur site Public réseau de téléphonique commuté (RTC).</span><span class="sxs-lookup"><span data-stu-id="c122f-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="c122f-137">**Figure 3 : PBX cloud avec Skype Entreprise Server**</span><span class="sxs-lookup"><span data-stu-id="c122f-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![PBX cloud avec Skype Entreprise Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="c122f-139">La figure 3 montre le système PBX sur le nuage avec Skype pour la configuration de Business Server, constitué d’une locale PBX existant ou passerelle télécommunications, un Skype pour Business Server et le réseau RTC connecté au PBX Microsoft Cloud dans Office 365, qui comprend Skype pour les entreprises En ligne.</span><span class="sxs-lookup"><span data-stu-id="c122f-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="c122f-140">Les utilisateurs au sein de l’organisation qui sont hébergés dans le cloud peuvent recevoir des services PBX (Private Branch Exchange) du cloud Microsoft qui incluent la signalisation et la messagerie vocale, mais la connectivité RTC (tonalité) est fournie via la fonctionnalité Voix Entreprise de votre déploiement Skype Entreprise Server local.</span><span class="sxs-lookup"><span data-stu-id="c122f-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="c122f-p104">Il s’agit d’un bon exemple de configuration hybride qui vous permet de migrer graduellement à un service en nuage. Vous pouvez conserver les fonctionnalités vocales de vos utilisateurs lorsque vous commencez à déplacer vers Skype pour Business Online. Vous pouvez déplacer vos utilisateurs à votre rythme, sachant que leurs fonctionnalités vocales continuera no question où ils sont hébergés.</span><span class="sxs-lookup"><span data-stu-id="c122f-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="c122f-144">Pour plus d’informations, voir [planification de la connectivité hybride entre Skype pour Business Server et Skype pour Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="c122f-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="c122f-145">Si vous n’avez pas encore mis en place un déploiement Lync Server ou Skype Entreprise Server, vous pouvez utiliser l’édition Cloud Connector de Skype Entreprise. Il s’agit d’un ensemble complet d’ordinateurs virtuels qui implémentent une connectivité RTC locale avec la fonctionnalité PBX cloud.</span><span class="sxs-lookup"><span data-stu-id="c122f-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="c122f-146">Pour plus d’informations, voir [planifier Skype pour l’édition de connecteur Business Cloud](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="c122f-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="c122f-147">Environnement hybride SharePoint</span><span class="sxs-lookup"><span data-stu-id="c122f-147">SharePoint Hybrid</span></span>

<span data-ttu-id="c122f-148">SharePoint hybride combine SharePoint Online dans Office 365 à votre batterie SharePoint locale. Vous pouvez ainsi profiter des avantages des deux environnements au travers d’une expérience connectée.</span><span class="sxs-lookup"><span data-stu-id="c122f-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="c122f-149">**Figure 4 : Configuration hybride SharePoint**</span><span class="sxs-lookup"><span data-stu-id="c122f-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Configuration hybride SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="c122f-151">La figure 4 illustre la configuration hybride SharePoint, constitué d’une batterie de serveurs SharePoint locale communiquer avec SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="c122f-152">Scénarios SharePoint hybrides</span><span class="sxs-lookup"><span data-stu-id="c122f-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="c122f-153">OneDrive Entreprise hybride</span><span class="sxs-lookup"><span data-stu-id="c122f-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="c122f-154">Hybride Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="c122f-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="c122f-155">Recherche hybride</span><span class="sxs-lookup"><span data-stu-id="c122f-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="c122f-156">Profils hybrides</span><span class="sxs-lookup"><span data-stu-id="c122f-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="c122f-157">Sélecteur de hybride</span><span class="sxs-lookup"><span data-stu-id="c122f-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="c122f-158">La mise en œuvre de scénarios hybrides est un jeu d’enfant à l’aide des Assistants, car ils permettent d’automatiser la configuration hybride. Ces derniers sont disponibles dans le Centre d’administration SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="c122f-159">Lanceur d'applications hybride extensible</span><span class="sxs-lookup"><span data-stu-id="c122f-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="c122f-160">Cette fonctionnalité permet aux utilisateurs d’afficher et d’utiliser les applications Office 365 Video et Delve ainsi que des expériences dans les pages de leur batterie SharePoint locale.</span><span class="sxs-lookup"><span data-stu-id="c122f-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="c122f-161">Tous ces scénarios SharePoint hybrides, à l’exception du lanceur d’applications hybride extensible, sont disponibles pour les utilisateurs de SharePoint 2016 et SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="c122f-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="c122f-162">Exchange Server 2016 hybride</span><span class="sxs-lookup"><span data-stu-id="c122f-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="c122f-163">Avec Exchange Server 2016 hybride, vous pouvez tirer parti du potentiel d’Exchange Online dans Office 365 pour les utilisateurs en ligne tandis que les utilisateurs locaux continueront à utiliser l’infrastructure Exchange Server existante. </span><span class="sxs-lookup"><span data-stu-id="c122f-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="c122f-164">**Figure 5 : Configuration hybride Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="c122f-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Configuration hybride Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="c122f-166">La figure 5 illustre la configuration hybride d’Exchange 2016, constituée de serveurs de boîtes aux lettres Exchange locale communiquant avec Exchange Online Protection et de boîtes aux lettres dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="c122f-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="c122f-167">Certains utilisateurs ont recours à un serveur de messagerie local tandis que d’autres utilisent Exchange Online, mais ils partagent tous le même espace d’adressage de messagerie. </span><span class="sxs-lookup"><span data-stu-id="c122f-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="c122f-168">Cette configuration hybride :</span><span class="sxs-lookup"><span data-stu-id="c122f-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="c122f-169">tire parti de votre infrastructure Exchange Server existante pendant que vous effectuez une migration progressive vers Exchange Online en respectant votre planning ;


</span><span class="sxs-lookup"><span data-stu-id="c122f-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="c122f-170">vous permet de prendre en charge les sites distants sans investir dans une infrastructure de succursale ;</span><span class="sxs-lookup"><span data-stu-id="c122f-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="c122f-171">vous permet d’acheminer le courrier électronique Internet entrant via Exchange Online Protection dans Office 365 ;</span><span class="sxs-lookup"><span data-stu-id="c122f-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="c122f-172">répond aux besoins des sociétés multinationales possédant des filiales qui exigent que les données soient hébergées sur site.</span><span class="sxs-lookup"><span data-stu-id="c122f-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="c122f-173">Vous pouvez également intégrer cette configuration hybride à d’autres applications Microsoft Office 365, notamment Skype Entreprise Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c122f-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="c122f-174">Pour plus d’informations, voir [Déploiements hybrides Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="c122f-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c122f-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c122f-175">See Also</span></span>

[<span data-ttu-id="c122f-176">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="c122f-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="c122f-177">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c122f-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

