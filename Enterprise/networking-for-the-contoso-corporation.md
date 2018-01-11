---
title: "Mise en réseau de Contoso Corporation"
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "Résumé : Comprendre la définition et les éléments du cloud hybride Microsoft."
ms.openlocfilehash: 0943864c8a9982eba00a139617ebe17d39cdde4e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="acb96-103">Mise en réseau de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="acb96-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="acb96-104">**Résumé :** Comprendre la définition et les éléments du cloud hybride Microsoft.</span><span class="sxs-lookup"><span data-stu-id="acb96-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="acb96-p101">Pour adopter une infrastructure cloud-inclus, les ingénieurs réseau de Contoso réalisé le changement fondamental dans la manière dont le trafic réseau vers les voyages de services en nuage. Au lieu de n’optimiser le trafic vers les serveurs locaux et des centres de données, égale de veiller à l’optimisation du trafic vers le bord de l’Internet et via Internet.</span><span class="sxs-lookup"><span data-stu-id="acb96-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="acb96-107">Infrastructure du réseau de Contoso</span><span class="sxs-lookup"><span data-stu-id="acb96-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="acb96-108">Contoso possède l’infrastructure réseau illustrée dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="acb96-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="acb96-109">**Figure 1 : Infrastructure de réseau étendu de Contoso**</span><span class="sxs-lookup"><span data-stu-id="acb96-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Infrastructure WAN de Contoso faisant la liaison avec les sièges sociaux, les centres régionaux et les succursales](images/Contoso_Poster/Contoso_WW_Net.png)
  
<span data-ttu-id="acb96-111">La Figure 1 présente les bureaux internationaux de Contoso et les connexions WAN qui relient les centres régionaux et les succursales.</span><span class="sxs-lookup"><span data-stu-id="acb96-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="acb96-112">Le réseau de Contoso comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="acb96-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="acb96-113">Réseau local</span><span class="sxs-lookup"><span data-stu-id="acb96-113">On-premises network</span></span>
    
    <span data-ttu-id="acb96-p102">Liaisons WAN connectent le siège social de Paris à des filiales et bureaux régionaux vers des bureaux satellites dans une configuration spoke and hub. Dans chaque bureau, les routeurs acheminer du trafic vers les hôtes ou les points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.</span><span class="sxs-lookup"><span data-stu-id="acb96-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="acb96-116">Connexion à Internet</span><span class="sxs-lookup"><span data-stu-id="acb96-116">Internet connectivity</span></span>
    
    <span data-ttu-id="acb96-p103">Chaque bureau a sa propre connexion à Internet via un serveur proxy. Cela est généralement implémenté comme un WAN lien vers un fournisseur de services Internet local qui fournit également des adresses IP publiques pour le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="acb96-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="acb96-119">Présence sur Internet</span><span class="sxs-lookup"><span data-stu-id="acb96-119">Internet presence</span></span>
    
    <span data-ttu-id="acb96-p104">Contoso possède le nom de domaine public de contoso.com. Le site web public de Contoso pour commander des produits est un ensemble de serveurs dans un centre de données connecté à Internet dans le campus de Paris. Contoso utilise un /24 plage d’adresses IP publique sur Internet.</span><span class="sxs-lookup"><span data-stu-id="acb96-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="acb96-123">Infrastructure d’application de Contoso</span><span class="sxs-lookup"><span data-stu-id="acb96-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="acb96-124">Contoso a conçu son infrastructure de serveur et d’application pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="acb96-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="acb96-125">**Figure 2 : Infrastructure de Contoso pour applications internes**</span><span class="sxs-lookup"><span data-stu-id="acb96-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Infrastructure des applications internes de Contoso](images/Contoso_Poster/App_Infra.png)
  
- <span data-ttu-id="acb96-127">Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.</span><span class="sxs-lookup"><span data-stu-id="acb96-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="acb96-p105">Concentrateurs régionaux utilisent les serveurs régionaux application régional et les bureaux satellites. Ces serveurs se synchronisent avec des serveurs au siège de Paris.</span><span class="sxs-lookup"><span data-stu-id="acb96-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="acb96-130">Le site de Paris comporte les centres de données contenant les serveurs d’applications centralisés qui servent l’organisation entière.</span><span class="sxs-lookup"><span data-stu-id="acb96-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="acb96-p106">Pour les utilisateurs des centres régionaux et des succursales, 60 % des ressources requises par les collaborateurs peuvent être prises en charge par les serveurs de ces sites. Les 40 % des demandes de ressources restantes doivent accéder au siège social parisien par le biais d’une connexion WAN.</span><span class="sxs-lookup"><span data-stu-id="acb96-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="acb96-133">Analyse du réseau de Contoso</span><span class="sxs-lookup"><span data-stu-id="acb96-133">Contoso's network analysis</span></span>

<span data-ttu-id="acb96-134">Voici les résultats de l’analyse de Contoso des modifications nécessaires sur leur réseau pour s’adapter à différentes catégories d’offres en nuage de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="acb96-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="acb96-135">**Les offres en nuage SaaS : Office 365, EMS et Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="acb96-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="acb96-136">**PaaS Azure : Les applications mobiles**</span><span class="sxs-lookup"><span data-stu-id="acb96-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="acb96-137">**IaaS Azure : Charges de travail serveur**</span><span class="sxs-lookup"><span data-stu-id="acb96-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="acb96-138">Adoption réussie de services SaaS par utilisateurs dépend hautement disponible et performante la connectivité à Internet, ou directement aux services de cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="acb96-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="acb96-139">Pour les utilisateurs mobiles, leur accès à Internet en cours est supposé pour être suffisante.</span><span class="sxs-lookup"><span data-stu-id="acb96-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="acb96-140">Pour les utilisateurs de l’intranet de Contoso, chaque bureau doit être analysé et optimisée pour le débit à Internet et de la durée des boucles avec le centre de données européen de Microsoft hébergeant les locataires Office 365, EMS et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="acb96-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="acb96-p107">Pour mieux accompagner les collaborateurs mobiles, des applications héritées et certains sites de partage de fichiers sont repensés et déployés en tant qu’applications Azure PaaS. Pour optimiser ses performances, Contoso prévoit de déployer de nouvelles applications dans le monde entier à partir de différents centres de données Azure. Azure Traffic Manager permet d’envoyer des demandes d’application cliente, qu’elles proviennent d’un utilisateur mobile ou d’un ordinateur situé dans un bureau, vers le centre de données Azure le plus proche hébergeant l’application.</span><span class="sxs-lookup"><span data-stu-id="acb96-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="acb96-144">Le service informatique doit ajouter PaaS les performances des applications et la distribution du trafic à leur solution de surveillance de la santé de réseau.</span><span class="sxs-lookup"><span data-stu-id="acb96-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="acb96-145">Pour déplacer certains serveurs hérités et archivage sur les centres de données campus Paris et ajouter les serveurs selon les besoins pour le traitement de fin de trimestre, Contoso veut utiliser des ordinateurs virtuels en cours d’exécution dans les services d’infrastructure Azure.</span><span class="sxs-lookup"><span data-stu-id="acb96-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="acb96-146">Les réseaux virtuels Azure qui contiennent ces serveurs doivent être conçus pour les espaces d’adressage non superposées, DNS et de routage intégré.</span><span class="sxs-lookup"><span data-stu-id="acb96-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="acb96-147">Le service informatique doit inclure ces nouveaux serveurs dans son système de gestion et de surveillance réseau.</span><span class="sxs-lookup"><span data-stu-id="acb96-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="acb96-148">Utilisation de Contoso de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="acb96-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="acb96-p108">ExpressRoute est une connexion WAN dédiée à partir de votre emplacement dans un emplacement d’homologation Microsoft qui connecte votre réseau pour le réseau de nuage de Microsoft. ExpressRoute les connexions offrent des performances prévisibles et une disponibilité de 99,9 % SLA. .</span><span class="sxs-lookup"><span data-stu-id="acb96-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="acb96-p109">Avec une connexion ExpressRoute, vous êtes connecté au réseau Microsoft cloud et à tous les emplacements de centre de données de Microsoft dans le même continent. Le trafic entre l’emplacement d’homologation cloud et le centre de données de Microsoft de destination est exécuté sur le réseau de nuage Microsoft</span><span class="sxs-lookup"><span data-stu-id="acb96-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="acb96-154">**Figure 3 : Le nuage réseau Microsoft dans le monde entier**</span><span class="sxs-lookup"><span data-stu-id="acb96-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![Réseau cloud mondial de Microsoft](images/Contoso_Poster/MS_WW_Cloud.png)
  
<span data-ttu-id="acb96-156">La Figure 3 montre le réseau cloud interconnecté de Microsoft pour les différentes régions du monde.</span><span class="sxs-lookup"><span data-stu-id="acb96-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="acb96-p110">Avec ExpressRoute Premium, vous pouvez atteindre tous les centres de données Microsoft sur tous les continents à partir de n’importe quel emplacement d’homologation Microsoft situé sur un des continents. Le trafic entre les continents est réalisé sur le réseau cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="acb96-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="acb96-159">Basée sur l’analyse du trafic en cours et à venir pour les offres en nuage de Microsoft, Contoso a effectué une évaluation du réseau et mise en œuvre d’une connexion (basés sur MPLS) de ExpressRoute à tout pour accéder aux ressources d’Azure, avec l’homologation de privés et publics relations, à partir du siège social de Paris à l’emplacement d’homologation Microsoft en Europe.</span><span class="sxs-lookup"><span data-stu-id="acb96-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="acb96-160">Cette connexion apportera au service informatique de Contoso :</span><span class="sxs-lookup"><span data-stu-id="acb96-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="acb96-161">Des performances cohérentes pour l’administration des applications Azure PaaS réparties</span><span class="sxs-lookup"><span data-stu-id="acb96-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="acb96-p111">Tous les développeurs d’applications et de l ' infrastructure informatique de Contoso administrateurs sont dans le campus de Paris. Avec les applications Azure PaaS distribuées aux différents centres de données Azure dans le monde entier, Contoso a besoin de performances cohérentes à partir du campus de Paris pour gérer les applications et leurs ressources de stockage, qui se composent de To de documents.</span><span class="sxs-lookup"><span data-stu-id="acb96-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="acb96-164">Des performances cohérentes pour l’administration des serveurs dans Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="acb96-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="acb96-p112">Les administrateurs du centre de données de Contoso se trouvent dans le campus de Paris et les serveurs pour être déployé dans Azure sont une extension du centre de données de Paris. Contoso a besoin de performances cohérentes vers ces nouveaux serveurs pour accéder aux applications héritées et le stockage d’archivage et de traitement de fin de trimestre.</span><span class="sxs-lookup"><span data-stu-id="acb96-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="acb96-167">Chemin d’accès de Contoso cloud la disponibilité du réseau</span><span class="sxs-lookup"><span data-stu-id="acb96-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="acb96-168">Contoso a établi la procédure suivante pour préparer son réseau au cloud de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="acb96-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="acb96-169">Optimiser les ordinateurs des employés pour l’accès Internet</span><span class="sxs-lookup"><span data-stu-id="acb96-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="acb96-170">Les ordinateurs individuels sont vérifiés pour assurer que les ressources les plus récentes (pile TCP/IP, navigateur, pilotes de carte réseau, mises à jour de sécurité et du système d’exploitation) sont bien installées.</span><span class="sxs-lookup"><span data-stu-id="acb96-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="acb96-171">Analyser l’utilisation de la connexion Internet dans chaque bureau et apporter des ressources supplémentaires selon les besoins</span><span class="sxs-lookup"><span data-stu-id="acb96-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="acb96-172">Chaque bureau est analysée pour l’utilisation d’Internet en cours et augmente la bande passante de la liaison réseau étendu si fonctionne sur 70 % ou au-dessus de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="acb96-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="acb96-173">Analyser les systèmes DMZ dans chaque bureau pour des performances optimales</span><span class="sxs-lookup"><span data-stu-id="acb96-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="acb96-p113">Une analyse des pare-feu, IDS et autres systèmes connectés à Internet a lieu pour garantir des performances optimales. Les serveurs proxy sont mis à jour ou à niveau selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="acb96-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="acb96-176">Ajouter ExpressRoute au site parisien</span><span class="sxs-lookup"><span data-stu-id="acb96-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="acb96-177">Offre un accès cohérent aux ressources Azure pour administrer les charges de travail Azure PaaS et IaaS.</span><span class="sxs-lookup"><span data-stu-id="acb96-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="acb96-178">Créer et tester un profil Azure Traffic Manager pour les applications Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="acb96-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="acb96-179">Tester un profil Azure Traffic Manager utilisant la méthode de routage des performances afin d’expérimenter la répartition du trafic Internet vers les sites régionaux.</span><span class="sxs-lookup"><span data-stu-id="acb96-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="acb96-180">Réserver de l’espace d’adresses privées pour Azure VNets</span><span class="sxs-lookup"><span data-stu-id="acb96-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="acb96-181">Se baser sur les chiffres des serveurs à court terme et long terme planifiés dans Azure IaaS pour réserver l’espace d’adressage privé aux réseaux virtuels Azure et à leurs sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="acb96-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="acb96-182">See Also</span><span class="sxs-lookup"><span data-stu-id="acb96-182">See Also</span></span>

[<span data-ttu-id="acb96-183">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="acb96-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="acb96-184">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="acb96-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="acb96-185">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="acb96-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



