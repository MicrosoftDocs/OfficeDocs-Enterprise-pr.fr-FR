---
title: Conception de réseaux pour Microsoft Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Résumé: Découvrez comment concevoir une mise en réseau optimisée pour les charges de travail dans Microsoft Azure IaaS.'
ms.openlocfilehash: c41e92445dd01a94b7d305b521bbd4330311fcb4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491026"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="38d6b-103">Conception de réseaux pour Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="38d6b-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="38d6b-104">**Résumé:** Découvrez comment concevoir une mise en réseau optimisée pour les charges de travail dans Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="38d6b-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="38d6b-105">L’optimisation du réseau pour les charges de travail informatiques hébergées dans Azure IaaS demande une bonne compréhension des réseaux virtuels Azure (VNets), des espaces d’adressage, du routage, de DNS et de l’équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="38d6b-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="38d6b-106">Étapes de préparation pour un réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="38d6b-106">Planning steps for any VNet</span></span>

<span data-ttu-id="38d6b-107">Suivez la procédure ci-dessous pour tout type de réseau virtuel (VNet).</span><span class="sxs-lookup"><span data-stu-id="38d6b-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="38d6b-108">Étape 1 : préparez votre intranet pour les services de cloud computing Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38d6b-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="38d6b-109">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="38d6b-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="38d6b-110">Étape 2 : optimisez votre bande passante Internet.</span><span class="sxs-lookup"><span data-stu-id="38d6b-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="38d6b-111">Optimisez votre bande passante Internet en suivant les étapes 2 à 4 de la **procédure de préparation de votre réseau pour les services Microsoft SaaS** fournie dans [Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="38d6b-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="38d6b-112">Étape 3 : déterminez le type du réseau virtuel (cloud uniquement ou intersites).</span><span class="sxs-lookup"><span data-stu-id="38d6b-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="38d6b-p101">Un réseau virtuel de type « cloud uniquement » n’a aucune connexion avec un réseau local. Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="38d6b-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="38d6b-115">**Figure 1 : Réseau virtuel de type « cloud uniquement »**</span><span class="sxs-lookup"><span data-stu-id="38d6b-115">**Figure 1: A cloud-only VNet**</span></span>

![Figure 1: réseau virtuel en nuage uniquement dans Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="38d6b-117">La figure 1 présente un ensemble de machines virtuelles placées dans un réseau virtuel de type « cloud uniquement ».</span><span class="sxs-lookup"><span data-stu-id="38d6b-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="38d6b-p102">Un réseau virtuel entre sites dispose d’une connexion VPN de site à site (S2S) ou ExpressRoute à un réseau local via une passerelle Azure. Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="38d6b-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="38d6b-120">**Figure 2 : Réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-120">**Figure 2: A cross-premises VNet**</span></span>

![Figure 2: réseau virtuel intersites dans Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="38d6b-122">La figure 2 présente un ensemble de machines virtuelles placées dans un réseau virtuel intersites, lequel est connecté à un réseau local.</span><span class="sxs-lookup"><span data-stu-id="38d6b-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="38d6b-123">Reportez-vous à la section [Étapes préparatoires pour un réseau virtuel intersites](designing-networking-for-microsoft-azure-iaas.md#cross_prem) de cet article.</span><span class="sxs-lookup"><span data-stu-id="38d6b-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="38d6b-124">Étape 4 : déterminez l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="38d6b-125">Le tableau 1 présente les espaces d’adressage correspondant aux différents types de réseaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="38d6b-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="38d6b-126">**Type de réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="38d6b-126">**Type of VNet**</span></span>|<span data-ttu-id="38d6b-127">**Espace d’adressage du réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="38d6b-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="38d6b-128">Cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="38d6b-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="38d6b-129">Espace d’adressage privé arbitraire</span><span class="sxs-lookup"><span data-stu-id="38d6b-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="38d6b-130">Cloud uniquement interconnecté</span><span class="sxs-lookup"><span data-stu-id="38d6b-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="38d6b-131">Privé arbitraire, mais sans chevauchement avec les autres réseaux virtuels connectés</span><span class="sxs-lookup"><span data-stu-id="38d6b-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="38d6b-132">Intersites</span><span class="sxs-lookup"><span data-stu-id="38d6b-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="38d6b-133">Privé, mais sans chevauchement avec les réseaux locaux</span><span class="sxs-lookup"><span data-stu-id="38d6b-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="38d6b-134">Intersites interconnecté</span><span class="sxs-lookup"><span data-stu-id="38d6b-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="38d6b-135">Privé, mais sans chevauchement avec les autres réseaux virtuels connectés et les réseaux locaux</span><span class="sxs-lookup"><span data-stu-id="38d6b-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-136">**Tableau 1 : types de réseaux virtuels et espaces d’adressage correspondants**</span><span class="sxs-lookup"><span data-stu-id="38d6b-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="38d6b-137">Une configuration d’adresse issue de l’espace d’adressage du sous-réseau est attribuée aux machines virtuelles par DHCP :</span><span class="sxs-lookup"><span data-stu-id="38d6b-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="38d6b-138">Adresse/masque de sous-réseau</span><span class="sxs-lookup"><span data-stu-id="38d6b-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="38d6b-139">Passerelle par défaut</span><span class="sxs-lookup"><span data-stu-id="38d6b-139">Default gateway</span></span>
    
- <span data-ttu-id="38d6b-140">Adresses IP du serveur DNS</span><span class="sxs-lookup"><span data-stu-id="38d6b-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="38d6b-141">Vous pouvez également réserver une adresse IP statique.</span><span class="sxs-lookup"><span data-stu-id="38d6b-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="38d6b-142">Une adresse IP publique peut également être attribuée aux machines virtuelles, individuellement ou à partir du service de cloud qui les contient (pour les ordinateurs avec déploiement classique uniquement).</span><span class="sxs-lookup"><span data-stu-id="38d6b-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="38d6b-143">Étape 5 : déterminez les sous-réseaux au sein du réseau virtuel et les espaces d’adressage affectés à chacun.</span><span class="sxs-lookup"><span data-stu-id="38d6b-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="38d6b-144">Il existe deux types de sous-réseaux dans un réseau virtuel : un sous-réseau de passerelle et un sous-réseau qui héberge les machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="38d6b-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="38d6b-145">**Figure 3 : les deux types de sous-réseaux dans Azure**</span><span class="sxs-lookup"><span data-stu-id="38d6b-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figure 3 : les deux types de sous-réseaux dans Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="38d6b-147">La figure 3 présente un réseau virtuel contenant un sous-réseau de passerelle doté d'une passerelle Azure et d'un ensemble de sous-réseaux hébergeant des machines virtuelles contenant des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="38d6b-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="38d6b-148">Le sous-réseau de passerelle Azure est requis par Azure pour héberger les deux machines virtuelles de votre passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="38d6b-149">Spécifiez un espace d’adressage avec une longueur de préfixe d’au moins 29 bits (exemple : 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="38d6b-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="38d6b-150">Une longueur de préfixe de 27 bits ou plus petite est recommandée, en particulier si vous envisagez d'utiliser ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="38d6b-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="38d6b-151">Pour déterminer l'espace d'adressage du sous-réseau de la passerelle Azure, il est recommandé de procéder comme suit:</span><span class="sxs-lookup"><span data-stu-id="38d6b-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="38d6b-152">Décidez de la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="38d6b-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="38d6b-153">Dans la variable bits de l’espace d’adressage du réseau virtuel, définissez la valeur de bits utilisée pour le sous-réseau de passerelle sur 0 et définissez les autres sur 1.</span><span class="sxs-lookup"><span data-stu-id="38d6b-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="38d6b-154">Convertissez les valeurs en nombres décimaux et exprimez-les sous forme d’espace d’adressage, en définissant la longueur du préfixe sur une valeur équivalente à la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="38d6b-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="38d6b-155">Avec cette méthode, l’espace d’adressage du sous-réseau de passerelle est toujours à l’extrémité de l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="38d6b-p104">Vous avez ci-dessous un exemple de définition du préfixe d’adresse pour le sous-réseau de passerelle : l’espace d’adressage du réseau virtuel est 10.119.0.0/16. L’organisation utilisera initialement une connexion VPN de site à site, mais emploiera ensuite ExpressRoute. Le tableau 2 indique les étapes pour déterminer le préfixe d’adresse pour le sous-réseau de passerelle, ainsi que leur résultat, dans la notation de préfixe réseau (également connue sous le nom de CIDR).</span><span class="sxs-lookup"><span data-stu-id="38d6b-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="38d6b-159">Voici les étapes et l'exemple de la détermination du préfixe d'adresse de sous-réseau de passerelle:</span><span class="sxs-lookup"><span data-stu-id="38d6b-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="38d6b-160">Décidez de la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="38d6b-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="38d6b-161">Pour notre exemple, nous avons choisi/28.</span><span class="sxs-lookup"><span data-stu-id="38d6b-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="38d6b-162">Définissez les bits dans la partie variable de l'espace d'adressage de réseau virtuel (b) sur 0 pour les bits de sous-réseau de passerelle (G), sinon 1 (V).</span><span class="sxs-lookup"><span data-stu-id="38d6b-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="38d6b-163">Pour notre exemple, nous utilisons l'espace d'adressage 10.119.0.0/16 pour le réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="38d6b-164">10,119.</span><span class="sxs-lookup"><span data-stu-id="38d6b-164">10.119.</span></span> <span data-ttu-id="38d6b-165">bbbbbbbb.</span><span class="sxs-lookup"><span data-stu-id="38d6b-165">bbbbbbbb .</span></span> <span data-ttu-id="38d6b-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="38d6b-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="38d6b-167">10,119.</span><span class="sxs-lookup"><span data-stu-id="38d6b-167">10.119.</span></span> <span data-ttu-id="38d6b-168">VVVVVVVV.</span><span class="sxs-lookup"><span data-stu-id="38d6b-168">VVVVVVVV .</span></span> <span data-ttu-id="38d6b-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="38d6b-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="38d6b-170">10,119.</span><span class="sxs-lookup"><span data-stu-id="38d6b-170">10.119.</span></span> <span data-ttu-id="38d6b-171">11111111.</span><span class="sxs-lookup"><span data-stu-id="38d6b-171">11111111 .</span></span> <span data-ttu-id="38d6b-172">11110000</span><span class="sxs-lookup"><span data-stu-id="38d6b-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="38d6b-173">Convertissez le résultat de l'étape 2 en Decimal et Express en tant qu'espace d'adressage.</span><span class="sxs-lookup"><span data-stu-id="38d6b-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="38d6b-174">Pour notre exemple, 10,119.</span><span class="sxs-lookup"><span data-stu-id="38d6b-174">For our example, 10.119.</span></span> <span data-ttu-id="38d6b-175">11111111.</span><span class="sxs-lookup"><span data-stu-id="38d6b-175">11111111 .</span></span> <span data-ttu-id="38d6b-176">11110000 est 10.119.255.240, et avec la longueur de préfixe de l'étape 1 (28 dans notre exemple), le préfixe d'adresse de sous-réseau de passerelle résultant est 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="38d6b-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="38d6b-177">Pour plus d'informations, voir [calculatrice d'espace d'adressage pour les sous-réseaux de la passerelle Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="38d6b-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="38d6b-178">Les machines virtuelles Azure doivent être placées dans des sous-réseaux dédiés à l’hébergement des machines virtuelles. Pour cela, vous pouvez suivre les consignes standard pour les configurations locales, par exemple, en fonction d’un rôle ou d’un niveau d’application commun ou de manière à isoler les sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="38d6b-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="38d6b-179">Azure utilise les trois premières adresses sur chaque sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="38d6b-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="38d6b-180">Par conséquent, le nombre d'adresses possibles sur un sous-réseau Azure est 2<sup>n</sup> -5, où n est le nombre de bits d'hôte.</span><span class="sxs-lookup"><span data-stu-id="38d6b-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="38d6b-181">Le tableau 3 indique la plage de machines virtuelles requises, le nombre de bits nécessaires pour l’hôte et la taille de sous-réseau correspondante.</span><span class="sxs-lookup"><span data-stu-id="38d6b-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="38d6b-182">**Machines virtuelles requises**</span><span class="sxs-lookup"><span data-stu-id="38d6b-182">**Virtual machines required**</span></span>|<span data-ttu-id="38d6b-183">**Bits hôte**</span><span class="sxs-lookup"><span data-stu-id="38d6b-183">**Host bits**</span></span>|<span data-ttu-id="38d6b-184">**Taille sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="38d6b-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="38d6b-185">1-3</span><span class="sxs-lookup"><span data-stu-id="38d6b-185">1-3</span></span>  <br/> |<span data-ttu-id="38d6b-186">3</span><span class="sxs-lookup"><span data-stu-id="38d6b-186">3</span></span>  <br/> |<span data-ttu-id="38d6b-187">/29</span><span class="sxs-lookup"><span data-stu-id="38d6b-187">/29</span></span>  <br/> |
|<span data-ttu-id="38d6b-188">4-11</span><span class="sxs-lookup"><span data-stu-id="38d6b-188">4-11</span></span>  <br/> |<span data-ttu-id="38d6b-189">4</span><span class="sxs-lookup"><span data-stu-id="38d6b-189">4</span></span>  <br/> |<span data-ttu-id="38d6b-190">/28</span><span class="sxs-lookup"><span data-stu-id="38d6b-190">/28</span></span>  <br/> |
|<span data-ttu-id="38d6b-191">12-27</span><span class="sxs-lookup"><span data-stu-id="38d6b-191">12-27</span></span>  <br/> |<span data-ttu-id="38d6b-192">disque</span><span class="sxs-lookup"><span data-stu-id="38d6b-192">5</span></span>  <br/> |<span data-ttu-id="38d6b-193">/27</span><span class="sxs-lookup"><span data-stu-id="38d6b-193">/27</span></span>  <br/> |
|<span data-ttu-id="38d6b-194">28-59</span><span class="sxs-lookup"><span data-stu-id="38d6b-194">28-59</span></span>  <br/> |<span data-ttu-id="38d6b-195">6.x</span><span class="sxs-lookup"><span data-stu-id="38d6b-195">6</span></span>  <br/> |<span data-ttu-id="38d6b-196">/26</span><span class="sxs-lookup"><span data-stu-id="38d6b-196">/26</span></span>  <br/> |
|<span data-ttu-id="38d6b-197">60-123</span><span class="sxs-lookup"><span data-stu-id="38d6b-197">60-123</span></span>  <br/> |<span data-ttu-id="38d6b-198">7j/7</span><span class="sxs-lookup"><span data-stu-id="38d6b-198">7</span></span>  <br/> |<span data-ttu-id="38d6b-199">/25</span><span class="sxs-lookup"><span data-stu-id="38d6b-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-200">**Tableau 3 : Configuration requise pour les machines virtuelles et tailles de sous-réseau correspondantes**</span><span class="sxs-lookup"><span data-stu-id="38d6b-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="38d6b-201">Pour plus d'informations sur la quantité maximale de machines virtuelles sur un sous-réseau ou un réseau virtuel, voir [limites de mise en réseau](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="38d6b-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="38d6b-202">Pour plus d'informations, voir [planifier et concevoir des réseaux virtuels Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="38d6b-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="38d6b-203">Étape 6 : déterminez la configuration du serveur DNS et les adresses des serveurs DNS à affecter aux machines virtuelles dans le réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="38d6b-p112">Azure attribue aux machines virtuelles les adresses des serveurs DNS par DHCP. Les serveurs DNS peuvent être :</span><span class="sxs-lookup"><span data-stu-id="38d6b-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="38d6b-206">Fournis par Azure : fournit l’enregistrement du nom en local, ainsi que la résolution des noms sur Internet et en local</span><span class="sxs-lookup"><span data-stu-id="38d6b-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="38d6b-207">Fournis par vous : fournit l’inscription des noms en local ou sur l’intranet, ainsi que la résolution des noms sur Internet ou l’intranet</span><span class="sxs-lookup"><span data-stu-id="38d6b-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="38d6b-208">Le tableau 4 présente les différentes configurations des serveurs DNS pour chaque type de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="38d6b-209">**Type de réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="38d6b-209">**Type of VNet**</span></span>|<span data-ttu-id="38d6b-210">**Serveur DNS**</span><span class="sxs-lookup"><span data-stu-id="38d6b-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="38d6b-211">Cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="38d6b-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="38d6b-212">Fourni par Azure pour la résolution des noms sur Internet et en local</span><span class="sxs-lookup"><span data-stu-id="38d6b-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="38d6b-213">Machine virtuelle Azure pour la résolution des noms sur Internet et en local (transfert DNS)</span><span class="sxs-lookup"><span data-stu-id="38d6b-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="38d6b-214">Intersites</span><span class="sxs-lookup"><span data-stu-id="38d6b-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="38d6b-215">En local pour la résolution des noms sur l’intranet et en local</span><span class="sxs-lookup"><span data-stu-id="38d6b-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="38d6b-216">Machine virtuelle Azure pour la résolution des noms sur l’intranet et en local (réplication et transfert DNS)</span><span class="sxs-lookup"><span data-stu-id="38d6b-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-217">**Tableau 4 : Options de serveur DNS pour les deux types de réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="38d6b-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="38d6b-218">Pour plus d'informations, consultez la rubrique [résolution de noms pour les machines virtuelles et les instances de rôles](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="38d6b-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="38d6b-219">Étape 7 : déterminez la configuration d’équilibrage de charge (connectée à Internet ou interne).</span><span class="sxs-lookup"><span data-stu-id="38d6b-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="38d6b-p113">Dans certains cas, vous devez distribuer le trafic entrant vers un ensemble de serveurs qui ont le même rôle. Le service IaaS Azure dispose d’une fonction intégrée permettant d’effectuer cette action pour les charges de trafic Internet ou internes.</span><span class="sxs-lookup"><span data-stu-id="38d6b-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="38d6b-222">L’équilibrage de charge Azure pour Internet distribue le trafic entrant non sollicité de façon aléatoire d’Internet vers les membres d’un jeu d’équilibrage de charge. </span><span class="sxs-lookup"><span data-stu-id="38d6b-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="38d6b-223">**Figure 4 : Équilibrage de charge externe dans Azure**</span><span class="sxs-lookup"><span data-stu-id="38d6b-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figure 4 : Équilibrage de charge externe dans Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="38d6b-225">La figure 4 illustre un programme d'équilibrage de la charge externe dans Azure qui distribue le trafic entrant sur une règle NAT entrante ou un point de terminaison à un ensemble de machines virtuelles dans un ensemble à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="38d6b-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="38d6b-226">L’équilibrage de charge interne d’Azure répartit le trafic entrant non sollicité de façon aléatoire des machines virtuelles Azure vers les membres d’un jeu d’équilibrage de charge. </span><span class="sxs-lookup"><span data-stu-id="38d6b-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="38d6b-227">**Figure 5 : Équilibrage de charge interne dans Azure**</span><span class="sxs-lookup"><span data-stu-id="38d6b-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figure 5 : Équilibrage de charge interne dans Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="38d6b-229">La figure 5 illustre un programme d'équilibrage de charge interne dans Azure qui distribue le trafic entrant sur une règle NAT entrante ou un point de terminaison à un ensemble de machines virtuelles dans un ensemble à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="38d6b-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="38d6b-230">Pour plus d'informations, consultez la rubrique relative à l'équilibreur de [charge Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="38d6b-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="38d6b-231">Étape 8 : déterminez l’utilisation des appliances virtuelles et des itinéraires définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38d6b-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="38d6b-232">Si vous devez transmettre du trafic vers des appliances virtuelles dans votre réseau virtuel, vous devrez peut-être ajouter un ou plusieurs itinéraires définis par l’utilisateur à un sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="38d6b-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="38d6b-233">**Figure 6 : Appliances virtuelles et itinéraires définis par l’utilisateur dans Azure**</span><span class="sxs-lookup"><span data-stu-id="38d6b-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figure 6 : Appliances virtuelles et itinéraires définis par l’utilisateur dans Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="38d6b-235">La figure 6 présente un réseau virtuel intersites et un itinéraire définis par l’utilisateur affecté à un sous-réseau hébergeant des machines virtuelles qui pointe vers une appliance virtuelle.</span><span class="sxs-lookup"><span data-stu-id="38d6b-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="38d6b-236">Pour plus d'informations, consultez la rubrique [itinéraires définis par l'utilisateur et transfert IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="38d6b-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="38d6b-237">Étape 9 : déterminez le mode de connexion aux machines virtuelles des ordinateurs sur Internet.</span><span class="sxs-lookup"><span data-stu-id="38d6b-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="38d6b-238">Il existe plusieurs méthodes pour fournir un accès Internet aux machines virtuelles sur un réseau virtuel, qui inclut l’accès à partir du réseau de votre entreprise via votre serveur proxy ou un autre appareil Edge.</span><span class="sxs-lookup"><span data-stu-id="38d6b-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="38d6b-239">Le tableau 5 présente les méthodes de filtrage ou de contrôle du trafic entrant non sollicité.</span><span class="sxs-lookup"><span data-stu-id="38d6b-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="38d6b-240">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="38d6b-240">**Method**</span></span>|<span data-ttu-id="38d6b-241">**Modèle de déploiement**</span><span class="sxs-lookup"><span data-stu-id="38d6b-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="38d6b-242">1. Points de terminaison et listes de contrôle d’accès configurés sur les services de cloud</span><span class="sxs-lookup"><span data-stu-id="38d6b-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="38d6b-243">Classiques</span><span class="sxs-lookup"><span data-stu-id="38d6b-243">Classic</span></span>  <br/> |
|<span data-ttu-id="38d6b-244">2. Groupes de sécurité réseau</span><span class="sxs-lookup"><span data-stu-id="38d6b-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="38d6b-245">Resource Manager et classique</span><span class="sxs-lookup"><span data-stu-id="38d6b-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="38d6b-246">3. Équilibrage de charge connecté à Internet avec règles NAT de trafic entrant</span><span class="sxs-lookup"><span data-stu-id="38d6b-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="38d6b-247">Responsable de ressources</span><span class="sxs-lookup"><span data-stu-id="38d6b-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="38d6b-248">4. appliances de sécurité réseau sur Azure Marketplace (non illustré)</span><span class="sxs-lookup"><span data-stu-id="38d6b-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="38d6b-249">Resource Manager et classique</span><span class="sxs-lookup"><span data-stu-id="38d6b-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-250">**Tableau 5 : Méthodes de connexion aux machines virtuelles et modèles de déploiement Azure correspondantes**</span><span class="sxs-lookup"><span data-stu-id="38d6b-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="38d6b-251">**Figure 7 : Connexion à des machines virtuelles Azure via Internet**</span><span class="sxs-lookup"><span data-stu-id="38d6b-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figure 7 : Connexion à des machines virtuelles Azure via Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="38d6b-253">La figure 7 présente un ordinateur connecté à Internet qui se connecte à une machine virtuelle dans un service cloud à l’aide d’un point de terminaison, à une machine virtuelle dans un sous-réseau à l’aide d’un groupe de sécurité réseau et à une machine virtuelle dans un sous-réseau en utilisant un programme d’équilibrage de charge externe et des règles NAT de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="38d6b-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="38d6b-254">Les éléments suivants offrent un degré de sécurité supplémentaire :</span><span class="sxs-lookup"><span data-stu-id="38d6b-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="38d6b-255">Connexions de bureau à distance et SSH, authentifiées et chiffrées.</span><span class="sxs-lookup"><span data-stu-id="38d6b-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="38d6b-256">Sessions Remote PowerShell, authentifiées et chiffrées.</span><span class="sxs-lookup"><span data-stu-id="38d6b-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="38d6b-257">Mode de transport IPsec, que vous pouvez utiliser pour le chiffrement de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="38d6b-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="38d6b-258">Protection par déni de service distribué Azure, qui permet d’éviter les attaques internes et externes</span><span class="sxs-lookup"><span data-stu-id="38d6b-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="38d6b-259">Pour plus d'informations, consultez la rubrique [sécurité Cloud Microsoft pour les architectes d'entreprise](https://aka.ms/cloudarchsecurity) et [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="38d6b-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="38d6b-260">Étape 10 : pour plusieurs réseaux virtuels, déterminez la topologie de connexion de réseau virtuel à réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="38d6b-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="38d6b-261">Les réseaux virtuels peuvent être connectés à l’aide de topologies semblables à celles utilisées pour connecter les sites d’une organisation.</span><span class="sxs-lookup"><span data-stu-id="38d6b-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="38d6b-262">Une configuration en série connecte les réseaux virtuels les uns après les autres.</span><span class="sxs-lookup"><span data-stu-id="38d6b-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="38d6b-263">**Figure 8 : Configuration en série pour des réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="38d6b-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figure 8: configuration en cascade pour les réseaux virtuels Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="38d6b-265">La figure 8 illustre cinq réseaux virtuels connectés en série à l'aide d'une configuration en cascade.</span><span class="sxs-lookup"><span data-stu-id="38d6b-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="38d6b-266">Une configuration « Hub and Spoke » connecte plusieurs réseaux virtuels à un ensemble de réseaux virtuels centraux, qui sont eux-mêmes connectés entre eux.</span><span class="sxs-lookup"><span data-stu-id="38d6b-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="38d6b-267">**Figure 9 : Configuration Hub and Spoke pour réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="38d6b-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figure 9: configuration d'un spoke et d'un concentrateur pour les réseaux virtuels Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="38d6b-269">La figure 9 présente six réseaux virtuels, dont deux sont des hubs centraux connectés l’un à l’autre, chacun étant également connecté à deux autres réseaux virtuels périphériques.</span><span class="sxs-lookup"><span data-stu-id="38d6b-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="38d6b-270">Une configuration en maille complète connecte chaque réseau virtuel entre eux.</span><span class="sxs-lookup"><span data-stu-id="38d6b-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="38d6b-271">**Figure 10 : Configuration en maille complète pour réseaux virtuels**</span><span class="sxs-lookup"><span data-stu-id="38d6b-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figure 10: configuration de maille pour les réseaux virtuels Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="38d6b-273">La figure 10 présente quatre réseaux virtuels connectés les uns aux autres, pour un total de six connexions de réseau virtuel à réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="38d6b-274">Étapes préparatoires pour un réseau virtuel intersites</span><span class="sxs-lookup"><span data-stu-id="38d6b-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="38d6b-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="38d6b-275"></span></span>

<span data-ttu-id="38d6b-276">Suivez la procédure ci-dessous pour un réseau virtuel intersites.</span><span class="sxs-lookup"><span data-stu-id="38d6b-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="38d6b-277">Pour créer un environnement de développement/test intersites, voir [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="38d6b-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="38d6b-278">Étape 1 : déterminez la connexion intersites au réseau virtuel (VPN S2S ou ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="38d6b-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="38d6b-279">Le tableau 6 présente les différents types de connexions.</span><span class="sxs-lookup"><span data-stu-id="38d6b-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="38d6b-280">**Type de connexion**</span><span class="sxs-lookup"><span data-stu-id="38d6b-280">**Type of connection**</span></span>|<span data-ttu-id="38d6b-281">**Objectif**</span><span class="sxs-lookup"><span data-stu-id="38d6b-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="38d6b-282">VPN de site à site (S2S)</span><span class="sxs-lookup"><span data-stu-id="38d6b-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="38d6b-283">Connectez les sites 1-10 (y compris les autres réseaux virtuels) à un seul réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="38d6b-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="38d6b-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="38d6b-285">Lien privé sécurisé à Azure via un fournisseur d’échange Internet (IXP) ou un fournisseur de service réseau (NSP).</span><span class="sxs-lookup"><span data-stu-id="38d6b-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="38d6b-286">VPN de point à site (P2S)</span><span class="sxs-lookup"><span data-stu-id="38d6b-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="38d6b-287">Connecte un seul ordinateur à un réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="38d6b-288">VPN de réseau virtuel à réseau virtuel (V2V) ou homologation de réseau virtuel </span><span class="sxs-lookup"><span data-stu-id="38d6b-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="38d6b-289">Connecte un réseau virtuel à un autre réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-290">**Tableau 6 : Types de connexions pour les réseaux virtuels intersites**</span><span class="sxs-lookup"><span data-stu-id="38d6b-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="38d6b-291">Pour plus d'informations sur le nombre maximal de connexions, voir [limites de mise en réseau](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="38d6b-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="38d6b-292">Pour plus d'informations sur les périphériques VPN, consultez [la rubrique périphériques VPN pour les connexions de réseau virtuel de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="38d6b-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="38d6b-293">Pour plus d'informations sur l'homologation VNet, voir [vnet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="38d6b-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="38d6b-294">**Figure 11 : Les quatre méthodes de connexion à un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figure 11: les trois méthodes de connexion à un réseau virtuel Azure intersites](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="38d6b-296">La figure 11 illustre un réseau virtuel avec quatre types de connexions: une connexion P2S à partir d'un ordinateur, une connexion VPN S2S à partir d'un réseau local, une connexion ExpressRoute à partir d'un réseau local et une connexion de réseau virtuel à réseau virtuel à partir d'un autre réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="38d6b-297">Vous pouvez vous connecter aux machines virtuelles dans un réseau virtuel des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="38d6b-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="38d6b-298">Administration des machines virtuelles de réseau virtuel à partir de votre réseau local ou d’Internet</span><span class="sxs-lookup"><span data-stu-id="38d6b-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="38d6b-299">Accès aux charges de travail informatique à partir de votre réseau local</span><span class="sxs-lookup"><span data-stu-id="38d6b-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="38d6b-300">Extension de votre réseau via des réseaux virtuels supplémentaires</span><span class="sxs-lookup"><span data-stu-id="38d6b-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="38d6b-301">La sécurité des connexions est assurée des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="38d6b-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="38d6b-302">Les connexions P2S utilisent le protocole SSTP (Secure Socket Tunneling Protocol) </span><span class="sxs-lookup"><span data-stu-id="38d6b-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="38d6b-303">Les connexions VPN de réseau virtuel à réseau virtuel et S2S utilisent le mode de tunnel IPsec avec AES256.</span><span class="sxs-lookup"><span data-stu-id="38d6b-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="38d6b-304">ExpressRoute est une connexion WAN privée</span><span class="sxs-lookup"><span data-stu-id="38d6b-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="38d6b-305">Pour plus d'informations, consultez la rubrique [sécurité Cloud Microsoft pour les architectes d'entreprise](https://aka.ms/cloudarchsecurity) et [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="38d6b-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="38d6b-306">Étape 2 : déterminez le routeur ou le périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="38d6b-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="38d6b-307">Votre routeur ou votre périphérique VPN local fait office :</span><span class="sxs-lookup"><span data-stu-id="38d6b-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="38d6b-308">D’homologue IPsec, qui termine la connexion VPN S2S à partir de la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="38d6b-309">D’homologue BPG et de point de terminaison pour la connexion ExpressRoute à homologation privée.</span><span class="sxs-lookup"><span data-stu-id="38d6b-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="38d6b-310">**Figure 12 : Routeur ou appareil VPN**</span><span class="sxs-lookup"><span data-stu-id="38d6b-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Figure 12 : Routeur ou appareil VPN](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="38d6b-312">La figure 12 présente un réseau virtuel intersites connecté à un routeur ou périphérique VPN local.</span><span class="sxs-lookup"><span data-stu-id="38d6b-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="38d6b-313">Pour plus d'informations, consultez la rubrique [à propos de la passerelle VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="38d6b-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="38d6b-314">Étape 3: ajouter des itinéraires à votre intranet pour que l'espace d'adressage du réseau virtuel soit accessible.</span><span class="sxs-lookup"><span data-stu-id="38d6b-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="38d6b-315">La configuration de routage vers des réseaux virtuels à partir de l’environnement local comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="38d6b-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="38d6b-316">Un itinéraire pour l’espace d’adressage de réseau virtuel qui pointe vers votre périphérique VPN.</span><span class="sxs-lookup"><span data-stu-id="38d6b-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="38d6b-317">Un itinéraire pour l’espace d’adressage de réseau virtuel sur votre périphérique VPN qui pointe vers la connexion VPN S2S ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="38d6b-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="38d6b-318">**Figure 13 : Itinéraires locaux nécessaires pour rendre un réseau virtuel accessible**</span><span class="sxs-lookup"><span data-stu-id="38d6b-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figure 13: itinéraires locaux nécessaires pour faire en sorte qu'un réseau virtuel Azure soit accessible](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="38d6b-320">La figure 13 présente les informations de routage requises par les routeurs locaux et le routeur ou le périphérique VPN qui représente l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="38d6b-321">Étape 4 : pour ExpressRoute, préparez la nouvelle connexion avec l’aide de votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="38d6b-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="38d6b-322">Il existe trois méthodes pour créer une connexion ExpressRoute avec homologation privée entre votre réseau local et le cloud Microsoft :</span><span class="sxs-lookup"><span data-stu-id="38d6b-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="38d6b-323">Colocation sur un échange cloud</span><span class="sxs-lookup"><span data-stu-id="38d6b-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="38d6b-324">Connexions Ethernet de point à point</span><span class="sxs-lookup"><span data-stu-id="38d6b-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="38d6b-325">Réseaux à connectivité complète (IP VPN)</span><span class="sxs-lookup"><span data-stu-id="38d6b-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="38d6b-326">**Figure 14 : Utilisation d’ExpressRoute pour établir une connexion vers un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figure 14: utilisation de ExpressRoute pour se connecter à un réseau virtuel Azure entre différents locaux](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="38d6b-328">La figure 14 présente un réseau virtuel intersites et une connexion ExpressRoute d’un routeur local vers Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="38d6b-329">Pour plus d'informations, voir [ExpressRoute pour la connectivité au cloud de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="38d6b-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="38d6b-330">Étape 5 : déterminez l’espace d’adressage du réseau Local pour la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="38d6b-331">Pour le routage vers des réseaux locaux ou d’autres réseaux virtuels à partir d’un réseau virtuel, Azure transfère le trafic via une passerelle Azure qui utilise l’espace d’adressage de réseau local affecté à la passerelle.</span><span class="sxs-lookup"><span data-stu-id="38d6b-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="38d6b-332">**Figure 15 : Espace d’adressage de réseau local pour un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figure 15: espace d'adressage de réseau local pour un réseau virtuel Azure entre différents locaux](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="38d6b-334">La figure 15 présente un réseau virtuel intersites et l’espace d’adressage du réseau local sur la passerelle Azure, qui représente l’espace d’adressage accessible sur le réseau local. </span><span class="sxs-lookup"><span data-stu-id="38d6b-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="38d6b-335">Vous pouvez définir l'espace d'adressage du réseau local de l'une des manières suivantes:</span><span class="sxs-lookup"><span data-stu-id="38d6b-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="38d6b-336">Option 1 : liste des préfixes pour l’espace d’adressage actuellement nécessaire ou utilisé (des mises à jour peuvent être nécessaire lorsque vous ajoutez de nouveaux sous-réseaux).</span><span class="sxs-lookup"><span data-stu-id="38d6b-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="38d6b-337">Option 2 : intégralité de votre espace d’adressage local (des mises à jour sont uniquement nécessaires lorsque vous ajoutez le nouvel espace d’adressage).</span><span class="sxs-lookup"><span data-stu-id="38d6b-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="38d6b-338">Étant donné que la passerelle Azure n’autorise pas les itinéraires résumés, vous devez définir l’espace d’adressage du réseau local pour l’option 2 afin qu’il n’inclue pas l’espace d’adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="38d6b-339">**Figure 16 : Trou dans l’espace d’adressage, créé par l’espace d’adressage réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="38d6b-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figure 16: trou d'espace d'adressage créé par l'espace d'adressage du réseau virtuel](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="38d6b-341">La figure 16 est une représentation d’un espace d’adressage, avec l’espace racine et l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="38d6b-342">Voici un exemple de définition des préfixes pour l'espace d'adressage du réseau local entourant l'espace d'adressage «Hole» créé par le réseau virtuel:</span><span class="sxs-lookup"><span data-stu-id="38d6b-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="38d6b-p114">Une organisation utilise des parties de l’espace d’adressage privé (10.0.0.0/8, 172.16.0.0/12 et 192.168.0.0/16) sur son réseau local. Elle choisit l’option 2 et utilise 10.100.100.0/24 comme espace d’adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="38d6b-345">Le tableau 7 présente les étapes de définition de l’espace d’adressage du réseau local pour cet exemple, avec les préfixes obtenus.</span><span class="sxs-lookup"><span data-stu-id="38d6b-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="38d6b-346">**Étape**</span><span class="sxs-lookup"><span data-stu-id="38d6b-346">**Step**</span></span>|<span data-ttu-id="38d6b-347">**Results**</span><span class="sxs-lookup"><span data-stu-id="38d6b-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="38d6b-348">1. Répertorier les préfixes qui ne correspondent pas à l’espace racine pour l’espace d’adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="38d6b-349">172.16.0.0/12 et 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="38d6b-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="38d6b-350">2. répertoriez les préfixes qui ne se chevauchent pas pour des octets variables jusqu'au dernier octet utilisé (non compris) dans l'espace d'adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="38d6b-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (préfixes 255, ignorer 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="38d6b-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="38d6b-352">3. répertoriez les préfixes qui ne se chevauchent pas dans le dernier octet utilisé de l'espace d'adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="38d6b-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="38d6b-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (préfixes 255, ignorer 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="38d6b-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="38d6b-354">**Tableau 7 : Exemple d’espace d’adressage du réseau local**</span><span class="sxs-lookup"><span data-stu-id="38d6b-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="38d6b-355">Étape 6 : configurez les serveurs DNS locaux pour la réplication DNS avec des serveurs DNS hébergés dans Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="38d6b-356">Pour vous assurer que les ordinateurs locaux peuvent résoudre les noms des serveurs Azure et que ces derniers peuvent résoudre les noms des ordinateurs locaux, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38d6b-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="38d6b-357">Configurez les serveurs DNS de votre réseau virtuel pour le transfert vers des serveurs DNS locaux</span><span class="sxs-lookup"><span data-stu-id="38d6b-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="38d6b-358">Configurez la réplication DNS des zones appropriées entre les serveurs DNS locaux et ceux du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="38d6b-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="38d6b-359">**Figure 17 : Réplication et transfert DNS pour un serveur DNS d’un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figure 17: réplication et transfert DNS pour un serveur DNS dans un réseau virtuel Azure entre différents locaux](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="38d6b-p115">La figure 17 présente un réseau virtuel intersites avec des serveurs DNS sur le réseau local et sur un sous-réseau du réseau virtuel. Le transfert et la réplication DNS ont été configurés entre les deux serveurs DNS.</span><span class="sxs-lookup"><span data-stu-id="38d6b-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="38d6b-363">Étape 7 : déterminez l’utilisation du tunneling forcé.</span><span class="sxs-lookup"><span data-stu-id="38d6b-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="38d6b-364">L'itinéraire système par défaut pour les sous-réseaux Azure pointe vers Internet.</span><span class="sxs-lookup"><span data-stu-id="38d6b-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="38d6b-365">Pour vous assurer que tout le trafic provenant des machines virtuelles circule sur la connexion intersite, créez une table de routage avec l'itinéraire par défaut qui utilise la passerelle Azure comme adresse de tronçon suivant.</span><span class="sxs-lookup"><span data-stu-id="38d6b-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="38d6b-366">Vous associez ensuite la table d'itinéraires au sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="38d6b-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="38d6b-367">C’est ce qu’on appelle le tunneling forcé.</span><span class="sxs-lookup"><span data-stu-id="38d6b-367">This is known as forced tunneling.</span></span> <span data-ttu-id="38d6b-368">Pour plus d'informations, [](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)consultez la rubrique Configure Forced tunneling.</span><span class="sxs-lookup"><span data-stu-id="38d6b-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="38d6b-369">**Figure 18 : Itinéraires définis par l’utilisateur et tunneling forcé pour un réseau virtuel entre différents locaux**</span><span class="sxs-lookup"><span data-stu-id="38d6b-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figure 18: itinéraires définis par l'utilisateur et tunneling forcé pour un réseau virtuel Azure entre différents locaux](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="38d6b-371">La figure 18 illustre un réseau virtuel intersites avec un itinéraire défini par l'utilisateur pour un sous-réseau pointant vers la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="38d6b-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="38d6b-372">Batterie SharePoint Server 2016 dans Azure</span><span class="sxs-lookup"><span data-stu-id="38d6b-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="38d6b-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="38d6b-373"></span></span>

<span data-ttu-id="38d6b-374">Un exemple de charge de travail informatique intranet hébergée dans Azure IaaS est une batterie de serveurs SharePoint Server 2016 à plusieurs niveaux hautement disponible.</span><span class="sxs-lookup"><span data-stu-id="38d6b-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="38d6b-375">**Figure 19 : Batterie de serveurs SharePoint Server 2016 intranet hautement disponible dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="38d6b-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Une batterie de serveurs SharePoint Server 2016 haute disponibilité dans Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="38d6b-377">La figure 19 illustre les neuf serveurs d'une batterie de serveurs SharePoint Server 2016 déployée dans un réseau virtuel intersites qui utilise des programmes d'équilibrage de charge interne pour les niveaux de données frontaux et de données.</span><span class="sxs-lookup"><span data-stu-id="38d6b-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="38d6b-378">Pour plus d'informations, y compris des instructions étape par étape de conception et de déploiement, voir [SharePoint Server 2016 dans Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span><span class="sxs-lookup"><span data-stu-id="38d6b-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="38d6b-379">Pour créer une batterie de serveurs SharePoint Server 2016 à un seul serveur dans un réseau virtuel intersites simulé, voir [Intranet SharePoint server 2016 dans un environnement de développement/test Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span><span class="sxs-lookup"><span data-stu-id="38d6b-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="38d6b-380">Pour obtenir des exemples supplémentaires de charges de travail informatiques déployées sur des machines virtuelles dans un réseau virtuel Azure entre différents locaux, consultez la rubrique [scénarios de Cloud hybride pour Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span><span class="sxs-lookup"><span data-stu-id="38d6b-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="38d6b-381">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d6b-381">See also</span></span>

[<span data-ttu-id="38d6b-382">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="38d6b-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="38d6b-383">Ressources relatives à l’architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="38d6b-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


