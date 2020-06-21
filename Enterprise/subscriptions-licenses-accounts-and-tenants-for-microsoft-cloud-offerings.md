---
title: Abonnements, licences, comptes et clients des offres de cloud de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Résumé : Comprenez les relations des organisations, des abonnements, des licences, des comptes d’utilisateur et des clients au sein des offres de cloud de Microsoft.'
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735962"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="651e6-103">Abonnements, licences, comptes et clients des offres de cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="651e6-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="651e6-104">**Résumé :** Comprenez les relations des organisations, des abonnements, des licences, des comptes d’utilisateur et des clients au sein des offres de cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="651e6-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="651e6-105">Microsoft fournit une hiérarchie d’organisations, d’abonnements, de licences et de comptes d’utilisateur pour une utilisation cohérente des identités et de la facturation au sein de ses offres de cloud :</span><span class="sxs-lookup"><span data-stu-id="651e6-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="651e6-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="651e6-106">Microsoft Office 365</span></span>
- <span data-ttu-id="651e6-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="651e6-107">Microsoft Azure</span></span>
- <span data-ttu-id="651e6-108">Microsoft Intune et Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="651e6-108">Microsoft Intune and Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="651e6-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="651e6-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="651e6-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combine Office 365, EMS, et Windows 10 Entreprise en un seul abonnement et ensemble de services intégrés.</span><span class="sxs-lookup"><span data-stu-id="651e6-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="651e6-111">Éléments de la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="651e6-111">Elements of the hierarchy</span></span>

<span data-ttu-id="651e6-112">Voici les éléments de la hiérarchie :</span><span class="sxs-lookup"><span data-stu-id="651e6-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="651e6-113">Organisation</span><span class="sxs-lookup"><span data-stu-id="651e6-113">Organization</span></span>

<span data-ttu-id="651e6-114">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span><span class="sxs-lookup"><span data-stu-id="651e6-114">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span></span> <span data-ttu-id="651e6-115">The organization is a container for subscriptions.</span><span class="sxs-lookup"><span data-stu-id="651e6-115">The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="651e6-116">Abonnements</span><span class="sxs-lookup"><span data-stu-id="651e6-116">Subscriptions</span></span>

<span data-ttu-id="651e6-117">Un abonnement est un accord conclu avec Microsoft sur l’utilisation d’une ou de plusieurs plateformes ou services de cloud Microsoft, dont les frais applicables sont calculés sur la base de frais de licence par utilisateur ou selon la consommation des ressources de cloud.</span><span class="sxs-lookup"><span data-stu-id="651e6-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="651e6-118">Les offres de cloud Microsoft Software as a Service (SaaS) (Office 365, Intune/EMS et Dynamics 365) facturent des frais de licence par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="651e6-118">Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="651e6-119">Les offres de cloud Microsoft Platform as a Service (PaaS) et Infrastructure as a Service (IaaS) (Azure) facturent des frais en fonction de la consommation des ressources de cloud.</span><span class="sxs-lookup"><span data-stu-id="651e6-119">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="651e6-120">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span><span class="sxs-lookup"><span data-stu-id="651e6-120">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span></span> <span data-ttu-id="651e6-121">You can convert a trial subscription to a paid subscription.</span><span class="sxs-lookup"><span data-stu-id="651e6-121">You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="651e6-122">Les organisations peuvent avoir plusieurs abonnements pour les offres de cloud Microsoft, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="651e6-122">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="651e6-123">La Figure 1 présente une organisation unique avec plusieurs abonnements Office 365, un abonnement Intune, un abonnement Dynamics 365 et plusieurs abonnements Azure.</span><span class="sxs-lookup"><span data-stu-id="651e6-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="651e6-124">**Figure 1 : Exemple de plusieurs abonnements pour une organisation**</span><span class="sxs-lookup"><span data-stu-id="651e6-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Un exemple d’organisation avec plusieurs abonnements pour les offres de cloud de Microsoft.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="651e6-126">Licences</span><span class="sxs-lookup"><span data-stu-id="651e6-126">Licenses</span></span>

<span data-ttu-id="651e6-127">Pour les offres de cloud SaaS de Microsoft, une licence permet à un compte d’utilisateur spécifique d’utiliser les services de l’offre de cloud.</span><span class="sxs-lookup"><span data-stu-id="651e6-127">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="651e6-128">Vous payez un coût mensuel fixe dans le cadre de votre abonnement.</span><span class="sxs-lookup"><span data-stu-id="651e6-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="651e6-129">Les administrateurs attribuent des licences à des comptes d’utilisateur individuels dans l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="651e6-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="651e6-130">Par exemple, dans la Figure 2, la société Contoso a un abonnement à Office 365 Entreprise E5 avec 100 licences, ce qui permet à un maximum de 100 comptes d’utilisateur individuels d’utiliser les services et fonctionnalités d’Entreprise E5 Office 365.</span><span class="sxs-lookup"><span data-stu-id="651e6-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Office 365 Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="651e6-131">**Figure 2 : Licences liées aux abonnements SaaS d’une organisation**</span><span class="sxs-lookup"><span data-stu-id="651e6-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Exemple de plusieurs licences au sein des abonnements pour les offres de cloud SaaS de Microsoft.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="651e6-133">Pour les services de cloud PaaS Azure, les licences logicielles sont intégrées dans la tarification du service.  </span><span class="sxs-lookup"><span data-stu-id="651e6-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="651e6-134">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span><span class="sxs-lookup"><span data-stu-id="651e6-134">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span></span> <span data-ttu-id="651e6-135">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span><span class="sxs-lookup"><span data-stu-id="651e6-135">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span></span> <span data-ttu-id="651e6-136">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="651e6-136">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="651e6-137">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span><span class="sxs-lookup"><span data-stu-id="651e6-137">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span></span> <span data-ttu-id="651e6-138">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span><span class="sxs-lookup"><span data-stu-id="651e6-138">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span></span> <span data-ttu-id="651e6-139">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span><span class="sxs-lookup"><span data-stu-id="651e6-139">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span></span> <span data-ttu-id="651e6-140">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span><span class="sxs-lookup"><span data-stu-id="651e6-140">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="651e6-141">Comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="651e6-141">User accounts</span></span>

<span data-ttu-id="651e6-142">Les comptes d’utilisateur pour toutes les offres de cloud de Microsoft sont stockés dans un client Azure Active Directory (Azure AD) qui contient des comptes et groupes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="651e6-142">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="651e6-143">Un client Azure AD peut être synchronisé avec vos comptes Active Directory Domain Services (AD DS) existants à l’aide d’Azure AD Connect, un service de serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="651e6-143">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="651e6-144">C’est ce que l’on appelle la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="651e6-144">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="651e6-145">La Figure 3 illustre un exemple de plusieurs abonnements d’une organisation à l’aide d’un client Azure Active Directory commun qui contient les comptes de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="651e6-146">**Figure 3 : Plusieurs abonnements d’une organisation qui utilisent le même client Azure AD**</span><span class="sxs-lookup"><span data-stu-id="651e6-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Un exemple d’organisation avec plusieurs abonnements utilisant tous le même client Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="651e6-148">Clients</span><span class="sxs-lookup"><span data-stu-id="651e6-148">Tenants</span></span>

<span data-ttu-id="651e6-149">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span><span class="sxs-lookup"><span data-stu-id="651e6-149">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="651e6-150">For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span><span class="sxs-lookup"><span data-stu-id="651e6-150">For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="651e6-151">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span><span class="sxs-lookup"><span data-stu-id="651e6-151">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span></span> <span data-ttu-id="651e6-152">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span><span class="sxs-lookup"><span data-stu-id="651e6-152">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="651e6-153">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span><span class="sxs-lookup"><span data-stu-id="651e6-153">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="651e6-154">Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant.</span><span class="sxs-lookup"><span data-stu-id="651e6-154">Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant.</span></span> <span data-ttu-id="651e6-155">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span><span class="sxs-lookup"><span data-stu-id="651e6-155">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="651e6-156">Résumé de la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="651e6-156">Summary of the hierarchy</span></span>

<span data-ttu-id="651e6-157">Voici un récapitulatif rapide :</span><span class="sxs-lookup"><span data-stu-id="651e6-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="651e6-158">Une organisation peut avoir plusieurs abonnements</span><span class="sxs-lookup"><span data-stu-id="651e6-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="651e6-159">Un abonnement peut avoir plusieurs licences</span><span class="sxs-lookup"><span data-stu-id="651e6-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="651e6-160">Des licences peuvent être affectées à des comptes d’utilisateur individuels</span><span class="sxs-lookup"><span data-stu-id="651e6-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="651e6-161">Les comptes d’utilisateur sont stockés dans un client Azure AD</span><span class="sxs-lookup"><span data-stu-id="651e6-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="651e6-162">Voici un exemple de relation des organisations, des abonnements, des licences et des comptes d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="651e6-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="651e6-163">Une organisation identifiée par son nom de domaine public.</span><span class="sxs-lookup"><span data-stu-id="651e6-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="651e6-164">Un abonnement Office 365 Entreprise E3 avec licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="651e6-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="651e6-165">Un abonnement Office 365 Entreprise E5 avec licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="651e6-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="651e6-166">Un abonnement EMS avec licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="651e6-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="651e6-167">Un abonnement Dynamics 365 avec licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="651e6-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="651e6-168">Abonnements Azure multiples</span><span class="sxs-lookup"><span data-stu-id="651e6-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="651e6-169">Les comptes d’utilisateurs de l’organisation dans un client Azure AD commun.</span><span class="sxs-lookup"><span data-stu-id="651e6-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="651e6-170">Plusieurs abonnements à des offres de cloud Microsoft peuvent utiliser le même client Azure AD, qui agit comme un fournisseur d’identité commun.</span><span class="sxs-lookup"><span data-stu-id="651e6-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="651e6-171">Un client Azure AD central qui contient les comptes synchronisés de votre AD DS local fournit une identité IDaaS dans le cloud pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="651e6-172">**Figure 4 : Comptes en local synchronisés et IDaaS pour une organisation**</span><span class="sxs-lookup"><span data-stu-id="651e6-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![Identité sous la forme d’un service (IaaS) IDaaS pour votre organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="651e6-174">La Figure 4 montre l’utilisation d’un client Azure AD commun par les offres cloud SaaS de Microsoft, les applications PaaS Azure et les machines virtuelles dans IaaS Azure qui utilisent Azure Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="651e6-174">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span></span> <span data-ttu-id="651e6-175">Azure AD Connect synchronise la forêt AD DS locale avec le client Azure AD.</span><span class="sxs-lookup"><span data-stu-id="651e6-175">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="651e6-176">Combiner les abonnements de plusieurs offres de cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="651e6-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="651e6-177">Le tableau suivant décrit la manière dont vous pouvez combiner plusieurs offres de cloud Microsoft en disposant déjà d’un abonnement pour un type d’offre de cloud (étiquettes actives vers le bas de la première colonne) et en ajoutant un abonnement pour une offre de cloud différente (à travers les colonnes).</span><span class="sxs-lookup"><span data-stu-id="651e6-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="651e6-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="651e6-178">**Office 365**</span></span>|<span data-ttu-id="651e6-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="651e6-179">**Azure**</span></span>|<span data-ttu-id="651e6-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="651e6-180">**Intune/EMS**</span></span>|<span data-ttu-id="651e6-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="651e6-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="651e6-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="651e6-182">**Office 365**</span></span> <br/> |<span data-ttu-id="651e6-183">N/A</span><span class="sxs-lookup"><span data-stu-id="651e6-183">NA</span></span>  <br/> |<span data-ttu-id="651e6-184">Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="651e6-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="651e6-185">Vous ajoutez un abonnement Intune/EMS à votre organisation à partir du Centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="651e6-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="651e6-186">Vous ajoutez un abonnement Dynamics 365 à votre organisation à partir du Centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="651e6-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="651e6-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="651e6-187">**Azure**</span></span> <br/> |<span data-ttu-id="651e6-188">Vous ajoutez un abonnement Office 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="651e6-189">N/A</span><span class="sxs-lookup"><span data-stu-id="651e6-189">NA</span></span>  <br/> |<span data-ttu-id="651e6-190">Vous ajoutez un abonnement Intune/EMS à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="651e6-191">Vous ajoutez un abonnement Dynamics 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="651e6-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="651e6-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="651e6-193">Vous ajoutez un abonnement Office 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="651e6-194">Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="651e6-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="651e6-195">N/A</span><span class="sxs-lookup"><span data-stu-id="651e6-195">NA</span></span>  <br/> |<span data-ttu-id="651e6-196">Vous ajoutez un abonnement Dynamics 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="651e6-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="651e6-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="651e6-198">Vous ajoutez un abonnement Office 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="651e6-199">Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="651e6-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="651e6-200">Vous ajoutez un abonnement Intune/EMS à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="651e6-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="651e6-201">N/A</span><span class="sxs-lookup"><span data-stu-id="651e6-201">NA</span></span>  <br/> |
   
<span data-ttu-id="651e6-202">Une solution simple pour ajouter des abonnements à votre organisation pour les services SaaS Microsoft consiste à utiliser le centre d’administration :</span><span class="sxs-lookup"><span data-stu-id="651e6-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="651e6-203">Connectez-vous au Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) avec votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="651e6-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="651e6-204">À partir du volet de navigation gauche de la page d’accueil du **centre d’administration**, cliquez sur **Facturation**, puis **Acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="651e6-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="651e6-205">Dans la page **Acheter des services**, achetez vos nouveaux abonnements.</span><span class="sxs-lookup"><span data-stu-id="651e6-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="651e6-206">Le centre d’administration affecte l’organisation et le client Azure AD de votre abonnement à Office 365 aux nouveaux abonnements pour les offres cloud SaaS.</span><span class="sxs-lookup"><span data-stu-id="651e6-206">The admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="651e6-207">Pour ajouter un abonnement Azure disposant de la même organisation et du même client Azure Active Directory que votre abonnement Office 365, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="651e6-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="651e6-208">Connectez-vous au portail Azure ([https://portal.azure.com](https://portal.azure.com)) avec votre compte Administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="651e6-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="651e6-209">Dans le volet de navigation gauche, cliquez sur **Abonnements**, puis sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="651e6-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="651e6-210">Dans la page **Ajouter un abonnement**, sélectionnez une offre et complétez l’accord et les informations de paiement.</span><span class="sxs-lookup"><span data-stu-id="651e6-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="651e6-211">Si vous avez obtenu séparément des abonnements Azure et Office 365, et que vous souhaitez accéder au client Office 365 Azure AD à partir de votre abonnement Azure, reportez-vous aux instructions décrites de l’article [Ajouter un abonnement Azure à votre locataire Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span><span class="sxs-lookup"><span data-stu-id="651e6-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="651e6-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="651e6-212">See also</span></span>

[<span data-ttu-id="651e6-213">Ressources relatives à l’architecture informatique Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="651e6-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="651e6-214">Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync</span><span class="sxs-lookup"><span data-stu-id="651e6-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="651e6-215">Solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="651e6-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="651e6-216">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="651e6-216">Next step</span></span>

[<span data-ttu-id="651e6-217">Évaluation de la connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="651e6-217">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
