---
title: "Diagramme accessible : Intégration réseau de produits Microsoft Office Server"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Cet article est une version texte accessible du diagramme intégration réseau des produits Microsoft Office Server."
ms.openlocfilehash: 2ced3ae648d07ae00c66b8ede8562df66826e4a9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="4861d-103">Diagramme accessible : Intégration réseau de produits Microsoft Office Server</span><span class="sxs-lookup"><span data-stu-id="4861d-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="4861d-104">**Résumé :** Cet article est une version texte accessible du diagramme nommé réseau des produits serveur de Microsoft Office Integration.</span><span class="sxs-lookup"><span data-stu-id="4861d-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="4861d-p101">Cette affiche donne une illustration générale d’un environnement réseau qui inclut Exchange Server 2013, SharePoint 2013 et Lync Server 2013. Il illustre également les éléments de mise en réseau suivantes qui sont communes à ces produits : accès interne et distant, l’authentification, le trafic client et le trafic de routage par le biais de périphériques partagés.</span><span class="sxs-lookup"><span data-stu-id="4861d-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="4861d-107">Concepts de haut niveau relatifs à Lync, Exchange, SharePoint Server et Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="4861d-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="4861d-108">À propos de la conception</span><span class="sxs-lookup"><span data-stu-id="4861d-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="4861d-109">Conception réseau simplifiée</span><span class="sxs-lookup"><span data-stu-id="4861d-109">Streamlined network design</span></span>

<span data-ttu-id="4861d-p102">Cette topologie illustre un déploiement du réseau local de SharePoint 2013, Exchange Server 2013 et Lync Server 2013. Il montre également l’utilisation de la service de nuage de Microsoft, Exchange Online Protection, ce qui assure une protection de spam et les logiciels malveillants pour le trafic SMTP Simple Mail Transfer Protocol () à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="4861d-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="4861d-p103">Cette conception réseau se résume à un ensemble minimal de fonctionnalités réseau. La conception ne prend pas en compte les fonctionnalités de sécurité et d’infrastructure supplémentaires dont certaines organisations peuvent avoir besoin.  </span><span class="sxs-lookup"><span data-stu-id="4861d-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="4861d-114">Ce schéma : </span><span class="sxs-lookup"><span data-stu-id="4861d-114">This diagram:</span></span> 
  
- <span data-ttu-id="4861d-115">Fournit un exemple de topologie réseau illustrant le trafic entrant et le trafic sortant via un routeur passerelle, ainsi que l'équilibrage de charge du trafic (interne et externe) de la session aux différents niveaux des serveurs SharePoint, Exchange et Lync.  </span><span class="sxs-lookup"><span data-stu-id="4861d-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="4861d-116">Illustre l'utilisation facultative de serveurs d’accès distants, comme une passerelle VPN tierce ou un serveur DirectAccess, afin de fournir une communication sécurisée aux employés itinérants ou distants. </span><span class="sxs-lookup"><span data-stu-id="4861d-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="4861d-117">Décrit en détail le flux du trafic SharePoint, Exchange et Lync à partir du client pour chaque niveau de serveur de plateforme. </span><span class="sxs-lookup"><span data-stu-id="4861d-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="4861d-118">Identifie le type de connexion d'accès distant ou interne basé sur le client (par exemple, le partenaire ou l'employé) et la méthode d'authentification utilisée. </span><span class="sxs-lookup"><span data-stu-id="4861d-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="4861d-119">Décompose les plates-formes SharePoint, Exchange et Lync par les rôles de serveur requis, qui identifie le serveur frontal, application, base de données et autres niveaux.</span><span class="sxs-lookup"><span data-stu-id="4861d-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="4861d-p104">L'architecture utilisée ici pour SharePoint, Lync, et Exchange ne privilégie pas une implémentation de ces plateformes. Elle ne fait que proposer un exemple, car les topologies varient selon les exigences réseau et de sécurité propres à chaque situation. </span><span class="sxs-lookup"><span data-stu-id="4861d-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="4861d-122">Routeur passerelle</span><span class="sxs-lookup"><span data-stu-id="4861d-122">Gateway router</span></span>

<span data-ttu-id="4861d-p105">Dans cette topologie, le routeur passerelle se trouve à la périphérie du réseau et achemine le trafic entrant et sortant vers et depuis l'intranet. Par ailleurs, d’autres composants, tels que plusieurs couches de pare-feu, peuvent combler l'écart entre le routeur et l'équilibrage de charge affiché. Cette topologie représente une façon parmi d’autres de déployer votre réseau. Dans cette configuration, la passerelle est configurée avec des listes de contrôle d’accès (LCA) destinées à filtrer le trafic IP entrant et sortant au niveau des interfaces du routeur. Il est possible d’utiliser les LCA, l’inspection avancée ou la traduction d'adresses réseau (NAT) sur d’autres périphériques, tels que les pare-feu, dans l'ensemble de votre réseau. </span><span class="sxs-lookup"><span data-stu-id="4861d-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="4861d-128">Périphériques d’équilibrage de charge et de proxy inverse</span><span class="sxs-lookup"><span data-stu-id="4861d-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="4861d-p106">Vous pouvez utiliser des solutions d’équilibrage de charge matérielle ou logicielle pour rediriger le trafic pour des segments, y compris les serveurs web frontaux de SharePoint et les serveurs d’accès Client (cas) Exchange. Dans certains cas, il est souhaitable d’utiliser un équilibreur de charge matérielle de couche 7 pour les besoins de persistance, comme il peut être plus performant dans la demande, telles que les cookies et en-têtes à l’aide des informations. Toutefois, les facteurs comme le coût et l’utilisation accrue et la charge de travail à partir d’une telle solution n’est peut-être pas souhaitable pour vos besoins spécifiques. Tenez compte des points suivants pour l’équilibrage de charge sur SharePoint, Exchange et Lync :</span><span class="sxs-lookup"><span data-stu-id="4861d-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="4861d-p107">SharePoint - pour SharePoint 2013, vous n’avez pas besoin à activer l’affinité pour les serveurs web frontaux. Normalement, ce serait utilisé pour la création de sessions persistantes et éviter plusieurs demandes d’authentification des clients sur chaque serveur web frontal. Le nouveau service de Cache distribué dans SharePoint 2013 stocke et distribue les jetons d’ouverture de session sur les serveurs web de la batterie de serveurs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4861d-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="4861d-p108">Exchange - dans Exchange 2013, le rôle des autorités de certification est conçu pour utiliser l’équilibrage de charge de couche 4, en distribuant les requêtes au niveau de la couche de transport. Cela peut sensiblement diminuer l’utilisation de l’équilibrage de la charge et la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="4861d-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="4861d-p109">Lync - équilibrage de la charge de système de nom de domaine (DNS) est recommandée pour le trafic du protocole SIP (Session Initiation) pour les pools de Lync. (HUMIDIFICATION à HLB) d’équilibrage de charge est nécessaire pour le trafic de Lync Web (protocole HTTPS).</span><span class="sxs-lookup"><span data-stu-id="4861d-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="4861d-140">Options d'accès distant</span><span class="sxs-lookup"><span data-stu-id="4861d-140">Remote access options</span></span>

<span data-ttu-id="4861d-p110">Plusieurs options permettent de publier des ressources intranet pour les partenaires sur Internet ou de fournir un accès distant sécurisé aux employés distants ou itinérants. Il s’agit notamment des proxys inverses, de DirectAccess et des passerelles VPN tierces. Les solutions d'accès à distance décrites plus loin dans cette section sont adaptées à SharePoint, Lync et Exchange, ou à toute combinaison de ces serveurs dans un déploiement local. Toutefois, certaines options distantes peuvent ne pas fonctionner avec une solution particulière.  </span><span class="sxs-lookup"><span data-stu-id="4861d-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="4861d-p111">Reverse Proxy - proxy inverse prend en charge le cryptage du trafic, telles que Secure Sockets Layer (SSL) et il que vous pouvez publier des applications intranet et ressources web authentifié utilisateurs et partenaires sur Internet. Par exemple, Microsoft Forefront Unified Access Gateway (UAG). De nombreux équilibreurs de charge matériels prennent également en charge la fonctionnalité de proxy inversé. Toutefois, il existe des scénarios toujours valides pour l’utilisation d’une solution autonome en fonction de vos besoins et exigences, telles que l’isolation du trafic cloisonnement de la sécurité et l’optimisation des performances.</span><span class="sxs-lookup"><span data-stu-id="4861d-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="4861d-149">Atouts et avantages du proxy inverse : </span><span class="sxs-lookup"><span data-stu-id="4861d-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="4861d-150">Fournit un accès authentifié et sécurisé aux partenaires et utilisateurs accédant aux ressources intranet (utilisation du port TCP 443 avec le protocole SSL entre le client et le serveur proxy inverse). </span><span class="sxs-lookup"><span data-stu-id="4861d-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="4861d-p112">Concernant Exchange, un proxy inverse, tel que Forefront UAG, fournit un mécanisme de pré-authentification avant le serveur d’accès au client Exchange. Les utilisateurs distants faisant usage d’applications publiées telles qu'Outlook Web Access (OWA) peuvent s’authentifier à l’aide des méthodes de base, NTLM ou Kerberos avant d'atteindre le réseau interne. </span><span class="sxs-lookup"><span data-stu-id="4861d-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="4861d-153">Concernant Exchange et SharePoint, des solutions, telles que Forefront UAG, peuvent mettre fin aux connexions SSL et diminuer la charge du serveur de ressources intranet tout en offrant un point unique de gestion des certificats. </span><span class="sxs-lookup"><span data-stu-id="4861d-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="4861d-p113">Pour Lync, le trafic Web (HTTPS) passe par le proxy inverse (TCP 443) pour la communication client. Les serveurs proxy de proxy inverse l’HTTPS connexion à Lync Web Services, les autorités de certification Exchange et Office Web Apps. Lync Server 2013 ne prend pas en charge les UAG.</span><span class="sxs-lookup"><span data-stu-id="4861d-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="4861d-p114">DirectAccess - il s’agit d’une technologie d’accès à distance qui s’appuie sur la sécurité du protocole Internet (IPsec) pour l’authentification et le cryptage du trafic entre le client DirectAccess et le serveur. DirectAccess fournit un accès simultané aux ressources intranet et Internet pour les employés itinérants et distants sans avoir à établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="4861d-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="4861d-159">Points à prendre en compte lors de l’utilisation de DirectAccess : </span><span class="sxs-lookup"><span data-stu-id="4861d-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="4861d-160">DirectAccess utilise le trafic protégé IPsec (protocole 50 et 51 et UDP 500) entre le client DirectAccess et le serveur. </span><span class="sxs-lookup"><span data-stu-id="4861d-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="4861d-161">DirectAccess pour Windows Server 2012 et Windows 8 n’a pas besoin de déploiement PKI (infrastructure de clé publique) pour l’authentification du serveur et du client. </span><span class="sxs-lookup"><span data-stu-id="4861d-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="4861d-162">Nous déconseillons l’utilisation de DirectAccess avec Lync Server 2013 en raison de problèmes de latence audio et vidéo liés à IPsec et le décryptage.</span><span class="sxs-lookup"><span data-stu-id="4861d-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="4861d-p115">Passerelle VPN - passerelles VPN standard fournissent une connexion d’accès distant dans lequel un ordinateur client d’accès distant est logiquement projeté sur l’intranet via une connexion par tunnel et initiée par l’utilisateur. Vous pouvez utiliser unifiée d’accès à distance dans Windows Server 2012 ou plusieurs solutions de tiers pour fournir un accès sécurisé à l’intranet pour les employés itinérants ou distants. VPN n’est pas recommandée pour Lync. Le trafic de Lync distant doit utiliser les serveurs Edge et tunneling fractionné.</span><span class="sxs-lookup"><span data-stu-id="4861d-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="4861d-167">Considérations relatives au système DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="4861d-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="4861d-168">Vous devez préparer le jeu d'enregistrements DNS qui permettra aux utilisateurs Internet et intranet de résoudre les noms DNS en adresses IP. </span><span class="sxs-lookup"><span data-stu-id="4861d-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="4861d-169">Pour les partenaires Internet et les employés itinérants ou distants, les enregistrements DNS inscrits auprès des serveurs DNS Internet fournissent une résolution à l'ensemble des adresses IP publiques correspondant au routeur passerelle, au serveur Edge de Lync, à l'ensemble des adresses IP virtuelles (VIP) sur l'équilibreur de charge et à la passerelle DirectAccess ou VPN selon vos besoins. </span><span class="sxs-lookup"><span data-stu-id="4861d-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="4861d-170">Pour les utilisateurs intranet, les enregistrements DNS inscrits auprès des serveurs DNS de l’intranet fournissent une résolution à l'ensemble des adresses IP virtuelles (VIP) de l'équilibreur de charge pour permettre d’accéder aux ressources Exchange, SharePoint et Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="4861d-p116">Les clients DirectAccess utilisent les serveurs DNS de l’intranet pour les noms appartenant à l'espace de noms DNS de l’intranet et ils utilisent les serveurs DNS Internet pour les autres noms. Pour une utilisation plus simple de DirectAccess, vous pouvez envisager de recourir à une implémentation de DNS fractionné utilisant des espaces de noms DNS différents pour les noms intranet et les noms Internet. Par exemple, utilisez contoso.com pour les noms Internet et corp.contoso.com pour l'espace de noms intranet. </span><span class="sxs-lookup"><span data-stu-id="4861d-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="4861d-p117">Exchange s’appuie sur un modèle DNS fractionné dans lequel la résolution de l’hôte vers l’adresse IP diffère selon que le trafic est routé dans l’espace public ou sur le réseau d’entreprise. Au minimum, vous devez disposer des enregistrements DNS pour OWA, de la découverte automatique, des URL ActiveSync pour le trafic du client et d’un enregistrement MX pour le courrier entrant. </span><span class="sxs-lookup"><span data-stu-id="4861d-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="4861d-176">Si vous utilisez Exchange Online Protection (EOP), votre enregistrement MX pointe vers ce service et non pas vers votre batterie de serveurs Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="4861d-177">Pour Exchange, vous avez besoin d'une preuve de propriété de l’enregistrement TXT dans votre DNS public et d’un ID d'organisation de fédération afin de configurer le partage fédéré. </span><span class="sxs-lookup"><span data-stu-id="4861d-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="4861d-178">Il est possible de configurer les clients VPN d'accès à distance de sorte qu’ils utilisent uniquement des serveurs DNS intranet lorsque la connexion VPN d'accès à distance est active. </span><span class="sxs-lookup"><span data-stu-id="4861d-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="4861d-179">Description du diagramme</span><span class="sxs-lookup"><span data-stu-id="4861d-179">Diagram Description</span></span>

<span data-ttu-id="4861d-p118">Ce diagramme fournit un exemple de topologie réseau illustrant le trafic entrant et sortant via un routeur passerelle et l'équilibrage de charge du trafic (externe et interne) de la session du client vers les niveaux appropriés des serveurs SharePoint, Exchange et Lync. La description de ce diagramme est divisée en deux : </span><span class="sxs-lookup"><span data-stu-id="4861d-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="4861d-182">Description des composants figurant dans le diagramme </span><span class="sxs-lookup"><span data-stu-id="4861d-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="4861d-183">Description de la façon dont le trafic se déplace dans les composants vers les niveaux serveur SharePoint, Exchange, Lync et Office Web Apps. </span><span class="sxs-lookup"><span data-stu-id="4861d-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="4861d-184">Description des composants figurant dans le diagramme </span><span class="sxs-lookup"><span data-stu-id="4861d-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="4861d-185">Types d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4861d-185">User types</span></span>

<span data-ttu-id="4861d-186">Il existe quatre types d'utilisateurs, trois types externes aux services réseau et services cloud, et un type interne, qui incluent : </span><span class="sxs-lookup"><span data-stu-id="4861d-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="4861d-187">Sociétés partenaires (B2B), externes </span><span class="sxs-lookup"><span data-stu-id="4861d-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="4861d-188">Partenaires individuels (SharePoint et anonymes (Lync)), externes </span><span class="sxs-lookup"><span data-stu-id="4861d-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="4861d-189">Employés itinérants et distants, externes </span><span class="sxs-lookup"><span data-stu-id="4861d-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="4861d-190">Employés internes</span><span class="sxs-lookup"><span data-stu-id="4861d-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="4861d-191">Trafic de messagerie sur le cloud</span><span class="sxs-lookup"><span data-stu-id="4861d-191">Cloud-based email traffic</span></span>

<span data-ttu-id="4861d-192">Il existe un composant cloud pour le trafic de messagerie SMTP : il peut s’agir d’hôtes de messagerie Internet ou d’Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="4861d-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="4861d-193">Authentification pour l'accès externe</span><span class="sxs-lookup"><span data-stu-id="4861d-193">Authentication for external access</span></span>

<span data-ttu-id="4861d-p119">Un ensemble de procédures d'authentification régit chacun des types d’utilisateur pour Lync, SharePoint et Exchange. Ces procédures sont décrites en détail plus loin dans le présent document. </span><span class="sxs-lookup"><span data-stu-id="4861d-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="4861d-196">Routeur passerelle avec LCA</span><span class="sxs-lookup"><span data-stu-id="4861d-196">Gateway router with ACLs</span></span>

<span data-ttu-id="4861d-197">Le routeur passerelle se trouve à la périphérie du réseau et achemine le trafic entrant et sortant vers et depuis l'intranet. </span><span class="sxs-lookup"><span data-stu-id="4861d-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="4861d-198">Serveurs d'accès distant pour Lync et SharePoint</span><span class="sxs-lookup"><span data-stu-id="4861d-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="4861d-199">Cette topologie comprend un serveur Edge Lync et une passerelle VPN SharePoint ou un serveur DirectAccess. </span><span class="sxs-lookup"><span data-stu-id="4861d-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="4861d-200">Équilibreur de charge et périphérique de proxy inverse</span><span class="sxs-lookup"><span data-stu-id="4861d-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="4861d-p120">Vous pouvez utiliser des solutions d'équilibrage de charge matérielles ou logicielles afin de rediriger le trafic pour des segments comprenant les serveurs web frontaux SharePoint et les serveurs d'accès Client (CAS) Exchange. Cette topologie présente des composants VIP Lync, VIP SharePoint et VIP Exchange dans l'équilibreur de charge. </span><span class="sxs-lookup"><span data-stu-id="4861d-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="4861d-203">Serveurs</span><span class="sxs-lookup"><span data-stu-id="4861d-203">Servers</span></span>

<span data-ttu-id="4861d-p121">Il existe quatre serveurs : Lync, SharePoint, Exchange et serveur de Office Web Apps. Chaque serveur peut avoir trois niveaux : frontal, couche d’accès au client, une couche application et une couche de stockage/base de données.</span><span class="sxs-lookup"><span data-stu-id="4861d-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="4861d-206">Niveau accès client frontal</span><span class="sxs-lookup"><span data-stu-id="4861d-206">Front-end, client-access tier</span></span>

<span data-ttu-id="4861d-207">Ce niveau comporte des éléments sur les quatre serveurs : </span><span class="sxs-lookup"><span data-stu-id="4861d-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="4861d-p122">Pool Lync (frontal). Le diagramme représente deux bases de données Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="4861d-p123">Serveur frontal SharePoint et cache distribué. Le diagramme représente trois bases de données SharePoint.  </span><span class="sxs-lookup"><span data-stu-id="4861d-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="4861d-p124">CAS Exchange. Le diagramme représente deux bases de données Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="4861d-p125">Serveur Office Web Apps Le diagramme représente deux bases de données Office Web Apps. </span><span class="sxs-lookup"><span data-stu-id="4861d-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="4861d-216">Niveau application</span><span class="sxs-lookup"><span data-stu-id="4861d-216">Application tier</span></span>

<span data-ttu-id="4861d-217">Ce niveau comprend les éléments qui résident uniquement sur le serveur SharePoint : </span><span class="sxs-lookup"><span data-stu-id="4861d-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="4861d-p126">Recherche (requête, index, administrateur). Le diagramme représente trois bases de données SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="4861d-p127">Traitement par lots. Le diagramme représente trois bases de données SharePoint.  </span><span class="sxs-lookup"><span data-stu-id="4861d-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="4861d-222">Niveau stockage/base de données</span><span class="sxs-lookup"><span data-stu-id="4861d-222">Database/storage tier</span></span>

<span data-ttu-id="4861d-223">Ce niveau comporte des éléments résidant sur les serveurs Exchange, SharePoint et Lync : </span><span class="sxs-lookup"><span data-stu-id="4861d-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="4861d-p128">Base de données Lync (serveur frontal). Le diagramme représente trois bases de données Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="4861d-p129">Base de données SharePoint. Le diagramme représente trois bases de données SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="4861d-p130">Serveur de boîtes aux lettres Exchange. Le diagramme représente deux serveurs de boîtes aux lettres Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="4861d-230">Pour plus d’informations sur les composants installés sur chacun des rôles de serveur SharePoint, consultez [Les Topologies rationalisée pour SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="4861d-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="4861d-231">Description du parcours du trafic dans les composants des différents niveaux serveur</span><span class="sxs-lookup"><span data-stu-id="4861d-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="4861d-232">Cette section décrit la façon dont les demandes utilisateur circulent dans la topologie réseau.  </span><span class="sxs-lookup"><span data-stu-id="4861d-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="4861d-233">Authentification et routage pour l'accès externe</span><span class="sxs-lookup"><span data-stu-id="4861d-233">Authentication and routing for external access</span></span>

<span data-ttu-id="4861d-234">Il existe trois types de clients externes aux services cloud et réseau, notamment : </span><span class="sxs-lookup"><span data-stu-id="4861d-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="4861d-235">Sociétés partenaires (B2B), externes </span><span class="sxs-lookup"><span data-stu-id="4861d-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="4861d-236">Partenaires individuels (SharePoint et anonymes (Lync)), externes </span><span class="sxs-lookup"><span data-stu-id="4861d-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="4861d-237">Employés itinérants et distants, externes </span><span class="sxs-lookup"><span data-stu-id="4861d-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="4861d-238">Le processus d'authentification et de routage est décrit individuellement pour chaque type d'utilisateur externe. </span><span class="sxs-lookup"><span data-stu-id="4861d-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="4861d-239">Sociétés partenaires (B2B) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="4861d-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="4861d-p131">Lync : approbation de fédération avec d'autres organisations, Skype et connectivité PIC (Public IM Connectivity) avec AOL. Le trafic de fédération Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="4861d-p132">SharePoint : Fournisseur d'identité du partenaire approuvé avec authentification SAML. Le trafic du client SharePoint passe par le routeur passerelle pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="4861d-p133">Exchange : Authentification mutuelle TLS pour le trafic de messagerie, authentification SAML pour le partage fédéré. Le trafic du client Exchange passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="4861d-246">Le trafic SMTP passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="4861d-247">Partenaires individuels (SharePoint) et anonymes (Lync) (https://partnerweb.contoso.com et https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="4861d-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="4861d-p134">Lync : les utilisateurs anonymes peuvent participer aux réunions Lync seulement si elles sont organisées par les employés. Le trafic de fédération Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, à l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync.  </span><span class="sxs-lookup"><span data-stu-id="4861d-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="4861d-p135">SharePoint : fournisseur d’identité du partenaire approuvé avec authentification SAML ou authentification basée sur les formulaires. Le trafic du client SharePoint passe par le routeur passerelle pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="4861d-252">Exchange : sans objet. </span><span class="sxs-lookup"><span data-stu-id="4861d-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="4861d-253">Le trafic web du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="4861d-254">Employés itinérants et distants</span><span class="sxs-lookup"><span data-stu-id="4861d-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="4861d-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="4861d-256">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="4861d-257">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="4861d-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="4861d-259">https://Mail.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="4861d-259">https://mail.contoso.com*</span></span> 
    
6. <span data-ttu-id="4861d-260">https://Dial.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="4861d-260">https://dial.contoso.com*</span></span>
    
7. <span data-ttu-id="4861d-261">https://Meet.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="4861d-261">https://meet.contoso.com*</span></span>
    
* <span data-ttu-id="4861d-262">L’URL de Exchange contient les répertoires virtuels suivants : service de découverte automatique, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="4861d-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="4861d-p136">Lync : authentification TLS-DSK ou NTLM. Le trafic du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, à l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="4861d-p137">SharePoint : services de domaine Active Directory, authentification basée sur les formulaires ou authentification SAML. Le trafic du client SharePoint passe par la passerelle VPN ou le serveur DirectAccess pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="4861d-p138">Exchange : Authentification de base sur SSL (ActiveSync, découverte automatique), authentification basée sur les formulaires (OWA). Le trafic du client Exchange passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="4861d-269">Le trafic du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="4861d-270">Authentification pour l'accès interne</span><span class="sxs-lookup"><span data-stu-id="4861d-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="4861d-271">Employés internes</span><span class="sxs-lookup"><span data-stu-id="4861d-271">Internal employees</span></span>

> <span data-ttu-id="4861d-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="4861d-273">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="4861d-274">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="4861d-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="4861d-276">https://Mail.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="4861d-276">https://mail.contoso.com*</span></span> 
    
> <span data-ttu-id="4861d-277">https://Dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="4861d-278">https://Meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="4861d-279">https://Admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="4861d-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="4861d-p139">Lync : authentification Kerberos, TLS-DSK ou NTLM. Le trafic du client Lync atteint l'adresse IP virtuelle Lync (serveur d’équilibrage de charge/proxy inverse), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="4861d-p140">SharePoint : services de domaine Active Directory, authentification basée sur les formulaires ou authentification SAML. Le trafic du client SharePoint atteint l’adresse IP virtuelle SharePoint (serveur d’équilibrage de charge/proxy inverse), puis le serveur SharePoint. </span><span class="sxs-lookup"><span data-stu-id="4861d-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="4861d-p141">Exchange : service de domaine Active Directory, authentification basée sur les formulaires. Le trafic du client Exchange atteint l’adresse IP virtuelle Exchange (serveur d’équilibrage de charge/proxy inverse), puis le serveur Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="4861d-286">Le trafic du client Lync atteint l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync. </span><span class="sxs-lookup"><span data-stu-id="4861d-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="4861d-287">Trafic de messagerie sur le cloud</span><span class="sxs-lookup"><span data-stu-id="4861d-287">Cloud-based email traffic</span></span>

<span data-ttu-id="4861d-288">Le composant de nuage pour le trafic de messagerie SMTP se compose d’hôtes de messagerie Internet ou de Protection en ligne d’Exchange.</span><span class="sxs-lookup"><span data-stu-id="4861d-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="4861d-p142">Ces composants acheminent le trafic de messagerie sur le réseau à l’aide du protocole SMTP. Le trafic passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange. </span><span class="sxs-lookup"><span data-stu-id="4861d-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="4861d-291">Légende relative au trafic réseau</span><span class="sxs-lookup"><span data-stu-id="4861d-291">Network traffic legend</span></span>

<span data-ttu-id="4861d-292">La zone de légende représente graphiquement les différents types de trafic à l’aide de lignes de couleur comme suit : </span><span class="sxs-lookup"><span data-stu-id="4861d-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="4861d-293">Vert ligne : Lync SIP le trafic</span><span class="sxs-lookup"><span data-stu-id="4861d-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="4861d-294">Ligne bleue : Trafic web Lync </span><span class="sxs-lookup"><span data-stu-id="4861d-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="4861d-295">Ligne violette : Trafic du client SharePoint </span><span class="sxs-lookup"><span data-stu-id="4861d-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="4861d-296">Ligne orange : Trafic du client Exchange </span><span class="sxs-lookup"><span data-stu-id="4861d-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="4861d-297">Ligne grise : Trafic du serveur de messagerie Exchange entre le site Exchange local et Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="4861d-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="4861d-298">La zone de légende contient également les descriptions des différents types de trafic et des ports que ceux-ci utilisent. </span><span class="sxs-lookup"><span data-stu-id="4861d-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="4861d-299">Trafic SIP Lync et trafic web Lync</span><span class="sxs-lookup"><span data-stu-id="4861d-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="4861d-300">Le serveur Edge de Lync utilise les ports suivants pour les communications utilisateur externes :  </span><span class="sxs-lookup"><span data-stu-id="4861d-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="4861d-301">Trafic de signalisation/messagerie instantanée (SIP/SIMPLE) : Port TCP 443 (ouvert pour le trafic entrant) </span><span class="sxs-lookup"><span data-stu-id="4861d-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="4861d-302">Trafic de conférence web (PSOM) : TCP 443 (ouvert pour le trafic entrant) </span><span class="sxs-lookup"><span data-stu-id="4861d-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="4861d-303">Trafic audio/vidéo (SRTP) : TCP 443, UDP 3478 et TCP 50000-59999 (facultatif) (ouvert pour le trafic entrant et sortant) </span><span class="sxs-lookup"><span data-stu-id="4861d-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="4861d-304">Le serveur Edge de Lync utilise les ports suivants pour les communications de fédération :  </span><span class="sxs-lookup"><span data-stu-id="4861d-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="4861d-305">Ports TCP 5061 (SIP), 5269 (XMPP), 443 et UDP 3478 (SRTP) (ouverts pour le trafic entrant et le trafic sortant) </span><span class="sxs-lookup"><span data-stu-id="4861d-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="4861d-306">Trafic du client SharePoint</span><span class="sxs-lookup"><span data-stu-id="4861d-306">SharePoint client traffic</span></span>

<span data-ttu-id="4861d-p143">SharePoint peut utiliser le port TCP 443 (SSL) pour la communication chiffrée entre le client et l’équilibreur de charge. Concernant l’accès externe à partir d’Internet, ce port doit être ouvert pour le trafic entrant et sortant sur un routeur passerelle (ou un pare-feu externe). </span><span class="sxs-lookup"><span data-stu-id="4861d-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="4861d-309">Trafic du client Exchange et trafic du serveur de messagerie Exchange</span><span class="sxs-lookup"><span data-stu-id="4861d-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="4861d-p144">Exchange utilise le port TCP 25 (SMTP) pour les communications de serveur à serveur. La plupart du trafic client (OWA, ActiveSync, Autodiscover, Outlook Anywhere) est traité sur le port 443 (HTTPS). Si vous avez des clients POP ou IMAP, les ports 110 (POP3), 995 (POP3 crypté), 143 (IMAP4), 993 (IMAP4 crypté) et 587 (SMTP) sont également utilisés pour prendre en charge ces clients.</span><span class="sxs-lookup"><span data-stu-id="4861d-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="4861d-313">En savoir plus sur le trafic réseau Lync</span><span class="sxs-lookup"><span data-stu-id="4861d-313">More on Lync network traffic?</span></span>

<span data-ttu-id="4861d-p145">Découvrez comment Lync Server peut aider votre entreprise à fournir une messagerie instantanée, les conférences web, partage d’application et la communication vocale. Pour plus d’informations, reportez-vous à la section [Comptabilisation de charges de travail de Microsoft Lync Server 2013 protocole](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="4861d-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="4861d-316">Le code QR figurant dans l’affiche permet d’accéder à ces informations. </span><span class="sxs-lookup"><span data-stu-id="4861d-316">The poster also includes a QR code to access this information.</span></span> 
  

