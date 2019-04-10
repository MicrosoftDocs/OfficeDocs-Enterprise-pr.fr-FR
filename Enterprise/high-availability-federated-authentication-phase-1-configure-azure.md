---
title: Authentification fédérée haute disponibilité, phase 1 configurer Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Résumé: conFigurez l'infrastructure Microsoft Azure pour qu'elle héberge l'authentification fédérée haute disponibilité pour Office 365."
ms.openlocfilehash: 937f22c4e54fa4ccc81a1770a3c924e1d9d07a91
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741310"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="a5c14-103">Authentification fédérée haute disponibilité, phase 1 : Configurer Azure</span><span class="sxs-lookup"><span data-stu-id="a5c14-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="a5c14-104">**Résumé:** ConFigurez l'infrastructure Microsoft Azure pour qu'elle héberge l'authentification fédérée haute disponibilité pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5c14-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="a5c14-105">Dans cette phase, vous créez les groupes de ressources, le réseau virtuel et les groupes à haute disponibilité dans Azure qui hébergeront les machines virtuelles dans les phases 2, 3 et 4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-105">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="a5c14-106">Vous devez effectuer cette phase avant de passer à [l'authentification fédérée haute disponibilité, phase 2: configurer](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)les contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="a5c14-106">You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="a5c14-107">Reportez-vous à la rubrique [Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.</span><span class="sxs-lookup"><span data-stu-id="a5c14-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="a5c14-108">Azure doit être mis en service avec ces composants de base:</span><span class="sxs-lookup"><span data-stu-id="a5c14-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="a5c14-109">Groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="a5c14-109">Resource groups</span></span>
    
- <span data-ttu-id="a5c14-110">Un réseau virtuel Azure entre différents locaux avec des sous-réseaux pour l'hébergement des machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="a5c14-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="a5c14-111">Groupes de sécurité réseau pour effectuer l'isolation des sous-réseaux</span><span class="sxs-lookup"><span data-stu-id="a5c14-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="a5c14-112">Groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="a5c14-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="a5c14-113">Configurer les composants Azure</span><span class="sxs-lookup"><span data-stu-id="a5c14-113">Configure Azure components</span></span>

<span data-ttu-id="a5c14-114">Avant de commencer à configurer les composants Azure, renseignez les tableaux suivants.</span><span class="sxs-lookup"><span data-stu-id="a5c14-114">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="a5c14-115">Pour vous aider dans les procédures de configuration Azure, imprimez cette section et notez les informations nécessaires ou copiez cette section dans un document et remplissez-le.</span><span class="sxs-lookup"><span data-stu-id="a5c14-115">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="a5c14-116">Pour les paramètres du réseau virtuel, remplissez le tableau V.</span><span class="sxs-lookup"><span data-stu-id="a5c14-116">For the settings of the VNet, fill in Table V.</span></span>
  
|**<span data-ttu-id="a5c14-117">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-117">Item</span></span>**|**<span data-ttu-id="a5c14-118">Paramètre de configuration</span><span class="sxs-lookup"><span data-stu-id="a5c14-118">Configuration setting</span></span>**|**<span data-ttu-id="a5c14-119">Description</span><span class="sxs-lookup"><span data-stu-id="a5c14-119">Description</span></span>**|**<span data-ttu-id="a5c14-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="a5c14-120">Value</span></span>**|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-121">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-121">1.</span></span>  <br/> |<span data-ttu-id="a5c14-122">Nom du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="a5c14-122">VNet name</span></span>  <br/> |<span data-ttu-id="a5c14-123">Nom à attribuer au réseau virtuel (exemple FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="a5c14-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-124">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-124">2.</span></span>  <br/> |<span data-ttu-id="a5c14-125">Emplacement du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="a5c14-125">VNet location</span></span>  <br/> |<span data-ttu-id="a5c14-126">Le centre de centres Azure régional qui contiendra le réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="a5c14-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-127">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-127">3.</span></span>  <br/> |<span data-ttu-id="a5c14-128">Adresse IP du périphérique VPN</span><span class="sxs-lookup"><span data-stu-id="a5c14-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="a5c14-129">Adresse IPv4 publique de l'interface de votre périphérique VPN sur Internet.</span><span class="sxs-lookup"><span data-stu-id="a5c14-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-130">4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-130">4.</span></span>  <br/> |<span data-ttu-id="a5c14-131">Espace d'adressage du réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="a5c14-131">VNet address space</span></span>  <br/> |<span data-ttu-id="a5c14-p103">Espace d'adressage du réseau virtuel. Renseignez-vous auprès de votre service informatique pour déterminer cet espace d'adressage.</span><span class="sxs-lookup"><span data-stu-id="a5c14-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-134">5.</span><span class="sxs-lookup"><span data-stu-id="a5c14-134">5.</span></span>  <br/> |<span data-ttu-id="a5c14-135">Clé partagée IPsec</span><span class="sxs-lookup"><span data-stu-id="a5c14-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="a5c14-p104">Chaîne alphanumérique aléatoire de 32 caractères, utilisée pour authentifier les deux côtés de la connexion VPN de site à site. Renseignez-vous auprès de votre service informatique ou de sécurité pour déterminer cette valeur de clé. Vous pouvez également consulter la page relative à la [création d'une chaîne aléatoire pour une clé prépartagée IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span><span class="sxs-lookup"><span data-stu-id="a5c14-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **<span data-ttu-id="a5c14-139">Tableau V : configuration de réseau virtuel entre différents locaux</span><span class="sxs-lookup"><span data-stu-id="a5c14-139">Table V: Cross-premises virtual network configuration</span></span>**
  
<span data-ttu-id="a5c14-p105">Remplissez ensuite le Tableau S pour les sous-réseaux de cette solution. Tous les espaces d’adressage doivent être au format de routage CIDR (Classless Interdomain Routing), également appelé format de préfixe de réseau. Par exemple, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="a5c14-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="a5c14-143">Pour les trois premiers sous-réseaux, spécifiez un nom et un espace d'adressage IP unique en fonction de l'espace d'adressage du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="a5c14-143">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span></span> <span data-ttu-id="a5c14-144">Pour le sous-réseau de passerelle, déterminez l'espace d'adressage 27 bits (avec une longueur de préfixe de/27) pour le sous-réseau de passerelle Azure avec les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="a5c14-144">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="a5c14-145">Définissez la variable bits de l'espace d'adressage du réseau virtuel sur 1, jusqu'aux bits utilisés par le sous-réseau de passerelle, puis définissez les autres sur 0.</span><span class="sxs-lookup"><span data-stu-id="a5c14-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="a5c14-146">Convertissez les bits résultants en nombres décimaux et exprimez-les sous forme d'espace d'adressage, en définissant la longueur du préfixe sur une valeur équivalente à la taille du sous-réseau de passerelle.</span><span class="sxs-lookup"><span data-stu-id="a5c14-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="a5c14-147">Voir [calculatrice d'espace d'adressage pour les sous-réseaux de la passerelle Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) pour un bloc de commandes PowerShell et une application de consoles C# ou python qui effectue ce calcul pour vous.</span><span class="sxs-lookup"><span data-stu-id="a5c14-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="a5c14-148">Renseignez-vous auprès de votre service informatique pour déterminer ces espaces d’adressage à partir de l’espace d’adressage de réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="a5c14-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|**<span data-ttu-id="a5c14-149">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-149">Item</span></span>**|**<span data-ttu-id="a5c14-150">Nom du sous-réseau</span><span class="sxs-lookup"><span data-stu-id="a5c14-150">Subnet name</span></span>**|**<span data-ttu-id="a5c14-151">Espace d’adressage de sous-réseau</span><span class="sxs-lookup"><span data-stu-id="a5c14-151">Subnet address space</span></span>**|**<span data-ttu-id="a5c14-152">Objectif</span><span class="sxs-lookup"><span data-stu-id="a5c14-152">Purpose</span></span>**|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-153">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-154">Le sous-réseau utilisé par le contrôleur de domaine des services de domaine Active Directory (AD DS) et les machines virtuelles de serveur dirSync.</span><span class="sxs-lookup"><span data-stu-id="a5c14-154">The subnet used by the Active Directory Domain Services (AD DS) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="a5c14-155">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-156">Sous-réseau utilisé par les machines virtuelles AD FS.</span><span class="sxs-lookup"><span data-stu-id="a5c14-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="a5c14-157">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-158">Sous-réseau utilisé par les machines virtuelles de proxy d'application Web.</span><span class="sxs-lookup"><span data-stu-id="a5c14-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="a5c14-159">4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-159">4.</span></span>  <br/> |<span data-ttu-id="a5c14-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="a5c14-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-161">Le sous-réseau utilisé par les machines virtuelles de la passerelle Azure.</span><span class="sxs-lookup"><span data-stu-id="a5c14-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 **<span data-ttu-id="a5c14-162">Tableau S : sous-réseaux dans le réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="a5c14-162">Table S: Subnets in the virtual network</span></span>**
  
<span data-ttu-id="a5c14-163">Ensuite, renseignez le Tableau I pour les adresses IP statiques affectées à des machines virtuelles et à des instances d’équilibreur de charge.</span><span class="sxs-lookup"><span data-stu-id="a5c14-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|**<span data-ttu-id="a5c14-164">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-164">Item</span></span>**|**<span data-ttu-id="a5c14-165">Objectif</span><span class="sxs-lookup"><span data-stu-id="a5c14-165">Purpose</span></span>**|**<span data-ttu-id="a5c14-166">Adresse IP sur le sous-réseau</span><span class="sxs-lookup"><span data-stu-id="a5c14-166">IP address on the subnet</span></span>**|**<span data-ttu-id="a5c14-167">Valeur</span><span class="sxs-lookup"><span data-stu-id="a5c14-167">Value</span></span>**|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-168">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-168">1.</span></span>  <br/> |<span data-ttu-id="a5c14-169">Adresse IP statique du premier contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="a5c14-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="a5c14-170">La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 1 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-171">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-171">2.</span></span>  <br/> |<span data-ttu-id="a5c14-172">Adresse IP statique du deuxième contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="a5c14-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="a5c14-173">La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 1 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-174">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-174">3.</span></span>  <br/> |<span data-ttu-id="a5c14-175">Adresse IP statique du serveur dirSync</span><span class="sxs-lookup"><span data-stu-id="a5c14-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="a5c14-176">La sixième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'élément 1 du tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-177">4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-177">4.</span></span>  <br/> |<span data-ttu-id="a5c14-178">Adresse IP statique de l'équilibreur de charge interne pour les serveurs AD FS</span><span class="sxs-lookup"><span data-stu-id="a5c14-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="a5c14-179">La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-180">5.</span><span class="sxs-lookup"><span data-stu-id="a5c14-180">5.</span></span>  <br/> |<span data-ttu-id="a5c14-181">Adresse IP statique du premier serveur AD FS</span><span class="sxs-lookup"><span data-stu-id="a5c14-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="a5c14-182">La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-183">6.</span><span class="sxs-lookup"><span data-stu-id="a5c14-183">6.</span></span>  <br/> |<span data-ttu-id="a5c14-184">Adresse IP statique du deuxième serveur AD FS</span><span class="sxs-lookup"><span data-stu-id="a5c14-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="a5c14-185">La sixième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 2 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-186">7.</span><span class="sxs-lookup"><span data-stu-id="a5c14-186">7.</span></span>  <br/> |<span data-ttu-id="a5c14-187">Adresse IP statique du premier serveur proxy d'application Web</span><span class="sxs-lookup"><span data-stu-id="a5c14-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="a5c14-188">La quatrième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 3 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-189">8.</span><span class="sxs-lookup"><span data-stu-id="a5c14-189">8.</span></span>  <br/> |<span data-ttu-id="a5c14-190">Adresse IP statique du deuxième serveur proxy d'application Web</span><span class="sxs-lookup"><span data-stu-id="a5c14-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="a5c14-191">La cinquième adresse IP possible pour l'espace d'adressage du sous-réseau défini dans l'Élément 3 du Tableau S.</span><span class="sxs-lookup"><span data-stu-id="a5c14-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **<span data-ttu-id="a5c14-192">Tableau I : Adresses IP statiques dans le réseau virtuel</span><span class="sxs-lookup"><span data-stu-id="a5c14-192">Table I: Static IP addresses in the virtual network</span></span>**
  
<span data-ttu-id="a5c14-193">Pour les deux serveurs DNS (Domain Name System) de votre réseau local que vous souhaitez utiliser lors de la configuration initiale des contrôleurs de domaine de votre réseau virtuel, renseignez le tableau D. collaborez avec votre service informatique pour déterminer cette liste.</span><span class="sxs-lookup"><span data-stu-id="a5c14-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|**<span data-ttu-id="a5c14-194">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-194">Item</span></span>**|**<span data-ttu-id="a5c14-195">Nom convivial du serveur DNS</span><span class="sxs-lookup"><span data-stu-id="a5c14-195">DNS server friendly name</span></span>**|**<span data-ttu-id="a5c14-196">Adresse IP du serveur DNS</span><span class="sxs-lookup"><span data-stu-id="a5c14-196">DNS server IP address</span></span>**|
|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-197">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-198">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **<span data-ttu-id="a5c14-199">Tableau D : serveurs DNS locaux</span><span class="sxs-lookup"><span data-stu-id="a5c14-199">Table D: On-premises DNS servers</span></span>**
  
<span data-ttu-id="a5c14-200">Pour acheminer les paquets à partir du réseau intersites vers le réseau de votre organisation à travers la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local disposant d'une liste des espaces d'adressage (en notation CIDR) pour toutes les connexions accessibles. emplacements sur le réseau local de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a5c14-200">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="a5c14-201">La liste des espaces d'adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec l'espace d'adressage utilisé pour d'autres réseaux virtuels ou d'autres réseaux locaux.</span><span class="sxs-lookup"><span data-stu-id="a5c14-201">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="a5c14-p108">Pour l’ensemble des espaces d’adressage du réseau local, remplissez le tableau L. Notez que le tableau comporte trois entrées vides, mais vous aurez généralement besoin d’en ajouter. Renseignez-vous auprès de votre service informatique pour déterminer cette liste d’espaces d’adressage.</span><span class="sxs-lookup"><span data-stu-id="a5c14-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|**<span data-ttu-id="a5c14-204">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-204">Item</span></span>**|**<span data-ttu-id="a5c14-205">Espace d’adressage du réseau local</span><span class="sxs-lookup"><span data-stu-id="a5c14-205">Local network address space</span></span>**|
|:-----|:-----|
|<span data-ttu-id="a5c14-206">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-207">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-208">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **<span data-ttu-id="a5c14-209">Tableau L : préfixes d’adresse pour le réseau local</span><span class="sxs-lookup"><span data-stu-id="a5c14-209">Table L: Address prefixes for the local network</span></span>**
  
<span data-ttu-id="a5c14-210">Commençons à présent à créer l'infrastructure Azure pour héberger votre authentification fédérée pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5c14-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a5c14-p109">[!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="a5c14-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="a5c14-213">Tout d'abord, démarrez une invite PowerShell Azure et connectez-vous à votre compte.</span><span class="sxs-lookup"><span data-stu-id="a5c14-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
<span data-ttu-id="a5c14-214">Obtenez le nom de votre abonnement à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="a5c14-214">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="a5c14-215">Pour les versions antérieures d'Azure PowerShell, utilisez cette commande à la place.</span><span class="sxs-lookup"><span data-stu-id="a5c14-215">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="a5c14-216">Définissez votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="a5c14-216">Set your Azure subscription.</span></span> <span data-ttu-id="a5c14-217">Remplacez tous les éléments entre guillemets, \< y compris les caractères et >, par le nom correct.</span><span class="sxs-lookup"><span data-stu-id="a5c14-217">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="a5c14-218">Ensuite, créez les groupes de ressources.</span><span class="sxs-lookup"><span data-stu-id="a5c14-218">Next, create the new resource groups.</span></span> <span data-ttu-id="a5c14-219">Pour déterminer un ensemble unique de noms de groupes de ressources, utilisez cette commande pour répertorier vos groupes de ressources existants.</span><span class="sxs-lookup"><span data-stu-id="a5c14-219">To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="a5c14-220">Renseignez le tableau suivant pour l’ensemble unique de noms de groupes de ressources.</span><span class="sxs-lookup"><span data-stu-id="a5c14-220">Fill in the following table for the set of unique resource group names.</span></span>
  
|**<span data-ttu-id="a5c14-221">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-221">Item</span></span>**|**<span data-ttu-id="a5c14-222">Nom de groupe de ressources</span><span class="sxs-lookup"><span data-stu-id="a5c14-222">Resource group name</span></span>**|**<span data-ttu-id="a5c14-223">Objectif</span><span class="sxs-lookup"><span data-stu-id="a5c14-223">Purpose</span></span>**|
|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-224">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-224">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-225">Contrôleurs de domaine</span><span class="sxs-lookup"><span data-stu-id="a5c14-225">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="a5c14-226">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-226">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-227">Serveurs AD FS</span><span class="sxs-lookup"><span data-stu-id="a5c14-227">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="a5c14-228">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-228">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-229">Serveurs proxy d'application Web</span><span class="sxs-lookup"><span data-stu-id="a5c14-229">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="a5c14-230">4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-230">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="a5c14-231">Éléments de l’infrastructure</span><span class="sxs-lookup"><span data-stu-id="a5c14-231">Infrastructure elements</span></span>  <br/> |
   
 **<span data-ttu-id="a5c14-232">Tableau R : Groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="a5c14-232">Table R: Resource groups</span></span>**
  
<span data-ttu-id="a5c14-233">Créez vos nouveaux groupes de ressources avec ces commandes.</span><span class="sxs-lookup"><span data-stu-id="a5c14-233">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="a5c14-234">Ensuite, vous créez le réseau virtuel Azure et ses sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="a5c14-234">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="a5c14-235">Ensuite, créez des groupes de sécurité réseau pour chaque sous-réseau qui a des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="a5c14-235">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="a5c14-236">Pour isoler des sous-réseaux, vous pouvez ajouter des règles pour certains types de trafic autorisés ou refusés vers le groupe de sécurité d'un sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="a5c14-236">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="a5c14-237">Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="a5c14-237">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="a5c14-238">L’authentification fédérée d’utilisateurs individuels n’utilise aucune ressource locale.</span><span class="sxs-lookup"><span data-stu-id="a5c14-238">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="a5c14-239">Toutefois, si cette connexion VPN de site à site devient indisponible, les contrôleurs de domaine dans le réseau virtuel ne recevront pas les mises à jour des comptes d'utilisateur et des groupes créés dans les services de domaine Active Directory locaux.</span><span class="sxs-lookup"><span data-stu-id="a5c14-239">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="a5c14-240">Pour éviter ce problème, vous pouvez configurer une haute disponibilité pour votre connexion VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="a5c14-240">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="a5c14-241">Pour plus d'informations, reportez-vous à l'article [Configuration haute disponibilité pour la connectivité entre les réseaux locaux et la connectivité entre deux réseaux virtuels](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="a5c14-241">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="a5c14-242">Ensuite, enregistrez l'adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel à partir de l'affichage de cette commande :</span><span class="sxs-lookup"><span data-stu-id="a5c14-242">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="a5c14-p114">Ensuite, configurez votre périphérique VPN local de sorte qu'il se connecte à la passerelle VPN Azure. Pour plus d'informations, reportez-vous à la rubrique [À propos des périphériques VPN pour les connexions de la passerelle VPN de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="a5c14-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="a5c14-245">Pour configurer votre périphérique VPN local, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a5c14-245">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="a5c14-246">L'adresse IPv4 publique de la passerelle VPN Azure.</span><span class="sxs-lookup"><span data-stu-id="a5c14-246">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="a5c14-247">La clé prépartagée IPsec pour la connexion VPN de site à site (Tableau V - Élément 5 - colonne Valeur).</span><span class="sxs-lookup"><span data-stu-id="a5c14-247">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="a5c14-p115">Ensuite, vérifiez que l'espace d'adressage du réseau virtuel est accessible à partir de votre réseau local. Pour cela, il convient généralement d'ajouter un chemin de routage correspondant à l'espace d'adressage du réseau virtuel à votre périphérique VPN puis d'annoncer ce chemin de routage au reste de l'infrastructure de routage du réseau de votre organisation. Renseignez-vous auprès de votre service informatique pour savoir comment procéder.</span><span class="sxs-lookup"><span data-stu-id="a5c14-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="a5c14-251">Ensuite, définissez les noms de trois groupes à haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="a5c14-251">Next, define the names of three availability sets.</span></span> <span data-ttu-id="a5c14-252">Remplissez le Tableau A.</span><span class="sxs-lookup"><span data-stu-id="a5c14-252">Fill out Table A.</span></span> 
  
|**<span data-ttu-id="a5c14-253">Option</span><span class="sxs-lookup"><span data-stu-id="a5c14-253">Item</span></span>**|**<span data-ttu-id="a5c14-254">Objectif</span><span class="sxs-lookup"><span data-stu-id="a5c14-254">Purpose</span></span>**|**<span data-ttu-id="a5c14-255">Nom du groupe de disponibilité</span><span class="sxs-lookup"><span data-stu-id="a5c14-255">Availability set name</span></span>**|
|:-----|:-----|:-----|
|<span data-ttu-id="a5c14-256">1.</span><span class="sxs-lookup"><span data-stu-id="a5c14-256">1.</span></span>  <br/> |<span data-ttu-id="a5c14-257">Contrôleurs de domaine</span><span class="sxs-lookup"><span data-stu-id="a5c14-257">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-258">2.</span><span class="sxs-lookup"><span data-stu-id="a5c14-258">2.</span></span>  <br/> |<span data-ttu-id="a5c14-259">Serveurs AD FS</span><span class="sxs-lookup"><span data-stu-id="a5c14-259">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="a5c14-260">3.</span><span class="sxs-lookup"><span data-stu-id="a5c14-260">3.</span></span>  <br/> |<span data-ttu-id="a5c14-261">Serveurs proxy d'application Web</span><span class="sxs-lookup"><span data-stu-id="a5c14-261">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **<span data-ttu-id="a5c14-262">Tableau A : Groupes de disponibilité</span><span class="sxs-lookup"><span data-stu-id="a5c14-262">Table A: Availability sets</span></span>**
  
<span data-ttu-id="a5c14-263">Vous aurez besoin de ces noms lorsque vous créerez les machines virtuelles aux phases 2, 3 et 4.</span><span class="sxs-lookup"><span data-stu-id="a5c14-263">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="a5c14-264">Créez les nouveaux groupes de disponibilité avec ces commandes Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5c14-264">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="a5c14-265">Voici la configuration obtenue à la fin de cette phase.</span><span class="sxs-lookup"><span data-stu-id="a5c14-265">This is the configuration resulting from the successful completion of this phase.</span></span>
  
**<span data-ttu-id="a5c14-266">Phase 1: l'infrastructure Azure pour l'authentification fédérée haute disponibilité pour Office 365</span><span class="sxs-lookup"><span data-stu-id="a5c14-266">Phase 1: The Azure infrastructure for high availability federated authentication for Office 365</span></span>**

![Phase 1 de l'authentification fédérée Office 365 à haute disponibilité dans Azure avec l'infrastructure Azure](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="a5c14-268">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="a5c14-268">Next step</span></span>

<span data-ttu-id="a5c14-269">Utiliser l' [authentification fédérée haute disponibilité, phase 2: configurer](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) les contrôleurs de domaine pour poursuivre la configuration de cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="a5c14-269">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5c14-270">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5c14-270">See Also</span></span>

[<span data-ttu-id="a5c14-271">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="a5c14-271">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="a5c14-272">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a5c14-272">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="a5c14-273">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="a5c14-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="a5c14-274">Présentation de l’identité Office 365 et d’Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="a5c14-274">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


