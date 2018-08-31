---
title: Conception de réseaux pour Microsoft Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Résumé : Découvrez comment concevoir réseau optimisé pour les charges de travail dans Microsoft Azure IaaS.'
ms.openlocfilehash: 0e7af14768aa1a21548b25a20a465b644b749f3e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915119"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="c0f34-103">Conception de réseaux pour Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="c0f34-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="c0f34-104">**Résumé :** Comprendre comment concevoir réseau optimisé pour les charges de travail dans Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="c0f34-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="c0f34-105">L’optimisation du réseau pour les charges de travail informatiques hébergées dans Azure IaaS demande une bonne compréhension des réseaux virtuels Azure (VNets), des espaces d’adressage, du routage, de DNS et de l’équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="c0f34-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="c0f34-106">Étapes de préparation pour un réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="c0f34-106">Planning steps for any VNet</span></span>

<span data-ttu-id="c0f34-107">Suivez la procédure ci-dessous pour tout type de réseau virtuel (VNet).</span><span class="sxs-lookup"><span data-stu-id="c0f34-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="c0f34-108">Étape 1 : préparez votre intranet pour les services de cloud computing Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c0f34-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="c0f34-109">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="c0f34-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="c0f34-110">Étape 2 : optimisez votre bande passante Internet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="c0f34-111">Optimisez votre bande passante Internet en suivant les étapes 2 à 4 de la **procédure de préparation de votre réseau pour les services Microsoft SaaS** fournie dans [Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="c0f34-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="c0f34-112">Étape 3 : déterminez le type du réseau virtuel (cloud uniquement ou intersites).</span><span class="sxs-lookup"><span data-stu-id="c0f34-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="c0f34-p101">Un réseau virtuel de type « cloud uniquement » n’a aucune connexion avec un réseau local. Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="c0f34-115">**Figure 1 : Réseau virtuel de type « cloud uniquement »**</span><span class="sxs-lookup"><span data-stu-id="c0f34-115">**Figure 1: A cloud-only VNet**</span></span>

![Figure 1 : réseau virtuel sur cloud uniquement dans Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="c0f34-117">La figure 1 présente un ensemble de machines virtuelles placées dans un réseau virtuel de type « cloud uniquement ».</span><span class="sxs-lookup"><span data-stu-id="c0f34-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="c0f34-p102">Un réseau virtuel entre sites dispose d’une connexion VPN de site à site (S2S) ou ExpressRoute à un réseau local via une passerelle Azure. Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="c0f34-120">**Figure 2 : Réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-120">**Figure 2: A cross-premises VNet**</span></span>

![Figure 2 : réseau virtuel intersites dans Azure.](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="c0f34-122">La figure 2 présente un ensemble de machines virtuelles placées dans un réseau virtuel intersites, lequel est connecté à un réseau local.</span><span class="sxs-lookup"><span data-stu-id="c0f34-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="c0f34-123">Reportez-vous à la section [Étapes préparatoires pour un réseau virtuel intersites](designing-networking-for-microsoft-azure-iaas.md#cross_prem) de cet article.</span><span class="sxs-lookup"><span data-stu-id="c0f34-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="c0f34-124">Étape 4 : déterminez l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="c0f34-125">Le tableau 1 présente les espaces d’adressage correspondant aux différents types de réseaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="c0f34-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="c0f34-126">**Type de réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="c0f34-126">**Type of VNet**</span></span>|<span data-ttu-id="c0f34-127">**Espace d’adressage du réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="c0f34-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0f34-128">Cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="c0f34-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="c0f34-129">Espace d’adressage privé arbitraire</span><span class="sxs-lookup"><span data-stu-id="c0f34-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="c0f34-130">Cloud uniquement interconnecté</span><span class="sxs-lookup"><span data-stu-id="c0f34-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="c0f34-131">Private arbitraire, mais ne se chevauchent ne pas avec les autres connecté VNets</span><span class="sxs-lookup"><span data-stu-id="c0f34-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="c0f34-132">Intersites</span><span class="sxs-lookup"><span data-stu-id="c0f34-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="c0f34-133">Privé, mais sans chevauchement avec les réseaux locaux</span><span class="sxs-lookup"><span data-stu-id="c0f34-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="c0f34-134">Intersites interconnecté</span><span class="sxs-lookup"><span data-stu-id="c0f34-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="c0f34-135">Privé, mais sans chevauchement avec les autres réseaux virtuels connectés et les réseaux locaux</span><span class="sxs-lookup"><span data-stu-id="c0f34-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-136">**Tableau 1 : types de réseaux virtuels et espaces d’adressage correspondants**</span><span class="sxs-lookup"><span data-stu-id="c0f34-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="c0f34-137">Une configuration d’adresse issue de l’espace d’adressage du sous-réseau est attribuée aux machines virtuelles par DHCP :</span><span class="sxs-lookup"><span data-stu-id="c0f34-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="c0f34-138">Adresse/masque de sous-réseau</span><span class="sxs-lookup"><span data-stu-id="c0f34-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="c0f34-139">Passerelle par défaut</span><span class="sxs-lookup"><span data-stu-id="c0f34-139">Default gateway</span></span>
    
- <span data-ttu-id="c0f34-140">Adresses IP du serveur DNS</span><span class="sxs-lookup"><span data-stu-id="c0f34-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="c0f34-141">Vous pouvez également réserver une adresse IP statique.</span><span class="sxs-lookup"><span data-stu-id="c0f34-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="c0f34-142">Une adresse IP publique peut également être attribuée aux machines virtuelles, individuellement ou à partir du service de cloud qui les contient (pour les ordinateurs avec déploiement classique uniquement).</span><span class="sxs-lookup"><span data-stu-id="c0f34-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="c0f34-143">Étape 5 : déterminez les sous-réseaux au sein du réseau virtuel et les espaces d’adressage affectés à chacun.</span><span class="sxs-lookup"><span data-stu-id="c0f34-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="c0f34-144">Il existe deux types de sous-réseaux dans un réseau virtuel : un sous-réseau de passerelle et un sous-réseau qui héberge les machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="c0f34-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="c0f34-145">**Figure 3 : les deux types de sous-réseaux dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c0f34-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figure 3 : les deux types de sous-réseaux dans Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="c0f34-147">La figure 3 présente un réseau virtuel contenant un sous-réseau de passerelle qui contient lui-même une passerelle Azure et un ensemble de sous-réseaux hébergeant des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="c0f34-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="c0f34-p103">Le sous-réseau de passerelle Azure est requis par Azure pour héberger les deux machines virtuelles de votre passerelle Azure. Spécifiez un espace d’adressage avec une longueur de préfixe d’au moins 29 bits (exemple : 192.168.15.248/29). Une longueur de préfixe de 28 bits ou moins est recommandée, en particulier si vous envisagez d’utiliser ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="c0f34-151">Pour déterminer l’espace d’adressage du sous-réseau Azure de passerelle, il est recommandé de procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0f34-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="c0f34-152">Décidez de la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="c0f34-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="c0f34-153">Dans la variable bits de l’espace d’adressage du réseau virtuel, définissez la valeur de bits utilisée pour le sous-réseau de passerelle sur 0 et définissez les autres sur 1.</span><span class="sxs-lookup"><span data-stu-id="c0f34-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="c0f34-154">Convertissez les valeurs en nombres décimaux et exprimez-les sous forme d’espace d’adressage, en définissant la longueur du préfixe sur une valeur équivalente à la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="c0f34-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="c0f34-155">Avec cette méthode, l’espace d’adressage du sous-réseau de passerelle est toujours à l’extrémité de l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="c0f34-p104">Vous avez ci-dessous un exemple de définition du préfixe d’adresse pour le sous-réseau de passerelle : l’espace d’adressage du réseau virtuel est 10.119.0.0/16. L’organisation utilisera initialement une connexion VPN de site à site, mais emploiera ensuite ExpressRoute. Le tableau 2 indique les étapes pour déterminer le préfixe d’adresse pour le sous-réseau de passerelle, ainsi que leur résultat, dans la notation de préfixe réseau (également connue sous le nom de CIDR).</span><span class="sxs-lookup"><span data-stu-id="c0f34-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="c0f34-159">Voici les étapes et un exemple pour déterminer le préfixe d’adresse de passerelle sous-réseau :</span><span class="sxs-lookup"><span data-stu-id="c0f34-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="c0f34-p105">Déterminez la taille du sous-réseau passerelle. Pour notre exemple, nous avons choisi /28.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="c0f34-p106">Définir les fichiers binaires dans la partie variable de l’espace d’adressage VNet (b) 0 pour la passerelle sous-réseau bits (G), 1 dans le cas contraire (V). Pour notre exemple, nous utilisons l’espace d’adressage 10.119.0.0/16 pour la VNet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="c0f34-p107">10.119. bbbbbbbb. bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="c0f34-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="c0f34-p108">10.119. VVVVVVVV. VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="c0f34-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="c0f34-p109">10.119. 11111111. 11110000</span><span class="sxs-lookup"><span data-stu-id="c0f34-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="c0f34-p110">Convertir le résultat de l’étape 2 décimal et express en tant qu’un espace d’adressage. Pour notre exemple, 10.119. 11111111. 11110000 est 10.119.255.240 et la longueur du préfixe de l’étape 1, (28 dans notre exemple), le préfixe d’adresse de sous-réseau passerelle qui en résulte est 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="c0f34-177">Pour plus d’informations, voir [calculateur d’espace d’adresse pour les sous-réseaux passerelle Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="c0f34-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="c0f34-178">Les machines virtuelles Azure doivent être placées dans des sous-réseaux dédiés à l’hébergement des machines virtuelles. Pour cela, vous pouvez suivre les consignes standard pour les configurations locales, par exemple, en fonction d’un rôle ou d’un niveau d’application commun ou de manière à isoler les sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="c0f34-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="c0f34-p111">Azure utilise les 3 adresses sur chaque sous-réseau. Par conséquent, le nombre d’adresses possibles sur un sous-réseau Azure est 2<sup>n</sup> - 5, où n est le nombre de bits de l’hôte. Tableau 3 affiche la plage des ordinateurs virtuels requis, le nombre de héberge bits nécessaires et la taille de sous-réseau correspondant.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="c0f34-182">**Machines virtuelles requises**</span><span class="sxs-lookup"><span data-stu-id="c0f34-182">**Virtual machines required**</span></span>|<span data-ttu-id="c0f34-183">**Bits hôte**</span><span class="sxs-lookup"><span data-stu-id="c0f34-183">**Host bits**</span></span>|<span data-ttu-id="c0f34-184">**Taille sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="c0f34-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c0f34-185">1-3</span><span class="sxs-lookup"><span data-stu-id="c0f34-185">1-3</span></span>  <br/> |<span data-ttu-id="c0f34-186">3</span><span class="sxs-lookup"><span data-stu-id="c0f34-186">3</span></span>  <br/> |<span data-ttu-id="c0f34-187">/29</span><span class="sxs-lookup"><span data-stu-id="c0f34-187">/29</span></span>  <br/> |
|<span data-ttu-id="c0f34-188">4-11</span><span class="sxs-lookup"><span data-stu-id="c0f34-188">4-11</span></span>  <br/> |<span data-ttu-id="c0f34-189">4</span><span class="sxs-lookup"><span data-stu-id="c0f34-189">4</span></span>  <br/> |<span data-ttu-id="c0f34-190">/28</span><span class="sxs-lookup"><span data-stu-id="c0f34-190">/28</span></span>  <br/> |
|<span data-ttu-id="c0f34-191">12-27</span><span class="sxs-lookup"><span data-stu-id="c0f34-191">12-27</span></span>  <br/> |<span data-ttu-id="c0f34-192">5</span><span class="sxs-lookup"><span data-stu-id="c0f34-192">5</span></span>  <br/> |<span data-ttu-id="c0f34-193">/27</span><span class="sxs-lookup"><span data-stu-id="c0f34-193">/27</span></span>  <br/> |
|<span data-ttu-id="c0f34-194">28-59</span><span class="sxs-lookup"><span data-stu-id="c0f34-194">28-59</span></span>  <br/> |<span data-ttu-id="c0f34-195">6</span><span class="sxs-lookup"><span data-stu-id="c0f34-195">6</span></span>  <br/> |<span data-ttu-id="c0f34-196">/26</span><span class="sxs-lookup"><span data-stu-id="c0f34-196">/26</span></span>  <br/> |
|<span data-ttu-id="c0f34-197">60-123</span><span class="sxs-lookup"><span data-stu-id="c0f34-197">60-123</span></span>  <br/> |<span data-ttu-id="c0f34-198">7</span><span class="sxs-lookup"><span data-stu-id="c0f34-198">7</span></span>  <br/> |<span data-ttu-id="c0f34-199">/25</span><span class="sxs-lookup"><span data-stu-id="c0f34-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-200">**Tableau 3 : Configuration requise pour les machines virtuelles et tailles de sous-réseau correspondantes**</span><span class="sxs-lookup"><span data-stu-id="c0f34-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="c0f34-201">Pour plus d’informations sur la quantité maximale de machines virtuelles sur un sous-réseau ou de VNet, voir [Limites du réseau](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="c0f34-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="c0f34-202">Pour plus d’informations, voir [planifier et concevoir des réseaux virtuels Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="c0f34-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="c0f34-203">Étape 6 : déterminez la configuration du serveur DNS et les adresses des serveurs DNS à affecter aux machines virtuelles dans le réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="c0f34-p112">Azure attribue aux machines virtuelles les adresses des serveurs DNS par DHCP. Les serveurs DNS peuvent être :</span><span class="sxs-lookup"><span data-stu-id="c0f34-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="c0f34-206">Fournis par Azure : fournit l’enregistrement du nom en local, ainsi que la résolution des noms sur Internet et en local</span><span class="sxs-lookup"><span data-stu-id="c0f34-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="c0f34-207">Fournis par vous : fournit l’inscription des noms en local ou sur l’intranet, ainsi que la résolution des noms sur Internet ou l’intranet</span><span class="sxs-lookup"><span data-stu-id="c0f34-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="c0f34-208">Le tableau 4 présente les différentes configurations des serveurs DNS pour chaque type de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="c0f34-209">**Type de réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="c0f34-209">**Type of VNet**</span></span>|<span data-ttu-id="c0f34-210">**Serveur DNS**</span><span class="sxs-lookup"><span data-stu-id="c0f34-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0f34-211">Cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="c0f34-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="c0f34-212">Fourni par Azure pour la résolution des noms sur Internet et en local</span><span class="sxs-lookup"><span data-stu-id="c0f34-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="c0f34-213">Machine virtuelle Azure pour la résolution des noms sur Internet et en local (transfert DNS)</span><span class="sxs-lookup"><span data-stu-id="c0f34-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="c0f34-214">Intersites</span><span class="sxs-lookup"><span data-stu-id="c0f34-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="c0f34-215">En local pour la résolution des noms sur l’intranet et en local</span><span class="sxs-lookup"><span data-stu-id="c0f34-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="c0f34-216">Machine virtuelle Azure pour la résolution des noms sur l’intranet et en local (réplication et transfert DNS)</span><span class="sxs-lookup"><span data-stu-id="c0f34-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-217">**Tableau 4 : Options de serveur DNS pour les deux types de réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="c0f34-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="c0f34-218">Pour plus d’informations, voir [Résolution de noms pour les ordinateurs virtuels et des Instances de rôle](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="c0f34-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="c0f34-219">Étape 7 : déterminez la configuration d’équilibrage de charge (connectée à Internet ou interne).</span><span class="sxs-lookup"><span data-stu-id="c0f34-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="c0f34-p113">Dans certains cas, vous devez distribuer le trafic entrant vers un ensemble de serveurs qui ont le même rôle. Le service IaaS Azure dispose d’une fonction intégrée permettant d’effectuer cette action pour les charges de trafic Internet ou internes.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="c0f34-222">L’équilibrage de charge Azure pour Internet distribue le trafic entrant non sollicité de façon aléatoire d’Internet vers les membres d’un jeu d’équilibrage de charge. </span><span class="sxs-lookup"><span data-stu-id="c0f34-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="c0f34-223">**Figure 4 : Équilibrage de charge externe dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c0f34-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figure 4 : équilibrage de charge externe dans Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="c0f34-225">La figure 4 illustre un équilibreur de charge externe dans Azure qui répartit le trafic entrant sur une règle de trafic entrant NAT ou un point de terminaison à un ensemble d’ordinateurs virtuels dans un jeu à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="c0f34-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="c0f34-226">L’équilibrage de charge interne d’Azure répartit le trafic entrant non sollicité de façon aléatoire des machines virtuelles Azure vers les membres d’un jeu d’équilibrage de charge. </span><span class="sxs-lookup"><span data-stu-id="c0f34-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="c0f34-227">**Figure 5 : Équilibrage de charge interne dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c0f34-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figure 5 : équilibrage de charge interne dans Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="c0f34-229">La figure 5 illustre un équilibreur de charge interne dans Azure qui répartit le trafic entrant sur une règle de trafic entrant NAT ou un point de terminaison à un ensemble d’ordinateurs virtuels dans un jeu à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="c0f34-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="c0f34-230">Pour plus d’informations, voir [Équilibrage de charge Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="c0f34-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="c0f34-231">Étape 8 : déterminez l’utilisation des appliances virtuelles et des itinéraires définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c0f34-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="c0f34-232">Si vous devez transmettre du trafic vers des appliances virtuelles dans votre réseau virtuel, vous devrez peut-être ajouter un ou plusieurs itinéraires définis par l’utilisateur à un sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="c0f34-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="c0f34-233">**Figure 6 : Appliances virtuelles et itinéraires définis par l’utilisateur dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c0f34-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figure 6 : appliances virtuelles et itinéraires définis par l’utilisateur dans Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="c0f34-235">La figure 6 présente un réseau virtuel intersites et un itinéraire définis par l’utilisateur affecté à un sous-réseau hébergeant des machines virtuelles qui pointe vers une appliance virtuelle.</span><span class="sxs-lookup"><span data-stu-id="c0f34-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="c0f34-236">Pour plus d’informations, voir [itinéraires de définies par l’utilisateur et le routage IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="c0f34-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="c0f34-237">Étape 9 : déterminez le mode de connexion aux machines virtuelles des ordinateurs sur Internet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="c0f34-238">Il existe plusieurs méthodes pour fournir un accès Internet aux machines virtuelles sur un réseau virtuel, qui inclut l’accès à partir du réseau de votre entreprise via votre serveur proxy ou un autre appareil Edge.</span><span class="sxs-lookup"><span data-stu-id="c0f34-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="c0f34-239">Le tableau 5 présente les méthodes de filtrage ou de contrôle du trafic entrant non sollicité.</span><span class="sxs-lookup"><span data-stu-id="c0f34-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="c0f34-240">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="c0f34-240">**Method**</span></span>|<span data-ttu-id="c0f34-241">**Modèle de déploiement**</span><span class="sxs-lookup"><span data-stu-id="c0f34-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0f34-242">1. Points de terminaison et listes de contrôle d’accès configurés sur les services de cloud</span><span class="sxs-lookup"><span data-stu-id="c0f34-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="c0f34-243">Classique</span><span class="sxs-lookup"><span data-stu-id="c0f34-243">Classic</span></span>  <br/> |
|<span data-ttu-id="c0f34-244">2. Groupes de sécurité réseau</span><span class="sxs-lookup"><span data-stu-id="c0f34-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="c0f34-245">Resource Manager et classique</span><span class="sxs-lookup"><span data-stu-id="c0f34-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="c0f34-246">3. Équilibrage de charge connecté à Internet avec règles NAT de trafic entrant</span><span class="sxs-lookup"><span data-stu-id="c0f34-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="c0f34-247">Responsable de ressources</span><span class="sxs-lookup"><span data-stu-id="c0f34-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="c0f34-248">4. appareils de sécurité réseau dans Azure Marketplace (non illustré)</span><span class="sxs-lookup"><span data-stu-id="c0f34-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="c0f34-249">Resource Manager et classique</span><span class="sxs-lookup"><span data-stu-id="c0f34-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-250">**Tableau 5 : Méthodes de connexion aux machines virtuelles et modèles de déploiement Azure correspondantes**</span><span class="sxs-lookup"><span data-stu-id="c0f34-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="c0f34-251">**Figure 7 : connexion aux machines virtuelles Azure via Internet**</span><span class="sxs-lookup"><span data-stu-id="c0f34-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figure 7 : connexion aux machines virtuelles Azure via Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="c0f34-253">La figure 7 présente un ordinateur connecté à Internet qui se connecte à une machine virtuelle dans un service cloud à l’aide d’un point de terminaison, à une machine virtuelle dans un sous-réseau à l’aide d’un groupe de sécurité réseau et à une machine virtuelle dans un sous-réseau en utilisant un programme d’équilibrage de charge externe et des règles NAT de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="c0f34-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="c0f34-254">Les éléments suivants offrent un degré de sécurité supplémentaire :</span><span class="sxs-lookup"><span data-stu-id="c0f34-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="c0f34-255">Connexions de bureau à distance et SSH, authentifiées et chiffrées.</span><span class="sxs-lookup"><span data-stu-id="c0f34-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="c0f34-256">Sessions Remote PowerShell, authentifiées et chiffrées.</span><span class="sxs-lookup"><span data-stu-id="c0f34-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="c0f34-257">Mode de transport IPsec, que vous pouvez utiliser pour le chiffrement de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="c0f34-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="c0f34-258">Protection par déni de service distribué Azure, qui permet d’éviter les attaques internes et externes</span><span class="sxs-lookup"><span data-stu-id="c0f34-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="c0f34-259">Pour plus d’informations, voir [Sécurité de Cloud Microsoft pour les architectes de l’entreprise](https://aka.ms/cloudarchsecurity) et [Azure réseau](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="c0f34-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="c0f34-260">Étape 10 : pour plusieurs réseaux virtuels, déterminez la topologie de connexion de réseau virtuel à réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="c0f34-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="c0f34-261">Les réseaux virtuels peuvent être connectés à l’aide de topologies semblables à celles utilisées pour connecter les sites d’une organisation.</span><span class="sxs-lookup"><span data-stu-id="c0f34-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="c0f34-262">Une configuration en série connecte les réseaux virtuels les uns après les autres.</span><span class="sxs-lookup"><span data-stu-id="c0f34-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="c0f34-263">**Figure 8 : Configuration en série pour des réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="c0f34-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figure 8 : configuration de chaîne en série pour les réseaux virtuels Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="c0f34-265">La figure 8 illustre cinq VNets connectés dans la série à l’aide d’une configuration cascade.</span><span class="sxs-lookup"><span data-stu-id="c0f34-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="c0f34-266">Une configuration « Hub and Spoke » connecte plusieurs réseaux virtuels à un ensemble de réseaux virtuels centraux, qui sont eux-mêmes connectés entre eux.</span><span class="sxs-lookup"><span data-stu-id="c0f34-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="c0f34-267">**Figure 9 : Configuration Hub and Spoke pour réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="c0f34-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figure 9 : configuration « Hub and Spoke » pour les réseaux virtuels Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="c0f34-269">La figure 9 présente six réseaux virtuels, dont deux sont des hubs centraux connectés l’un à l’autre, chacun étant également connecté à deux autres réseaux virtuels périphériques.</span><span class="sxs-lookup"><span data-stu-id="c0f34-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="c0f34-270">Une configuration en maille complète connecte chaque réseau virtuel entre eux.</span><span class="sxs-lookup"><span data-stu-id="c0f34-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="c0f34-271">**Figure 10 : Configuration en maille complète pour réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="c0f34-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figure 10 : Configuration en maille pour les réseaux virtuels Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="c0f34-273">La figure 10 présente quatre réseaux virtuels connectés les uns aux autres, pour un total de six connexions de réseau virtuel à réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="c0f34-274">Étapes préparatoires pour un réseau virtuel intersites</span><span class="sxs-lookup"><span data-stu-id="c0f34-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="c0f34-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="c0f34-275"></span></span>

<span data-ttu-id="c0f34-276">Suivez la procédure ci-dessous pour un réseau virtuel intersites.</span><span class="sxs-lookup"><span data-stu-id="c0f34-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="c0f34-277">Pour créer un environnement de développement/test intersites, voir [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c0f34-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="c0f34-278">Étape 1 : déterminez la connexion intersites au réseau virtuel (VPN S2S ou ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="c0f34-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="c0f34-279">Le tableau 6 présente les différents types de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0f34-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="c0f34-280">**Type de connexion**</span><span class="sxs-lookup"><span data-stu-id="c0f34-280">**Type of connection**</span></span>|<span data-ttu-id="c0f34-281">**Objectif**</span><span class="sxs-lookup"><span data-stu-id="c0f34-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0f34-282">VPN de site à site (S2S)</span><span class="sxs-lookup"><span data-stu-id="c0f34-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="c0f34-283">Se connecter à des sites de 1 à 10 (y compris les autres VNets) à un seul VNet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="c0f34-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c0f34-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="c0f34-285">Lien privé sécurisé à Azure via un fournisseur d’échange Internet (IXP) ou un fournisseur de service réseau (NSP).</span><span class="sxs-lookup"><span data-stu-id="c0f34-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="c0f34-286">VPN de point à site (P2S)</span><span class="sxs-lookup"><span data-stu-id="c0f34-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="c0f34-287">Connecte un seul ordinateur à un réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="c0f34-288">VPN de réseau virtuel à réseau virtuel (V2V) ou homologation de réseau virtuel </span><span class="sxs-lookup"><span data-stu-id="c0f34-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="c0f34-289">Connecte un réseau virtuel à un autre réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-290">**Tableau 6 : Types de connexions pour les réseaux virtuels intersites**</span><span class="sxs-lookup"><span data-stu-id="c0f34-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="c0f34-291">Pour plus d’informations sur le nombre maximal de connexions, voir [Limites du réseau](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="c0f34-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="c0f34-292">Pour plus d’informations sur les périphériques VPN, voir [périphériques VPN pour les connexions de réseau virtuel de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="c0f34-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="c0f34-293">Pour plus d’informations sur VNet peering, consultez [peering VNet](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="c0f34-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="c0f34-294">**Figure 11 : Les quatre méthodes de connexion à un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figure 11 : les trois méthodes de connexion à un réseau virtuel Azure intersites](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="c0f34-296">La figure 11 montre un VNet avec les quatre types de connexions : une connexion P2S à partir d’un ordinateur, une connexion VPN S2S à partir d’un réseau local, une connexion ExpressRoute à partir d’un réseau local et une connexion VNet-à-VNet à partir d’une autre VNet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="c0f34-297">Vous pouvez vous connecter aux machines virtuelles dans un réseau virtuel des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0f34-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="c0f34-298">Administration des machines virtuelles de réseau virtuel à partir de votre réseau local ou d’Internet</span><span class="sxs-lookup"><span data-stu-id="c0f34-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="c0f34-299">Accès aux charges de travail informatique à partir de votre réseau local</span><span class="sxs-lookup"><span data-stu-id="c0f34-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="c0f34-300">Extension de votre réseau via des réseaux virtuels supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c0f34-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="c0f34-301">La sécurité des connexions est assurée des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0f34-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="c0f34-302">Les connexions P2S utilisent le protocole SSTP (Secure Socket Tunneling Protocol) </span><span class="sxs-lookup"><span data-stu-id="c0f34-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="c0f34-303">Les connexions VPN de réseau virtuel à réseau virtuel et S2S utilisent le mode de tunnel IPsec avec AES256.</span><span class="sxs-lookup"><span data-stu-id="c0f34-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="c0f34-304">ExpressRoute est une connexion WAN privée</span><span class="sxs-lookup"><span data-stu-id="c0f34-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="c0f34-305">Pour plus d’informations, voir [Sécurité de Cloud Microsoft pour les architectes de l’entreprise](https://aka.ms/cloudarchsecurity) et [Azure réseau](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="c0f34-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="c0f34-306">Étape 2 : déterminez le routeur ou le périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="c0f34-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="c0f34-307">Votre routeur ou votre périphérique VPN local fait office :</span><span class="sxs-lookup"><span data-stu-id="c0f34-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="c0f34-308">D’homologue IPsec, qui termine la connexion VPN S2S à partir de la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="c0f34-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="c0f34-309">D’homologue BPG et de point de terminaison pour la connexion ExpressRoute à homologation privée.</span><span class="sxs-lookup"><span data-stu-id="c0f34-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="c0f34-310">**Figure 12 : Routeur ou appareil VPN**</span><span class="sxs-lookup"><span data-stu-id="c0f34-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Figure 12 : routeur ou périphérique VPN local](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="c0f34-312">La figure 12 présente un réseau virtuel intersites connecté à un routeur ou périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="c0f34-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="c0f34-313">Pour plus d’informations, voir [passerelle sur VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="c0f34-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="c0f34-314">Étape 3 : Ajouter des itinéraires à votre intranet pour rendre l’espace d’adressage de la VNet accessibles.</span><span class="sxs-lookup"><span data-stu-id="c0f34-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="c0f34-315">La configuration de routage vers des réseaux virtuels à partir de l’environnement local comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c0f34-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="c0f34-316">Un itinéraire pour l’espace d’adressage de réseau virtuel qui pointe vers votre périphérique VPN.</span><span class="sxs-lookup"><span data-stu-id="c0f34-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="c0f34-317">Un itinéraire pour l’espace d’adressage de réseau virtuel sur votre périphérique VPN qui pointe vers la connexion VPN S2S ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="c0f34-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="c0f34-318">**Figure 13 : Itinéraires locaux nécessaires pour rendre un réseau virtuel accessible**</span><span class="sxs-lookup"><span data-stu-id="c0f34-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figure 13 : itinéraires locaux nécessaires pour rendre un réseau virtuel Azure accessible](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="c0f34-320">La figure 13 présente les informations de routage requises par les routeurs locaux et le routeur ou le périphérique VPN qui représente l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="c0f34-321">Étape 4 : pour ExpressRoute, préparez la nouvelle connexion avec l’aide de votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c0f34-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="c0f34-322">Il existe trois méthodes pour créer une connexion ExpressRoute avec homologation privée entre votre réseau local et le cloud Microsoft :</span><span class="sxs-lookup"><span data-stu-id="c0f34-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="c0f34-323">Colocation sur un échange cloud</span><span class="sxs-lookup"><span data-stu-id="c0f34-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="c0f34-324">Connexions Ethernet de point à point</span><span class="sxs-lookup"><span data-stu-id="c0f34-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="c0f34-325">Réseaux à connectivité complète (IP VPN)</span><span class="sxs-lookup"><span data-stu-id="c0f34-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="c0f34-326">**Figure 14 : Utilisation d’ExpressRoute pour établir une connexion vers un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figure 14 : utilisation d’ExpressRoute pour établir une connexion à un réseau virtuel Azure intersites](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="c0f34-328">La figure 14 présente un réseau virtuel intersites et une connexion ExpressRoute d’un routeur local vers Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c0f34-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="c0f34-329">Pour plus d'informations, voir [ExpressRoute pour la connectivité au cloud de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="c0f34-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="c0f34-330">Étape 5 : déterminez l’espace d’adressage du réseau Local pour la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="c0f34-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="c0f34-331">Pour le routage vers des réseaux locaux ou d’autres réseaux virtuels à partir d’un réseau virtuel, Azure transfère le trafic via une passerelle Azure qui utilise l’espace d’adressage de réseau local affecté à la passerelle.</span><span class="sxs-lookup"><span data-stu-id="c0f34-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="c0f34-332">**Figure 15 : Espace d’adressage de réseau local pour un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figure 15 : espace d’adressage de réseau local pour un réseau virtuel Azure intersites](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="c0f34-334">La figure 15 présente un réseau virtuel intersites et l’espace d’adressage du réseau local sur la passerelle Azure, qui représente l’espace d’adressage accessible sur le réseau local. </span><span class="sxs-lookup"><span data-stu-id="c0f34-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="c0f34-335">Vous pouvez définir l’espace d’adressage du réseau local des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0f34-335">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="c0f34-336">Option 1 : liste des préfixes pour l’espace d’adressage actuellement nécessaire ou utilisé (des mises à jour peuvent être nécessaire lorsque vous ajoutez de nouveaux sous-réseaux).</span><span class="sxs-lookup"><span data-stu-id="c0f34-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="c0f34-337">Option 2 : intégralité de votre espace d’adressage local (des mises à jour sont uniquement nécessaires lorsque vous ajoutez le nouvel espace d’adressage).</span><span class="sxs-lookup"><span data-stu-id="c0f34-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="c0f34-338">Étant donné que la passerelle Azure n’autorise pas les itinéraires résumés, vous devez définir l’espace d’adressage du réseau local pour l’option 2 afin qu’il n’inclue pas l’espace d’adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="c0f34-339">**Figure 16 : Trou dans l’espace d’adressage, créé par l’espace d’adressage réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="c0f34-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figure 16 : trou dans l’espace d’adressage, créé par l’espace d’adressage du réseau virtuel](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="c0f34-341">La figure 16 est une représentation d’un espace d’adressage, avec l’espace racine et l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="c0f34-342">Voici un exemple de définition des préfixes de l’espace d’adressage de réseau Local autour de l’espace d’adressage « trous » créée par le VNet :</span><span class="sxs-lookup"><span data-stu-id="c0f34-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="c0f34-p114">Une organisation utilise des parties de l’espace d’adressage privé (10.0.0.0/8, 172.16.0.0/12 et 192.168.0.0/16) sur son réseau local. Elle choisit l’option 2 et utilise 10.100.100.0/24 comme espace d’adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="c0f34-345">Le tableau 7 présente les étapes de définition de l’espace d’adressage du réseau local pour cet exemple, avec les préfixes obtenus.</span><span class="sxs-lookup"><span data-stu-id="c0f34-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="c0f34-346">**Étape**</span><span class="sxs-lookup"><span data-stu-id="c0f34-346">**Step**</span></span>|<span data-ttu-id="c0f34-347">**Résultats**</span><span class="sxs-lookup"><span data-stu-id="c0f34-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0f34-348">1. Répertorier les préfixes qui ne correspondent pas à l’espace racine pour l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c0f34-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="c0f34-349">172.16.0.0/12 et 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="c0f34-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="c0f34-350">2. liste les préfixes sans chevauchement des octets variables jusqu'à, mais non compris le dernier octet utilisé dans l’espace d’adressage VNet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="c0f34-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 préfixes, en ignorant 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="c0f34-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="c0f34-352">3. liste des préfixes non qui se chevauchent dans le dernier octet utilisé de l’espace d’adressage VNet.</span><span class="sxs-lookup"><span data-stu-id="c0f34-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="c0f34-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 préfixes, en ignorant 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="c0f34-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="c0f34-354">**Tableau 7 : Exemple d’espace d’adressage du réseau local**</span><span class="sxs-lookup"><span data-stu-id="c0f34-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="c0f34-355">Étape 6 : configurez les serveurs DNS locaux pour la réplication DNS avec des serveurs DNS hébergés dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c0f34-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="c0f34-356">Pour vous assurer que les ordinateurs locaux peuvent résoudre les noms des serveurs Azure et que ces derniers peuvent résoudre les noms des ordinateurs locaux, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0f34-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="c0f34-357">Configurez les serveurs DNS de votre réseau virtuel pour le transfert vers des serveurs DNS locaux</span><span class="sxs-lookup"><span data-stu-id="c0f34-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="c0f34-358">Configurez la réplication DNS des zones appropriées entre les serveurs DNS locaux et ceux du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="c0f34-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="c0f34-359">**Figure 17 : Réplication et transfert DNS pour un serveur DNS d’un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figure 17 : réplication DNS et transfert pour un serveur DNS dans un réseau virtuel Azure intersites](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="c0f34-p115">La figure 17 présente un réseau virtuel intersites avec des serveurs DNS sur le réseau local et sur un sous-réseau du réseau virtuel. Le transfert et la réplication DNS ont été configurés entre les deux serveurs DNS.</span><span class="sxs-lookup"><span data-stu-id="c0f34-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="c0f34-363">Étape 7 : déterminez l’utilisation du tunneling forcé.</span><span class="sxs-lookup"><span data-stu-id="c0f34-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="c0f34-p116">L’itinéraire du système par défaut pour les sous-réseaux Azure pointe vers Internet. Pour vous assurer que tout le trafic des machines virtuelles parcourt la connexion entre différents locaux, créez une table de routage avec l’itinéraire par défaut qui utilise la passerelle Azure en tant que son adresse de tronçon suivant. Puis associer la table de routage du sous-réseau. Il s’agit comme forcée tunnel. Pour plus d’informations, voir [Configure forcée tunnel](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="c0f34-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="c0f34-369">**Figure 18 : Itinéraires définis par l’utilisateur et tunneling forcé pour un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="c0f34-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figure 18 : itinéraires définis par l’utilisateur et tunnel forcé pour un réseau virtuel Azure intersites](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="c0f34-371">La figure 18 montre un VNet entre différents locaux avec un itinéraire défini par l’utilisateur pour un sous-réseau pointant vers la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="c0f34-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="c0f34-372">Batterie SharePoint Server 2016 dans Azure</span><span class="sxs-lookup"><span data-stu-id="c0f34-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="c0f34-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="c0f34-373"></span></span>

<span data-ttu-id="c0f34-374">Un exemple d’un charge de travail informatique hébergée dans Azure IaaS intranet est une batterie de serveurs SharePoint Server 2016 hautement disponible, à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="c0f34-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="c0f34-375">**Figure 19 : Batterie de serveurs SharePoint Server 2016 intranet hautement disponible dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="c0f34-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Batterie SharePoint Server 2016 à disponibilité élevée dans Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="c0f34-p117">La figure 19 représente les neuf serveurs d’une batterie de serveurs SharePoint Server 2016 déployé dans un VNet entre différents locaux qui utilise des équilibreurs de charge interne pour les niveaux frontal et données. Pour plus d’informations, y compris la conception détaillée et des instructions de déploiement, voir [SharePoint Server 2016 dans Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0f34-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="c0f34-379">Pour créer une batterie de serveurs SharePoint Server 2016 serveur unique dans un VNet simulé intersite, voir [Intranet SharePoint Server 2016 dans l’environnement de développement/test Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0f34-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="c0f34-380">Pour obtenir des exemples supplémentaires des charges de travail informatique déployés sur des ordinateurs virtuels dans un Azure intersite virtuel réseau, voir les [scénarios de cloud hybride pour Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0f34-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0f34-381">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0f34-381">See also</span></span>

<span data-ttu-id="c0f34-382"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="c0f34-382"></span></span>

[<span data-ttu-id="c0f34-383">Mise en réseau cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="c0f34-383">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="c0f34-384">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c0f34-384">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="c0f34-385">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)
</span><span class="sxs-lookup"><span data-stu-id="c0f34-385">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



