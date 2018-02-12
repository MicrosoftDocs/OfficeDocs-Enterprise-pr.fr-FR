---
title: "ExpressRoute pour la connectivité au cloud de Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: "Résumé : Comprendre comment ExpressRoute peut garantir des connexions plus fiables et plus rapides aux services et aux plateformes cloud de Microsoft."
ms.openlocfilehash: 40cde8753a5e6de6a76a04198fe90d510ee9a315
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="bbb75-103">ExpressRoute pour la connectivité au cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbb75-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="bbb75-104">**Résumé :** Comprendre comment ExpressRoute peut garantir des connexions plus fiables et plus rapides aux services et aux plateformes cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="bbb75-105">ExpressRoute fournit une connexion réseau privée dédiée à haut débit au cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="bbb75-106">ExpressRoute vers le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbb75-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="bbb75-107">Voici le chemin d’accès au réseau sur le cloud de Microsoft sans connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bbb75-108">**Figure 1 : chemin de mise en réseau sans ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="bbb75-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figure 1 : chemin de mise en réseau sans ExpressRoute](images/Network_Poster/ExpressRoute.png)
  
<span data-ttu-id="bbb75-p101">La figure 1 présente le chemin d'accès standard entre un réseau local et le cloud de Microsoft. Le périmètre du réseau local se connecte à Internet via un lien WAN vers un fournisseur de services Internet. Ensuite, le trafic circule à travers Internet vers le périmètre cloud de Microsoft. Les offres de cloud au sein du cloud de Microsoft incluent Office 365, Microsoft Azure, Microsoft Intune et Dynamics 365. Les utilisateurs d'une organisation peuvent se trouver sur le réseau local ou sur Internet.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="bbb75-115">Sans une connexion ExpressRoute, la seule partie du chemin d’accès au trafic vers le cloud de Microsoft que vous pouvez contrôler (et ayant une relation avec le fournisseur de services) est le lien entre le périmètre du réseau local et votre fournisseur de services Internet.</span><span class="sxs-lookup"><span data-stu-id="bbb75-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="bbb75-116">Le chemin d’accès entre votre fournisseur de services Internet et le périmètre du cloud de Microsoft représente le système de remise optimal sur Internet soumis à des interruptions, à des congestions du trafic et à la surveillance par des utilisateurs malveillants.</span><span class="sxs-lookup"><span data-stu-id="bbb75-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="bbb75-117">Les utilisateurs sur Internet, tels que les utilisateurs itinérants ou distants, envoient leur trafic vers le cloud de Microsoft via Internet.</span><span class="sxs-lookup"><span data-stu-id="bbb75-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="bbb75-118">Voici les chemins d’accès au réseau vers le cloud de Microsoft avec une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bbb75-119">**Figure 2 : chemins de mise en réseau avec ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="bbb75-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figure 2 : chemins d’accès au réseau avec ExpressRoute](images/Network_Poster/ExpressRoute_post.png)
  
<span data-ttu-id="bbb75-p102">La figure 2 présente deux chemins d’accès au réseau. Le trafic vers Microsoft Intune utilise le même chemin que le trafic Internet normal. Le trafic vers Office 365, Microsoft Azure et Dynamics  365 circule à travers la connexion ExpressRoute, un chemin d’accès dédié entre le périmètre du réseau local et le périmètre du cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="bbb75-p103">Avec une connexion ExpressRoute, vous contrôlez désormais le chemin d’accès au trafic dans son intégralité, de votre périmètre jusqu’au périmètre du cloud de Microsoft, grâce à une relation avec votre fournisseur de services. Cette connexion peut offrir des performances prévisibles et un SLA de disponibilité de 99,9 %.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a 99.9% uptime SLA.</span></span>
  
<span data-ttu-id="bbb75-p104">Vous pouvez maintenant compter sur un débit et une latence prévisibles, en fonction de la connexion de votre fournisseur de services, pour les services Office 365, Azure et Dynamics 365. Les connexions ExpressRoute à Microsoft Intune ne sont pas prises en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="bbb75-128">Le trafic transmis par la connexion ExpressRoute n’est plus soumis aux interruptions Internet, aux congestions du trafic et à la surveillance.</span><span class="sxs-lookup"><span data-stu-id="bbb75-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="bbb75-p105">Les utilisateurs sur Internet, tels que les utilisateurs itinérants ou distants, envoient toujours leur le trafic vers le cloud de Microsoft via Internet. Une exception existe pour le trafic vers une ligne intranet d’une application métier hébergée dans Azure IaaS, qui est transmis par la connexion ExpressRoute via une connexion d’accès à distance au réseau local.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="bbb75-131">Même avec une connexion ExpressRoute, le trafic est toujours transmis par Internet, comme les requêtes DNS, la vérification de la liste de révocation de certificats et les demandes de réseau de distribution de contenu (CDN).</span><span class="sxs-lookup"><span data-stu-id="bbb75-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="bbb75-132">Consultez les ressources supplémentaires suivantes pour plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="bbb75-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="bbb75-133">ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="bbb75-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="bbb75-134">ExpressRoute pour Azure</span><span class="sxs-lookup"><span data-stu-id="bbb75-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="bbb75-135">Avantages d’ExpressRoute pour Azure</span><span class="sxs-lookup"><span data-stu-id="bbb75-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="bbb75-136">Voici quelques avantages liés à l’utilisation des services cloud basés sur ExpressRoute pour Azure :</span><span class="sxs-lookup"><span data-stu-id="bbb75-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="bbb75-p106">**Performances prévisibles :** Avec un chemin d'accès dédié vers le périmètre du cloud de Microsoft, vos performances ne sont pas soumises aux interruptions du fournisseur Internet et aux pics du trafic Internet. Vous pouvez déterminer un SLA concernant le débit et la latence vers le cloud de Microsoft dont vos fournisseurs seront tenus responsables.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="bbb75-p107">**Confidentialité des données de votre trafic :** Le trafic transmis via votre connexion ExpressRoute dédiée n'est pas soumis à la surveillance Internet ou à la capture de paquet et à l'analyse par des utilisateurs malveillants. Il est aussi sécurisé que les liens WAN basés sur la fonctionnalité MPLS (Multiprotocol Label Switching).</span><span class="sxs-lookup"><span data-stu-id="bbb75-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="bbb75-141">**Connexions à haut débit :** Avec l'importante prise en charge des connexions ExpressRoute par les fournisseurs d'échange et les fournisseurs de services de réseau, vous pouvez obtenir un lien de 10 Gbits/s au maximum dans le cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="bbb75-142">**Coût moins élevé pour certaines configurations :** Bien que les connexions ExpressRoute représentent un coût supplémentaire, dans certains cas, une seule connexion ExpressRoute peut constituer un coût moins élevé que l'augmentation de votre capacité Internet dans plusieurs emplacements de votre organisation afin de fournir un débit suffisant pour les services cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="bbb75-p108">Une connexion ExpressRoute ne garantit pas de meilleures performances dans chaque configuration. Il est possible d’avoir des performances inférieures en utilisant une connexion ExpressRoute avec une faible bande passante au lieu d’une connexion Internet avec une bande passante élevée qui se trouve seulement à quelques sauts d’un centre de données Microsoft régional.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="bbb75-145">Pour obtenir les dernières recommandations sur l'utilisation d'ExpressRoute avec Office 365, voir [ExpressRoute pour Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="bbb75-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="bbb75-146">Modèles de connectivité ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bbb75-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="bbb75-147">Le tableau 1 affiche les trois principaux modèles de connectivité pour les connexions ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="bbb75-148">**Même emplacement au niveau d'un échange de cloud**</span><span class="sxs-lookup"><span data-stu-id="bbb75-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="bbb75-149">**Ethernet de point à point**</span><span class="sxs-lookup"><span data-stu-id="bbb75-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="bbb75-150">**Connectivité complète (IP VPN)**</span><span class="sxs-lookup"><span data-stu-id="bbb75-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modèle de connectivité ExpressRoute : même emplacement au niveau d’un échange de cloud](images/Network_Poster/ER_Conn1.png)|![Modèle de connectivité ExpressRoute : ethernet de point à point](images/Network_Poster/ER_Conn2.png)|![Modèle de connectivité ExpressRoute : Connectivité complète (IP VPN)](images/Network_Poster/ER_Conn3.png)|
|<span data-ttu-id="bbb75-154">Si votre centre de données se trouve au même emplacement dans une installation comprenant un échange de cloud, vous pouvez organiser une connexion croisée virtuelle au cloud de Microsoft via l’échange Ethernet du fournisseur de la colocalisation.</span><span class="sxs-lookup"><span data-stu-id="bbb75-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="bbb75-155">Si votre centre de données se trouve sur votre site, vous pouvez utiliser une liaison Ethernet de point à point pour vous connecter au cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="bbb75-156">Si vous utilisez déjà un fournisseur IP VPN (MPLS) pour connecter les sites de votre organisation, une connexion ExpressRoute au cloud de Microsoft fonctionnera comme un autre emplacement sur votre réseau étendu privé.</span><span class="sxs-lookup"><span data-stu-id="bbb75-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="bbb75-157">**Tableau 1 : Modèles de connectivité ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="bbb75-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="bbb75-158">Relations d’homologation ExpressRoute avec les services cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbb75-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="bbb75-p109">Une seule connexion ExpressRoute prend en charge jusqu'à trois relations d’homologation de protocole de passerelle frontière (BGP) avec les différentes parties du cloud de Microsoft. BPG utilise les relations d’homologation afin d’établir l’approbation et d’échanger des informations de routage.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="bbb75-161">**Figure 3 : Les trois relations BGP dans une seule connexion ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="bbb75-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![Figure 3 : trois relations BGP différentes dans une seule connexion ExpressRoute](images/Network_Poster/ERPeering.png)
  
<span data-ttu-id="bbb75-p110">La figure 3 illustre une connexion ExpressRoute à partir d’un réseau local. La connexion ExpressRoute contient trois relations d’homologation logiques. Une relation d’homologation Microsoft accède aux services Microsoft SaaS, y compris Office 365 et Dynamics CRM Online. Une relation d’homologation publique accède aux services Azure PaaS. Une relation d’homologation privée accède à Azure IaaS et à une passerelle de réseau virtuel qui héberge des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection contains three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="bbb75-168">Relation BGP d’homologation de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="bbb75-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="bbb75-169">Représente un routeur dans votre zone DMZ vers les adresses publiques des services Office 365 et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="bbb75-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="bbb75-170">Prend en charge la communication initiée de manière bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="bbb75-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="bbb75-171">Relation BGP d’homologation publique :</span><span class="sxs-lookup"><span data-stu-id="bbb75-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="bbb75-172">Provient d’un routeur dans votre zone DMZ et se dirige vers les adresses IP publiques des services Azure.</span><span class="sxs-lookup"><span data-stu-id="bbb75-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="bbb75-p111">Prend uniquement en charge la communication initiée de manière bidirectionnelle à partir des systèmes locaux. La relation d’homologation ne prend pas en charge la communication initiée à partir de services Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="bbb75-175">Relation BGP d’homologation privée :</span><span class="sxs-lookup"><span data-stu-id="bbb75-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="bbb75-176">Provient d’un routeur situé sur le périmètre du réseau de votre organisation et se dirige vers les adresses IP privées attribuées à Azure VNets.</span><span class="sxs-lookup"><span data-stu-id="bbb75-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="bbb75-177">Prend en charge la communication initiée de manière bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="bbb75-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="bbb75-178">Est une extension du réseau de votre organisation vers le cloud de Microsoft, comprenant un adressage et un routage cohérents en interne.</span><span class="sxs-lookup"><span data-stu-id="bbb75-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="bbb75-179">Exemple de déploiement d’application et de flux de trafic avec ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bbb75-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="bbb75-p112">La manière dont le trafic circule à travers les connexions ExpressRoute et au sein du cloud de Microsoft est une fonction des itinéraires au niveau des sauts du chemin d’accès entre la source et la destination et le comportement de l’application. Voici un exemple d’application en cours d’exécution sur une machine virtuelle Azure qui accède à une batterie de serveurs SharePoint locale sur une connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="bbb75-182">**Figure 4 : application sur une machine virtuelle Azure accédant à une batterie de serveurs SharePoint locale**</span><span class="sxs-lookup"><span data-stu-id="bbb75-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figure 4 : application sur une machine virtuelle Azure accédant à une batterie de serveurs SharePoint locale](images/Network_Poster/ER_App_Flow1.png)

  
<span data-ttu-id="bbb75-184">La figure 4 montre une batterie de serveurs SharePoint locale, une connexion VPN de site à site entre le réseau local et un réseau virtuel dans Azure IaaS, un serveur d’applications exécuté en tant que machine virtuelle Azure IaaS et le flux de trafic entre le serveur d’applications et la batterie de serveurs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bbb75-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="bbb75-185">L’application localise l’adresse IP de la batterie de serveurs SharePoint à l’aide du DNS local et tout le trafic bascule sur la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="bbb75-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="bbb75-186">Cette organisation a migré sa batterie de serveurs SharePoint locale vers SharePoint Online dans Office 365 et a déployé une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bbb75-187">**Figure 5 : Déplacement de la batterie de serveurs SharePoint locale vers SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="bbb75-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figure 5 : déplacement de la batterie de serveurs SharePoint locale vers SharePoint Online](images/Network_Poster/Hairpin1.png)
  
<span data-ttu-id="bbb75-p113">La figure 5 indique l’ajout d’une connexion ExpressRoute avec des relations d’homologation à Microsoft SaaS, à Office 365 et à Azure IaaS contenant le serveur d’applications sur un réseau virtuel. La batterie de serveurs SharePoint locale a été migrée vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="bbb75-191">Avec les relations d’homologation privées et de Microsoft, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bbb75-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="bbb75-192">À partir de la passerelle de réseau virtuel Azure, les emplacements locaux sont disponibles sur la connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bbb75-193">À partir de l’abonnement à Office 365, les adresses IP publiques des périphériques de périmètre, tels que les serveurs proxy, sont disponibles sur la connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bbb75-194">À partir du périmètre du réseau local, les adresses IP privées d’Azure VNet et les adresses IP publiques d’Office 365 sont disponibles sur la connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="bbb75-195">Lorsque l’application accède aux URL de SharePoint Online, elle transfère son trafic sur la connexion ExpressRoute à un serveur proxy du périmètre.</span><span class="sxs-lookup"><span data-stu-id="bbb75-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="bbb75-p114">Lorsque le serveur proxy localise l’adresse IP de SharePoint Online, il transfère à nouveau le trafic sur la connexion ExpressRoute. Le trafic de réponse utilise le chemin d’accès inverse.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="bbb75-198">**Figure 6 flux de trafic lorsque la batterie de serveurs SharePoint a été migrée vers SharePoint Online dans Office 365**</span><span class="sxs-lookup"><span data-stu-id="bbb75-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figure 6 flux de trafic lorsque la batterie de serveurs SharePoint a été migrée vers SharePoint Online dans Office 365](images/Network_Poster/Hairpin2.png)

  
<span data-ttu-id="bbb75-200">La figure 6 indique comment le trafic entre le serveur d'applications et SharePoint Online dans Office 365 circule sur la relation d'homologation privée à partir du serveur d'applications vers le périmètre du réseau local, puis à partir du périmètre sur la relation d'homologation Microsoft vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="bbb75-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="bbb75-201">Le résultat est un branchement en épingle en raison du routage et du comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="bbb75-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="bbb75-202">ExpressRoute et réseau cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbb75-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="bbb75-203">Les connexions ExpressRoute sont disponibles dans deux versions différentes : ExpressRoute et ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="bbb75-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="bbb75-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bbb75-204">ExpressRoute</span></span>

<span data-ttu-id="bbb75-205">La manière dont le trafic se déplace entre le réseau de votre organisation et un centre de données Microsoft constitue une combinaison des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="bbb75-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="bbb75-206">Vos emplacements.</span><span class="sxs-lookup"><span data-stu-id="bbb75-206">Your locations.</span></span>
    
- <span data-ttu-id="bbb75-207">Emplacements d’homologation cloud de Microsoft (emplacements physiques pour se connecter au périmètre de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="bbb75-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="bbb75-208">Emplacements du centre de données Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="bbb75-209">Le centre de données Microsoft et les emplacements d’homologation cloud sont tous connectés au réseau cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bbb75-p115">Lorsque vous créez une connexion ExpressRoute vers un emplacement d'homologation cloud de Microsoft, vous êtes connecté au réseau cloud de Microsoft et à tous les emplacements de centre de données Microsoft sur le même continent. Le trafic entre l'emplacement d'homologation cloud et le centre de données Microsoft de destination est exécuté sur le réseau cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bbb75-212">Cela peut entraîner une remise non optimale dans les centres de données Microsoft locaux pour le modèle de connectivité complète.</span><span class="sxs-lookup"><span data-stu-id="bbb75-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="bbb75-213">**Figure 7 : Exemple d'une organisation géographiquement dispersée qui utilise une seule connexion ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="bbb75-213">**Figure 7: Example of an geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figure 7 : exemple d’une organisation géographiquement dispersée qui utilise une seule connexion ExpressRoute](images/Network_Poster/MSNet1.png)
  
<span data-ttu-id="bbb75-p116">La figure 7 illustre une organisation avec deux emplacements : l’emplacement 1 est situé dans le nord-ouest des États-Unis et l’emplacement 2 dans le nord-est du pays. Ils sont connectés par un fournisseur de réseau étendu complet. Cette organisation possède également une connexion ExpressRoute vers un emplacement d’homologation Microsoft sur la côte ouest. Le trafic de l’emplacement 2 dans le nord-est destiné à un centre de données de la côte est doit emprunter l’ensemble du réseau étendu de l’organisation jusqu’à la côte ouest où se trouve l’emplacement d’homologation Microsoft, puis traverser le pays sur le réseau cloud de Microsoft pour revenir au centre de données de la côte est.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="bbb75-219">Pour une remise optimale, utilisez plusieurs connexions ExpressRoute aux emplacements d’homologation cloud de Microsoft régionaux.</span><span class="sxs-lookup"><span data-stu-id="bbb75-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="bbb75-220">**Figure 8 : Utilisation de plusieurs connexions ExpressRoute pour un transfert optimal vers les centres de données régionaux**</span><span class="sxs-lookup"><span data-stu-id="bbb75-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figure 8 : utilisation de plusieurs connexions ExpressRoute pour remise optimale aux centres de données régionaux](images/Network_Poster/MSNet2.png)
  
<span data-ttu-id="bbb75-p117">La figure 8 montre la même organisation avec deux connexions ExpressRoute, une pour chaque emplacement, à des emplacements d'homologation Microsoft locaux à l'échelle de la région. Dans cette configuration, le trafic de l'emplacement 2 dans le nord-est destiné à un centre de données de la côte est accède directement à un emplacement d'homologation de la côte est, au réseau cloud de Microsoft, puis au centre de données de la côte est.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="bbb75-224">Plusieurs connexions ExpressRoute peuvent fournir les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="bbb75-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="bbb75-225">Meilleures performances pour les emplacements de centre de données Microsoft locaux à l’échelle de la région.</span><span class="sxs-lookup"><span data-stu-id="bbb75-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="bbb75-226">Disponibilité accrue dans le Microsoft Cloud lorsqu’une connexion ExpressRoute locale n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="bbb75-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="bbb75-p118">Cela fonctionne bien pour les organisations situées sur le même continent. Toutefois, le trafic vers les centres de données Microsoft à l'extérieur du continent de l'organisation utilise Internet.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="bbb75-229">Pour le trafic intercontinental sur le réseau cloud de Microsoft, vous devez utiliser des connexions ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="bbb75-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="bbb75-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="bbb75-230">ExpressRoute Premium</span></span>

<span data-ttu-id="bbb75-231">Pour les organisations qui sont dispersées mondialement sur tous les continents, vous pouvez utiliser ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="bbb75-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="bbb75-p119">Avec ExpressRoute Premium, vous pouvez atteindre tous les centres de données Microsoft sur tous les continents à partir de n’importe quel emplacement d’homologation Microsoft situé sur un des continents. Le trafic entre les continents est réalisé sur le réseau cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bbb75-234">Avec plusieurs connexions ExpressRoute Premium, vous pouvez avoir les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="bbb75-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="bbb75-235">Meilleures performances pour les centres de données Microsoft locaux à l’échelle des continents.</span><span class="sxs-lookup"><span data-stu-id="bbb75-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="bbb75-236">Disponibilité accrue dans le Microsoft Cloud global lorsqu’une connexion ExpressRoute locale n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="bbb75-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="bbb75-p120">ExpressRoute Premium est requis pour les connexions ExpressRoute basées sur Office 365. Toutefois, il n’existe aucun coût supplémentaire pour les entreprises ayant au moins 500 utilisateurs sous licence.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="bbb75-239">**Figure 9 : Réseau cloud mondial de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="bbb75-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figure 9 : réseau cloud mondial de Microsoft](images/Network_Poster/MSNet3.png)
  
<span data-ttu-id="bbb75-p121">La figure 9 représente un diagramme logique du réseau cloud mondial de Microsoft, avec des réseaux qui couvrent les continents et les régions du monde entier et leurs interconnexions. Avec une partie du réseau cloud de Microsoft sur chaque continent, une entreprise présente à l’échelle mondiale crée des connexions ExpressRoute Premium aux emplacements d’homologation Microsoft locaux à partir de ses bureaux régionaux.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="bbb75-243">Pour un bureau régional, attribuez le trafic Office 365 aux centres de données suivants :</span><span class="sxs-lookup"><span data-stu-id="bbb75-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="bbb75-244">Les centres de données Office 365 continentaux utilisent le réseau cloud Microsoft du continent.</span><span class="sxs-lookup"><span data-stu-id="bbb75-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="bbb75-245">Les centres de données Office 365 sur un autre continent utilisent sur le réseau cloud de Microsoft intercontinental.</span><span class="sxs-lookup"><span data-stu-id="bbb75-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="bbb75-246">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="bbb75-246">For more information, see:</span></span>
  
- [<span data-ttu-id="bbb75-247">Azure ExpressRoute for Office 365 Training</span><span class="sxs-lookup"><span data-stu-id="bbb75-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="bbb75-248">Planification réseau et optimisation des performances pour Office 365</span><span class="sxs-lookup"><span data-stu-id="bbb75-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="bbb75-249">Gestion des performances Office 365</span><span class="sxs-lookup"><span data-stu-id="bbb75-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/fr-FR/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="bbb75-250">Options ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bbb75-250">ExpressRoute options</span></span>

<span data-ttu-id="bbb75-251">Vous pouvez également intégrer les options suivantes dans votre déploiement ExpressRoute :</span><span class="sxs-lookup"><span data-stu-id="bbb75-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="bbb75-252">**Sécurité au niveau de votre périmètre :** pour fournir une sécurité avancée pour le trafic envoyé et reçu via la connexion ExpressRoute, comme l'inspection du trafic ou la détection des intrusions/programmes malveillants, placez vos appliances de sécurité dans le chemin d'accès au trafic au sein de la zone DMZ ou à la bordure de votre intranet.</span><span class="sxs-lookup"><span data-stu-id="bbb75-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="bbb75-p122">Trafic Internet pour les machines virtuelles : pour empêcher les machines virtuelles Azure de lancer le trafic directement avec des emplacements sur Internet, annoncez l'itinéraire par défaut à Microsoft. Le trafic vers Internet est acheminé via la connexion ExpressRoute et vos serveurs proxy locaux. Le trafic provenant des machines virtuelles Azure et allant vers des services Azure PaaS ou Office 365 est réacheminé via la connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bbb75-p123">**Optimiseurs de réseau étendu :** Vous pouvez déployer des optimiseurs de réseau étendu sur les deux côtés d'une connexion d'homologation privée pour un réseau virtuel (VNet) Azure entre différents locaux. À l'intérieur du réseau virtuel Azure, utilisez une appliance de réseau d'optimiseur de réseau étendu à partir d'Azure Marketplace et un routage défini par l'utilisateur pour router le trafic via l'équipement.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="bbb75-p124">**Qualité de service :** Utilisez des valeurs DSCP (Differentiated Services Code Point) dans l'en-tête IPv4 de votre trafic afin de le marquer pour remise vocale, vidéo/interactive ou optimale. Ceci est particulièrement important pour la relation d'homologation Microsoft et le trafic Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="bbb75-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="bbb75-260">Consultez les ressources supplémentaires suivantes pour plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="bbb75-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="bbb75-261">ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="bbb75-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="bbb75-262">Azure ExpressRoute for Office 365 Training</span><span class="sxs-lookup"><span data-stu-id="bbb75-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="bbb75-263">ExpressRoute pour Azure</span><span class="sxs-lookup"><span data-stu-id="bbb75-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="bbb75-264">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="bbb75-264">Next step</span></span>

[<span data-ttu-id="bbb75-265">Conception de réseaux pour Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="bbb75-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="bbb75-266">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbb75-266">See also</span></span>

[<span data-ttu-id="bbb75-267">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="bbb75-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="bbb75-268">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbb75-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bbb75-269">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="bbb75-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



