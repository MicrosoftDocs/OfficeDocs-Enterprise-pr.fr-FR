---
title: Présentation du cloud hybride
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 'Résumé : Comprendre la définition et les éléments du cloud hybride Microsoft.'
ms.openlocfilehash: 21f107c9f096e90cd0eb1dfc17f14431dec54a73
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327346"
---
# <a name="hybrid-cloud-overview"></a><span data-ttu-id="bff21-103">Présentation du cloud hybride</span><span class="sxs-lookup"><span data-stu-id="bff21-103">Hybrid cloud overview</span></span>

 <span data-ttu-id="bff21-104">**Résumé :** Comprendre la définition et les éléments du cloud hybride Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bff21-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="bff21-p101">Le cloud hybride utilise des ressources de calcul ou de stockage sur votre réseau local et dans le cloud. Vous pouvez utiliser le cloud hybride pour migrer votre entreprise et ses besoins en ressources informatiques vers le cloud, ou intégrer des services et plateformes cloud à votre infrastructure locale existante dans le cadre de la mise en œuvre de votre stratégie informatique globale.</span><span class="sxs-lookup"><span data-stu-id="bff21-p101">Hybrid cloud uses compute or storage resources on your on-premises network and in the cloud. You can use hybrid cloud as a path to migrate your business and its IT needs to the cloud or integrate cloud platforms and services with your existing on-premises infrastructure as part of your overall IT strategy.</span></span>
  
## <a name="microsoft-hybrid-cloud"></a><span data-ttu-id="bff21-107">Cloud hybride Microsoft</span><span class="sxs-lookup"><span data-stu-id="bff21-107">Microsoft hybrid cloud</span></span>

<span data-ttu-id="bff21-108">Le cloud hybride Microsoft représente un ensemble de scénarios professionnels qui combinent une plateforme cloud Microsoft à un composant local, par exemple :</span><span class="sxs-lookup"><span data-stu-id="bff21-108">Microsoft hybrid cloud is a set of business scenarios that combine a Microsoft cloud platform with an on-premises component, such as:</span></span> 
  
- <span data-ttu-id="bff21-109">Obtention de résultats de recherche pour du contenu stocké dans une batterie SharePoint locale et dans SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="bff21-109">Getting search results from content both in an on-premises SharePoint farm and in SharePoint Online in Office 365.</span></span>
    
- <span data-ttu-id="bff21-110">Application mobile exécutée dans Azure qui interroge un magasin de données local.</span><span class="sxs-lookup"><span data-stu-id="bff21-110">A mobile app running in Azure that queries an on-premises data store.</span></span>
    
- <span data-ttu-id="bff21-111">Charge de travail informatique sur un intranet exécutée sur des ordinateurs virtuels Azure.</span><span class="sxs-lookup"><span data-stu-id="bff21-111">An intranet IT workload running on Azure virtual machines.</span></span>
    
<span data-ttu-id="bff21-112">**Figure 1 : Composants du cloud hybride Microsoft**</span><span class="sxs-lookup"><span data-stu-id="bff21-112">**Figure 1: Components of the Microsoft hybrid cloud**</span></span>

![Composants du cloud hybride Microsoft](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
<span data-ttu-id="bff21-114">La figure 1 présente les composants du cloud hybride Microsoft, d’un réseau local à l’ensemble des services Office 365, Paas Azure et IaaS Azure disponibles sur Internet ou une connexion ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bff21-114">Figure 1 shows the components of the Microsoft hybrid cloud, from an on-premises network to the set of Office 365, Azure Platform as a Service (PaaS), and Azure Infrastructure as a Service (IaaS) services available across the Internet or an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bff21-115">Étant donné que Microsoft propose l’une des solutions cloud les plus complètes sur le marché (Software as a Service (SaaS), Platform as a Service (PaaS) et Infrastructure as a Service (IaaS), vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="bff21-115">Because Microsoft has the most complete cloud solution in the marketplace—including Software as a Service (SaaS), PaaS, and IaaS—you can:</span></span>
  
- <span data-ttu-id="bff21-116">tirer parti des investissements que vous avez effectués dans votre environnement local lorsque vous migrez des charges de travail et des applications vers le cloud ;</span><span class="sxs-lookup"><span data-stu-id="bff21-116">Leverage your existing on-premises investments as you migrate workloads and applications to the cloud.</span></span>
    
- <span data-ttu-id="bff21-117">incorporer des scénarios de cloud hybride dans votre planification informatique à long terme, par exemple, lorsque des réglementations ou des politiques vous empêchent de déplacer des données ou des charges de travail spécifiques vers le cloud ;</span><span class="sxs-lookup"><span data-stu-id="bff21-117">Incorporate hybrid cloud scenarios into your long-term IT plans, for example, when regulations or policies do not permit moving specific data or workloads to the cloud.</span></span>
    
- <span data-ttu-id="bff21-118">créer des scénarios hybrides supplémentaires qui incluent plusieurs services et plateformes cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bff21-118">Create additional hybrid scenarios that include multiple Microsoft cloud services and platforms.</span></span>
    
<span data-ttu-id="bff21-119">Les scénarios de cloud hybride utilisant les services cloud Microsoft dépendent de la plateforme utilisée.</span><span class="sxs-lookup"><span data-stu-id="bff21-119">Scenarios for hybrid cloud with Microsoft cloud services vary with the platform.</span></span>
  
- <span data-ttu-id="bff21-120">SaaS</span><span class="sxs-lookup"><span data-stu-id="bff21-120">SaaS</span></span>
    
    <span data-ttu-id="bff21-p102">Services Microsoft SaaS incluent Office 365 et Microsoft Dynamics 365 Intune Microsoft. Scénarios de nuage hybride avec Microsoft SaaS combinent ces services avec les services locaux ou des applications. Par exemple, Exchange Online en cours d’exécution dans Office 365 peut être intégré avec Skype pour 2019 Business qui est déployé localement.</span><span class="sxs-lookup"><span data-stu-id="bff21-p102">Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Hybrid cloud scenarios with Microsoft SaaS combine these services with on-premises services or applications. For example, Exchange Online running in Office 365 can be integrated with Skype for Business 2019 that is deployed on-premises.</span></span>
    
- <span data-ttu-id="bff21-124">Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="bff21-124">Azure PaaS</span></span>
    
    <span data-ttu-id="bff21-p103">Les services PaaS de Microsoft Azure permettent de créer des applications basées sur le cloud. Les scénarios de cloud hybride avec les services PaaS Azure combinent une application PaaS Azure aux applications ou ressources locales. Par exemple, une application PaaS Azure peut interroger en toute sécurité une banque de données locale afin d'obtenir les informations nécessaires à afficher pour les utilisateurs de l'application mobile.</span><span class="sxs-lookup"><span data-stu-id="bff21-p103">Microsoft Azure PaaS services allow you to create cloud-based applications. Hybrid cloud scenarios with Azure PaaS services combine an Azure PaaS app with on-premises resources or applications. For example, an Azure PaaS app could securely query an on-premises data store for information needed to display to mobile app users.</span></span>
    
- <span data-ttu-id="bff21-128">Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="bff21-128">Azure IaaS</span></span>
    
    <span data-ttu-id="bff21-p104">Les services IaaS Azure permettent de créer et d'exécuter des charges de travail informatiques basées sur serveur dans le cloud, et non dans votre centre de données local. Les scénarios de cloud hybride avec les services IaaS Azure sont généralement constitués d'une charge de travail informatique qui s'exécute sur des ordinateurs virtuels et qui est connectée en toute transparence à votre réseau local. Les utilisateurs locaux ne verront pas la différence.</span><span class="sxs-lookup"><span data-stu-id="bff21-p104">Azure IaaS services allow you to build and run server-based IT workloads in the cloud, rather than in your on-premises datacenter. Hybrid cloud scenarios with Azure IaaS services typically consist of an IT workload that runs on virtual machines that is transparently connected to your on-premises network. Your on-premises users will not notice the difference.</span></span>
    
## <a name="elements-of-hybrid-cloud"></a><span data-ttu-id="bff21-132">Éléments du cloud hybride</span><span class="sxs-lookup"><span data-stu-id="bff21-132">Elements of hybrid cloud</span></span>

<span data-ttu-id="bff21-133">Vous devez tenir compte des éléments suivants lorsque vous planifiez et implémentez des scénarios de cloud hybride utilisant des plateformes et services cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bff21-133">You must account for the following elements when planning and implementing hybrid cloud scenarios with Microsoft cloud platforms and services.</span></span>
  
- <span data-ttu-id="bff21-134">Réseau</span><span class="sxs-lookup"><span data-stu-id="bff21-134">Networking</span></span>
    
    <span data-ttu-id="bff21-p105">Dans le cadre de scénarios de cloud hybride, la mise en réseau inclut la connectivité aux plateformes et services cloud de Microsoft et suffisamment de bande passante pour conserver les performances en cas de pic au niveau des charges. Pour plus d'informations, voir [Mise en réseau cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-networking-for-enterprise-architects.md).</span><span class="sxs-lookup"><span data-stu-id="bff21-p105">Networking for hybrid cloud scenarios includes the connectivity to Microsoft cloud platforms and services and enough bandwidth to be performant under peak loads. For more information, see [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md).</span></span>
    
- <span data-ttu-id="bff21-137">Identity</span><span class="sxs-lookup"><span data-stu-id="bff21-137">Identity</span></span>
    
    <span data-ttu-id="bff21-p106">Dans le cadre de scénarios hybrides SaaS et PaaS Azure, l'identité peut inclure Azure AD en tant que fournisseur d'identité commun, qui peut alors être synchronisé avec Windows Server AD en local, ou fédéré avec Windows Server AD ou d'autres fournisseurs d'identité. Vous pouvez également étendre votre infrastructure d'identité locale pour IaaS Azure. Pour plus d'informations, voir [Identité cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-it-architecture-resources.md#identity).</span><span class="sxs-lookup"><span data-stu-id="bff21-p106">Identity for SaaS and Azure PaaS hybrid scenarios can include Azure AD as a common identity provider, which can be synchronized with your on-premises Windows Server AD, or federated with Windows Server AD or other identity providers. You can also extend your on-premises Identity infrastructure to Azure IaaS. For more information, see [Microsoft Cloud Identity for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity).</span></span>
    
- <span data-ttu-id="bff21-141">Sécurité</span><span class="sxs-lookup"><span data-stu-id="bff21-141">Security</span></span>
    
    <span data-ttu-id="bff21-p107">Dans le cadre de scénarios cloud hybrides, la sécurité inclut la protection et la gestion de vos identités, la protection des données, la gestion des privilèges d'administrateur, la sensibilisation aux menaces et l'implémentation de stratégies de gouvernance et de sécurité. Pour plus d'informations, voir [Sécurité cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-it-architecture-resources.md#security).</span><span class="sxs-lookup"><span data-stu-id="bff21-p107">Security for hybrid cloud scenarios includes protection and management for your identities, data protection, administrative privilege management, threat awareness, and the implementation of governance and security policies. For more information, see [Microsoft Cloud Security for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#security).</span></span>
    
- <span data-ttu-id="bff21-144">Gestion</span><span class="sxs-lookup"><span data-stu-id="bff21-144">Management</span></span>
    
    <span data-ttu-id="bff21-p108">Dans le cadre de scénarios cloud hybrides, la gestion inclut la capacité à assurer l'entretien des paramètres, données, comptes, stratégies et autorisations, ainsi qu'à assurer la surveillance continue de l'état d'intégrité des éléments du scénario et de ses performances. Vous pouvez également utiliser le même ensemble d'outils, tels que Systems Management Server, pour la gestion des ordinateurs virtuels dans IaaS Azure.</span><span class="sxs-lookup"><span data-stu-id="bff21-p108">Management for hybrid cloud scenarios includes the ability to maintain settings, data, accounts, policies, and permissions and to monitor the ongoing health of the elements of the scenario and its performance. You can also use the same tool set, such as Systems Management Server, for managing virtual machines in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="bff21-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bff21-147">See Also</span></span>

[<span data-ttu-id="bff21-148">Cloud hybride Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="bff21-148">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="bff21-149">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="bff21-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

