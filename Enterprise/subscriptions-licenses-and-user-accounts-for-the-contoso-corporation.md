---
title: Abonnements, licences et comptes d’utilisateur de Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Résumé : Comprendre la structure des abonnements de cloud de Contoso, licences, des comptes d’utilisateurs et des clients.'
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915509"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="e73e3-103">Abonnements, licences et comptes d’utilisateur de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="e73e3-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="e73e3-104">**Résumé :** Comprendre la structure des abonnements de cloud de Contoso, licences, des comptes d’utilisateurs et des clients.</span><span class="sxs-lookup"><span data-stu-id="e73e3-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="e73e3-105">Pour une utilisation cohérente des identités et de la facturation au sein de ses offres cloud, Microsoft fournit une hiérarchie d’organisation/d’abonnements/de licences/de comptes d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="e73e3-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="e73e3-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="e73e3-106">Organization</span></span>
    
    <span data-ttu-id="e73e3-107">Entité commerciale qui utilise les offres cloud de Microsoft et qui est généralement identifiée par un nom de domaine DNS public, par exemple contoso.com.</span><span class="sxs-lookup"><span data-stu-id="e73e3-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="e73e3-108">Abonnements</span><span class="sxs-lookup"><span data-stu-id="e73e3-108">Subscriptions</span></span>
    
    <span data-ttu-id="e73e3-p101">SaaS Microsoft cloud offres (Office 365, Intune/EMS et Dynamics 365), un abonnement est un produit spécifique et un ensemble acheté des licences utilisateur. Pour Azure, un abonnement permet de facturation des services en nuage consommés à l’organisation.</span><span class="sxs-lookup"><span data-stu-id="e73e3-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="e73e3-111">Licences</span><span class="sxs-lookup"><span data-stu-id="e73e3-111">Licenses</span></span>
    
    <span data-ttu-id="e73e3-p102">Pour les offres de cloud Microsoft SaaS, une licence permet à un compte d’utilisateur spécifique à utiliser les services en nuage. Pour Azure, les licences logicielles sont créées dans le service de tarification, mais dans certains cas, que vous devez acquérir des licences logicielles supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e73e3-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="e73e3-114">Comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="e73e3-114">User accounts</span></span>
    
    <span data-ttu-id="e73e3-115">Les comptes d’utilisateur sont stockés dans un client Azure AD et peuvent être synchronisés à partir d’un fournisseur d’identités local, tel que Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="e73e3-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="e73e3-116">Structure de Contoso</span><span class="sxs-lookup"><span data-stu-id="e73e3-116">Contoso's structure</span></span>

<span data-ttu-id="e73e3-117">Contoso a établi la structure d’organisation, d’abonnements, de licences, de comptes et de clients suivante :</span><span class="sxs-lookup"><span data-stu-id="e73e3-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="e73e3-118">**Figure 1 : organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso**</span><span class="sxs-lookup"><span data-stu-id="e73e3-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso](media/Contoso-Poster/Subscriptions.png)
  
<span data-ttu-id="e73e3-120">La Figure 1 montre comment l’organisation Contoso inclut plusieurs abonnements et est liée à un client Azure AD commun qui contient les comptes d’utilisateurs synchronisés à partir de la forêt Windows Server AD contoso.com.</span><span class="sxs-lookup"><span data-stu-id="e73e3-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="e73e3-121">**Organisation** La société Contoso est identifiée par son nom de domaine de public contoso.com.</span><span class="sxs-lookup"><span data-stu-id="e73e3-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="e73e3-122">**Abonnements et licences** La société Contoso utilise les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e73e3-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="e73e3-123">Le produit Office 365 entreprise E3 avec 5 000 licences</span><span class="sxs-lookup"><span data-stu-id="e73e3-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="e73e3-124">Produit Office 365 Entreprise E5 avec 200 licences</span><span class="sxs-lookup"><span data-stu-id="e73e3-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="e73e3-125">Le produit EMS avec 5 000 licences</span><span class="sxs-lookup"><span data-stu-id="e73e3-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="e73e3-126">Produit Dynamic 365 avec 100 licences
</span><span class="sxs-lookup"><span data-stu-id="e73e3-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="e73e3-127">Abonnements Azure multiples en fonction des régions</span><span class="sxs-lookup"><span data-stu-id="e73e3-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="e73e3-128">**Comptes d’utilisateurs** Un client Azure AD common contient la liste des comptes d’utilisateurs et les groupes utilisés par tous les abonnements de Contoso, à l’exception de développement/test abonnements Azure.</span><span class="sxs-lookup"><span data-stu-id="e73e3-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="e73e3-129">Pour les clients de Contoso :</span><span class="sxs-lookup"><span data-stu-id="e73e3-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="e73e3-p103">Dans le cadre des offres cloud SaaS, le client désigne l’emplacement régional qui héberge les serveurs fournissant des services cloud. Contoso a choisi la région Europe pour héberger ses clients Office 365, EMS et Dynamics 365.
 </span><span class="sxs-lookup"><span data-stu-id="e73e3-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="e73e3-p104">Services PaaS Azure et les applications et les charges de travail informatique IaaS peuvent avoir location dans les centres de données Azure dans le monde entier. Un client Azure AD est une instance spécifique d’Azure Active Directory contenant les comptes et groupes.</span><span class="sxs-lookup"><span data-stu-id="e73e3-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="e73e3-134">Le client Azure AD courants qui contient les comptes synchronisés pour la forêt Contoso Windows Server AD assure IDaaS entre les offres de cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e73e3-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="e73e3-135">Pour plus d’informations, voir [abonnements, licences et des comptes et clients pour les offres de cloud de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="e73e3-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="e73e3-136">Abonnements Azure de Contoso</span><span class="sxs-lookup"><span data-stu-id="e73e3-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="e73e3-137">La Figure 2 présente la structure hiérarchique des abonnements Azure de Contoso : 


</span><span class="sxs-lookup"><span data-stu-id="e73e3-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="e73e3-138">**Figure 2 : structure des abonnements Azure de Contoso**</span><span class="sxs-lookup"><span data-stu-id="e73e3-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Structure des abonnements Azure de Contoso](media/Contoso-Poster/Subscriptions-Nested.png)
  
- <span data-ttu-id="e73e3-140">Contoso est prioritaire, conformément à l’Accord Entreprise conclu avec Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e73e3-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="e73e3-141">Il existe un ensemble de comptes correspondant aux différentes régions de la société Contoso dans le monde, basée sur les domaines de la forêt de Windows Server AD de Contoso.</span><span class="sxs-lookup"><span data-stu-id="e73e3-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="e73e3-142">Dans chaque région, il existe un ou plusieurs des abonnements en fonction des besoins de déploiement de développement, de test et de production de cette région.</span><span class="sxs-lookup"><span data-stu-id="e73e3-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="e73e3-p105">Chaque abonnement Azure peut être associé à un même client Azure AD possédant des comptes et groupes d’utilisateurs pour l’authentification aux services Azure et les droits qui leur sont associés. Les abonnements de production utilisent le client Azure AD commun de Contoso.</span><span class="sxs-lookup"><span data-stu-id="e73e3-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e73e3-145">See Also</span><span class="sxs-lookup"><span data-stu-id="e73e3-145">See Also</span></span>

[<span data-ttu-id="e73e3-146">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e73e3-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="e73e3-147">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="e73e3-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="e73e3-148">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)
</span><span class="sxs-lookup"><span data-stu-id="e73e3-148">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>




