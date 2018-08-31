---
title: Connectivité client
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Résumé : Explique comment les ordinateurs clients se connectent aux clients Office 365, selon l’emplacement de l’ordinateur client et du centre de données client d’Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223036"
---
# <a name="client-connectivity"></a><span data-ttu-id="d7c20-103">Connectivité client</span><span class="sxs-lookup"><span data-stu-id="d7c20-103">Client connectivity</span></span>

 <span data-ttu-id="d7c20-104">**Résumé :** Explique comment les ordinateurs clients se connectent aux clients Office 365, selon l’emplacement de l’ordinateur client et du centre de données client d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="d7c20-p101">Office 365 réside dans les centres de données Microsoft dans le monde entier qui assurent le service et en cours d’exécution même lorsqu’il existe un problème majeur dans une région, par exemple un séisme ou une panne de courant. Lorsque vous vous connectez à votre client Office 365, la connexion du client est redirigée vers le centre de données appropriée hébergeant votre client. Les règles qui déterminent l’hébergement de votre client sont définis par votre contrat avec Microsoft. Les règles qui déterminent la façon dont votre client acquiert les données à partir de cet emplacement du centre de données dépendent de l’architecture du service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="d7c20-p102">Par exemple, lorsque vous ouvrez une session sur le portail Office 365, vous êtes généralement connecté au centre de données le plus proche pour le client et dirigées selon le service que vous utilisez suivant. Si vous lancez le courrier électronique, la connexion initiale à afficher l’interface utilisateur peut quand même provenir du centre de données le plus proche, mais une deuxième connexion peut être ouvert entre le centre de données le plus proche et le centre de données où se trouve votre client à afficher est dans les courriers électroniques lire. Microsoft dirige l’un des dix réseaux principales dans le monde résultant dans Connexions très rapide de centre de données-datacenter rapides.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="d7c20-112">Après avoir lu l’article, vous aurez probablement comprendre pourquoi nous ne fournissent pas [les plages d’adresses IP et Office 365 URL](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) par centre de données, ils sont simplement trop interconnexion et dépend de l’autre pour être que possible.</span><span class="sxs-lookup"><span data-stu-id="d7c20-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="d7c20-p103">Si vous utilisez ExpressRoute Azure pour Office 365, dans la plupart des cas, votre connectivity est acheminés via une connexion privée Office 365 au lieu de la connexion publique décrite ici. Les principes sur le mode de connexion des clients sont toujours précis. En savoir plus sur [ExpressRoute Azure pour Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="d7c20-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="d7c20-116">Pour approfondir sur Skype pour les demandes de réseau d’entreprise, consultez l’article de [la qualité des médias et des performances pour la connectivité réseau dans Skype pour Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="d7c20-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="d7c20-117">Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="d7c20-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="d7c20-p104">Nous prenons précaution pour gérer les données du client afin qu’il soit sécurisé et privées dans nos centres de données. Plus d’informations sur les étapes à que réaliser pour gérer la confidentialité sont inclus dans le [Centre de gestion de la confidentialité](https://go.microsoft.com/fwlink/?LinkID=397383).</span><span class="sxs-lookup"><span data-stu-id="d7c20-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="d7c20-120">Connexion au centre de données le plus proche</span><span class="sxs-lookup"><span data-stu-id="d7c20-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="d7c20-p105">Il s’agit du type de connexion les plus courantes, et il est utilisé par le portail Office 365 et Exchange Online. Dans ce cas, lorsque les clients tentent de se connecter à Office 365, requête DNS de leur ordinateur détermine la région du monde que provenant de leur ordinateur et Office 365 redirige la demande vers le centre de données le plus proche.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="d7c20-123">Connexions au portail arrêtez au centre de données plus proche, et l’ordinateur client est présenté avec des informations sur le client du client à partir de cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="d7c20-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="d7c20-p106">Exchange Online est une étape supplémentaire. Une fois l’ordinateur client est connecté au centre de données le plus proche, un serveur Exchange dans ce centre de données se connecte au centre de données où se trouve comme illustré dans le client le *comment cela fonctionne section* ci-dessous. Les serveurs Exchange Online dans le centre de données le plus proche puis proxy les demandes à partir de l’ordinateur client au serveur de boîtes aux lettres. Cela accélère l’expérience de l’ordinateur client en déplaçant l’essentiel de la récupération des messages électroniques et les éléments de calendrier pour le réseau Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="d7c20-128">Comment cela fonctionne pour les offres de cloud standard ?</span><span class="sxs-lookup"><span data-stu-id="d7c20-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="d7c20-p107">Ce processus de connexion est standard pour un trafic élevé, les applications web haute valeur comme Office 365. Dans cette section, nous hiérarchique et illustrent les étapes du processus. Lorsque l’ordinateur client n’est pas dans la même région en tant que le client, la connexion de recherche très différente en fonction du service que client se connecte.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="d7c20-p108">Ce diagramme illustre un client à l’aide d’une offre Office 365 standard avec un client en Amérique du Nord. Dans ce scénario, la personne qui effectue la demande de déplacement pour l’Europe et utilise Office 365 à partir de cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="d7c20-134">L’ordinateur client demande aux serveurs DNS locaux l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7c20-135">Serveurs DNS locaux de l’ordinateur client demandent aux serveurs DNS de Microsoft pour l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7c20-136">Les serveurs DNS de Microsoft renvoient le nom du serveur local (basé sur l’emplacement des serveurs DNS du client) et l’ordinateur client répète les étapes 1 et 2 pour obtenir l’adresse IP du centre de données Office 365 régionaux.</span><span class="sxs-lookup"><span data-stu-id="d7c20-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7c20-137">L’ordinateur client se connecte à l’adresse IP du centre de données régional.</span><span class="sxs-lookup"><span data-stu-id="d7c20-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d7c20-138">Les serveurs Exchange Online établissent une connexion au centre de données actif où réside le client du client.</span><span class="sxs-lookup"><span data-stu-id="d7c20-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Centre de données régional le plus proche](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="d7c20-140">Comment ce travail pour souverains cloud des offres ?</span><span class="sxs-lookup"><span data-stu-id="d7c20-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="d7c20-p109">Cette connexion est légèrement différente pour les offres de cloud souverains, tels qu’Office 365 exploité par 21 Vianet. Avec client dans une instance souverain d’Office 365, les serveurs Office 365 le plus proche qui acceptent les connexions portails sont les serveurs dans la région souveraine où réside le client. De même, les clients de l’accès à SharePoint Online dans notre souverains ou offres standards seront redirigés vers les serveurs frontaux où réside le client. Voir connexion au centre de données active ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="d7c20-145">L’ordinateur client demande aux serveurs DNS locaux l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7c20-146">Serveurs DNS locaux de l’ordinateur client demandent aux serveurs DNS de Microsoft pour l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7c20-147">Les serveurs DNS de Microsoft renvoient le nom du serveur local (basé sur l’emplacement des serveurs DNS du client) et l’ordinateur client répète les étapes 1 et 2 pour obtenir l’adresse IP du centre de données Office 365 régionaux.</span><span class="sxs-lookup"><span data-stu-id="d7c20-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7c20-148">L’ordinateur client se connecte à l’adresse IP du centre de données régional.</span><span class="sxs-lookup"><span data-stu-id="d7c20-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d7c20-149">Les serveurs Exchange Online établissent une connexion au centre de données actif où réside le client du client.</span><span class="sxs-lookup"><span data-stu-id="d7c20-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Centre de données régional américain le plus proche](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="d7c20-151">Connexion au centre de données actif</span><span class="sxs-lookup"><span data-stu-id="d7c20-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="d7c20-p110">Connexion au centre de données active est conçu pour les charges de transfert de données plus importante et actuellement utilisé par SharePoint Online. Dans ce cas, lorsque les clients tentent de se connecter à Office 365, son navigateur est redirigé vers le centre de données active pour leurs clients SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d7c20-154">Comment cela fonctionne-t-il ?</span><span class="sxs-lookup"><span data-stu-id="d7c20-154">How does this work?</span></span>

<span data-ttu-id="d7c20-p111">Lorsque l’ordinateur client se connecte à SharePoint Online à partir d’une région différente, la connexion est redirigée vers le centre de données SharePoint Online active. Dans ce scénario, le client utilise une norme offrant, ce qui les connexions portails restant local et les connexions de SharePoint Online est dirigées vers le centre de données active.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="d7c20-157">L’ordinateur client demande aux serveurs DNS locaux l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7c20-158">Serveurs DNS locaux de l’ordinateur client demandent aux serveurs DNS de Microsoft pour l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7c20-159">Les serveurs DNS de Microsoft renvoient le nom du serveur de SharePoint Online Centre de données actif (basé sur l’emplacement du client d’Office 365 du client) et l’ordinateur client répète les étapes 1 et 2 pour obtenir l’adresse IP du centre de données Office 365 active.</span><span class="sxs-lookup"><span data-stu-id="d7c20-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7c20-160">L’ordinateur client se connecte à l’adresse IP du centre de données actif.</span><span class="sxs-lookup"><span data-stu-id="d7c20-160">The client computer connects to the active datacenter IP address.</span></span>

![Centre de données américain actif](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="d7c20-162">Connexion sur des réseaux privés virtuels (VPN)</span><span class="sxs-lookup"><span data-stu-id="d7c20-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="d7c20-p112">Ce type de connexion s’applique uniquement lorsqu’un réseau privé virtuel (VPN) est utilisé par les ordinateurs clients. En réalité, le comportement d’Office 365 n’est pas modifié simplement comme un VPN est utilisé, mais VPN sont couramment utilisés pour contrôler comment les ordinateurs clients établissent des connexions vers Office 365 et généralement les résultats dans une expérience de dégradé, il est donc important couvrir.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d7c20-165">Comment cela fonctionne-t-il ?</span><span class="sxs-lookup"><span data-stu-id="d7c20-165">How does this work?</span></span>

<span data-ttu-id="d7c20-p113">Lorsque l’ordinateur client établit une connexion VPN avec un réseau d’entreprise dans une région différente, les serveurs DNS qu’office sont utilisés au lieu des serveurs DNS de l’emplacement de l’ordinateur client. Dans la plupart des cas, cette connexion supplémentaire sur le réseau privé virtuel entraîne une dégradation l’expérience Office 365. Les services Office 365 sont optimisées pour les connexions client de service en tant que proche de l’utilisateur final que possible. Tirer parti de nombreux services du réseau de périphérie Azure, les réseaux de distribution de contenu et la capacité du réseau fiable sur le réseau Microsoft pour fournir la meilleure expérience possible lorsque des requêtes de réseau pour les services Office 365 aussi proche de l’ordinateur client que possible.</span><span class="sxs-lookup"><span data-stu-id="d7c20-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="d7c20-170">L’ordinateur client demande des serveurs DNS VPN pour l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7c20-171">Serveurs DNS VPN de l’ordinateur client demandent aux serveurs DNS de Microsoft pour l’adresse IP associée à Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7c20-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7c20-172">Les serveurs DNS de Microsoft renvoient le nom du serveur local (basé sur l’emplacement des serveurs DNS VPN) et l’ordinateur client répète les étapes 1 et 2 pour obtenir les informations d’adresse IP du centre de données Office 365 régionaux.</span><span class="sxs-lookup"><span data-stu-id="d7c20-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7c20-173">L’ordinateur client connecte au centre de données adresse IP qui est le plus proche du siège que lequel il a établi une connexion VPN.</span><span class="sxs-lookup"><span data-stu-id="d7c20-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![Connectivité VPN du centre de données](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="d7c20-175">Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="d7c20-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d7c20-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7c20-176">See also</span></span>

[<span data-ttu-id="d7c20-177">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="d7c20-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="d7c20-178">Connectivité réseau à Office 365</span><span class="sxs-lookup"><span data-stu-id="d7c20-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
