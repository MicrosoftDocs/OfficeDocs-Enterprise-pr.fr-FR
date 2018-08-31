---
title: Mise en réseau de Contoso Corporation
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
description: 'Résumé : Découvrez l’infrastructure du réseau Contoso et comment il peut utiliser ExpressRoute pour un accès optimisé pour les offres de cloud de Microsoft.'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915219"
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="59e45-103">Mise en réseau de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="59e45-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="59e45-104">**Résumé :** Comprendre l’infrastructure du réseau Contoso et comment il peut utiliser ExpressRoute pour un accès optimisé pour les offres de cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59e45-104">**Summary:** Understand the Contoso networking infrastructure and how it can use ExpressRoute for optimized acccess to Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="59e45-p101">Pour adopter une infrastructure cloud-inclus, les ingénieurs réseau de Contoso réalisé le changement fondamental dans la façon dont le trafic réseau vers le déplacement des services en nuage. Au lieu d’optimisation uniquement le trafic vers les serveurs locaux et des centres de données, égale veiller à optimiser le trafic sur le bord Internet et sur Internet.</span><span class="sxs-lookup"><span data-stu-id="59e45-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="59e45-107">Infrastructure du réseau de Contoso</span><span class="sxs-lookup"><span data-stu-id="59e45-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="59e45-108">Contoso possède l’infrastructure réseau illustrée dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="59e45-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="59e45-109">**Figure 1 : infrastructure WAN de Contoso**</span><span class="sxs-lookup"><span data-stu-id="59e45-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Infrastructure WAN de Contoso faisant la liaison avec les sièges sociaux, les centres régionaux et les succursales](media/Contoso-Poster/Contoso-WW-Net.png)
  
<span data-ttu-id="59e45-111">La Figure 1 présente les bureaux internationaux de Contoso et les connexions WAN qui relient les centres régionaux et les succursales.</span><span class="sxs-lookup"><span data-stu-id="59e45-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="59e45-112">Le réseau de Contoso comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="59e45-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="59e45-113">Réseau local</span><span class="sxs-lookup"><span data-stu-id="59e45-113">On-premises network</span></span>
    
    <span data-ttu-id="59e45-p102">Liaisons WAN connectent le siège social Paris à des bureaux régionaux et les bureaux régionaux aux filiales dans une configuration spoke and hub. Dans chaque bureau, routeurs acheminer du trafic vers les hôtes ou les points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.</span><span class="sxs-lookup"><span data-stu-id="59e45-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="59e45-116">Connexion à Internet</span><span class="sxs-lookup"><span data-stu-id="59e45-116">Internet connectivity</span></span>
    
    <span data-ttu-id="59e45-p103">Chaque bureau a sa propre connectivité Internet via un serveur proxy. Cela est généralement implémenté comme un réseau étendu un lien vers un fournisseur d’accès local qui fournit également des adresses IP publiques pour le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="59e45-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="59e45-119">Présence sur Internet</span><span class="sxs-lookup"><span data-stu-id="59e45-119">Internet presence</span></span>
    
    <span data-ttu-id="59e45-p104">Contoso possède le nom de domaine public contoso.com. Le site web public de Contoso pour le classement des produits est un ensemble de serveurs dans un centre de données connectés à Internet dans le campus Paris. Contoso utilise un /24 plage d’adresses IP publique sur Internet.</span><span class="sxs-lookup"><span data-stu-id="59e45-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="59e45-123">Infrastructure d’application de Contoso</span><span class="sxs-lookup"><span data-stu-id="59e45-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="59e45-124">Contoso a conçu son infrastructure d’applications et serveur pour les éléments suivants :



</span><span class="sxs-lookup"><span data-stu-id="59e45-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="59e45-125">**Figure 2 : infrastructure des applications internes de Contoso**</span><span class="sxs-lookup"><span data-stu-id="59e45-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Infrastructure des applications internes de Contoso](media/Contoso-Poster/App-Infra.png)
  
- <span data-ttu-id="59e45-127">Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.</span><span class="sxs-lookup"><span data-stu-id="59e45-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="59e45-p105">
Les centres régionaux utilisent les serveurs d’applications régionaux pour les bureaux régionaux et les succursales. Ces serveurs se synchronisent avec les serveurs du siège social parisien.</span><span class="sxs-lookup"><span data-stu-id="59e45-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="59e45-130">Le site de Paris comporte les centres de données contenant les serveurs d’applications centralisés qui servent l’organisation entière.</span><span class="sxs-lookup"><span data-stu-id="59e45-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="59e45-p106">Pour les utilisateurs des centres régionaux et des succursales, 60 % des ressources requises par les collaborateurs peuvent être prises en charge par les serveurs de ces sites. Les 40 % des demandes de ressources restantes doivent accéder au siège social parisien par le biais d’une connexion WAN.</span><span class="sxs-lookup"><span data-stu-id="59e45-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="59e45-133">Analyse du réseau de Contoso</span><span class="sxs-lookup"><span data-stu-id="59e45-133">Contoso's network analysis</span></span>

<span data-ttu-id="59e45-134">Voici les résultats d’analyse de Contoso des modifications nécessaires sur leur réseau pour prendre en charge les différentes catégories d’offres de cloud de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="59e45-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="59e45-135">**Offres de cloud SaaS : Office 365, EMS et Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="59e45-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="59e45-136">**PaaS Azure : Applications mobiles**</span><span class="sxs-lookup"><span data-stu-id="59e45-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="59e45-137">**Azure IaaS : Charges de travail sur le serveur**</span><span class="sxs-lookup"><span data-stu-id="59e45-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="59e45-138">L’adoption réussie des services SaaS par les utilisateurs dépend de la haute disponibilité et des performances de la connectivité à Internet ou directement aux services cloud de Microsoft.
</span><span class="sxs-lookup"><span data-stu-id="59e45-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="59e45-139">L’accès Internet actuel est censé être satisfaisant pour les utilisateurs mobiles.
</span><span class="sxs-lookup"><span data-stu-id="59e45-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="59e45-140">Pour les utilisateurs sur l’intranet de Contoso, chaque bureau doit être analysé et optimisé pour le débit à Internet et au centre de données pour l’Europe de Microsoft qui héberge les clients Office 365, EMS et Dynamics 365 des boucles.</span><span class="sxs-lookup"><span data-stu-id="59e45-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="59e45-p107">Pour mieux accompagner les collaborateurs mobiles, des applications héritées et certains sites de partage de fichiers sont repensés et déployés en tant qu’applications Azure PaaS. Pour optimiser ses performances, Contoso prévoit de déployer de nouvelles applications dans le monde entier à partir de différents centres de données Azure. Azure Traffic Manager permet d’envoyer des demandes d’application cliente, qu’elles proviennent d’un utilisateur mobile ou d’un ordinateur situé dans un bureau, vers le centre de données Azure le plus proche hébergeant l’application.</span><span class="sxs-lookup"><span data-stu-id="59e45-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="59e45-144"> 

Le service informatique doit ajouter des performances d’application PaaS et la répartition du trafic à sa solution de contrôle d’intégrité du réseau.</span><span class="sxs-lookup"><span data-stu-id="59e45-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="59e45-145">Pour migrer les serveurs existants et les serveurs d’archivage hors des centres de données du siège social parisien et ajouter des serveurs selon les besoins en fin de trimestre, Contoso prévoit d’utiliser des machines virtuelles s’exécutant dans les services d’infrastructure Azure. 

</span><span class="sxs-lookup"><span data-stu-id="59e45-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="59e45-146">Les réseaux virtuels Azure qui contiennent ces serveurs doivent être conçus pour des espaces d’adresse, un routage et une structure DNS intégrée non superposés.

</span><span class="sxs-lookup"><span data-stu-id="59e45-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="59e45-147">Le service informatique doit inclure ces nouveaux serveurs dans son système de gestion et de surveillance réseau.</span><span class="sxs-lookup"><span data-stu-id="59e45-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="59e45-148">Utilisation de Contoso de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="59e45-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="59e45-p108">ExpressRoute est une connexion WAN dédiée à partir de votre emplacement vers un emplacement homologation Microsoft qui connecte votre réseau pour le réseau de cloud Microsoft. Connexions ExpressRoute fournissent des performances prévisibles et un SLA de disponibilité de 99,9 %. .</span><span class="sxs-lookup"><span data-stu-id="59e45-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="59e45-p109">Avec une connexion ExpressRoute, vous êtes connecté au réseau Microsoft dans le nuage et à tous les emplacements de centre de données de Microsoft dans le même continent. Le trafic entre l’emplacement homologation cloud et le centre de données Microsoft destination est transmise via le réseau de cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="59e45-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="59e45-154">**Figure 3 : réseau cloud mondial de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="59e45-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![Réseau cloud mondial de Microsoft](media/Contoso-Poster/MS-WW-Cloud.png)
  
<span data-ttu-id="59e45-156">La Figure 3 montre le réseau cloud interconnecté de Microsoft pour les différentes régions du monde.</span><span class="sxs-lookup"><span data-stu-id="59e45-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="59e45-p110">Avec ExpressRoute Premium, vous pouvez atteindre tous les centres de données Microsoft sur tous les continents à partir de n’importe quel emplacement d’homologation Microsoft situé sur un des continents. Le trafic entre les continents est réalisé sur le réseau cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59e45-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="59e45-159">En fonction de l’analyse du trafic actuel et futur d’offres de cloud de Microsoft, Contoso a effectué une évaluation du réseau et implémenté une connexion ExpressRoute (basés sur MPLS) pour tout pour accéder aux ressources Azure, avec peering privée et publique relations, à partir du siège social Paris à l’emplacement homologation Microsoft en Europe.</span><span class="sxs-lookup"><span data-stu-id="59e45-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="59e45-160">Cette connexion apportera au service informatique de Contoso :</span><span class="sxs-lookup"><span data-stu-id="59e45-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="59e45-161">Des performances cohérentes pour l’administration des applications Azure PaaS réparties</span><span class="sxs-lookup"><span data-stu-id="59e45-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="59e45-p111">Tous les développeurs d’applications et d’infrastructure principaux de Contoso administrateurs sont dans le campus Paris. Avec les applications Azure PaaS distribuées à différents centres de données Azure dans le monde entier, Contoso doit des performances homogènes à partir du campus Paris pour gérer les applications et leurs ressources de stockage, qui sont composés de To de documents.</span><span class="sxs-lookup"><span data-stu-id="59e45-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="59e45-164">Des performances cohérentes pour l’administration des serveurs dans Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="59e45-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="59e45-p112">Les administrateurs du centre de données de Contoso se trouvent dans le campus Paris et les serveurs à être déployés dans Azure sont une extension du centre de données Paris. Contoso doit des performances homogènes à ces nouveaux serveurs pour l’accès aux applications héritées et d’archivage et de traitement de la fin du trimestre.</span><span class="sxs-lookup"><span data-stu-id="59e45-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="59e45-167">Chemin d’accès de Contoso cloud préparation mise en réseau</span><span class="sxs-lookup"><span data-stu-id="59e45-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="59e45-168">Contoso a établi la procédure suivante pour préparer son réseau au cloud de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="59e45-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="59e45-169">Optimiser les ordinateurs des collaborateurs pour accéder à Internet
</span><span class="sxs-lookup"><span data-stu-id="59e45-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="59e45-170">Les ordinateurs individuels sont vérifiés pour assurer que les ressources les plus récentes (pile TCP/IP, navigateur, pilotes de carte réseau, mises à jour de sécurité et du système d’exploitation) sont bien installées.</span><span class="sxs-lookup"><span data-stu-id="59e45-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="59e45-171">Analyser l’utilisation de la connexion Internet dans chaque bureau et apporter des ressources supplémentaires selon les besoins</span><span class="sxs-lookup"><span data-stu-id="59e45-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="59e45-172">
Une analyse de l’utilisation d’Internet est réalisée dans chaque bureau et la bande passante de la connexion WAN est renforcée si son utilisation est supérieure ou égale à 70 %.</span><span class="sxs-lookup"><span data-stu-id="59e45-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="59e45-173">Analyser les systèmes du DMZ de chaque bureau pour obtenir des performances optimales
</span><span class="sxs-lookup"><span data-stu-id="59e45-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="59e45-p113">Une analyse des pare-feu, IDS et autres systèmes connectés à Internet a lieu pour garantir des performances optimales. Les serveurs proxy sont mis à jour ou à niveau selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="59e45-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="59e45-176">Ajouter ExpressRoute au site parisien</span><span class="sxs-lookup"><span data-stu-id="59e45-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="59e45-177">Offre un accès cohérent aux ressources Azure pour administrer les charges de travail Azure PaaS et IaaS.</span><span class="sxs-lookup"><span data-stu-id="59e45-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="59e45-178">Créer et tester un profil Azure Traffic Manager pour les applications Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="59e45-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="59e45-179">Tester un profil Azure Traffic Manager utilisant la méthode de routage des performances afin d’expérimenter la répartition du trafic Internet vers les sites régionaux.</span><span class="sxs-lookup"><span data-stu-id="59e45-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="59e45-180">Réserver l’espace d’adressage privé pour les réseaux virtuels Azure
</span><span class="sxs-lookup"><span data-stu-id="59e45-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="59e45-181">Se baser sur les chiffres des serveurs à court terme et long terme planifiés dans Azure IaaS pour réserver l’espace d’adressage privé aux réseaux virtuels Azure et à leurs sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="59e45-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="59e45-182">See Also</span><span class="sxs-lookup"><span data-stu-id="59e45-182">See Also</span></span>

[<span data-ttu-id="59e45-183">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="59e45-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="59e45-184">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="59e45-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="59e45-185">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)
</span><span class="sxs-lookup"><span data-stu-id="59e45-185">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



