---
title: Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Résumé : Configurer l'authentification fédérée haute disponibilité pour votre abonnement Office 365 dans Microsoft Azure."
ms.openlocfilehash: a95a079c8bdee6d36769461666769f9a75ea9f40
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="80c34-103">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="80c34-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="80c34-104">**Résumé :** Configurer l'authentification fédérée haute disponibilité pour votre abonnement Office 365 dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="80c34-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="80c34-105">Cet article contient des liens vers les instructions détaillées de déploiement de l’authentification fédérée haute disponibilité pour Microsoft Office 365 dans les services d’infrastructure Azure avec ces machines virtuelles :</span><span class="sxs-lookup"><span data-stu-id="80c34-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="80c34-106">Deux serveurs proxy d’application web</span><span class="sxs-lookup"><span data-stu-id="80c34-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="80c34-107">Deux serveurs de services ADFS (Active Directory Federation Services)</span><span class="sxs-lookup"><span data-stu-id="80c34-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="80c34-108">Deux contrôleurs de domaine répliqués</span><span class="sxs-lookup"><span data-stu-id="80c34-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="80c34-109">Un serveur de synchronisation d’annuaire (DirSync) exécutant Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="80c34-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="80c34-110">Voici la configuration, avec les noms d’espace réservé pour chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="80c34-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="80c34-111">**Une authentification fédérée haute disponibilité pour l'infrastructure Office 365 dans Azure**</span><span class="sxs-lookup"><span data-stu-id="80c34-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Configuration finale de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="80c34-113">Toutes les machines virtuelles sont dans un réseau virtuel intersites unique Azure.</span><span class="sxs-lookup"><span data-stu-id="80c34-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="80c34-p101">L'authentification fédérée d'utilisateurs individuels n'utilise aucune ressource locale. Toutefois, si la connexion intersites devient indisponible, les contrôleurs de domaine du réseau virtuel ne reçoivent plus les mises à jour des comptes d'utilisateurs et des groupes apportées dans l'instance Active Directory Windows Server locale. Pour que cela n'arrive pas, vous pouvez configurer une haute disponibilité pour votre connexion intersites. Pour plus d'informations, reportez-vous à l'article [Configuration haute disponibilité pour la connectivité entre les réseaux locaux et la connectivité entre deux réseaux virtuels](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="80c34-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="80c34-118">Chaque paire de machines virtuelles utilisée pour un rôle spécifique est dans son propre sous-réseau et son propre groupe à haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="80c34-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="80c34-p102">Étant donné que ce réseau virtuel est connecté au réseau local, cette configuration n'inclut pas de machines virtuelles jumpbox ou de machines virtuelles de surveillance sur un sous-réseau de gestion. Pour plus d'informations, voir l'article relatif à l'[exécution de machines virtuelles Windows pour une architecture n-tiers](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="80c34-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="80c34-p103">Cette configuration met en place une authentification fédérée pour tous vos utilisateurs Office 365, qui peuvent ainsi utiliser leurs informations d'identification Active Directory Windows Server pour se connecter au lieu de leur compte Office 365. L'infrastructure d'authentification fédérés utilise un ensemble redondant de serveurs qui sont plus faciles à déployer dans les services d'infrastructure Azure que dans votre réseau de périmètre en local.</span><span class="sxs-lookup"><span data-stu-id="80c34-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="80c34-123">Nomenclature</span><span class="sxs-lookup"><span data-stu-id="80c34-123">Bill of materials</span></span>

<span data-ttu-id="80c34-124">Cette configuration de base requiert l’ensemble de composants et services Azure suivant :</span><span class="sxs-lookup"><span data-stu-id="80c34-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="80c34-125">Sept machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="80c34-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="80c34-126">Un réseau virtuel intersites avec quatre sous-réseaux.</span><span class="sxs-lookup"><span data-stu-id="80c34-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="80c34-127">Quatre groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="80c34-127">Four resource groups</span></span>
    
- <span data-ttu-id="80c34-128">Trois groupes à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="80c34-128">Three availability sets</span></span>
    
- <span data-ttu-id="80c34-129">Un abonnement Azure</span><span class="sxs-lookup"><span data-stu-id="80c34-129">One Azure subscription</span></span>
    
<span data-ttu-id="80c34-130">Voici les machines virtuelles et leurs tailles par défaut pour cette configuration.</span><span class="sxs-lookup"><span data-stu-id="80c34-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="80c34-131">**Élément**</span><span class="sxs-lookup"><span data-stu-id="80c34-131">**Item**</span></span>|<span data-ttu-id="80c34-132">**Description de la machine virtuelle**</span><span class="sxs-lookup"><span data-stu-id="80c34-132">**Virtual machine description**</span></span>|<span data-ttu-id="80c34-133">**Image de la galerie Azure**</span><span class="sxs-lookup"><span data-stu-id="80c34-133">**Azure gallery image**</span></span>|<span data-ttu-id="80c34-134">**Taille par défaut**</span><span class="sxs-lookup"><span data-stu-id="80c34-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="80c34-135">1.</span><span class="sxs-lookup"><span data-stu-id="80c34-135">1.</span></span>  <br/> |<span data-ttu-id="80c34-136">Premier contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="80c34-136">First domain controller</span></span>  <br/> |<span data-ttu-id="80c34-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-138">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-138">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-139">2.</span><span class="sxs-lookup"><span data-stu-id="80c34-139">2.</span></span>  <br/> |<span data-ttu-id="80c34-140">Deuxième contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="80c34-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="80c34-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-142">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-142">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-143">3.</span><span class="sxs-lookup"><span data-stu-id="80c34-143">3.</span></span>  <br/> |<span data-ttu-id="80c34-144">Serveur Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="80c34-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="80c34-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-146">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-146">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-147">4.</span><span class="sxs-lookup"><span data-stu-id="80c34-147">4.</span></span>  <br/> |<span data-ttu-id="80c34-148">Premier serveur AD FS</span><span class="sxs-lookup"><span data-stu-id="80c34-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="80c34-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-150">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-150">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-151">5.</span><span class="sxs-lookup"><span data-stu-id="80c34-151">5.</span></span>  <br/> |<span data-ttu-id="80c34-152">Deuxième serveur AD FS</span><span class="sxs-lookup"><span data-stu-id="80c34-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="80c34-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-154">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-154">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-155">6.</span><span class="sxs-lookup"><span data-stu-id="80c34-155">6.</span></span>  <br/> |<span data-ttu-id="80c34-156">Premier serveur proxy d’application web</span><span class="sxs-lookup"><span data-stu-id="80c34-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="80c34-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-158">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-158">D2</span></span>  <br/> |
|<span data-ttu-id="80c34-159">7.</span><span class="sxs-lookup"><span data-stu-id="80c34-159">7.</span></span>  <br/> |<span data-ttu-id="80c34-160">Deuxième serveur proxy d’application web</span><span class="sxs-lookup"><span data-stu-id="80c34-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="80c34-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="80c34-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="80c34-162">D2</span><span class="sxs-lookup"><span data-stu-id="80c34-162">D2</span></span>  <br/> |
   
<span data-ttu-id="80c34-163">Pour calculer les coûts estimés pour cette configuration, utilisez la [calculatrice de prix Azure](https://azure.microsoft.com/pricing/calculator/)</span><span class="sxs-lookup"><span data-stu-id="80c34-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="80c34-164">Phases de déploiement</span><span class="sxs-lookup"><span data-stu-id="80c34-164">Phases of deployment</span></span>

<span data-ttu-id="80c34-165">Vous déployez cette charge de travail au cours des phases suivantes :</span><span class="sxs-lookup"><span data-stu-id="80c34-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="80c34-p104">[Authentification fédérée haute disponibilité, phase 1 : Configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Créez des groupes de ressources, des comptes de stockage, des groupes à haute disponibilité et un réseau virtuel intersite.</span><span class="sxs-lookup"><span data-stu-id="80c34-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="80c34-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Créez et configurez des contrôleurs de domaine répliqués Windows Server Active Directory (AD) et le serveur DirSync.</span><span class="sxs-lookup"><span data-stu-id="80c34-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="80c34-p106">[Authentification fédérée haute disponibilité, phase 3 : Configurer les serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Créez et configurez les deux serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="80c34-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="80c34-p107">[Authentification fédérée haute disponibilité, phase 4 : Configurer les proxys d’application web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Créez et configurez les deux serveurs proxy d’application web.</span><span class="sxs-lookup"><span data-stu-id="80c34-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="80c34-p108">[Authentification fédérée haute disponibilité, phase 5 : Configurer l’authentification fédérée pour Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configurez l’authentification fédérée pour votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="80c34-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="80c34-p109">Ces articles fournissent un guide normatif phase par phase pour créer une authentification fédérée haute disponibilité fonctionnelle pour Office 365 dans les services d’infrastructure Azure à partir d’une architecture prédéfinie. Gardez les éléments suivants à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="80c34-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="80c34-178">Si vous êtes un implémenteur d’AD FS expérimenté, n’hésitez pas à adapter les instructions des étapes 3 à 4 et à créer l’ensemble de serveurs qui correspond le mieux à vos besoins. </span><span class="sxs-lookup"><span data-stu-id="80c34-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="80c34-179">Si vous disposez déjà d’un déploiement de cloud hybride Azure avec un réseau virtuel entre différents locaux, n’hésitez pas à adapter ou à ignorer les instructions des phases 1 et 2 et placez les serveurs proxy AD FS et d’application web dans les sous-réseaux appropriés.</span><span class="sxs-lookup"><span data-stu-id="80c34-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="80c34-180">Pour créer un environnement de développement/test ou une preuve de concept de cette configuration, voir [Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="80c34-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="80c34-181">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="80c34-181">Next step</span></span>

<span data-ttu-id="80c34-182">Commencez la configuration de cette charge de travail avec [Authentification fédérée haute disponibilité, phase 1 : Configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="80c34-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="80c34-183">Pour qu'un jeu de fichiers déploie plus rapidement votre authentification fédérée haute disponibilité pour Office 365 dans Azure, voir le [Kit de déploiement de l'authentification fédérée pour Office 365 dans Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="80c34-183">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
 

