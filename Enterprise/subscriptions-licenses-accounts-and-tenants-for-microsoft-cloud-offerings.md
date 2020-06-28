---
title: Abonnements, licences, comptes et clients des offres de cloud de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
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
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906263"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="986d6-103">Abonnements, licences, comptes et clients des offres de cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="986d6-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

<span data-ttu-id="986d6-104">Microsoft fournit une hiérarchie d’organisations, d’abonnements, de licences et de comptes d’utilisateur pour une utilisation cohérente des identités et de la facturation au sein de ses offres de cloud :</span><span class="sxs-lookup"><span data-stu-id="986d6-104">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="986d6-105">Microsoft 365 et Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="986d6-105">Microsoft 365 and Microsoft Office 365</span></span>
- <span data-ttu-id="986d6-106">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="986d6-106">Microsoft Azure</span></span>
- <span data-ttu-id="986d6-107">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="986d6-107">Microsoft Dynamics 365</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="986d6-108">Éléments de la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="986d6-108">Elements of the hierarchy</span></span>

<span data-ttu-id="986d6-109">Voici les éléments de la hiérarchie :</span><span class="sxs-lookup"><span data-stu-id="986d6-109">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="986d6-110">Organisation</span><span class="sxs-lookup"><span data-stu-id="986d6-110">Organization</span></span>

<span data-ttu-id="986d6-111">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span><span class="sxs-lookup"><span data-stu-id="986d6-111">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span></span> <span data-ttu-id="986d6-112">The organization is a container for subscriptions.</span><span class="sxs-lookup"><span data-stu-id="986d6-112">The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="986d6-113">Abonnements</span><span class="sxs-lookup"><span data-stu-id="986d6-113">Subscriptions</span></span>

<span data-ttu-id="986d6-114">Un abonnement est un accord conclu avec Microsoft sur l’utilisation d’une ou de plusieurs plateformes ou services de cloud Microsoft, dont les frais applicables sont calculés sur la base de frais de licence par utilisateur ou selon la consommation des ressources de cloud.</span><span class="sxs-lookup"><span data-stu-id="986d6-114">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="986d6-115">Offres Cloud de Microsoft Software as a service (SaaS) (Microsoft 365 et Dynamics 365) frais de licence par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="986d6-115">Microsoft's Software as a Service (SaaS)-based cloud offerings (Microsoft 365 and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="986d6-116">Les offres de cloud Microsoft Platform as a Service (PaaS) et Infrastructure as a Service (IaaS) (Azure) facturent des frais en fonction de la consommation des ressources de cloud.</span><span class="sxs-lookup"><span data-stu-id="986d6-116">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="986d6-117">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span><span class="sxs-lookup"><span data-stu-id="986d6-117">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span></span> <span data-ttu-id="986d6-118">You can convert a trial subscription to a paid subscription.</span><span class="sxs-lookup"><span data-stu-id="986d6-118">You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="986d6-119">Les organisations peuvent avoir plusieurs abonnements pour les offres de cloud Microsoft, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="986d6-119">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="986d6-120">La figure 1 présente une organisation unique comportant plusieurs abonnements Microsoft 365, un abonnement Dynamics 365 et plusieurs abonnements Azure.</span><span class="sxs-lookup"><span data-stu-id="986d6-120">Figure 1 shows a single organization that has multiple Microsoft 365 subscriptions, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="986d6-121">**Figure 1 : Exemple de plusieurs abonnements pour une organisation**</span><span class="sxs-lookup"><span data-stu-id="986d6-121">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Un exemple d’organisation avec plusieurs abonnements pour les offres de cloud de Microsoft.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a><span data-ttu-id="986d6-123">Licences</span><span class="sxs-lookup"><span data-stu-id="986d6-123">Licenses</span></span>

<span data-ttu-id="986d6-124">Pour les offres de cloud SaaS de Microsoft, une licence permet à un compte d’utilisateur spécifique d’utiliser les services de l’offre de cloud.</span><span class="sxs-lookup"><span data-stu-id="986d6-124">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="986d6-125">Vous payez un coût mensuel fixe dans le cadre de votre abonnement.</span><span class="sxs-lookup"><span data-stu-id="986d6-125">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="986d6-126">Les administrateurs attribuent des licences à des comptes d’utilisateur individuels dans l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="986d6-126">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="986d6-127">Pour l’exemple de la figure 2, Contoso Corporation dispose d’un abonnement Microsoft 365 E5 avec 100 licences, ce qui permet jusqu’à 100 comptes d’utilisateur individuels d’utiliser les fonctionnalités et services de Microsoft 365 E5.</span><span class="sxs-lookup"><span data-stu-id="986d6-127">For the example in Figure 2, the Contoso Corporation has a Microsoft 365 E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Microsoft 365 E5 features and services.</span></span>
  
<span data-ttu-id="986d6-128">**Figure 2 : Licences liées aux abonnements SaaS d’une organisation**</span><span class="sxs-lookup"><span data-stu-id="986d6-128">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Exemple de plusieurs licences au sein des abonnements pour les offres de cloud SaaS de Microsoft.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="986d6-130">Pour les services de cloud PaaS Azure, les licences logicielles sont intégrées dans la tarification du service.  </span><span class="sxs-lookup"><span data-stu-id="986d6-130">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="986d6-131">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span><span class="sxs-lookup"><span data-stu-id="986d6-131">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span></span> <span data-ttu-id="986d6-132">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span><span class="sxs-lookup"><span data-stu-id="986d6-132">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span></span> <span data-ttu-id="986d6-133">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="986d6-133">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="986d6-134">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span><span class="sxs-lookup"><span data-stu-id="986d6-134">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span></span> <span data-ttu-id="986d6-135">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span><span class="sxs-lookup"><span data-stu-id="986d6-135">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span></span> <span data-ttu-id="986d6-136">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span><span class="sxs-lookup"><span data-stu-id="986d6-136">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span></span> <span data-ttu-id="986d6-137">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span><span class="sxs-lookup"><span data-stu-id="986d6-137">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="986d6-138">Comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="986d6-138">User accounts</span></span>

<span data-ttu-id="986d6-139">Les comptes d’utilisateur pour toutes les offres de cloud de Microsoft sont stockés dans un client Azure Active Directory (Azure AD) qui contient des comptes et groupes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="986d6-139">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="986d6-140">Un client Azure AD peut être synchronisé avec vos comptes Active Directory Domain Services (AD DS) existants à l’aide d’Azure AD Connect, un service de serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="986d6-140">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="986d6-141">C’est ce que l’on appelle la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="986d6-141">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="986d6-142">La Figure 3 illustre un exemple de plusieurs abonnements d’une organisation à l’aide d’un client Azure Active Directory commun qui contient les comptes de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="986d6-142">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="986d6-143">**Figure 3 : Plusieurs abonnements d’une organisation qui utilisent le même client Azure AD**</span><span class="sxs-lookup"><span data-stu-id="986d6-143">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Un exemple d’organisation avec plusieurs abonnements utilisant tous le même client Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="986d6-145">Clients</span><span class="sxs-lookup"><span data-stu-id="986d6-145">Tenants</span></span>

<span data-ttu-id="986d6-146">Pour les offres SaaS cloud, le client est l’emplacement régional qui héberge les serveurs fournissant des services de cloud.</span><span class="sxs-lookup"><span data-stu-id="986d6-146">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="986d6-147">Par exemple, la société Contoso Corporation a choisi la région européenne pour héberger ses locataires Microsoft 365, EMS et Dynamics 365 pour les travailleurs 15 000 dans leur siège social de Paris.</span><span class="sxs-lookup"><span data-stu-id="986d6-147">For example, the Contoso Corporation chose the European region to host its Microsoft 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="986d6-148">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span><span class="sxs-lookup"><span data-stu-id="986d6-148">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span></span> <span data-ttu-id="986d6-149">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span><span class="sxs-lookup"><span data-stu-id="986d6-149">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="986d6-150">Un client Azure Active Directory est une instance spécifique d’Azure AD contenant des comptes et des groupes.</span><span class="sxs-lookup"><span data-stu-id="986d6-150">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="986d6-151">Les abonnements payants ou d’évaluation de Microsoft 365 ou Dynamics 365 incluent un locataire Azure AD gratuit.</span><span class="sxs-lookup"><span data-stu-id="986d6-151">Paid or trial subscriptions of Microsoft 365 or Dynamics 365 include a free Azure AD tenant.</span></span> <span data-ttu-id="986d6-152">Ce client Azure Active Directory n’inclut pas les autres services Azure et n’est pas identique à un abonnement d’évaluation ou payant Azure.</span><span class="sxs-lookup"><span data-stu-id="986d6-152">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="986d6-153">Résumé de la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="986d6-153">Summary of the hierarchy</span></span>

<span data-ttu-id="986d6-154">Voici un récapitulatif rapide :</span><span class="sxs-lookup"><span data-stu-id="986d6-154">Here is a quick recap:</span></span>
  
- <span data-ttu-id="986d6-155">Une organisation peut avoir plusieurs abonnements</span><span class="sxs-lookup"><span data-stu-id="986d6-155">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="986d6-156">Un abonnement peut avoir plusieurs licences</span><span class="sxs-lookup"><span data-stu-id="986d6-156">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="986d6-157">Des licences peuvent être affectées à des comptes d’utilisateur individuels</span><span class="sxs-lookup"><span data-stu-id="986d6-157">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="986d6-158">Les comptes d’utilisateur sont stockés dans un client Azure AD</span><span class="sxs-lookup"><span data-stu-id="986d6-158">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="986d6-159">Voici un exemple de relation des organisations, des abonnements, des licences et des comptes d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="986d6-159">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="986d6-160">Une organisation identifiée par son nom de domaine public.</span><span class="sxs-lookup"><span data-stu-id="986d6-160">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="986d6-161">Un abonnement Microsoft 365 E3 avec des licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="986d6-161">A Microsoft 365 E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="986d6-162">Un abonnement Microsoft 365 E5 avec des licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="986d6-162">A Microsoft 365 E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="986d6-163">Un abonnement Dynamics 365 avec licences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="986d6-163">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="986d6-164">Abonnements Azure multiples</span><span class="sxs-lookup"><span data-stu-id="986d6-164">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="986d6-165">Les comptes d’utilisateurs de l’organisation dans un client Azure AD commun.</span><span class="sxs-lookup"><span data-stu-id="986d6-165">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="986d6-166">Plusieurs abonnements à des offres de cloud Microsoft peuvent utiliser le même client Azure AD, qui agit comme un fournisseur d’identité commun.</span><span class="sxs-lookup"><span data-stu-id="986d6-166">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="986d6-167">Un client Azure AD central qui contient les comptes synchronisés de votre AD DS local fournit une identité IDaaS dans le cloud pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="986d6-167">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="986d6-168">**Figure 4 : Comptes en local synchronisés et IDaaS pour une organisation**</span><span class="sxs-lookup"><span data-stu-id="986d6-168">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![Identité sous la forme d’un service (IaaS) IDaaS pour votre organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="986d6-170">La Figure 4 montre l’utilisation d’un client Azure AD commun par les offres cloud SaaS de Microsoft, les applications PaaS Azure et les machines virtuelles dans IaaS Azure qui utilisent Azure Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="986d6-170">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span></span> <span data-ttu-id="986d6-171">Azure AD Connect synchronise la forêt AD DS locale avec le client Azure AD.</span><span class="sxs-lookup"><span data-stu-id="986d6-171">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="986d6-172">Combiner les abonnements de plusieurs offres de cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="986d6-172">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="986d6-173">Le tableau suivant décrit la manière dont vous pouvez combiner plusieurs offres de cloud Microsoft en disposant déjà d’un abonnement pour un type d’offre de cloud (étiquettes actives vers le bas de la première colonne) et en ajoutant un abonnement pour une offre de cloud différente (à travers les colonnes).</span><span class="sxs-lookup"><span data-stu-id="986d6-173">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="986d6-174">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="986d6-174">**Microsoft 365**</span></span>|<span data-ttu-id="986d6-175">**Azure**</span><span class="sxs-lookup"><span data-stu-id="986d6-175">**Azure**</span></span>|<span data-ttu-id="986d6-176">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="986d6-176">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="986d6-177">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="986d6-177">**Microsoft 365**</span></span> <br/> |<span data-ttu-id="986d6-178">N/A</span><span class="sxs-lookup"><span data-stu-id="986d6-178">NA</span></span>  <br/> |<span data-ttu-id="986d6-179">Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="986d6-179">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="986d6-180">Vous ajoutez un abonnement Dynamics 365 à votre organisation à partir du Centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="986d6-180">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="986d6-181">**Azure**</span><span class="sxs-lookup"><span data-stu-id="986d6-181">**Azure**</span></span> <br/> |<span data-ttu-id="986d6-182">Vous ajoutez un abonnement Microsoft 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="986d6-182">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="986d6-183">N/A</span><span class="sxs-lookup"><span data-stu-id="986d6-183">NA</span></span>  <br/> |<span data-ttu-id="986d6-184">Vous ajoutez un abonnement Dynamics 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="986d6-184">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="986d6-185">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="986d6-185">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="986d6-186">Vous ajoutez un abonnement Microsoft 365 à votre organisation.</span><span class="sxs-lookup"><span data-stu-id="986d6-186">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="986d6-187">Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="986d6-187">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="986d6-188">N/A</span><span class="sxs-lookup"><span data-stu-id="986d6-188">NA</span></span>  <br/> |
   
<span data-ttu-id="986d6-189">Une solution simple pour ajouter des abonnements à votre organisation pour les services SaaS Microsoft consiste à utiliser le centre d’administration :</span><span class="sxs-lookup"><span data-stu-id="986d6-189">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="986d6-190">Connectez-vous au Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) avec votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="986d6-190">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="986d6-191">À partir du volet de navigation gauche de la page d’accueil du **centre d’administration**, cliquez sur **Facturation**, puis **Acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="986d6-191">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="986d6-192">Dans la page **Acheter des services**, achetez vos nouveaux abonnements.</span><span class="sxs-lookup"><span data-stu-id="986d6-192">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="986d6-193">Le centre d’administration affecte l’organisation et le client Azure AD de votre abonnement Microsoft 365 aux nouveaux abonnements pour les offres de Cloud SaaS.</span><span class="sxs-lookup"><span data-stu-id="986d6-193">The admin center assigns the organization and Azure AD tenant of your Microsoft 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="986d6-194">Pour ajouter un abonnement Azure avec la même organisation et le même client Azure AD que votre abonnement Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="986d6-194">To add an Azure subscription with the same organization and Azure AD tenant as your Microsoft 365 subscription:</span></span>
  
1. <span data-ttu-id="986d6-195">Connectez-vous au portail Azure ( [https://portal.azure.com](https://portal.azure.com) ) avec votre compte d’administrateur général Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="986d6-195">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Microsoft 365 global administrator account.</span></span>
    
2. <span data-ttu-id="986d6-196">Dans le volet de navigation gauche, cliquez sur **Abonnements**, puis sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="986d6-196">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="986d6-197">Dans la page **Ajouter un abonnement**, sélectionnez une offre et complétez l’accord et les informations de paiement.</span><span class="sxs-lookup"><span data-stu-id="986d6-197">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="986d6-198">Si vous avez acheté des abonnements Azure et Microsoft 365 séparément et que vous souhaitez accéder au client Microsoft 365 Azure AD à partir de votre abonnement Azure, reportez-vous aux instructions de la rubrique [Ajouter un abonnement Azure existant à votre client Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span><span class="sxs-lookup"><span data-stu-id="986d6-198">If you purchased Azure and Microsoft 365 subscriptions separately and want to access the Microsoft 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="986d6-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="986d6-199">See also</span></span>

[<span data-ttu-id="986d6-200">Ressources relatives à l’architecture informatique Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="986d6-200">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="986d6-201">Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync</span><span class="sxs-lookup"><span data-stu-id="986d6-201">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="986d6-202">Solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="986d6-202">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="986d6-203">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="986d6-203">Next step</span></span>

[<span data-ttu-id="986d6-204">Évaluation de la connectivité réseau Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="986d6-204">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
