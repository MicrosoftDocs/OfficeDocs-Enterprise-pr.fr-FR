---
title: "Conception de réseaux pour Microsoft SaaS"
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Résumé : Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365."
ms.openlocfilehash: e4d83f9ab88408b3eb5ca98379bbc709ec8f31a7
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="018b2-103">Conception de réseaux pour Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="018b2-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="018b2-104">**Résumé :** Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="018b2-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="018b2-105">L’optimisation de votre réseau pour les services SaaS de Microsoft nécessite une analyse approfondie de votre périmètre Internet, de vos périphériques client et de vos opérations informatiques standard.</span><span class="sxs-lookup"><span data-stu-id="018b2-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="018b2-106">Étapes pour préparer votre réseau aux services SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="018b2-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="018b2-107">Procédez comme suit pour optimiser votre réseau pour les services SaaS de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="018b2-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="018b2-108">Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="018b2-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="018b2-109">Optimisez votre sortie Internet pour les services SaaS de Microsoft en utilisant les recommandations de serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="018b2-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="018b2-110">Optimisez votre débit Internet en utilisant les recommandations en matière de proximité et d’emplacement.</span><span class="sxs-lookup"><span data-stu-id="018b2-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="018b2-111">Optimisez les performances des ordinateurs de vos clients et de l’intranet sur lequel ils se trouvent à l’aide des considérations relatives à l’utilisation du client.</span><span class="sxs-lookup"><span data-stu-id="018b2-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="018b2-112">Le cas échéant, optimisez les performances des migrations des données et de la synchronisation à l’aide des considérations relatives aux opérations informatiques.</span><span class="sxs-lookup"><span data-stu-id="018b2-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="018b2-113">Considérations relatives au périmètre Internet</span><span class="sxs-lookup"><span data-stu-id="018b2-113">Internet edge considerations</span></span>

<span data-ttu-id="018b2-114">Voici quelques éléments à prendre en considération pour l’optimisation de votre périmètre Internet et du débit vers les services SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="018b2-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="018b2-115">**Figure 1 : Options de connexion pour les services SaaS de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="018b2-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Figure 1 : options de connexion pour les services SaaS de Microsoft](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="018b2-117">La figure 1 présente un réseau local qui se connecte aux services SaaS de Microsoft via un canal Internet ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="018b2-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="018b2-118">Voici quelques recommandations pour optimiser votre serveur proxy :</span><span class="sxs-lookup"><span data-stu-id="018b2-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="018b2-119">Configurez les clients web à l’aide du protocole WPAD, du certificat PAC ou de l’objet de stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="018b2-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="018b2-120">N'utilisez pas interception SSL</span><span class="sxs-lookup"><span data-stu-id="018b2-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="018b2-121">Utilisez un fichier PAC pour contourner le proxy pour les noms DNS de service  SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="018b2-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="018b2-122">Autorisez le trafic pour la vérification de la liste de révocation de certificats/du protocole OCSP</span><span class="sxs-lookup"><span data-stu-id="018b2-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="018b2-123">Voici quelques goulots d’étranglement de serveur proxy à vérifier :</span><span class="sxs-lookup"><span data-stu-id="018b2-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="018b2-124">Connexions persistantes insuffisantes (Outlook)</span><span class="sxs-lookup"><span data-stu-id="018b2-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="018b2-125">Capacité insuffisante</span><span class="sxs-lookup"><span data-stu-id="018b2-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="018b2-126">Réalisation de l’évaluation hors réseau</span><span class="sxs-lookup"><span data-stu-id="018b2-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="018b2-127">Demande d’authentification</span><span class="sxs-lookup"><span data-stu-id="018b2-127">Requiring authentication</span></span>
    
- <span data-ttu-id="018b2-128">Aucune prise en charge pour le trafic UDP (Skype Entreprise)</span><span class="sxs-lookup"><span data-stu-id="018b2-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="018b2-129">Voici quelques recommandations en matière de proximité et d’emplacement :</span><span class="sxs-lookup"><span data-stu-id="018b2-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="018b2-130">N'acheminez pas le trafic Internet sur le réseau étendu privé</span><span class="sxs-lookup"><span data-stu-id="018b2-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="018b2-131">Utilisez le flux de trafic DNS et Internet dans la région pour les utilisateurs à l’extérieur de la région</span><span class="sxs-lookup"><span data-stu-id="018b2-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="018b2-132">Utilisez ExpressRoute pour une large bande passante vers Office 365 et une connectivité simultanée avec les services Azure</span><span class="sxs-lookup"><span data-stu-id="018b2-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="018b2-133">Voici les ports de sortie nécessaires pour le trafic Office 365 :</span><span class="sxs-lookup"><span data-stu-id="018b2-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="018b2-134">TCP 80 (pour les vérifications de liste de révocation de certificats/de protocole OCSP)</span><span class="sxs-lookup"><span data-stu-id="018b2-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="018b2-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="018b2-135">TCP 443</span></span>
    
- <span data-ttu-id="018b2-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="018b2-136">UDP 3478</span></span>
    
- <span data-ttu-id="018b2-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="018b2-137">TCP 5223</span></span>
    
- <span data-ttu-id="018b2-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="018b2-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="018b2-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="018b2-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="018b2-140">Considérations relative à l’utilisation client</span><span class="sxs-lookup"><span data-stu-id="018b2-140">Client usage considerations</span></span>

<span data-ttu-id="018b2-141">Tout d’abord, configurez l’ensemble des services que vos clients utiliseront, tels que :</span><span class="sxs-lookup"><span data-stu-id="018b2-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="018b2-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="018b2-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="018b2-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="018b2-143">Office 365</span></span>
    
  - <span data-ttu-id="018b2-144">Applications client Office</span><span class="sxs-lookup"><span data-stu-id="018b2-144">Office client apps</span></span>
    
  - <span data-ttu-id="018b2-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="018b2-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="018b2-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="018b2-146">Exchange Online</span></span>
    
  - <span data-ttu-id="018b2-147">Skype Entreprise</span><span class="sxs-lookup"><span data-stu-id="018b2-147">Skype for Business</span></span>
    
- <span data-ttu-id="018b2-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="018b2-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="018b2-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="018b2-149">Dynamics 365</span></span>
    
<span data-ttu-id="018b2-150">Pour les ordinateurs de vos clients, déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="018b2-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="018b2-151">Nombre maximal à chaque fois (heure du jour, saisonnier, pics et creux d’utilisation)</span><span class="sxs-lookup"><span data-stu-id="018b2-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="018b2-152">Bande passante totale nécessaire pour les pics</span><span class="sxs-lookup"><span data-stu-id="018b2-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="018b2-153">Latence vers le périphérique de sortie Internet</span><span class="sxs-lookup"><span data-stu-id="018b2-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="018b2-154">Pays d’origine et pays de colocalisation des centres de données</span><span class="sxs-lookup"><span data-stu-id="018b2-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="018b2-155">Pour chaque type de client (PC, smartphone ou tablette), vérifiez les éléments suivants actuels :</span><span class="sxs-lookup"><span data-stu-id="018b2-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="018b2-156">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="018b2-156">Operating system</span></span>
    
- <span data-ttu-id="018b2-157">Navigateur Internet</span><span class="sxs-lookup"><span data-stu-id="018b2-157">Internet browser</span></span>
    
- <span data-ttu-id="018b2-158">Pile TCP/IP</span><span class="sxs-lookup"><span data-stu-id="018b2-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="018b2-159">Matériel réseau</span><span class="sxs-lookup"><span data-stu-id="018b2-159">Network hardware</span></span>
    
- <span data-ttu-id="018b2-160">Pilotes du système d’exploitation du matériel réseau</span><span class="sxs-lookup"><span data-stu-id="018b2-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="018b2-161">Installation des mises à jour et des correctifs</span><span class="sxs-lookup"><span data-stu-id="018b2-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="018b2-162">En outre, optimisez le débit de connexion intranet (par câble, sans fil ou VPN).</span><span class="sxs-lookup"><span data-stu-id="018b2-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="018b2-163">Pour plus d'informations, voir l'article [Prise en charge NAT avec Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span><span class="sxs-lookup"><span data-stu-id="018b2-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="018b2-164">Pour obtenir les dernières recommandations sur l'utilisation d'ExpressRoute avec Office 365, voir [ExpressRoute pour Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="018b2-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="018b2-165">Pour optimiser les performances de votre intranet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018b2-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="018b2-166">Utilisez des outils pour évaluer la durée approximative des boucles sur vos périphériques du périmètre Internet (PsPing, Ping, Tracert, TraceTCP, Moniteur réseau)</span><span class="sxs-lookup"><span data-stu-id="018b2-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="018b2-167">Effectuez l’analyse de chemin de sortie à l’aide des protocoles de flux</span><span class="sxs-lookup"><span data-stu-id="018b2-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="018b2-168">Effectuez l’analyse des périphériques intermédiaires (âge, intégrité, etc.)</span><span class="sxs-lookup"><span data-stu-id="018b2-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="018b2-169">Pour plus d'informations, voir l'article concernant l'[outil PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span><span class="sxs-lookup"><span data-stu-id="018b2-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="018b2-170">Considérations relatives aux opérations informatiques</span><span class="sxs-lookup"><span data-stu-id="018b2-170">IT operations considerations</span></span>

<span data-ttu-id="018b2-171">Voici quelques éléments à prendre en considération lors de l’exploitation d’une charge de travail informatique dans un service SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="018b2-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="018b2-172">Migrations exceptionnelles</span><span class="sxs-lookup"><span data-stu-id="018b2-172">One-time migrations</span></span>

<span data-ttu-id="018b2-173">Le transfert de données en bloc pour les applications basées sur le cloud ou le stockage d’archives représentent des exemples de migrations exceptionnelles.</span><span class="sxs-lookup"><span data-stu-id="018b2-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="018b2-174">Afin d’optimiser votre réseau pour les migrations exceptionnelles, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018b2-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="018b2-175">Évitez l’utilisation maximale du réseau et les heures de correctifs de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="018b2-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="018b2-176">En cas de ligne de base et de guidage, évaluez l’intégrité du réseau et résolvez les problèmes avant d’essayer la migration réelle</span><span class="sxs-lookup"><span data-stu-id="018b2-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="018b2-177">Effectuez un post-mortem pour les prochaines migrations</span><span class="sxs-lookup"><span data-stu-id="018b2-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="018b2-178">Synchronisations en cours</span><span class="sxs-lookup"><span data-stu-id="018b2-178">Ongoing synchronizations</span></span>

<span data-ttu-id="018b2-179">Les informations du répertoire, les paramètres ou les fichiers sont des exemples de synchronisations en cours.</span><span class="sxs-lookup"><span data-stu-id="018b2-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="018b2-180">Pour optimiser votre réseau pour les synchronisations en cours, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018b2-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="018b2-181">Assurez-vous qu’un système de suivi de la bande passante réseau est en place, et résolvez ou ignorez les erreurs collectées</span><span class="sxs-lookup"><span data-stu-id="018b2-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="018b2-182">Utilisez les résultats du suivi de la bande passante pour déterminer les modifications de réseau nécessaires (monter en puissance/en charge, nouveaux circuits ou ajouter des périphériques)</span><span class="sxs-lookup"><span data-stu-id="018b2-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="018b2-183">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="018b2-183">For more information, see:</span></span>
  
- [<span data-ttu-id="018b2-184">Planification réseau et de migration pour Office 365</span><span class="sxs-lookup"><span data-stu-id="018b2-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="018b2-185">Cours Microsoft Virtual Academy concernant la gestion des performances pour Office 365</span><span class="sxs-lookup"><span data-stu-id="018b2-185">Office 365 Performance Management Microsoft Virtual Academy course</span></span>](https://aka.ms/o365perf)
    
- [<span data-ttu-id="018b2-186">ExpressRoute pour Office 365</span><span class="sxs-lookup"><span data-stu-id="018b2-186">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a><span data-ttu-id="018b2-187">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="018b2-187">Next step</span></span>

[<span data-ttu-id="018b2-188">Conception de réseau pour Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="018b2-188">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="018b2-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="018b2-189">See also</span></span>

[<span data-ttu-id="018b2-190">Mise en réseau cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="018b2-190">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="018b2-191">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="018b2-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="018b2-192">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="018b2-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



