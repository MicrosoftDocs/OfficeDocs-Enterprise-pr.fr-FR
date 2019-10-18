---
title: Déploiement de la synchronisation d’annuaires Office 365 dans Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
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
ms.openlocfilehash: 8b521746946c3f1be077fe49bf12be6a72125738
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068028"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="9887c-103">Déploiement de la synchronisation d’annuaires Office 365 dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="9887c-104">**Résumé :** déployez Azure AD Connect sur une machine virtuelle dans Azure pour synchroniser les comptes entre votre répertoire local et le client Azure AD de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure infrastructure services to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="9887c-105">Azure Active Directory (AD) Connect (auparavant appelé outil de synchronisation d’annuaires ou outil DirSync.exe) est une application à installer sur un serveur appartenant à un domaine pour synchroniser vos utilisateurs Active Directory Domain Services (AD DS) locaux sur le client Azure AD de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-105">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="9887c-106">Office 365 utilise Azure Active Directory (Azure AD) pour son service d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="9887c-106">Office 365 uses Azure Active Directory (Azure AD) for its directory service.</span></span> <span data-ttu-id="9887c-107">Votre abonnement à Office 365 comprend un client Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9887c-107">Your Office 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="9887c-108">Ce client peut également être utilisé pour la gestion des identités de votre organisation avec d’autres charges de travail de cloud, y compris d’autres applications SaaS et des applications dans Azure.</span><span class="sxs-lookup"><span data-stu-id="9887c-108">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="9887c-109">Vous pouvez installer Azure AD Connect sur un serveur local, mais également sur une machine virtuelle dans Azure, pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="9887c-109">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="9887c-110">Vous pouvez mettre en service et configurer les serveurs cloud plus rapidement, les rendant ainsi disponibles plus tôt pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9887c-110">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="9887c-111">Azure offre une meilleure disponibilité de site avec moins d'efforts.</span><span class="sxs-lookup"><span data-stu-id="9887c-111">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="9887c-112">Vous pouvez réduire le nombre de serveurs locaux de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="9887c-112">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="9887c-113">Cette solution exige une connectivité entre votre réseau local et votre réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="9887c-113">This solution requires connectivity between your on-premises network and your Azure virtual network.</span></span> <span data-ttu-id="9887c-114">Pour plus d’informations, reportez-vous à [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="9887c-114">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="9887c-p103">Cet article décrit la synchronisation d’un domaine unique dans une forêt unique. Azure AD Connect synchronise tous les domaines AD DS dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, voir l’article sur le [scénario de synchronisation d’annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="9887c-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="9887c-118">Vue d’ensemble du déploiement de la synchronisation d’annuaires Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="9887c-119">Le diagramme suivant montre Azure AD Connect en cours d’exécution sur une machine virtuelle dans Azure (le serveur de synchronisation d’annuaires) qui synchronise une forêt AD DS locale avec un abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to an Office 365 subscription.</span></span>
  
![Outil Azure AD Connect sur une machine virtuelle dans Azure synchronisant des comptes Azure locaux sur le client Azure AD d’un abonnement Office 365 avec le flux de trafic](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="9887c-p104">Dans le diagramme, il y a deux réseaux reliés par une connexion de site à site VPN ou ExpressRoute. Il existe un réseau local contenant les contrôleurs de domaine AD DS et un réseau virtuel Azure avec un serveur de synchronisation d’annuaires, qui est une machine virtuelle exécutant [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Il existe deux flux de trafic principal à partir du serveur de synchronisation d’annuaires d’origine :</span><span class="sxs-lookup"><span data-stu-id="9887c-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="9887c-124">Azure AD Connect interroge un contrôleur de domaine sur le réseau local concernant les modifications apportées aux comptes et aux mots de passe.</span><span class="sxs-lookup"><span data-stu-id="9887c-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="9887c-p105">Azure AD Connect envoie les modifications apportées aux comptes et aux mots de passe à l'instance Azure AD de votre abonnement Office 365. Le serveur de synchronisation d’annuaires étant situé dans une partie étendue de votre réseau local, ces modifications sont envoyées par le biais du serveur proxy du réseau local.</span><span class="sxs-lookup"><span data-stu-id="9887c-p105">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9887c-p106">Cette solution décrit la synchronisation d'un domaine Active Directory unique dans une forêt Active Directory unique. Azure AD Connect synchronise tous les domaines Active Directory dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, reportez-vous à l'article sur le [scénario de synchronisation d'annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="9887c-p106">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="9887c-130">Le déploiement de cette solution comporte deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="9887c-130">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="9887c-p107">La création d'un réseau virtuel Azure et l'établissement d'une connexion VPN de site à site vers votre réseau local. Pour plus d'informations, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="9887c-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="9887c-p108">L’installation d’[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) sur une machine virtuelle appartenant à un domaine dans Azure, puis la synchronisation du service AD DS local avec Office 365. Cela implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9887c-p108">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Office 365. This involves:</span></span>
    
    <span data-ttu-id="9887c-135">Création d'un Ordinateur virtuel Azure pour exécuter Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="9887c-135">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="9887c-136">Installation et configuration d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="9887c-136">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="9887c-p109">La configuration d’Azure AD Connect exige les informations d’identification (nom d’utilisateur et mot de passe) d’un compte d’administrateur Azure AD et d’un compte d’administrateur d’entreprise AD DS. Azure AD Connect est exécuté immédiatement et régulièrement pour synchroniser la forêt AD DS locale avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-p109">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Office 365.</span></span>
    
<span data-ttu-id="9887c-139">Avant de déployer cette solution en production, suivez les instructions de l’article [Synchronisation d’annuaires pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md) pour définir cette configuration comme une preuve de concept, de démonstrations ou d'expérimentation.</span><span class="sxs-lookup"><span data-stu-id="9887c-139">Before you deploy this solution in production, you can use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="9887c-140">Une fois la configuration d’Azure AD Connect terminée, les informations d’identification de compte d’administrateur d’entreprise AD DS ne sont pas enregistrées.</span><span class="sxs-lookup"><span data-stu-id="9887c-140">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="9887c-p110">Cette solution décrit la synchronisation d’une forêt AD DS unique sur Office 365. La topologie décrite dans cet article représente la seule façon d’implémenter cette solution. La topologie de votre organisation peut varier en fonction de vos exigences de réseau uniques et des considérations en matière de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9887c-p110">This solution describes synchronizing a single AD DS forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="9887c-144">Planification de l’hébergement d’un serveur de synchronisation d’annuaires pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-144">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="9887c-145"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="9887c-145"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="9887c-146">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9887c-146">Prerequisites</span></span>

<span data-ttu-id="9887c-147">Avant de commencer, passez en revue les conditions préalables suivantes pour cette solution :</span><span class="sxs-lookup"><span data-stu-id="9887c-147">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="9887c-148">Examinez le contenu de planification associé dans[Planifier votre réseau virtuel Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network). </span><span class="sxs-lookup"><span data-stu-id="9887c-148">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="9887c-149">Veillez à respecter toutes les[conditions préalables](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) relatives à la configuration du réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="9887c-149">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="9887c-p111">Vous devez disposer d'un abonnement Office 365 qui inclut la fonctionnalité d'intégration Active Directory. Pour plus d'informations sur les abonnements Office 365, accédez à la [page d'abonnement Office 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span><span class="sxs-lookup"><span data-stu-id="9887c-p111">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="9887c-152">Vous devez configurer un ordinateur virtuel Azure qui exécute Azure AD Connect pour synchroniser votre forêt AD DS locale avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-152">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Office 365.</span></span>
    
    <span data-ttu-id="9887c-153">Vous devez disposer des informations d’identification (noms et mots de passe) d’un compte d’administrateur d’entreprise AD DS et d’un compte d’administrateur Active Directory Azure.</span><span class="sxs-lookup"><span data-stu-id="9887c-153">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="9887c-154">Hypothèses en matière de conception de l’architecture de la solution</span><span class="sxs-lookup"><span data-stu-id="9887c-154">Solution architecture design assumptions</span></span>

<span data-ttu-id="9887c-155">La liste suivante décrit les choix de conception effectués pour cette solution.</span><span class="sxs-lookup"><span data-stu-id="9887c-155">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="9887c-156">Cette solution utilise un réseau virtuel Azure unique avec une connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="9887c-156">This solution uses a single Azure virtual network with a site-to-site VPN connection.</span></span> <span data-ttu-id="9887c-157">Le réseau virtuel Azure héberge un sous-réseau unique qui possède un serveur, le serveur de synchronisation d’annuaires qui exécute Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="9887c-157">The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="9887c-158">Sur le réseau local, un contrôleur de domaine et des serveurs DNS existent.</span><span class="sxs-lookup"><span data-stu-id="9887c-158">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="9887c-p113">Azure AD Connect exécute la synchronisation de hachage de mot de passe à la place de l’authentification unique. Il est inutile de déployer une infrastructure AD FS (Active Directory Federation Services). Pour plus d’informations sur les options de synchronisation de hachage de mot de passe et d’authentification unique, reportez-vous à l’article [Choisir la méthode d’authentification adaptée à votre solution d’identité hybride Azure Active Directory](http://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="9887c-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="9887c-p114">Il existe des choix de conception supplémentaires que vous pourriez envisager lorsque vous déployez cette solution dans votre environnement. Ceux-ci incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="9887c-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="9887c-164">Si un réseau virtuel Azure existant comporte des serveurs DNS, déterminez si vous voulez que votre serveur de synchronisation d’annuaires les utilise pour la résolution de noms à la place des serveurs DNS sur le réseau local.</span><span class="sxs-lookup"><span data-stu-id="9887c-164">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="9887c-p115">Si un réseau virtuel Azure existant comporte des contrôleurs de domaine, déterminez si la configuration des services et sites Active Directory peut être une meilleure option pour vous. Le serveur de synchronisation d’annuaires peut interroger les contrôleurs de domaine dans le réseau virtuel Azure pour rechercher des modifications des comptes et des mots de passe à la place des contrôleurs de domaine sur le réseau local.</span><span class="sxs-lookup"><span data-stu-id="9887c-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="9887c-167">Feuille de route de déploiement</span><span class="sxs-lookup"><span data-stu-id="9887c-167">Deployment roadmap</span></span>

<span data-ttu-id="9887c-168">Le déploiement d'Azure AD Connect sur une machine virtuelle dans Azure consiste en trois phases :</span><span class="sxs-lookup"><span data-stu-id="9887c-168">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="9887c-169">Phase 1 : créer et configurer le réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-169">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="9887c-170">Phase 2 : créer et configurer les machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-170">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="9887c-171">Phase 3 : installer et configurer Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="9887c-171">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="9887c-172">Après le déploiement, vous devez également affecter des emplacements et des licences pour les nouveaux comptes d’utilisateur dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="9887c-172">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>

<!--  
> [!TIP]
> The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) has all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.
-->
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="9887c-173">Phase 1 : créer et configurer le réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-173">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="9887c-174">Pour créer et configurer le réseau virtuel Azure, effectuez la [phase 1 en préparant votre réseau local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) et la [phase 2 en créant le réseau virtuel entre différents locaux dans Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) décrites dans la feuille de route de déploiement de l’article [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="9887c-174">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="9887c-175">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="9887c-175">This is your resulting configuration.</span></span>
  
![Phase 1 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="9887c-177">Cette illustration montre un réseau local connecté à un réseau virtuel Azure via une connexion VPN ou ExpressRoute de site à site.</span><span class="sxs-lookup"><span data-stu-id="9887c-177">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="9887c-178">Phase 2 : créer et configurer les machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="9887c-178">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="9887c-p116">Créez la machine virtuelle dans Azure en suivant les instructions décrites dans [Créer votre première machine virtuelle Windows dans le portail Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilisez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="9887c-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="9887c-p117">Dans le volet **De base**, sélectionnez le même abonnement, le même emplacement et le même groupe de ressources que votre réseau virtuel. Enregistrez le nom d'utilisateur et le mot de passe dans un emplacement sécurisé. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9887c-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="9887c-184">Dans le volet **Choisir une taille**, choisissez la taille **A2 Standard**.</span><span class="sxs-lookup"><span data-stu-id="9887c-184">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="9887c-p118">Dans le volet **Paramètres**, dans la section **Stockage**, sélectionnez le type de stockage **Standard**. Dans la section **Réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l'hébergement du serveur de synchronisation d’annuaires (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="9887c-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="9887c-188">Vérifiez que votre serveur de synchronisation d’annuaires utilise correctement DNS en vérifiant votre DNS interne pour vous assurer qu’un enregistrement d’adresse (A) a été ajouté pour la machine virtuelle avec son adresse IP.</span><span class="sxs-lookup"><span data-stu-id="9887c-188">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="9887c-p119">Suivez les instructions décrites dans [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) pour vous connecter au serveur de synchronisation d’annuaires avec une connexion Bureau à distance. Une fois connecté, associez la machine virtuelle au domaine AD DS local.</span><span class="sxs-lookup"><span data-stu-id="9887c-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="9887c-p120">Pour qu’Azure AD Connect puisse accéder aux ressources Internet, vous devez configurer le serveur de synchronisation d’annuaires de sorte qu’il utilise le serveur proxy du réseau local. Nous vous recommandons de contacter votre administrateur réseau pour toute étape de configuration supplémentaire à effectuer.</span><span class="sxs-lookup"><span data-stu-id="9887c-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="9887c-193">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="9887c-193">This is your resulting configuration.</span></span>
  
![Phase 2 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="9887c-195">Cette illustration montre la machine virtuelle du serveur de synchronisation d’annuaires dans le réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="9887c-195">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="9887c-196">Phase 3 : installer et configurer Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="9887c-196">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="9887c-197">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9887c-197">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="9887c-p121">Connectez-vous au serveur de synchronisation d’annuaires à l’aide d’une connexion Bureau à distance avec un compte de domaine AD DS qui possède des privilèges d’administrateur local. Voir [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="9887c-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="9887c-200">À partir du serveur de synchronisation d’annuaires, ouvrez l'article [Configurer la synchronisation d'annuaires pour Office 365](set-up-directory-synchronization.md) et suivez les instructions pour la synchronisation d'annuaires avec la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9887c-200">From the directory sync server, open the [Set up directory synchronization for Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="9887c-p122">Le programme d’installation crée le compte **AAD_xxxxxxxxxxxx** dans l’unité d’organisation (UO) Utilisateurs Locaux. Ne déplacez pas et ne supprimez pas ce compte, sinon la synchronisation échouera.</span><span class="sxs-lookup"><span data-stu-id="9887c-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="9887c-203">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="9887c-203">This is your resulting configuration.</span></span>
  
![Phase 3 du serveur de synchronisation d’annuaires pour Office 365 hébergé dans Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="9887c-205">Cette illustration montre le serveur de synchronisation d’annuaires avec Azure AD Connect dans le réseau virtuel Azure entre différents locaux.</span><span class="sxs-lookup"><span data-stu-id="9887c-205">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="9887c-206">Affectation d’emplacements et de licences à des utilisateurs dans Office 365</span><span class="sxs-lookup"><span data-stu-id="9887c-206">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="9887c-207">Azure AD Connect ajoute des comptes à votre abonnement Office 365 à partir du service AD DS local, mais pour que les utilisateurs se connectent à Office 365 et utilisent ses services, les comptes doivent être configurés avec un emplacement et des licences.</span><span class="sxs-lookup"><span data-stu-id="9887c-207">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises AD DS, but in order for users to sign in to Office 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="9887c-208">Utilisez ces étapes pour ajouter l’emplacement et activer les licences pour les comptes d’utilisateur appropriés :</span><span class="sxs-lookup"><span data-stu-id="9887c-208">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="9887c-209">Connectez-vous à la [page du portail Office 365](https://www.office.com), puis cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="9887c-209">Sign in to the [Office 365 portal page](https://www.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="9887c-210">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="9887c-210">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="9887c-211">Dans la liste des comptes d’utilisateur, sélectionnez la case à cocher en regard de l’utilisateur que vous souhaitez activer.</span><span class="sxs-lookup"><span data-stu-id="9887c-211">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="9887c-212">Sur la page de l'utilisateur, cliquez sur **Modifier** pour **Licences de produits**.</span><span class="sxs-lookup"><span data-stu-id="9887c-212">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="9887c-213">Sur la page **Licences de produit**, sélectionnez un emplacement pour l'utilisateur pour **Emplacement**, puis activez les licences appropriées pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9887c-213">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="9887c-214">Lorsque vous avez terminé, cliquez sur **Enregistrer**, puis sur **Fermer** deux fois.</span><span class="sxs-lookup"><span data-stu-id="9887c-214">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="9887c-215">Revenez à l’étape 3 pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9887c-215">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9887c-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9887c-216">See also</span></span>

[<span data-ttu-id="9887c-217">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="9887c-217">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="9887c-218">Connecter un réseau local à Microsoft Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="9887c-218">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="9887c-219">Télécharger Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="9887c-219">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="9887c-220">Configurer la synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="9887c-220">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
<!--
[Directory Synchronization server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)
-->


