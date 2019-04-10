---
title: Scénarios de cloud hybride pour les services PaaS Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Résumé : Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure."
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741370"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="ee813-103">Scénarios de cloud hybride pour les services PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="ee813-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="ee813-104">**Résumé :** Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ee813-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="ee813-105">Combinez des données locales ou des ressources de calcul à des applications nouvelles ou converties exécutées dans les services PaaS Azure. Vous pouvez ainsi tirer parti des performances, de la fiabilité et de la dimension du cloud tout en offrant une prise en charge optimale aux utilisateurs mobiles.</span><span class="sxs-lookup"><span data-stu-id="ee813-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="ee813-106">Architecture de scénario hybride pour les services PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="ee813-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="ee813-107">La Figure 1 présente l’architecture des scénarios hybrides PaaS de Microsoft dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ee813-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
**<span data-ttu-id="ee813-108">Figure 1 : Scénarios hybrides Microsoft PaaS dans Azure</span><span class="sxs-lookup"><span data-stu-id="ee813-108">Figure 1: Microsoft PaaS-based hybrid scenarios in Azure</span></span>**

![Scénarios hybrides Microsoft PaaS dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="ee813-110">Pour chaque couche de l’architecture :</span><span class="sxs-lookup"><span data-stu-id="ee813-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="ee813-111">Applications et scénarios</span><span class="sxs-lookup"><span data-stu-id="ee813-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="ee813-112">Une application PaaS hybride est exécutée dans Azure et utilise les ressources de calcul ou de stockage locales.</span><span class="sxs-lookup"><span data-stu-id="ee813-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="ee813-113">Identity</span><span class="sxs-lookup"><span data-stu-id="ee813-113">Identity</span></span>
    
    <span data-ttu-id="ee813-114">Se compose de la synchronisation d’annuaires ou de la fédération avec un fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="ee813-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="ee813-115">Réseau</span><span class="sxs-lookup"><span data-stu-id="ee813-115">Network</span></span>
    
    <span data-ttu-id="ee813-p101">Se compose de votre canal Internet existant ou d'une connexion ExpressRoute avec homologation publique pour Azure PaaS. Vous devez inclure un moyen pour l'application Azure PaaS d'accéder à la ressource de calcul ou de stockage locale.</span><span class="sxs-lookup"><span data-stu-id="ee813-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="ee813-118">Sur site</span><span class="sxs-lookup"><span data-stu-id="ee813-118">On-premises</span></span>
    
    <span data-ttu-id="ee813-119">Se compose d’une infrastructure d’identité et de sécurité et d’applications métier ou de serveurs de bases de données existants auxquels une application Azure PaaS peut accéder en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="ee813-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="ee813-120">Application hybride Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="ee813-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="ee813-121">La Figure 2 illustre la configuration d’une application hybride exécutée dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ee813-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="ee813-122">Figure 2 : Application hybride Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="ee813-122">Figure 2: Azure PaaS-based hybrid application</span></span>**

![Application hybride Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="ee813-p102">Dans la Figure 2, un réseau local héberge le stockage ou des applications sur des serveurs et une zone DMZ contenant un serveur proxy. Il est connecté à des services Azure PaaS via Internet ou avec une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ee813-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="ee813-126">Une organisation peut mettre ses ressources de calcul ou de stockage à disposition de l’application Azure PaaS hybride :</span><span class="sxs-lookup"><span data-stu-id="ee813-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="ee813-127">en hébergeant les ressources sur des serveurs dans la zone DMZ ;</span><span class="sxs-lookup"><span data-stu-id="ee813-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="ee813-128">en hébergeant un serveur proxy inverse dans la zone DMZ, ce qui permet d’envoyer des requêtes HTTPS entrantes et authentifiées à la ressource locale.</span><span class="sxs-lookup"><span data-stu-id="ee813-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="ee813-129">L’application Azure peut utiliser les informations d’identification des sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee813-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="ee813-130">Azure AD, qui peut être synchronisé avec votre fournisseur d'identité local, tel que les services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="ee813-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="ee813-131">Fournisseur d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="ee813-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="ee813-132">Exemple d’application Azure PaaS hybride</span><span class="sxs-lookup"><span data-stu-id="ee813-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="ee813-133">La Figure 3 illustre un exemple d’application hybride exécutée dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ee813-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="ee813-134">Figure 3 : Exemple d’application hybride Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="ee813-134">Figure 3: An example Azure PaaS-based hybrid application</span></span>**

![Exemple d’application hybride Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="ee813-p103">Dans la Figure 3, un réseau local héberge une application métier. Azure PaaS héberge une application mobile personnalisée. Un smartphone sur Internet accède à l'application mobile personnalisée dans Azure, qui envoie des demandes de données à l'application métier locale.</span><span class="sxs-lookup"><span data-stu-id="ee813-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="ee813-p104">Cet exemple d'application Azure PaaS hybride est une application mobile personnalisée qui propose des informations de contact à jour concernant les employés. Le scénario hybride de bout en bout se compose de :</span><span class="sxs-lookup"><span data-stu-id="ee813-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="ee813-141">Un application pour smartphone qui, pour fonctionner, nécessite des informations d’identification locales et validées.</span><span class="sxs-lookup"><span data-stu-id="ee813-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="ee813-142">Une application mobile personnalisée exécutée dans les services PaaS Azure, qui demande des informations concernant des employés spécifiques en fonction de requêtes envoyées par l'application pour smartphone d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ee813-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="ee813-143">Un serveur proxy inverse dans la zone DMZ qui valide l’application mobile personnalisée et transfère la requête.</span><span class="sxs-lookup"><span data-stu-id="ee813-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="ee813-144">Une batterie de serveurs d'applications métier qui gère la requête de contact. Elle est soumise aux autorisations du compte de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ee813-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="ee813-145">Étant donné que le fournisseur d'identité local a été synchronisé avec Azure AD, l'application mobile personnalisée et l'application métier peuvent valider le nom du compte de l'utilisateur qui envoie la requête.</span><span class="sxs-lookup"><span data-stu-id="ee813-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ee813-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee813-146">See Also</span></span>

[<span data-ttu-id="ee813-147">Cloud hybride Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="ee813-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="ee813-148">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="ee813-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

