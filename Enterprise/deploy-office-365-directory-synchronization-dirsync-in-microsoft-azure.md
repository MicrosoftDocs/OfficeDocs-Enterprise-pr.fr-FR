---
title: Déploiement de la synchronisation d’annuaires Office 365 dans Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Résumé : Déployez Azure AD Connect sur une machine virtuelle dans Azure pour synchroniser les comptes entre votre répertoire local et le client Azure AD de votre abonnement Office 365.'
ms.openlocfilehash: 01dede756142c08722e3cf21d91a0028eb815051
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915639"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="5200a-103">Déploiement de la synchronisation d’annuaires Office 365 dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="5200a-104">**Résumé :** Déployez Azure AD Connect sur une machine virtuelle dans Azure pour synchroniser les comptes entre votre répertoire local et le client Azure AD de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="5200a-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="5200a-p101">Azure Active Directory (AD) Connect (auparavant appelé outil de synchronisation d'annuaires ou outil DirSync.exe) est une application serveur à installer sur un serveur appartenant à un domaine pour synchroniser vos utilisateurs Windows Server Active Directory locaux sur le client Azure Active Directory de votre abonnement Office 365. Vous pouvez installer Azure AD Connect sur un serveur local, mais également sur une machine virtuelle dans Azure, pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="5200a-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="5200a-107">Vous pouvez mettre en service et configurer les serveurs cloud plus rapidement, les rendant ainsi disponibles plus tôt pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5200a-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="5200a-108">Azure offre une meilleure disponibilité de site avec moins d'efforts.</span><span class="sxs-lookup"><span data-stu-id="5200a-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="5200a-109">Vous pouvez réduire le nombre de serveurs locaux de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="5200a-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="5200a-p102">Cette solution exige une connectivité entre votre réseau local et votre réseau virtuel Azure. Pour plus d'informations, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5200a-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="5200a-p103">Cet article décrit la synchronisation d'un domaine unique dans une forêt unique. Azure AD Connect synchronise tous les domaines Windows Server AD dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, voir l'article sur le [scénario de synchronisation d'annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="5200a-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5200a-p104">Office 365 utilise Azure Active Directory (Azure AD) pour son service d'annuaire. Votre abonnement à Office 365 comprend un client Azure AD. Ce client peut également être utilisé pour la gestion des identités de votre organisation avec d'autres charges de travail de cloud, y compris d'autres applications SaaS et des applications dans Azure.</span><span class="sxs-lookup"><span data-stu-id="5200a-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="5200a-118">Vue d’ensemble du déploiement de la synchronisation d’annuaires Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="5200a-119">Le diagramme suivant montre Azure AD Connect en cours d'exécution sur une machine virtuelle dans Azure (le serveur de synchronisation d'annuaires) qui synchronise une forêt Windows Server AD sur site d'un abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="5200a-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Outil Azure AD Connect sur une machine virtuelle dans Azure synchronisant des comptes Azure locaux sur le client Azure AD d’un abonnement Office 365 avec le flux de trafic](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="5200a-p105">Dans le diagramme, il y a deux réseaux reliés par une connexion de site à site VPN ou ExpressRoute. Il existe un réseau local contenant les contrôleurs de domaine Windows Server AD et un réseau virtuel Azure avec un serveur de synchronisation d'annuaires, qui est une machine virtuelle exécutant [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Il existe deux flux de trafic principal à partir du serveur de synchronisation d'annuaires d'origine :</span><span class="sxs-lookup"><span data-stu-id="5200a-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="5200a-124">Azure AD Connect interroge un contrôleur de domaine sur le réseau local concernant les modifications apportées aux comptes et aux mots de passe.</span><span class="sxs-lookup"><span data-stu-id="5200a-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="5200a-p106">Azure AD Connect envoie les modifications apportées aux comptes et aux mots de passe à l'instance Azure AD de votre abonnement Office 365. Le serveur de synchronisation d’annuaires étant situé dans une partie étendue de votre réseau local, ces modifications sont envoyées par le biais du serveur proxy du réseau local.</span><span class="sxs-lookup"><span data-stu-id="5200a-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5200a-p107">Cette solution décrit la synchronisation d'un domaine Active Directory unique dans une forêt Active Directory unique. Azure AD Connect synchronise tous les domaines Active Directory dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, reportez-vous à l'article sur le [scénario de synchronisation d'annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="5200a-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="5200a-p108">Dans les deux cas, le trafic provenant d'Azure AD Connect en cours d'exécution sur la machine virtuelle Azure est transféré vers une passerelle sur le réseau virtuel dans Azure, qui transfert ensuite le trafic via la connexion VPN ou ExpressRoute de site à site au périphérique de passerelle VPN sur le réseau local. L'infrastructure de routage du réseau local transfert par la suite le trafic à sa destination, par exemple un contrôleur de domaine ou un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="5200a-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="5200a-132">Le déploiement de cette solution comporte deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="5200a-132">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="5200a-p109">La création d'un réseau virtuel Azure et l'établissement d'une connexion VPN de site à site vers votre réseau local. Pour plus d'informations, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5200a-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="5200a-p110">L'installation d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) sur une machine virtuelle appartenant à un domaine dans Azure, puis la synchronisation de Windows Server AD local avec Office 365. Cela implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5200a-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="5200a-137">Création d'un Ordinateur virtuel Azure pour exécuter Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="5200a-137">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="5200a-138">Installation et configuration d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="5200a-138">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="5200a-p111">La configuration d'Azure AD Connect exige les informations d'identification (nom d'utilisateur et mot de passe) d'un compte d'administrateur Azure AD et d'un compte d'administrateur d'entreprise Windows Server AD. Azure AD Connect est exécuté immédiatement et régulièrement pour synchroniser la forêt Windows Server AD locale avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="5200a-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="5200a-141">Avant de déployer cette solution en production, suivez les instructions de l’article [Synchronisation d’annuaires pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md) pour définir cette configuration comme une preuve de concept, de démonstrations ou d'expérimentation.</span><span class="sxs-lookup"><span data-stu-id="5200a-141">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="5200a-142">Une fois la configuration d’Azure AD Connect terminée, les informations d’identification de compte d’administrateur d’entreprise Windows Server AD ne sont pas enregistrées.</span><span class="sxs-lookup"><span data-stu-id="5200a-142">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5200a-p112">Cette solution décrit la synchronisation d'une seule forêt Active Directory de Windows Server à Office 365. La topologie décrite dans cet article ne représente qu'un seul moyen de mettre en œuvre cette solution. La topologie de votre organisation peut-être différer en fonction de vos besoins réseau unique et les considérations sur la sécurité.</span><span class="sxs-lookup"><span data-stu-id="5200a-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="5200a-146">Planification de l’hébergement d’un serveur de synchronisation d’annuaires pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-146">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="5200a-147"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="5200a-147"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="5200a-148">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5200a-148">Prerequisites</span></span>

<span data-ttu-id="5200a-149">Avant de commencer, passez en revue les conditions préalables suivantes pour cette solution :</span><span class="sxs-lookup"><span data-stu-id="5200a-149">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="5200a-150">Examinez le contenu de planification associé dans[Planifier votre réseau virtuel Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network). </span><span class="sxs-lookup"><span data-stu-id="5200a-150">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="5200a-151">Veillez à respecter toutes les[conditions préalables](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) relatives à la configuration du réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="5200a-151">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="5200a-p113">Vous devez disposer d'un abonnement Office 365 qui inclut la fonctionnalité d'intégration Active Directory. Pour plus d'informations sur les abonnements Office 365, accédez à la [page d'abonnement Office 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span><span class="sxs-lookup"><span data-stu-id="5200a-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="5200a-154">Vous devez configurer un Ordinateur virtuel Azure qui exécute Azure AD Connect pour synchroniser votre forêt Windows Server AD locale avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="5200a-154">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="5200a-155">Vous devez disposer des informations d'identification (noms et mots de passe) d'un compte d'administrateur d'entreprise Windows Server AD et d'un compte d'administrateur Active Directory Azure.</span><span class="sxs-lookup"><span data-stu-id="5200a-155">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="5200a-156">Hypothèses en matière de conception de l’architecture de la solution</span><span class="sxs-lookup"><span data-stu-id="5200a-156">Solution architecture design assumptions</span></span>

<span data-ttu-id="5200a-157">La liste suivante décrit les choix de conception effectués pour cette solution.</span><span class="sxs-lookup"><span data-stu-id="5200a-157">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="5200a-p114">Cette solution utilise un seul réseau virtuel Azure avec une connexion VPN de site à site. Le réseau virtuel Azure héberge un sous-réseau unique qui contient un serveur, le serveur de synchronisation d’annuaires qui exécute Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="5200a-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="5200a-160">Sur le réseau local, un contrôleur de domaine et des serveurs DNS existent.</span><span class="sxs-lookup"><span data-stu-id="5200a-160">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="5200a-p115">Azure AD Connect exécute la synchronisation de hachage de mot de passe à la place de l’authentification unique. Il est inutile de déployer une infrastructure AD FS (Active Directory Federation Services). Pour plus d’informations sur les options de synchronisation de hachage de mot de passe et d’authentification unique, reportez-vous à l’article [Choisir la méthode d’authentification adaptée à votre solution d’identité hybride Azure Active Directory](http://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="5200a-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="5200a-p116">Il existe des choix de conception supplémentaires que vous pourriez envisager lorsque vous déployez cette solution dans votre environnement. Ceux-ci incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="5200a-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="5200a-166">Si un réseau virtuel Azure existant comporte des serveurs DNS, déterminez si vous voulez que votre serveur de synchronisation d’annuaires les utilise pour la résolution de noms à la place des serveurs DNS sur le réseau local.</span><span class="sxs-lookup"><span data-stu-id="5200a-166">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="5200a-p117">Si un réseau virtuel Azure existant comporte des contrôleurs de domaine, déterminez si la configuration des services et sites Active Directory peut être une meilleure option pour vous. Le serveur de synchronisation d’annuaires peut interroger les contrôleurs de domaine dans le réseau virtuel Azure pour rechercher des modifications des comptes et des mots de passe à la place des contrôleurs de domaine sur le réseau local.</span><span class="sxs-lookup"><span data-stu-id="5200a-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="5200a-169">Feuille de route de déploiement</span><span class="sxs-lookup"><span data-stu-id="5200a-169">Deployment roadmap</span></span>

<span data-ttu-id="5200a-170">Le déploiement d'Azure AD Connect sur une machine virtuelle dans Azure consiste en trois phases :</span><span class="sxs-lookup"><span data-stu-id="5200a-170">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="5200a-171">Phase 1 : créer et configurer le réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-171">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="5200a-172">Phase 2 : créer et configurer les machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-172">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="5200a-173">Phase 3 : installer et configurer Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5200a-173">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="5200a-174">Après le déploiement, vous devez également affecter des emplacements et des licences pour les nouveaux comptes d’utilisateur dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="5200a-174">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="5200a-175">Le [serveur de synchronisation d’annuaires du kit de déploiement Azure](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contient tous les blocs PowerShell Azure pour créer cette solution, les diagrammes au format Microsoft PowerPoint et Visio et un classeur de configuration Microsoft Excel qui génère des blocs de commandes Azure PowerShell correspondant à vos paramètres.</span><span class="sxs-lookup"><span data-stu-id="5200a-175">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="5200a-176">Phase 1 : créer et configurer le réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-176">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="5200a-177">Pour créer et configurer le réseau virtuel Azure, effectuez la [phase 1 en préparant votre réseau local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) et la [phase 2 en créant le réseau virtuel entre différents locaux dans Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) décrites dans la feuille de route de déploiement de l’article [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5200a-177">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="5200a-178">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="5200a-178">This is your resulting configuration.</span></span>
  
![Phase 1 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="5200a-180">Cette illustration montre un réseau local connecté à un réseau virtuel Azure via une connexion VPN ou ExpressRoute de site à site.</span><span class="sxs-lookup"><span data-stu-id="5200a-180">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="5200a-181">Phase 2 : créer et configurer les machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-181">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="5200a-p118">Créez la machine virtuelle dans Azure en suivant les instructions décrites dans [Créer votre première machine virtuelle Windows dans le portail Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilisez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="5200a-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="5200a-p119">Dans le volet **De base**, sélectionnez le même abonnement, le même emplacement et le même groupe de ressources que votre réseau virtuel. Enregistrez le nom d'utilisateur et le mot de passe dans un emplacement sécurisé. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="5200a-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="5200a-187">Dans le volet **Choisir une taille**, choisissez la taille **A2 Standard**.</span><span class="sxs-lookup"><span data-stu-id="5200a-187">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="5200a-p120">Dans le volet **Paramètres**, dans la section **Stockage**, sélectionnez le type de stockage **Standard**. Dans la section **Réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l'hébergement du serveur de synchronisation d’annuaires (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="5200a-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="5200a-191">Vérifiez que votre serveur de synchronisation d’annuaires utilise correctement DNS en vérifiant votre DNS interne pour vous assurer qu’un enregistrement d’adresse (A) a été ajouté pour la machine virtuelle avec son adresse IP.</span><span class="sxs-lookup"><span data-stu-id="5200a-191">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="5200a-p121">Suivez les instructions décrites dans [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) pour vous connecter au serveur de synchronisation d’annuaires avec une connexion Bureau à distance. Une fois connecté, associez la machine virtuelle au domaine Windows Server AD local.</span><span class="sxs-lookup"><span data-stu-id="5200a-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="5200a-p122">Pour qu’Azure AD Connect puisse accéder aux ressources Internet, vous devez configurer le serveur de synchronisation d’annuaires de sorte qu’il utilise le serveur proxy du réseau local. Nous vous recommandons de contacter votre administrateur réseau pour toute étape de configuration supplémentaire à effectuer.</span><span class="sxs-lookup"><span data-stu-id="5200a-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="5200a-196">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="5200a-196">This is your resulting configuration.</span></span>
  
![Phase 2 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="5200a-198">Cette illustration montre la machine virtuelle du serveur de synchronisation d’annuaires dans le réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="5200a-198">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="5200a-199">Phase 3 : installer et configurer Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5200a-199">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="5200a-200">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5200a-200">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="5200a-p123">Connectez-vous au serveur de synchronisation d’annuaires à l'aide d'une connexion Bureau à distance avec un compte de domaine Windows Server AD qui possède des privilèges d'administrateur local. Voir [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="5200a-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="5200a-203">À partir du serveur de synchronisation d’annuaires, ouvrez l'article [Configurer la synchronisation d'annuaires pour Office 365](set-up-directory-synchronization.md) et suivez les instructions pour la synchronisation d'annuaires avec la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5200a-203">From the directory sync server, open the [Set up directory synchronization in Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="5200a-p124">Le programme d’installation crée le compte **AAD_xxxxxxxxxxxx** dans l’unité d’organisation (UO) Utilisateurs Locaux. Ne déplacez pas et ne supprimez pas ce compte, sinon la synchronisation échouera.</span><span class="sxs-lookup"><span data-stu-id="5200a-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="5200a-206">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="5200a-206">This is your resulting configuration.</span></span>
  
![Phase 3 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="5200a-208">Cette illustration montre le serveur de synchronisation d’annuaires avec Azure AD Connect dans le réseau virtuel Azure entre différents locaux.</span><span class="sxs-lookup"><span data-stu-id="5200a-208">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="5200a-209">Affectation d’emplacements et de licences à des utilisateurs dans Office 365</span><span class="sxs-lookup"><span data-stu-id="5200a-209">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="5200a-p125">Azure AD Connect ajoute des comptes à votre abonnement Office 365 à partir de Windows Server AD en local, mais pour que les utilisateurs se connectent à Office 365 et utilisent ses services, les comptes doivent être configurés avec un emplacement et des licences. Utilisez ces étapes pour ajouter l’emplacement et activer les licences pour les comptes d’utilisateur appropriés :</span><span class="sxs-lookup"><span data-stu-id="5200a-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="5200a-212">Connectez-vous à la [page du portail Office 365](https://portal.office.com), puis cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="5200a-212">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="5200a-213">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="5200a-213">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="5200a-214">Dans la liste des comptes d’utilisateur, sélectionnez la case à cocher en regard de l’utilisateur que vous souhaitez activer.</span><span class="sxs-lookup"><span data-stu-id="5200a-214">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="5200a-215">Sur la page de l'utilisateur, cliquez sur **Modifier** pour **Licences de produits**.</span><span class="sxs-lookup"><span data-stu-id="5200a-215">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="5200a-216">Sur la page **Licences de produit**, sélectionnez un emplacement pour l'utilisateur pour **Emplacement**, puis activez les licences appropriées pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5200a-216">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="5200a-217">Lorsque vous avez terminé, cliquez sur **Enregistrer**, puis sur **Fermer** deux fois.</span><span class="sxs-lookup"><span data-stu-id="5200a-217">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="5200a-218">Revenez à l’étape 3 pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5200a-218">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5200a-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5200a-219">See Also</span></span>

[<span data-ttu-id="5200a-220">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="5200a-220">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="5200a-221">Connecter un réseau local à Microsoft Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="5200a-221">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="5200a-222">Télécharger Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5200a-222">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="5200a-223">Configurer la synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="5200a-223">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
[<span data-ttu-id="5200a-224">Serveur de synchronisation d’annuaires dans le kit de déploiement Azure</span><span class="sxs-lookup"><span data-stu-id="5200a-224">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



