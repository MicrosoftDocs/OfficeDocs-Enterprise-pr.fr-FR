---
title: Scénarios de cloud hybride pour les services IaaS Azure
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Résumé : Découvrez les scénarios et l’architecture hybride pour l’Infrastructure de Microsoft en tant que Service (IaaS)-en fonction des offres de cloud dans Azure.'
ms.openlocfilehash: 441565adae46d50ad1b7139525ff3146c5f88ca3
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181035"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="c6df8-103">Scénarios de cloud hybride pour Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="c6df8-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="c6df8-104">**Résumé :** Comprendre l’architecture de hybride et les scénarios de l’Infrastructure de Microsoft en tant que Service (IaaS)-en fonction des offres de cloud dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="c6df8-105">Étendez votre infrastructure de calcul et d’identité au cloud en hébergeant des charges de travail informatiques exécutées dans des réseaux virtuels Azure intersites. </span><span class="sxs-lookup"><span data-stu-id="c6df8-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="c6df8-106">Architecture de scénario hybride pour les services IaaS Azure</span><span class="sxs-lookup"><span data-stu-id="c6df8-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="c6df8-107">La figure 1 présente l’architecture des scénarios hybrides IaaS de Microsoft dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="c6df8-108">**Figure 1 : Scénarios hybrides Microsoft IaaS dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c6df8-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Scénarios hybrides Microsoft IaaS dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="c6df8-110">Pour chaque couche de l’architecture :</span><span class="sxs-lookup"><span data-stu-id="c6df8-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="c6df8-111">Applications et scénarios</span><span class="sxs-lookup"><span data-stu-id="c6df8-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="c6df8-112">Une charge de travail informatique est généralement une application multiniveau à haut niveau de disponibilité qui est composée d’ordinateurs virtuels Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="c6df8-113">Identity</span><span class="sxs-lookup"><span data-stu-id="c6df8-113">Identity</span></span>
    
    <span data-ttu-id="c6df8-114">Ajoutez des serveurs d’identité, tels que des contrôleurs de domaine Windows Server AD, à l’ensemble de serveurs exécutés dans les réseaux virtuels Azure à des fins d’authentification locale.</span><span class="sxs-lookup"><span data-stu-id="c6df8-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="c6df8-115">Réseau</span><span class="sxs-lookup"><span data-stu-id="c6df8-115">Network</span></span>
    
    <span data-ttu-id="c6df8-116">Utilisez une connexion VPN de site à site via Internet ou une connexion ExpressRoute avec homologation privée vers les services IaaS Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="c6df8-117">Sur site</span><span class="sxs-lookup"><span data-stu-id="c6df8-117">On-premises</span></span>
    
    <span data-ttu-id="c6df8-p101">Contient des serveurs d’identité qui sont synchronisés avec les serveurs d’identité exécutés dans Azure. Peut également contenir des ressources auxquelles les ordinateurs virtuels exécutés dans Azure peuvent accéder, telles que le stockage et l’infrastructure de gestion des systèmes.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="c6df8-120">Serveur de synchronisation d’annuaire pour Office 365</span><span class="sxs-lookup"><span data-stu-id="c6df8-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="c6df8-121">Exécution de votre serveur de synchronisation d’annuaire à partir d’un VNet Azure, comme indiqué dans la Figure 2, est un exemple d’extension de votre infrastructure informatique et identité vers le nuage.</span><span class="sxs-lookup"><span data-stu-id="c6df8-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="c6df8-122">**La figure 2 : Serveur de synchronisation pour Office 365 dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="c6df8-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Serveur de synchronisation d’annuaire pour Office 365 dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="c6df8-p102">Dans la Figure 2, un réseau local héberge une infrastructure Windows Server Active Directory, avec un serveur proxy et un routeur au bord. Le routeur se connecte à une passerelle Azure sur le bord d’un VNet Azure avec une connexion de site à ExpressRoute à distance ou VPN. À l’intérieur de la VNet, un serveur de synchronisation d’annuaires exécute Azure AD se connecter.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="c6df8-127">Un serveur de synchronisation d’annuaire pour Office 365 synchronise la liste des comptes dans Windows Server Active Directory avec le client Azure AD d’un abonnement à Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6df8-127">A directory synchronization server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="c6df8-p103">Un serveur de synchronisation d’annuaires est un serveur basé sur Windows qui exécute Azure AD se connecter. Pour la mise en service plus rapide ou pour réduire le nombre de serveurs locaux dans votre organisation, déployez le serveur de synchronisation d’annuaire dans un réseau virtuel (VNet) dans Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p103">A directory synchronization server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="c6df8-130">Le serveur de synchronisation d’annuaire interroge Windows Server Active Directory pour que les modifications, puis les synchronise avec l’abonnement à Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6df8-130">The directory synchronization server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="c6df8-131">Pour plus d’informations, voir [Déployer Office 365 la synchronisation d’annuaires dans Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c6df8-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="c6df8-132">Application métier</span><span class="sxs-lookup"><span data-stu-id="c6df8-132">Line of business (LOB) application</span></span>

<span data-ttu-id="c6df8-133">La figure 3 illustre la configuration d’une application métier basée sur un serveur exécutée dans Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="c6df8-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="c6df8-134">**Figure 3 : Application métier dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="c6df8-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Application métier serveur dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="c6df8-p104">Dans la Figure 3, un réseau local héberge des utilisateurs et une infrastructure d’identité. Il est connecté à une passerelle Azure IaaS avec une connexion ExpressRoute ou VPN de site à site. Azure IaaS héberge un réseau virtuel qui contient les serveurs de l’application métier.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="c6df8-139">Vous pouvez créer des applications métier exécutées sur des ordinateurs virtuels Azure qui résident sur des sous-réseaux d’un réseau virtuel Azure dans un centre de données Azure (également appelé « emplacement »). 


</span><span class="sxs-lookup"><span data-stu-id="c6df8-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="c6df8-140">Étant donné que vous cherchez à étendre votre infrastructure locale à Azure, vous devez attribuer un espace d’adressage privé unique à vos réseaux virtuels et mettre à jour vos tables de routage locales afin de veiller à ce que chaque réseau virtuel soit accessible.</span><span class="sxs-lookup"><span data-stu-id="c6df8-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="c6df8-141">Une fois connectés, ces ordinateurs virtuels peuvent être gérés via des connexions Bureau à distance ou via votre logiciel de gestion de systèmes, tout comme vos serveurs locaux.</span><span class="sxs-lookup"><span data-stu-id="c6df8-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="c6df8-142">En configurant des ports exposés publiquement, des utilisateurs mobile ou distants peuvent également accéder à ces ordinateurs virtuels via Internet.</span><span class="sxs-lookup"><span data-stu-id="c6df8-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="c6df8-143">Pour consulter une configuration avec preuve de concept, reportez-vous à la rubrique [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c6df8-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="c6df8-144">Les attributs des applications métier hébergées sur des ordinateurs virtuels Azure sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="c6df8-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="c6df8-145">Multiniveau</span><span class="sxs-lookup"><span data-stu-id="c6df8-145">Multiple tiers</span></span>
    
    <span data-ttu-id="c6df8-p105">Les applications métier classiques utilisent une approche à plusieurs niveaux. Les ensembles de serveurs fournissent des fonctionnalités de traitement des identités et des base de données, de traitement logique et applicatif ainsi que des serveurs web frontaux réservés à l’accès des employés ou des clients. </span><span class="sxs-lookup"><span data-stu-id="c6df8-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="c6df8-148">Disponibilité élevée</span><span class="sxs-lookup"><span data-stu-id="c6df8-148">High availability</span></span>
    
    <span data-ttu-id="c6df8-p106">Les applications métier classiques offrent une disponibilité élevée en utilisant plusieurs serveurs dans chaque niveau. Azure IaaS fournit un SLA de disponibilité de 99,9 % pour les serveurs des groupes à haute disponibilité Azure. </span><span class="sxs-lookup"><span data-stu-id="c6df8-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="c6df8-151">Répartition de la charge</span><span class="sxs-lookup"><span data-stu-id="c6df8-151">Load distribution</span></span>
    
    <span data-ttu-id="c6df8-p107">Pour répartir la charge de trafic réseau entre plusieurs serveurs dans un niveau, vous pouvez utiliser un équilibreur de charge Azure accessible sur Internet ou interne. Vous pouvez aussi utiliser un équilibreur de charge dédié disponible sur le marketplace Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="c6df8-154">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c6df8-154">Security</span></span>
    
    <span data-ttu-id="c6df8-p108">Pour protéger les serveurs du trafic entrant non sollicité provenant d’Internet, vous pouvez utiliser des groupes de sécurité réseau Azure. Vous pouvez définir un trafic autorisé ou refusé pour un sous-réseau ou l’interface réseau d’un ordinateur virtuel individuel.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="c6df8-157">Batterie SharePoint Server 2016 dans Azure</span><span class="sxs-lookup"><span data-stu-id="c6df8-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="c6df8-158">Une batterie de serveurs SharePoint Server 2016 est un exemple d’application métier hautement disponible à plusieurs niveaux dans Azure, comme illustré dans la figure 4.</span><span class="sxs-lookup"><span data-stu-id="c6df8-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="c6df8-159">**Figure 4 : Batterie SharePoint Server 2016 à disponibilité élevée dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="c6df8-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Batterie SharePoint Server 2016 à disponibilité élevée dans Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="c6df8-p109">Dans la figure 4, un réseau local héberge des utilisateurs et une infrastructure d’identité. Il est connecté à une passerelle Azure IaaS avec une connexion ExpressRoute ou VPN de site à site. Le réseau virtuel Azure contient les serveurs de la batterie SharePoint Server 2016, qui inclut des niveaux séparés pour les serveurs frontaux, les serveurs d’applications, le cluster SQL Server et les contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="c6df8-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="c6df8-164">Cette configuration a les attributs suivants des applications métier dans Azure : </span><span class="sxs-lookup"><span data-stu-id="c6df8-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="c6df8-165">Niveaux</span><span class="sxs-lookup"><span data-stu-id="c6df8-165">Tiers</span></span>
    
    <span data-ttu-id="c6df8-166">Les serveurs exécutant différents rôles au sein de la batterie créent les niveaux et chaque niveau possède son propre sous-réseau.
</span><span class="sxs-lookup"><span data-stu-id="c6df8-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="c6df8-167">Disponibilité élevée</span><span class="sxs-lookup"><span data-stu-id="c6df8-167">High-availability</span></span>
    
    <span data-ttu-id="c6df8-168">Obtenue à l’aide de plusieurs serveurs dans chaque niveau et en plaçant tous les serveurs d’un niveau dans le même groupe à disponibilité élevée.</span><span class="sxs-lookup"><span data-stu-id="c6df8-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="c6df8-169">Répartition de la charge</span><span class="sxs-lookup"><span data-stu-id="c6df8-169">Load distribution</span></span>
    
    <span data-ttu-id="c6df8-170">Les équilibreurs de charge Azure internes distribuent le trafic web client entrant vers les serveurs frontaux (WEB1 et WEB2) et vers l’adresse IP d’écouteur du cluster SQL Server (SQL1 SQL2 et MN1).</span><span class="sxs-lookup"><span data-stu-id="c6df8-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="c6df8-171">Security</span><span class="sxs-lookup"><span data-stu-id="c6df8-171">Security</span></span>
    
    <span data-ttu-id="c6df8-172">Les groupes de sécurité réseau pour chaque sous-réseau vous permettent de configurer le trafic entrant et sortant autorisé.</span><span class="sxs-lookup"><span data-stu-id="c6df8-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="c6df8-173">Suivez cette procédure pour une adoption réussie :</span><span class="sxs-lookup"><span data-stu-id="c6df8-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="c6df8-174">Évaluer et expérimenter</span><span class="sxs-lookup"><span data-stu-id="c6df8-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="c6df8-175">Voir [SharePoint Server 2016 dans Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) pour comprendre les avantages de l’exécution de SharePoint Server 2016 dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c6df8-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="c6df8-176">Voir [Intranet SharePoint Server 2016 dans l’environnement de développement/test Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) pour créer un environnement de développement/test simulé</span><span class="sxs-lookup"><span data-stu-id="c6df8-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="c6df8-177">Conception</span><span class="sxs-lookup"><span data-stu-id="c6df8-177">Design</span></span>
    
    <span data-ttu-id="c6df8-178">Voir la [conception d’une batterie de serveurs SharePoint Server 2016 dans Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) pour parcourir un processus pour déterminer l’ensemble des réseaux Azure IaaS, compute et éléments de stockage pour héberger votre batterie de serveurs et de leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="c6df8-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="c6df8-179">Déployer</span><span class="sxs-lookup"><span data-stu-id="c6df8-179">Deploy</span></span>
    
    <span data-ttu-id="c6df8-180">Consultez [déploiement de SharePoint Server 2016 avec les groupes de disponibilité AlwaysOn SQL Server dans Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) afin de parcourir la configuration de bout en bout de la batterie de serveurs haute disponibilité dans cinq phases.</span><span class="sxs-lookup"><span data-stu-id="c6df8-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="c6df8-181">Identité fédérée pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="c6df8-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="c6df8-182">Un autre exemple d’une application métier à plusieurs niveaux, hautement disponible dans Azure est l’identité fédérée pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6df8-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="c6df8-183">**La figure 5 : Une infrastructure identité fédérée de haute disponibilité pour Office 365 dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="c6df8-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Une haute disponibilité Office 365 fédéré de l’infrastructure d’authentification dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="c6df8-p110">Dans la Figure 5, un réseau local héberge une infrastructure d’identité et les utilisateurs. Il est connecté à une passerelle Azure IaaS avec une connexion de site à ExpressRoute à distance ou VPN. Le VNet Azure contient les serveurs proxy, les serveurs d’Active Directory Federation Services (ADFS) et les contrôleurs de domaine Windows Server Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="c6df8-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="c6df8-188">Cette configuration a les attributs suivants des applications métier dans Azure : </span><span class="sxs-lookup"><span data-stu-id="c6df8-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="c6df8-189">**Couches :** Il existe des couches pour les serveurs proxy web, serveurs AD FS et contrôleurs de domaine Windows Server Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c6df8-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="c6df8-190">**Répartition de la charge :** Un équilibreur de charge Azure externe distribue les demandes d’authentification client entrantes vers les serveurs proxy web et un équilibreur de charge Azure interne distribue les demandes d’authentification pour les serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="c6df8-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="c6df8-191">Suivez cette procédure pour une adoption réussie :</span><span class="sxs-lookup"><span data-stu-id="c6df8-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="c6df8-192">Évaluer et expérimenter</span><span class="sxs-lookup"><span data-stu-id="c6df8-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="c6df8-193">Consultez l' [identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md) pour créer un environnement de développement/test simulé pour l’authentification fédérée avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6df8-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="c6df8-194">Déployer</span><span class="sxs-lookup"><span data-stu-id="c6df8-194">Deploy</span></span>
    
    <span data-ttu-id="c6df8-195">Voir [authentification fédérée de déploiement haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) afin de parcourir la configuration de bout en bout de la haute disponibilité infrastructure AD FS dans cinq phases.</span><span class="sxs-lookup"><span data-stu-id="c6df8-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="c6df8-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6df8-196">See Also</span></span>

[<span data-ttu-id="c6df8-197">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="c6df8-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="c6df8-198">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c6df8-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


