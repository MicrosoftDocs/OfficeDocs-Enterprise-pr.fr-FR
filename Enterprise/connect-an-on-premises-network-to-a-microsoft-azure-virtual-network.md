---
title: "Connecter un réseau local à Microsoft Azure Virtual Network"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "Résumé : Découvrez comment configurer un réseau virtuel Azure intersites pour les charges de travail de serveur Office."
ms.openlocfilehash: c071806bda74f9ecb4669b0cd6bc91704cf3182a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a><span data-ttu-id="82d60-103">Connecter un réseau local à Microsoft Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="82d60-103">Connect an on-premises network to a Microsoft Azure virtual network</span></span>

 <span data-ttu-id="82d60-104">**Résumé :** Découvrez comment configurer un réseau virtuel Azure intersites pour les charges de travail de serveur Office.</span><span class="sxs-lookup"><span data-stu-id="82d60-104">**Summary:** Learn how to configure a cross-premises Azure virtual network for Office server workloads.</span></span>
  
<span data-ttu-id="82d60-p101">Un réseau virtuel Azure entre différents locaux est connecté à votre réseau local, étendant ainsi votre réseau pour inclure des sous-réseaux et machines virtuelles hébergés dans les services d’infrastructure Azure. Cette connexion permet aux ordinateurs de votre réseau local d’accéder directement aux machines virtuelles dans Azure et inversement. Par exemple, un serveur DirSync en cours d’exécution sur une machine virtuelle Azure doit interroger vos contrôleurs de domaine locaux pour apporter des modifications aux comptes et synchroniser ces modifications avec votre abonnement Office 365. Cet article vous explique comment configurer un réseau virtuel Azure prêt à héberger des machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-p101">A cross-premises Azure virtual network is connected to your on-premises network, extending your network to include subnets and virtual machines hosted in Azure infrastructure services. This connection allows computers on your on-premises network to directly access virtual machines in Azure and vice versa. For example, a DirSync server running on an Azure virtual machine needs to query your on-premises domain controllers for changes to accounts and synchronize those changes with your Office 365 subscription. This article shows you how to set up a cross-premises Azure virtual network that is ready to host Azure virtual machines.</span></span>

## <a name="overview"></a><span data-ttu-id="82d60-109">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="82d60-109">Overview</span></span>

<span data-ttu-id="82d60-p102">Vos machines virtuelles dans Azure n’ont pas besoin d’être isolées de votre environnement local. Pour connecter des machines virtuelles Azure à des ressources réseau locales, vous devez configurer un réseau virtuel Azure local. Le diagramme suivant montre les composants requis pour déployer un réseau virtuel Azure entre différents locaux avec une machine virtuelle dans Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-p102">Your virtual machines in Azure don't have to be isolated from your on-premises environment. To connect Azure virtual machines to your on-premises network resources, you must configure a cross-premises Azure virtual network. The following diagram shows the required components to deploy a cross-premises Azure virtual network with a virtual machine in Azure.</span></span>
  
![Réseau local connecté à Microsoft Azure via une connexion VPN de site à site](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
<span data-ttu-id="82d60-p103">Dans le diagramme, il existe deux réseaux connectés via une connexion de réseau privé virtuel (VPN) de site à site : le réseau local et le réseau virtuel Azure. La connexion VPN de site à site se termine par un périphérique VPN sur le réseau local et par une passerelle VPN Azure sur le réseau virtuel Azure. Le réseau virtuel Azure dispose de machines virtuelles. Le trafic réseau provenant des machines virtuelles sur le réseau virtuel Azure est acheminé vers la passerelle VPN, laquelle transmet le trafic de la connexion VPN de site à site sur le périphérique VPN sur le réseau local. L’infrastructure de routage du réseau local transmet ensuite le trafic à sa destination.</span><span class="sxs-lookup"><span data-stu-id="82d60-p103">In the diagram, there are two networks connected by a site-to-site virtual private network (VPN) connection: the on-premises network and the Azure virtual network. The site-to-site VPN connection is terminated by a VPN device on the on-premises network and an Azure VPN gateway on the Azure virtual network. The Azure virtual network has virtual machines. Network traffic originating from virtual machines on the Azure virtual network gets forwarded to the VPN gateway, which then forwards the traffic across the site-to-site VPN connection to the VPN device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination.</span></span>
  
<span data-ttu-id="82d60-119">Pour configurer la connexion VPN entre votre réseau Azure Virtual Network et votre réseau local, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="82d60-119">To set up the VPN connection between your Azure virtual network and your on-premises network, do the following steps:</span></span> 
  
1. <span data-ttu-id="82d60-120">**Local :** Définissez et créez un itinéraire réseau local pour l'espace d'adressage du réseau virtuel Azure qui pointe vers votre périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="82d60-120">**On-premises:** Define and create an on-premises network route for the address space of the Azure virtual network that points to your on-premises VPN device.</span></span>
    
2. <span data-ttu-id="82d60-p104">**Microsoft Azure :** créez un réseau virtuel Azure avec une connexion VPN de site à site. Cet article ne décrit pas l’utilisation d’[ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span><span class="sxs-lookup"><span data-stu-id="82d60-p104">**Microsoft Azure:** Create an Azure virtual network with a site-to-site VPN connection. This article does not describe the use of [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span></span>
    
3. <span data-ttu-id="82d60-123">**Local :** Configurez votre périphérique VPN matériel ou logiciel local pour marquer la fin de la connexion VPN en utilisant la sécurité du protocole Internet (IPsec).</span><span class="sxs-lookup"><span data-stu-id="82d60-123">**On premises:** Configure your on-premises hardware or software VPN device to terminate the VPN connection, which uses Internet Protocol security (IPsec).</span></span>
    
<span data-ttu-id="82d60-124">Après avoir établi la connexion VPN de site à site, vous ajoutez des machines virtuelles Azure aux sous-réseaux du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="82d60-124">After you establish the site-to-site VPN connection, you add Azure virtual machines to the subnets of the virtual network.</span></span>
  
## <a name="plan-your-azure-virtual-network"></a><span data-ttu-id="82d60-125">Planification de votre réseau Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="82d60-125">Plan your Azure virtual network</span></span>
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a><span data-ttu-id="82d60-126">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="82d60-126">Prerequisites</span></span>
<a name="Prerequisites"></a>

- <span data-ttu-id="82d60-p105">Un abonnement Azure. Pour plus d’informations sur les abonnements Azure, accédez à la [page des abonnements Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).</span><span class="sxs-lookup"><span data-stu-id="82d60-p105">An Azure subscription. For information about Azure subscriptions, go to the [Microsoft Azure subscription page](https://azure.microsoft.com/pricing/purchase-options/).</span></span>
    
- <span data-ttu-id="82d60-129">Un espace d’adressage IPv4 privé disponible à affecter au réseau virtuel et à ses sous-réseaux, avec suffisamment d’espace pour leur croissance afin d’accueillir le nombre de machines virtuelles nécessaires maintenant et à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="82d60-129">An available private IPv4 address space to assign to the virtual network and its subnets, with sufficient room for growth to accommodate the number of virtual machines needed now and in the future.</span></span>
    
- <span data-ttu-id="82d60-p106">Un périphérique VPN disponible dans votre réseau local pour marquer la fin de la connexion VPN de site à site qui prend en charge la configuration requise IPsec. Pour plus d’informations, reportez-vous à l’article [À propos des périphériques VPN pour les connexions de réseau virtuel de site à site](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span><span class="sxs-lookup"><span data-stu-id="82d60-p106">An available VPN device in your on-premises network to terminate the site-to-site VPN connection that supports the requirements for IPsec. For more information, see [About VPN devices for site-to-site virtual network connections](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span></span>
    
- <span data-ttu-id="82d60-132">La modification de votre infrastructure de routage pour que le trafic routé vers l’espace d’adressage du réseau virtuel Azure soit acheminé vers le périphérique VPN qui héberge la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="82d60-132">Changes to your routing infrastructure so that traffic routed to the address space of the Azure virtual network gets forwarded to the VPN device that hosts the site-to-site VPN connection.</span></span>
    
- <span data-ttu-id="82d60-133">Un proxy web fournissant un accès à Internet aux ordinateurs connectés au réseau local et au réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-133">A web proxy that gives computers that are connected to the on-premises network and the Azure virtual network access to the Internet.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="82d60-134">Hypothèses en matière de conception de l’architecture de la solution</span><span class="sxs-lookup"><span data-stu-id="82d60-134">Solution architecture design assumptions</span></span>

<span data-ttu-id="82d60-135">La liste suivante répertorie les choix de conception qui ont été faits pour l’architecture de cette solution.</span><span class="sxs-lookup"><span data-stu-id="82d60-135">The following list represents the design choices that have been made for this solution architecture.</span></span> 
  
- <span data-ttu-id="82d60-p107">Cette solution utilise un seul réseau virtuel Azure avec une connexion VPN de site à site. Le réseau virtuel Azure héberge un sous-réseau unique qui contient plusieurs machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="82d60-p107">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that can contain multiple virtual machines.</span></span> 
    
- <span data-ttu-id="82d60-p108">Vous pouvez utiliser le service Routage et accès distant (RRAS) dans Windows Server 2016 ou Windows Server 2012 pour établir une connexion VPN de site à site IPsec entre le réseau local et le réseau virtuel Azure. Vous pouvez également utiliser d’autres options, telles que des périphériques VPN Cisco ou Juniper Networks.</span><span class="sxs-lookup"><span data-stu-id="82d60-p108">You can use the Routing and Remote Access Service (RRAS) in Windows Server 2016 or Windows Server 2012 to establish an IPsec site-to-site VPN connection between the on-premises network and the Azure virtual network. You can also use other options, such as Cisco or Juniper Networks VPN devices.</span></span>
    
- <span data-ttu-id="82d60-p109">Le réseau local peut tout de même disposer de services réseau, tels que Windows Server Active Directory (AD), un système DNS (Domain Name System) et des serveurs proxy. Selon vos besoins, il peut être utile de placer certaines de ces ressources réseau dans le réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-p109">The on-premises network might still have network services like Windows Server Active Directory (AD), Domain Name System (DNS), and proxy servers. Depending on your requirements, it might be beneficial to place some of these network resources in the Azure virtual network.</span></span>
    
<span data-ttu-id="82d60-p110">Pour un réseau virtuel Azure existant comportant un ou plusieurs sous-réseaux, déterminez s’il reste assez d’espace d’adressage pour qu’un sous-réseau supplémentaire puisse héberger les machines virtuelles dont vous avez besoin. Si vous n’avez pas assez d’espace d’adressage restant pour un sous-réseau supplémentaire, créez un réseau virtuel supplémentaire qui dispose de sa propre connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="82d60-p110">For an existing Azure virtual network with one or more subnets, determine whether there is remaining address space for an additional subnet to host your needed virtual machines, based on your requirements. If you don't have remaining address space for an additional subnet, create an additional virtual network that has its own site-to-site VPN connection.</span></span>
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a><span data-ttu-id="82d60-144">Planification des modifications d’infrastructure de routage pour le réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="82d60-144">Plan the routing infrastructure changes for the Azure virtual network</span></span>

<span data-ttu-id="82d60-145">Vous devez configurer votre infrastructure de routage locale pour acheminer le trafic destiné à l'espace d'adressage du réseau virtuel Azure au périphérique VPN local qui héberge la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="82d60-145">You must configure your on-premises routing infrastructure to forward traffic destined for the address space of the Azure virtual network to the on-premises VPN device that is hosting the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="82d60-146">La méthode de mise à jour exacte de votre infrastructure de routage dépend de votre gestion des informations de routage, c’est-à-dire :</span><span class="sxs-lookup"><span data-stu-id="82d60-146">The exact method of updating your routing infrastructure depends on how you manage routing information, which can be:</span></span>
  
- <span data-ttu-id="82d60-147">Des mises à jour de la table de routage en fonction de la configuration manuelle.</span><span class="sxs-lookup"><span data-stu-id="82d60-147">Routing table updates based on manual configuration.</span></span>
    
- <span data-ttu-id="82d60-148">Des mises à jour de la table de routage en fonction des protocoles de routage, tels que le protocole RIP (Routing Information Protocol) ou le protocole OSPF (Open Shortest Path First).</span><span class="sxs-lookup"><span data-stu-id="82d60-148">Routing table updates based on routing protocols, such as Routing Information Protocol (RIP) or Open Shortest Path First (OSPF).</span></span>
    
<span data-ttu-id="82d60-149">Consultez votre spécialiste du routage pour vous assurer que le trafic destiné au réseau virtuel Azure est transféré au périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="82d60-149">Consult with your routing specialist to make sure that traffic destined for the Azure virtual network is forwarded to the on-premises VPN device.</span></span>
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a><span data-ttu-id="82d60-150">Planification des règles de pare-feu pour le trafic vers et depuis le périphérique VPN local</span><span class="sxs-lookup"><span data-stu-id="82d60-150">Plan for firewall rules for traffic to and from the on-premises VPN device</span></span>

<span data-ttu-id="82d60-151">Si votre périphérique VPN se trouve sur un réseau de périmètre qui dispose d’un pare-feu entre le réseau de périmètre et Internet, vous devrez peut-être configurer le pare-feu pour que les règles suivantes autorisent la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="82d60-151">If your VPN device is on a perimeter network that has a firewall between the perimeter network and the Internet, you might have to configure the firewall for the following rules to allow the site-to-site VPN connection.</span></span>
  
- <span data-ttu-id="82d60-152">Trafic vers le périphérique VPN (entrant, à partir d’Internet) :</span><span class="sxs-lookup"><span data-stu-id="82d60-152">Traffic to the VPN device (incoming from the Internet):</span></span>
    
  - <span data-ttu-id="82d60-153">Adresse IP de destination du périphérique VPN et protocole IP 50</span><span class="sxs-lookup"><span data-stu-id="82d60-153">Destination IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="82d60-154">Adresse IP de destination du périphérique VPN et port 500 de destination UDP</span><span class="sxs-lookup"><span data-stu-id="82d60-154">Destination IP address of the VPN device and UDP destination port 500</span></span>
    
  - <span data-ttu-id="82d60-155">Adresse IP de destination du périphérique VPN et port 4500 de destination UDP</span><span class="sxs-lookup"><span data-stu-id="82d60-155">Destination IP address of the VPN device and UDP destination port 4500</span></span>
    
- <span data-ttu-id="82d60-156">Trafic provenant du périphérique VPN (sortant, en direction d’Internet) :</span><span class="sxs-lookup"><span data-stu-id="82d60-156">Traffic from the VPN device (outgoing to the Internet):</span></span>
    
  - <span data-ttu-id="82d60-157">Adresse IP source du périphérique VPN et protocole IP 50</span><span class="sxs-lookup"><span data-stu-id="82d60-157">Source IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="82d60-158">Adresse IP source du périphérique VPN et port 500 source UDP</span><span class="sxs-lookup"><span data-stu-id="82d60-158">Source IP address of the VPN device and UDP source port 500</span></span>
    
  - <span data-ttu-id="82d60-159">Adresse IP source du périphérique VPN et port 4500 source UDP</span><span class="sxs-lookup"><span data-stu-id="82d60-159">Source IP address of the VPN device and UDP source port 4500</span></span>
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a><span data-ttu-id="82d60-160">Planification de l’espace d’adressage IP privé du réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="82d60-160">Plan for the private IP address space of the Azure virtual network</span></span>

<span data-ttu-id="82d60-161">L'espace d'adressage IP privé du réseau virtuel Azure doit pouvoir prendre en charge les adresses utilisées par Azure pour héberger le réseau virtuel et au moins un sous-réseau disposant de suffisamment d'adresses pour vos machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-161">The private IP address space of the Azure virtual network must be able to accommodate addresses used by Azure to host the virtual network and with at least one subnet that has enough addresses for your Azure virtual machines.</span></span>
  
<span data-ttu-id="82d60-162">Pour déterminer le nombre d’adresses nécessaires pour le sous-réseau, comptez le nombre de machines virtuelles dont vous avez besoin maintenant, estimez la croissance future, puis utilisez le tableau suivant pour déterminer la taille du sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="82d60-162">To determine the number of addresses needed for the subnet, count the number of virtual machines that you need now, estimate for future growth, and then use the following table to determine the size of the subnet.</span></span>
  
|<span data-ttu-id="82d60-163">**Nombre de machines virtuelles nécessaires**</span><span class="sxs-lookup"><span data-stu-id="82d60-163">**Number of virtual machines needed**</span></span>|<span data-ttu-id="82d60-164">**Nombre de bits d'hôte requis**</span><span class="sxs-lookup"><span data-stu-id="82d60-164">**Number of host bits needed**</span></span>|<span data-ttu-id="82d60-165">**Taille du sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="82d60-165">**Size of the subnet**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="82d60-166">1-3</span><span class="sxs-lookup"><span data-stu-id="82d60-166">1-3</span></span>  <br/> |<span data-ttu-id="82d60-167">3</span><span class="sxs-lookup"><span data-stu-id="82d60-167">3</span></span>  <br/> |<span data-ttu-id="82d60-168">/29</span><span class="sxs-lookup"><span data-stu-id="82d60-168">/29</span></span>  <br/> |
|<span data-ttu-id="82d60-169">4-11</span><span class="sxs-lookup"><span data-stu-id="82d60-169">4-11</span></span>  <br/> |<span data-ttu-id="82d60-170">4</span><span class="sxs-lookup"><span data-stu-id="82d60-170">4</span></span>  <br/> |<span data-ttu-id="82d60-171">/28</span><span class="sxs-lookup"><span data-stu-id="82d60-171">/28</span></span>  <br/> |
|<span data-ttu-id="82d60-172">12-27</span><span class="sxs-lookup"><span data-stu-id="82d60-172">12-27</span></span>  <br/> |<span data-ttu-id="82d60-173">5</span><span class="sxs-lookup"><span data-stu-id="82d60-173">5</span></span>  <br/> |<span data-ttu-id="82d60-174">/27</span><span class="sxs-lookup"><span data-stu-id="82d60-174">/27</span></span>  <br/> |
|<span data-ttu-id="82d60-175">28-59</span><span class="sxs-lookup"><span data-stu-id="82d60-175">28-59</span></span>  <br/> |<span data-ttu-id="82d60-176">6</span><span class="sxs-lookup"><span data-stu-id="82d60-176">6</span></span>  <br/> |<span data-ttu-id="82d60-177">/26</span><span class="sxs-lookup"><span data-stu-id="82d60-177">/26</span></span>  <br/> |
|<span data-ttu-id="82d60-178">60-123</span><span class="sxs-lookup"><span data-stu-id="82d60-178">60-123</span></span>  <br/> |<span data-ttu-id="82d60-179">7</span><span class="sxs-lookup"><span data-stu-id="82d60-179">7</span></span>  <br/> |<span data-ttu-id="82d60-180">/25</span><span class="sxs-lookup"><span data-stu-id="82d60-180">/25</span></span>  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a><span data-ttu-id="82d60-181">Planification de la feuille de travail pour la configuration de votre réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="82d60-181">Planning worksheet for configuring your Azure virtual network</span></span>
<span data-ttu-id="82d60-182"><a name="worksheet"> </a></span><span class="sxs-lookup"><span data-stu-id="82d60-182"><a name="worksheet"> </a></span></span>

<span data-ttu-id="82d60-183">Avant de créer un réseau virtuel Azure pour héberger des machines virtuelles, vous devez déterminer les paramètres nécessaires dans les tableaux suivants.</span><span class="sxs-lookup"><span data-stu-id="82d60-183">Before you create an Azure virtual network to host virtual machines, you must determine the settings needed in the following tables.</span></span>
  
<span data-ttu-id="82d60-184">Pour les paramètres du réseau virtuel, remplissez le tableau V.</span><span class="sxs-lookup"><span data-stu-id="82d60-184">For the settings of the virtual network, fill in Table V.</span></span>
  
 <span data-ttu-id="82d60-185">**Tableau V : configuration de réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="82d60-185">**Table V: Cross-premises virtual network configuration**</span></span>
  
|<span data-ttu-id="82d60-186">**Élément**</span><span class="sxs-lookup"><span data-stu-id="82d60-186">**Item**</span></span>|<span data-ttu-id="82d60-187">**Élément Configuration**</span><span class="sxs-lookup"><span data-stu-id="82d60-187">**Configuration element**</span></span>|<span data-ttu-id="82d60-188">**Description**</span><span class="sxs-lookup"><span data-stu-id="82d60-188">**Description**</span></span>|<span data-ttu-id="82d60-189">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="82d60-189">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="82d60-190">1.</span><span class="sxs-lookup"><span data-stu-id="82d60-190">1.</span></span>  <br/> |<span data-ttu-id="82d60-191">Nom du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="82d60-191">Virtual network name</span></span>  <br/> |<span data-ttu-id="82d60-192">Nom à affecter au réseau virtuel Azure (par exemple, DirSyncNet).</span><span class="sxs-lookup"><span data-stu-id="82d60-192">A name to assign to the Azure virtual network (example DirSyncNet).</span></span>  <br/> |![](./images/Common_Images/TableLine.png) |
|<span data-ttu-id="82d60-193">2.</span><span class="sxs-lookup"><span data-stu-id="82d60-193">2.</span></span>  <br/> |<span data-ttu-id="82d60-194">Emplacement du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="82d60-194">Virtual network location</span></span>  <br/> |<span data-ttu-id="82d60-195">Centre de données Azure qui contiendra le réseau virtuel (par exemple, Ouest des États-Unis).</span><span class="sxs-lookup"><span data-stu-id="82d60-195">The Azure datacenter that will contain the virtual network (such as West US).</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="82d60-196">3.</span><span class="sxs-lookup"><span data-stu-id="82d60-196">3.</span></span>  <br/> |<span data-ttu-id="82d60-197">Adresse IP du périphérique VPN</span><span class="sxs-lookup"><span data-stu-id="82d60-197">VPN device IP address</span></span>  <br/> |<span data-ttu-id="82d60-p111">Adresse IPv4 publique de l’interface de votre périphérique VPN sur Internet. Renseignez-vous auprès de votre service informatique pour déterminer cette adresse.</span><span class="sxs-lookup"><span data-stu-id="82d60-p111">The public IPv4 address of your VPN device's interface on the Internet. Work with your IT department to determine this address.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="82d60-200">4.</span><span class="sxs-lookup"><span data-stu-id="82d60-200">4.</span></span>  <br/> |<span data-ttu-id="82d60-201">Espace d’adressage du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="82d60-201">Virtual network address space</span></span>  <br/> |<span data-ttu-id="82d60-p112">Espace d’adressage (défini dans un préfixe d’adresse privée unique) pour le réseau virtuel. Renseignez-vous auprès de votre service informatique pour déterminer cet espace d’adressage. L’espace d’adressage doit être au format de routage CIDR (Classless Interdomain Routing), également appelé format de préfixe de réseau. Par exemple, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="82d60-p112">The address space (defined in a single private address prefix) for the virtual network. Work with your IT department to determine this address space. The address space should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>  <br/> |![](./images/Common_Images/TableLine.png) <br/> |
|<span data-ttu-id="82d60-206">5.</span><span class="sxs-lookup"><span data-stu-id="82d60-206">5.</span></span>  <br/> |<span data-ttu-id="82d60-207">Clé partagée IPsec</span><span class="sxs-lookup"><span data-stu-id="82d60-207">IPsec shared key</span></span>  <br/> |<span data-ttu-id="82d60-p113">Chaîne alphanumérique aléatoire de 32 caractères, qui sera utilisée pour authentifier les deux côtés de la connexion VPN de site à site. Renseignez-vous auprès de votre service informatique ou de sécurité pour déterminer la valeur de cette clé, puis stockez-la dans un emplacement sécurisé. Vous pouvez également consulter la page relative à la [création d’une chaîne aléatoire pour une clé prépartagée IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="82d60-p113">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value and then store it in a secure location. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./images/Common_Images/TableLine.png) <br/> |
   
<span data-ttu-id="82d60-211">Remplissez le tableau S pour les sous-réseaux de cette solution.</span><span class="sxs-lookup"><span data-stu-id="82d60-211">Fill in Table S for the subnets of this solution.</span></span>
  
- <span data-ttu-id="82d60-p114">Pour le premier sous-réseau, déterminez un espace d’adressage 28 bits (avec une longueur de préfixe de /28) pour le sous-réseau de passerelle Azure. Reportez-vous à la rubrique sur le [calcul de l’espace d’adressage de sous-réseau de passerelle pour les réseaux virtuels Azure](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) pour savoir comment déterminer cet espace d’adressage.</span><span class="sxs-lookup"><span data-stu-id="82d60-p114">For the first subnet, determine a 28-bit address space (with a /28 prefix length) for the Azure gateway subnet. See [Calculating the gateway subnet address space for Azure virtual networks](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) for information about how to determine this address space.</span></span>
    
- <span data-ttu-id="82d60-214">Pour le deuxième sous-réseau, indiquez un nom convivial, un espace d’adressage IP unique fondé sur l’espace d’adressage de réseau virtuel et une description de l’objectif.</span><span class="sxs-lookup"><span data-stu-id="82d60-214">For the second subnet, specify a friendly name, a single IP address space based on the virtual network address space, and a descriptive purpose.</span></span>
    
<span data-ttu-id="82d60-p115">Renseignez-vous auprès de votre service informatique pour déterminer ces espaces d’adressage à partir de l’espace d’adressage de réseau virtuel. Les deux espaces d’adressage doivent être au format CIDR.</span><span class="sxs-lookup"><span data-stu-id="82d60-p115">Work with your IT department to determine these address spaces from the virtual network address space. Both address spaces should be in CIDR format.</span></span>
  
 <span data-ttu-id="82d60-217">**Tableau S : sous-réseaux dans le réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="82d60-217">**Table S: Subnets in the virtual network**</span></span>
  
|<span data-ttu-id="82d60-218">**Élément**</span><span class="sxs-lookup"><span data-stu-id="82d60-218">**Item**</span></span>|<span data-ttu-id="82d60-219">**Nom du sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="82d60-219">**Subnet name**</span></span>|<span data-ttu-id="82d60-220">**Espace d'adressage de sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="82d60-220">**Subnet address space**</span></span>|<span data-ttu-id="82d60-221">**Objectif**</span><span class="sxs-lookup"><span data-stu-id="82d60-221">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="82d60-222">1.</span><span class="sxs-lookup"><span data-stu-id="82d60-222">1.</span></span>  <br/> |<span data-ttu-id="82d60-223">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="82d60-223">GatewaySubnet</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="82d60-224">Sous-réseau utilisé par la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-224">The subnet used by the Azure gateway.</span></span>  <br/> |
|<span data-ttu-id="82d60-225">2.</span><span class="sxs-lookup"><span data-stu-id="82d60-225">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
<span data-ttu-id="82d60-p116">Concernant les serveurs DNS locaux qui doivent être utilisés par les machines virtuelles du réseau virtuel, remplissez le tableau D. Donnez un nom convivial et une adresse IP unique à chaque serveur DNS. Ce nom convivial n’a pas besoin de correspondre au nom d’hôte ou au nom de l’ordinateur du serveur DNS. Notez que le tableau comporte deux entrées vides, mais vous pouvez en ajouter d’autres. Renseignez-vous auprès de votre service informatique pour déterminer cette liste.</span><span class="sxs-lookup"><span data-stu-id="82d60-p116">For the on-premises DNS servers that you want the virtual machines in the virtual network to use, fill in Table D. Give each DNS server a friendly name and a single IP address. This friendly name does not need to match the host name or computer name of the DNS server. Note that two blank entries are listed, but you can add more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="82d60-230">**Tableau D : serveurs DNS locaux**</span><span class="sxs-lookup"><span data-stu-id="82d60-230">**Table D: On-premises DNS servers**</span></span>
  
|<span data-ttu-id="82d60-231">**Élément**</span><span class="sxs-lookup"><span data-stu-id="82d60-231">**Item**</span></span>|<span data-ttu-id="82d60-232">**Nom convivial du serveur DNS**</span><span class="sxs-lookup"><span data-stu-id="82d60-232">**DNS server friendly name**</span></span>|<span data-ttu-id="82d60-233">**Adresse IP du serveur DNS**</span><span class="sxs-lookup"><span data-stu-id="82d60-233">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="82d60-234">1.</span><span class="sxs-lookup"><span data-stu-id="82d60-234">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="82d60-235">2.</span><span class="sxs-lookup"><span data-stu-id="82d60-235">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
<span data-ttu-id="82d60-p117">Pour acheminer les paquets du réseau virtuel Azure vers le réseau de votre organisation par le biais de la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local. Ce réseau local contient la liste des espaces d’adressage (au format CIDR) pour l’ensemble des emplacements sur le réseau local de votre organisation que les machines virtuelles du réseau virtuel doivent atteindre. Il peut s’agir de l’ensemble des emplacements sur le réseau local ou un sous-ensemble. La liste des espaces d’adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec les espaces d’adressage utilisés pour ce réseau virtuel ou vos autres réseaux virtuels entre différents locaux.</span><span class="sxs-lookup"><span data-stu-id="82d60-p117">To route packets from the Azure virtual network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network. This local network contains a list of the address spaces (in CIDR format) for all of the locations on your organization's on-premises network that the virtual machines in the virtual network must reach. This can be all of the locations on the on-premises network or a subset. The list of address spaces that define your local network must be unique and must not overlap with the address spaces used for this virtual network or your other cross-premises virtual networks.</span></span>
  
<span data-ttu-id="82d60-p118">Pour l’ensemble des espaces d’adressage du réseau local, remplissez le tableau L. Notez que le tableau comporte trois entrées vides, mais vous aurez généralement besoin d’en ajouter. Renseignez-vous auprès de votre service informatique pour déterminer cette liste.</span><span class="sxs-lookup"><span data-stu-id="82d60-p118">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="82d60-242">**Tableau L : préfixes d’adresse pour le réseau local**</span><span class="sxs-lookup"><span data-stu-id="82d60-242">**Table L: Address prefixes for the local network**</span></span>
  
|<span data-ttu-id="82d60-243">**Élément**</span><span class="sxs-lookup"><span data-stu-id="82d60-243">**Item**</span></span>|<span data-ttu-id="82d60-244">**Espace d'adressage du réseau local**</span><span class="sxs-lookup"><span data-stu-id="82d60-244">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="82d60-245">1.</span><span class="sxs-lookup"><span data-stu-id="82d60-245">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="82d60-246">2.</span><span class="sxs-lookup"><span data-stu-id="82d60-246">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="82d60-247">3.</span><span class="sxs-lookup"><span data-stu-id="82d60-247">3.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a><span data-ttu-id="82d60-248">Feuille de route de déploiement</span><span class="sxs-lookup"><span data-stu-id="82d60-248">Deployment roadmap</span></span>
<span data-ttu-id="82d60-249"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="82d60-249"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="82d60-250">La création du réseau virtuel entre différents locaux et l'ajout de machines virtuelles dans Azure se composent de trois phases :</span><span class="sxs-lookup"><span data-stu-id="82d60-250">Creating the cross-premises virtual network and adding virtual machines in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="82d60-251">Phase 1 : préparer votre réseau local.</span><span class="sxs-lookup"><span data-stu-id="82d60-251">Phase 1: Prepare your on-premises network.</span></span>
    
- <span data-ttu-id="82d60-252">Phase 2 : créer le réseau virtuel entre différents locaux dans Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-252">Phase 2: Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="82d60-253">Phase 3 (facultative) : ajouter des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="82d60-253">Phase 3 (Optional): Add virtual machines.</span></span>
    
### <a name="phase-1-prepare-your-on-premises-network"></a><span data-ttu-id="82d60-254">Phase 1 : préparer votre réseau local</span><span class="sxs-lookup"><span data-stu-id="82d60-254">Phase 1: Prepare your on-premises network</span></span>
<a name="Phase1"></a>

<span data-ttu-id="82d60-p119">Vous devez configurer votre réseau local avec un itinéraire qui pointe vers l’espace d’adressage du réseau virtuel et remet finalement le trafic qui y est destiné au routeur sur le périmètre du réseau local. Contactez votre administrateur réseau pour savoir comment ajouter l’itinéraire à l’infrastructure de routage de votre réseau local.</span><span class="sxs-lookup"><span data-stu-id="82d60-p119">You must configure your on-premises network with a route that points to and ultimately delivers traffic destined for the address space of the virtual network to the router on the edge of the on-premises network. Consult with your network administrator to determine how to add the route to the routing infrastructure of your on-premises network.</span></span>
  
<span data-ttu-id="82d60-257">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="82d60-257">Here is your resulting configuration.</span></span>
  
![Le réseau local doit disposer d’un itinéraire pour l’espace d’adressage du réseau virtuel qui pointe vers l’appareil VPN.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="82d60-259">Phase 2 : créer le réseau virtuel entre différents locaux dans Azure</span><span class="sxs-lookup"><span data-stu-id="82d60-259">Phase 2: Create the cross-premises virtual network in Azure</span></span>
<a name="Phase2"></a>

<span data-ttu-id="82d60-p120">Tout d’abord, ouvrez une invite PowerShell Azure. Si vous n’avez pas installé Azure PowerShell, reportez-vous à l’article sur la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="82d60-p120">First, open an Azure PowerShell prompt. If you have not installed Azure PowerShell, see [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="82d60-p121">Ces commandes sont destinées à Azure PowerShell 1.0 et versions précédentes. Pour accéder à un fichier texte qui contient toutes les commandes PowerShell décrites dans cet article, cliquez [ici](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span><span class="sxs-lookup"><span data-stu-id="82d60-p121">These commands are for Azure PowerShell 1.0 and above. For a text file that contains all the PowerShell commands in this article, click [here](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span></span> 
  
<span data-ttu-id="82d60-264">Ensuite, connectez-vous à votre compte Azure avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="82d60-264">Next, login to your Azure account with this command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="82d60-265">Obtenez le nom de votre abonnement à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="82d60-265">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

<span data-ttu-id="82d60-p122">Définissez votre abonnement Azure avec les commandes suivantes. Remplacez tout le texte entre guillemets, y compris les caractères < et >, par le nom d’abonnement correct.</span><span class="sxs-lookup"><span data-stu-id="82d60-p122">Set your Azure subscription with these commands. Replace everything within the quotes, including the < and > characters, with the correct subscription name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

<span data-ttu-id="82d60-p123">Ensuite, créez un nouveau groupe de ressources pour votre réseau virtuel. Pour déterminer un nom de groupe de ressources unique, utilisez cette commande pour répertorier vos groupes de ressources existants.</span><span class="sxs-lookup"><span data-stu-id="82d60-p123">Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="82d60-270">Créez votre nouveau groupe de ressources avec ces commandes.</span><span class="sxs-lookup"><span data-stu-id="82d60-270">Create your new resource group with these commands.</span></span>
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

<span data-ttu-id="82d60-p124">Les machines virtuelles basées sur le gestionnaire des ressources requièrent un compte de stockage basé sur le gestionnaire des ressources. Vous devez choisir un nom global unique pour votre compte de stockage, contenant uniquement des lettres minuscules et des chiffres. Vous pouvez utiliser cette commande pour répertorier les comptes de stockage existants.</span><span class="sxs-lookup"><span data-stu-id="82d60-p124">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account that contains only lowercase letters and numbers. You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

<span data-ttu-id="82d60-274">Utilisez cette commande pour vérifier si un nom proposé pour un compte de stockage est unique.</span><span class="sxs-lookup"><span data-stu-id="82d60-274">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="82d60-275">Pour créer un nouveau compte de stockage, exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="82d60-275">To create a new storage account, run these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="82d60-276">Ensuite, créez le réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="82d60-276">Next, you create the Azure virtual network.</span></span>
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="82d60-277">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="82d60-277">Here is your resulting configuration.</span></span>
  
![Le réseau virtuel n’est pas encore connecté au réseau local.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
<span data-ttu-id="82d60-279">Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="82d60-279">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

<span data-ttu-id="82d60-280">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="82d60-280">Here is your resulting configuration.</span></span>
  
![Le réseau virtuel dispose maintenant d’une passerelle.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
<span data-ttu-id="82d60-p125">Ensuite, configurez votre périphérique VPN local de sorte qu’il se connecte à la passerelle VPN Azure. Pour plus d’informations, reportez-vous à l’article [À propos des périphériques VPN pour les connexions du réseau virtuel Azure de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="82d60-p125">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [About VPN Devices for site-to-site Azure Virtual Network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="82d60-284">Pour configurer votre périphérique VPN, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="82d60-284">To configure your VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="82d60-p126">L’adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel. Utilisez la commande **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** pour afficher cette adresse.</span><span class="sxs-lookup"><span data-stu-id="82d60-p126">The public IPv4 address of the Azure VPN gateway for your virtual network. Use the **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** command to display this address.</span></span>
    
- <span data-ttu-id="82d60-287">La clé prépartagée IPsec pour la connexion VPN de site à site (Tableau V - Élément 5 - colonne Valeur).</span><span class="sxs-lookup"><span data-stu-id="82d60-287">The IPsec pre-shared key for the site-to-site VPN connection (Table V- Item 5 - Value column).</span></span>
    
<span data-ttu-id="82d60-288">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="82d60-288">Here is your resulting configuration.</span></span>
  
![Le réseau virtuel est désormais connecté au réseau local.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a><span data-ttu-id="82d60-290">Phase 3 (facultative) : ajouter des machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="82d60-290">Phase 3 (Optional): Add virtual machines</span></span>

<span data-ttu-id="82d60-p127">Créez les machines virtuelles dont vous avez besoin dans Azure. Pour plus d’informations, reportez-vous à [Créer votre première machine virtuelle Windows dans le portail Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span><span class="sxs-lookup"><span data-stu-id="82d60-p127">Create the virtual machines you need in Azure. For more information, see [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span>
  
<span data-ttu-id="82d60-293">Utilisez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="82d60-293">Use the following settings:</span></span>
  
- <span data-ttu-id="82d60-p128">Dans le volet **De base**, sélectionnez le même abonnement et le même groupe de ressources que votre réseau virtuel. Enregistrez le nom d’utilisateur et le mot de passe dans un emplacement sécurisé. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="82d60-p128">On the **Basics** pane, select the same subscription and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to sign in to the virtual machine.</span></span>
    
- <span data-ttu-id="82d60-297">Dans le volet **Taille**, choisissez la taille appropriée.</span><span class="sxs-lookup"><span data-stu-id="82d60-297">On the **Size** pane, choose the appropriate size.</span></span>
    
- <span data-ttu-id="82d60-p129">Dans le volet **Paramètres**, dans la section **Stockage**, sélectionnez le type de stockage **Standard** et le compte de stockage configuré avec votre réseau virtuel. Dans la section **Réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l’hébergement de machines virtuelles (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="82d60-p129">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type and the storage account set up with your virtual network. In the **Network** section, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="82d60-p130">Vérifiez que votre machine virtuelle utilise le DNS correctement en vérifiant votre DNS interne pour vous assurer que les enregistrements d’adresse (A) ont été ajoutés pour votre nouvelle machine virtuelle. Pour accéder à Internet, vos machines virtuelles Azure doivent être configurées pour utiliser le serveur proxy de votre réseau local. Contactez votre administrateur réseau pour les étapes de configuration supplémentaires à effectuer sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="82d60-p130">Verify that your virtual machine is using DNS correctly by checking your internal DNS to ensure that Address (A) records were added for you new virtual machine. To access the Internet, your Azure virtual machines must be configured to use your on-premises network's proxy server. Contact your network administrator for additional configuration steps to perform on the server.</span></span>
  
<span data-ttu-id="82d60-304">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="82d60-304">Here is your resulting configuration.</span></span>
  
![Le réseau virtuel héberge maintenant des machines virtuelles qui sont accessibles à partir du réseau local.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a><span data-ttu-id="82d60-306">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="82d60-306">Next step</span></span>
  
[<span data-ttu-id="82d60-307">Déployer la synchronisation d’annuaires (DirSync) Office 365 dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="82d60-307">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)
 


