---
title: "Abonnements, licences et comptes d’utilisateur de Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "Résumé : Comprendre la structure des abonnements de nuage de Contoso, les licences, les comptes utilisateur et les locataires."
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="c9cad-103">Abonnements, licences et comptes d’utilisateur de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="c9cad-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="c9cad-104">**Résumé :** Comprendre la structure des abonnements de nuage de Contoso, les licences, les comptes utilisateur et les locataires.</span><span class="sxs-lookup"><span data-stu-id="c9cad-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="c9cad-105">Pour une utilisation cohérente des identités et de la facturation au sein de ses offres cloud, Microsoft fournit une hiérarchie d’organisation/d’abonnements/de licences/de comptes d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="c9cad-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="c9cad-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="c9cad-106">Organization</span></span>
    
    <span data-ttu-id="c9cad-107">Entité commerciale qui utilise les offres cloud de Microsoft et qui est généralement identifiée par un nom de domaine DNS public, par exemple contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c9cad-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="c9cad-108">Abonnements</span><span class="sxs-lookup"><span data-stu-id="c9cad-108">Subscriptions</span></span>
    
    <span data-ttu-id="c9cad-p101">Pour Microsoft SaaS (Office 365, Intune/EMS et Dynamics 365) les offres en nuage, un abonnement est un produit spécifique et un ensemble acheté des licences utilisateur. Pour Azure, permet à un abonnement pour la facturation des services en nuage consommés à l’organisation.</span><span class="sxs-lookup"><span data-stu-id="c9cad-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="c9cad-111">Licences</span><span class="sxs-lookup"><span data-stu-id="c9cad-111">Licenses</span></span>
    
    <span data-ttu-id="c9cad-p102">Pour les offres de cloud Microsoft SaaS, une licence permet à un compte d’utilisateur spécifique utiliser les services en nuage. Pour Azure, licences logicielles sont intégrées dans le prix du service, mais dans certains cas, que vous devez acquérir des licences logicielles supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c9cad-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="c9cad-114">Comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c9cad-114">User accounts</span></span>
    
    <span data-ttu-id="c9cad-115">Les comptes d’utilisateur sont stockés dans un client Azure AD et peuvent être synchronisés à partir d’un fournisseur d’identités local, tel que Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="c9cad-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="c9cad-116">Structure de Contoso</span><span class="sxs-lookup"><span data-stu-id="c9cad-116">Contoso's structure</span></span>

<span data-ttu-id="c9cad-117">Contoso a établi la structure d’organisation, d’abonnements, de licences, de comptes et de clients suivante :</span><span class="sxs-lookup"><span data-stu-id="c9cad-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="c9cad-118">**Figure 1 : Contoso organisation, abonnements, licences, comptes d’utilisateurs et locataires**</span><span class="sxs-lookup"><span data-stu-id="c9cad-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="c9cad-120">La Figure 1 montre comment l’organisation Contoso inclut plusieurs abonnements et est liée à un client Azure AD commun qui contient les comptes d’utilisateurs synchronisés à partir de la forêt Windows Server AD contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c9cad-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="c9cad-121">**Organisation** La société Contoso est identifiée par son contoso.com de nom de domaine public.</span><span class="sxs-lookup"><span data-stu-id="c9cad-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="c9cad-122">**Abonnements et licences** La société Contoso utilise les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c9cad-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="c9cad-123">Le produit Office 365 entreprise E3 avec 5 000 licences</span><span class="sxs-lookup"><span data-stu-id="c9cad-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="c9cad-124">Produit Office 365 Entreprise E5 avec 200 licences</span><span class="sxs-lookup"><span data-stu-id="c9cad-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="c9cad-125">Le produit EMS avec 5 000 licences</span><span class="sxs-lookup"><span data-stu-id="c9cad-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="c9cad-126">Le produit de Dynamics 365 avec 100 licences</span><span class="sxs-lookup"><span data-stu-id="c9cad-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="c9cad-127">Abonnements Azure multiples en fonction des régions</span><span class="sxs-lookup"><span data-stu-id="c9cad-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="c9cad-128">**Comptes d’utilisateurs** Un locataire AD Azure commun contient la liste des comptes d’utilisateurs et les groupes utilisés par tous les abonnements de Contoso, à l’exception de développement/test abonnements Azure.</span><span class="sxs-lookup"><span data-stu-id="c9cad-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="c9cad-129">Pour les clients de Contoso :</span><span class="sxs-lookup"><span data-stu-id="c9cad-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="c9cad-p103">Pour les offres de cloud SaaS, le locataire est l’emplacement régional qui héberge les serveurs fournissant des services de cloud. Contoso a choisi de la région Europe pour héberger ses locataires Office 365, EMS et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c9cad-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="c9cad-p104">Les services PaaS Azure et les applications et les charges de travail IaaS informatique peuvent avoir location dans n’importe quel centre de données Azure dans le monde entier. Un locataire AD Azure est une instance spécifique de publicité Azure contenant les comptes et les groupes.</span><span class="sxs-lookup"><span data-stu-id="c9cad-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="c9cad-134">Le locataire AD Azure commun qui contient les comptes synchronisés pour la forêt Contoso Windows Server Active Directory fournit des IDaaS entre les offres en nuage de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c9cad-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="c9cad-135">Pour plus d’informations, consultez [abonnements, des licences, des comptes et des locataires pour les offres en nuage de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="c9cad-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="c9cad-136">Abonnements Azure de Contoso</span><span class="sxs-lookup"><span data-stu-id="c9cad-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="c9cad-137">La figure 2 illustre la structure hiérarchique des abonnements d’Azure de Contoso :</span><span class="sxs-lookup"><span data-stu-id="c9cad-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="c9cad-138">**Figure 2 : Structure de Contoso pour les abonnements Azure**</span><span class="sxs-lookup"><span data-stu-id="c9cad-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Structure des abonnements Azure de Contoso](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="c9cad-140">Contoso est prioritaire, conformément à l’Accord Entreprise conclu avec Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c9cad-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="c9cad-141">Il existe un ensemble de comptes correspondant à différentes régions de la société Contoso dans le monde entier, basée sur les domaines de la forêt de Windows Server, Active Directory de Contoso.</span><span class="sxs-lookup"><span data-stu-id="c9cad-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="c9cad-142">Dans chaque région, il y a un ou plusieurs abonnements en fonction des besoins de déploiement de développement, de test et de production de cette région.</span><span class="sxs-lookup"><span data-stu-id="c9cad-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="c9cad-p105">Chaque abonnement Azure peut être associé à un même client Azure AD possédant des comptes et groupes d’utilisateurs pour l’authentification aux services Azure et les droits qui leur sont associés. Les abonnements de production utilisent le client Azure AD commun de Contoso.</span><span class="sxs-lookup"><span data-stu-id="c9cad-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c9cad-145">See Also</span><span class="sxs-lookup"><span data-stu-id="c9cad-145">See Also</span></span>

[<span data-ttu-id="c9cad-146">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="c9cad-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="c9cad-147">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c9cad-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="c9cad-148">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="c9cad-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




