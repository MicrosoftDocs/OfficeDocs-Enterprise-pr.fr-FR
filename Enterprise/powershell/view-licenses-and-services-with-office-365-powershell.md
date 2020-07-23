---
title: Afficher les licences et les services Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explique comment utiliser PowerShell pour afficher des informations sur les plans de gestion des licences, les services et les licences disponibles dans votre organisation Microsoft 365.
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230210"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a><span data-ttu-id="f17fd-103">Afficher les licences et les services Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f17fd-103">View Microsoft 365 licenses and services with PowerShell</span></span>

<span data-ttu-id="f17fd-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="f17fd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f17fd-105">Chaque abonnement Microsoft 365 se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f17fd-105">Every Microsoft 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="f17fd-106">**Plans** de gestion des licences Ils sont également appelés plans de licence ou plans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f17fd-106">**Licensing plans** These are also known as license plans or Microsoft 365 plans.</span></span> <span data-ttu-id="f17fd-107">Les plans de gestion des licences définissent les services Microsoft 365 disponibles pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f17fd-107">Licensing plans define the Microsoft 365 services that are available to users.</span></span> <span data-ttu-id="f17fd-108">Votre abonnement Microsoft 365 peut contenir plusieurs plans de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="f17fd-108">Your Microsoft 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="f17fd-109">Un exemple de plan de gestion des licences serait Microsoft 365 E3.</span><span class="sxs-lookup"><span data-stu-id="f17fd-109">An example licensing plan would be Microsoft 365 E3.</span></span>
    
- <span data-ttu-id="f17fd-110">**Services** Ces derniers sont également appelés plans de service.</span><span class="sxs-lookup"><span data-stu-id="f17fd-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="f17fd-111">Les services sont les produits, les fonctionnalités et les fonctionnalités de Microsoft 365 qui sont disponibles dans chaque plan de gestion des licences, par exemple les applications Exchange Online et Microsoft 365 pour entreprise (précédemment nommé Office 365 ProPlus).</span><span class="sxs-lookup"><span data-stu-id="f17fd-111">Services are the Microsoft 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Microsoft 365 Apps for enterprise (previously named Office 365 ProPlus).</span></span> <span data-ttu-id="f17fd-112">Des licences issues de différents plans de licence peuvent être attribuées à un même utilisateur, lui accordant l’accès à des services différents.</span><span class="sxs-lookup"><span data-stu-id="f17fd-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="f17fd-113">**Licences** Chaque plan de gestion des licences contient le nombre de licences que vous avez achetées.</span><span class="sxs-lookup"><span data-stu-id="f17fd-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="f17fd-114">Vous attribuez des licences aux utilisateurs afin qu’ils puissent utiliser les services Microsoft 365 définis par le plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="f17fd-114">You assign licenses to users so they can use the Microsoft 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="f17fd-115">Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences afin qu’il puisse se connecter à Microsoft 365 et utiliser les services.</span><span class="sxs-lookup"><span data-stu-id="f17fd-115">Every user account requires at least one license from one licensing plan so they can log on to Microsoft 365 and use the services.</span></span>
    
<span data-ttu-id="f17fd-116">Vous pouvez utiliser PowerShell pour Microsoft 365 pour afficher des détails sur les plans de licence, les licences et les services disponibles dans votre organisation Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f17fd-116">You can use PowerShell for Microsoft 365 to view details about the available licensing plans, licenses, and services in your Microsoft 365 organization.</span></span> <span data-ttu-id="f17fd-117">Pour plus d’informations sur les produits, les fonctionnalités et les services disponibles dans les différents abonnements Office 365, reportez-vous à la rubrique [office 365 plan options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="f17fd-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f17fd-118">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="f17fd-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f17fd-119">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="f17fd-119">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="f17fd-120">Pour afficher des informations récapitulatives sur vos plans de gestion de licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f17fd-120">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="f17fd-121">Les résultats contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f17fd-121">The results contain:</span></span>
  
- <span data-ttu-id="f17fd-122">**SkuPartNumber :** Affiche les plans de gestion des licences disponibles pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="f17fd-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="f17fd-123">Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="f17fd-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="f17fd-124">**Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="f17fd-125">**ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="f17fd-126">Pour afficher les détails des services Microsoft 365 disponibles dans tous vos plans de licence, commencez par afficher la liste de vos plans de licence.</span><span class="sxs-lookup"><span data-stu-id="f17fd-126">To view details about the Microsoft 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="f17fd-127">Ensuite, stockez les informations des plans de licence dans une variable.</span><span class="sxs-lookup"><span data-stu-id="f17fd-127">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="f17fd-128">Ensuite, affichez les services dans un plan de licence spécifique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-128">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="f17fd-129">\<index>est un entier qui spécifie le numéro de ligne du plan de licence à partir de l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande, moins 1.</span><span class="sxs-lookup"><span data-stu-id="f17fd-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="f17fd-130">Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande est le suivant :</span><span class="sxs-lookup"><span data-stu-id="f17fd-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="f17fd-131">La commande permettant d’afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f17fd-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="f17fd-132">ENTERPRISEPREMIUM est la troisième ligne.</span><span class="sxs-lookup"><span data-stu-id="f17fd-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="f17fd-133">Par conséquent, la valeur d’index est (3-1) ou 2.</span><span class="sxs-lookup"><span data-stu-id="f17fd-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="f17fd-134">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="f17fd-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f17fd-135">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f17fd-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f17fd-136">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f17fd-136">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="f17fd-137">Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="f17fd-138">Plus précisément, le script vous permet d’afficher et de désactiver les services de votre organisation Microsoft 365, y compris Sway.</span><span class="sxs-lookup"><span data-stu-id="f17fd-138">Specifically, the script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="f17fd-139">Pour plus d’informations, consultez la rubrique [désactiver l’accès à Sway avec PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f17fd-139">For more information, see [Disable access to Sway with PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="f17fd-140">Pour afficher des informations récapitulatives sur vos plans de gestion des licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f17fd-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="f17fd-141">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="f17fd-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f17fd-142">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f17fd-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="f17fd-143">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f17fd-143">The results contain the following information:</span></span>
  
- <span data-ttu-id="f17fd-144">**AccountSkuId :** Affichez les plans de gestion des licences disponibles pour votre organisation à l’aide de la syntaxe `<CompanyName>:<LicensingPlan>` .</span><span class="sxs-lookup"><span data-stu-id="f17fd-144">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="f17fd-145">_\<CompanyName>_ est la valeur que vous avez fournie lorsque vous vous êtes inscrit à Microsoft 365 et qui est unique pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="f17fd-145">_\<CompanyName>_ is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="f17fd-146">La _\<LicensingPlan>_ valeur est la même pour tout le monde.</span><span class="sxs-lookup"><span data-stu-id="f17fd-146">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="f17fd-147">Par exemple, dans la valeur `litwareinc:ENTERPRISEPACK` , le nom de la société `litwareinc` et le nom du plan de gestion des licences `ENTERPRISEPACK` , qui est le nom du système pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="f17fd-147">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="f17fd-148">**ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-148">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="f17fd-149">**WarningUnits :** Nombre de licences dans un plan de gestion des licences que vous n’avez pas renouvelé et qui expireront après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="f17fd-149">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="f17fd-150">**ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="f17fd-150">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="f17fd-151">Pour afficher les détails des services Microsoft 365 disponibles dans tous vos plans de licence, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f17fd-151">To view details about the Microsoft 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="f17fd-152">Le tableau suivant présente les plans de service Microsoft 365 et leurs noms conviviaux pour les services les plus courants.</span><span class="sxs-lookup"><span data-stu-id="f17fd-152">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="f17fd-153">La liste de vos plans de services peut être différente.</span><span class="sxs-lookup"><span data-stu-id="f17fd-153">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="f17fd-154">**Plan de services**</span><span class="sxs-lookup"><span data-stu-id="f17fd-154">**Service plan**</span></span>|<span data-ttu-id="f17fd-155">**Description**</span><span class="sxs-lookup"><span data-stu-id="f17fd-155">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="f17fd-156">Sway</span><span class="sxs-lookup"><span data-stu-id="f17fd-156">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="f17fd-157">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f17fd-157">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="f17fd-158">Yammer</span><span class="sxs-lookup"><span data-stu-id="f17fd-158">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="f17fd-159">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="f17fd-159">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="f17fd-160">Applications Microsoft 365 pour les entreprises *(précédemment nommé Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="f17fd-160">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="f17fd-161">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="f17fd-161">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="f17fd-162">Office</span><span class="sxs-lookup"><span data-stu-id="f17fd-162">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="f17fd-163">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f17fd-163">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="f17fd-164">Exchange Online (plan 2)</span><span class="sxs-lookup"><span data-stu-id="f17fd-164">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="f17fd-165">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="f17fd-165">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="f17fd-166">Pour afficher les détails des services Microsoft 365 disponibles dans un plan de gestion de licences spécifique, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="f17fd-166">To view details about the Microsoft 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="f17fd-167">Cet exemple présente les services disponibles dans le plan de gestion des licences litwareinc : ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="f17fd-167">This example shows the services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="f17fd-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f17fd-168">See also</span></span>

[<span data-ttu-id="f17fd-169">Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f17fd-169">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f17fd-170">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f17fd-170">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f17fd-171">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f17fd-171">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
