---
title: Afficher les licences et les services avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de gestion des licences, les services et les licences disponibles dans votre organisation Office 365.
ms.openlocfilehash: b8a0bb1845f3c0db5aa47cea0c2f6e5e580c804f
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655846"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="4c008-103">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c008-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="4c008-104">Chaque abonnement Office 365 se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="4c008-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="4c008-105">**Plans** de gestion des licences Il s’agit également de plans de licence ou de plans Office 365.</span><span class="sxs-lookup"><span data-stu-id="4c008-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="4c008-106">Les plans de gestion des licences définissent les services Office 365 disponibles pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4c008-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="4c008-107">Votre abonnement Office 365 peut contenir plusieurs plans de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="4c008-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="4c008-108">Un exemple de plan de gestion des licences serait Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="4c008-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="4c008-109">**Services** Ces derniers sont également appelés plans de service.</span><span class="sxs-lookup"><span data-stu-id="4c008-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="4c008-110">Les services sont les produits, les fonctionnalités et les fonctionnalités Office 365 qui sont disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Office professionnel plus.</span><span class="sxs-lookup"><span data-stu-id="4c008-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="4c008-111">Des licences issues de différents plans de licence peuvent être attribuées à un même utilisateur, lui accordant l’accès à des services différents.</span><span class="sxs-lookup"><span data-stu-id="4c008-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="4c008-112">**Licences** Chaque plan de gestion des licences contient le nombre de licences que vous avez achetées.</span><span class="sxs-lookup"><span data-stu-id="4c008-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="4c008-113">Vous attribuez des licences aux utilisateurs afin qu’ils puissent utiliser les services Office 365 définis par le plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="4c008-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="4c008-114">Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences afin qu’il puisse se connecter à Office 365 et utiliser les services.</span><span class="sxs-lookup"><span data-stu-id="4c008-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="4c008-115">Vous pouvez utiliser Office 365 PowerShell pour afficher des détails sur les plans de licence, les licences et les services disponibles dans votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="4c008-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="4c008-116">Pour plus d’informations sur les produits, les fonctionnalités et les services disponibles dans les différents abonnements Office 365, reportez-vous à la rubrique [office 365 plan options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="4c008-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="4c008-117">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="4c008-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="4c008-118">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="4c008-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="4c008-119">Pour afficher des informations récapitulatives sur vos plans de gestion des licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4c008-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="4c008-120">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c008-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="4c008-121">**SkuPartNumber :** Affiche les plans de gestion des licences disponibles pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="4c008-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="4c008-122">Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="4c008-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="4c008-123">**Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c008-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="4c008-124">**ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c008-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="4c008-125">Pour afficher des détails sur les services Office 365 disponibles dans tous vos plans de licence, commencez par afficher la liste de vos plans de licence.</span><span class="sxs-lookup"><span data-stu-id="4c008-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="4c008-126">Ensuite, stockez les informations des plans de licence dans une variable.</span><span class="sxs-lookup"><span data-stu-id="4c008-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="4c008-127">Ensuite, affichez les services dans un plan de licence spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c008-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="4c008-128">\<index> est un entier qui spécifie le numéro de ligne du plan de licence à partir de `Get-AzureADSubscribedSku | Select SkuPartNumber` l’affichage de la commande, moins 1.</span><span class="sxs-lookup"><span data-stu-id="4c008-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="4c008-129">Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande est le suivant :</span><span class="sxs-lookup"><span data-stu-id="4c008-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="4c008-130">La commande permettant d’afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4c008-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="4c008-131">ENTERPRISEPREMIUM est la troisième ligne.</span><span class="sxs-lookup"><span data-stu-id="4c008-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="4c008-132">Par conséquent, la valeur d’index est (3-1) ou 2.</span><span class="sxs-lookup"><span data-stu-id="4c008-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="4c008-133">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="4c008-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4c008-134">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c008-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4c008-135">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4c008-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="4c008-136">Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4c008-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="4c008-137">Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Office 365, y compris Sway.</span><span class="sxs-lookup"><span data-stu-id="4c008-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="4c008-138">Pour plus d’informations, reportez-vous à la rubrique [désactiver l’accès à Sway avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="4c008-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="4c008-139">Pour afficher des informations récapitulatives sur vos plans de gestion des licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4c008-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="4c008-140">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="4c008-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="4c008-141">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c008-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="4c008-142">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c008-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="4c008-143">**AccountSkuId :** Affichez les plans de gestion des licences disponibles pour votre organisation `<CompanyName>:<LicensingPlan>`à l’aide de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="4c008-143">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="4c008-144">_<CompanyName>_ est la valeur que vous avez fournie lorsque vous vous êtes inscrit dans Office 365 et qui est unique pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="4c008-144">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="4c008-145">La _<LicensingPlan>_ valeur est la même pour tout le monde.</span><span class="sxs-lookup"><span data-stu-id="4c008-145">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="4c008-146">Par exemple, dans la valeur `litwareinc:ENTERPRISEPACK`, le nom `litwareinc`de la société et le nom `ENTERPRISEPACK`du plan de gestion des licences, qui est le nom du système pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="4c008-146">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="4c008-147">**ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c008-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="4c008-148">**WarningUnits :** Nombre de licences dans un plan de gestion des licences que vous n’avez pas renouvelé et qui expireront après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="4c008-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="4c008-149">**ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c008-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="4c008-150">Pour afficher les détails des services Office 365 disponibles dans tous vos plans de licence, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4c008-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="4c008-151">Le tableau suivant présente les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants.</span><span class="sxs-lookup"><span data-stu-id="4c008-151">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="4c008-152">La liste de vos plans de services peut être différente.</span><span class="sxs-lookup"><span data-stu-id="4c008-152">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="4c008-153">**Plan de services**</span><span class="sxs-lookup"><span data-stu-id="4c008-153">**Service plan**</span></span>|<span data-ttu-id="4c008-154">**Description**</span><span class="sxs-lookup"><span data-stu-id="4c008-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="4c008-155">Sway</span><span class="sxs-lookup"><span data-stu-id="4c008-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="4c008-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4c008-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="4c008-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="4c008-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="4c008-158">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="4c008-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="4c008-159">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="4c008-159">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="4c008-160">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="4c008-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="4c008-161">Office</span><span class="sxs-lookup"><span data-stu-id="4c008-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="4c008-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4c008-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="4c008-163">Exchange Online (plan 2)</span><span class="sxs-lookup"><span data-stu-id="4c008-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="4c008-164">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="4c008-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="4c008-165">Pour afficher des détails sur les services Office 365 disponibles dans un plan de gestion de licences spécifique, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="4c008-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="4c008-166">Cet exemple illustre les services Office 365 disponibles dans le plan de gestion des licences litwareinc : ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="4c008-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="4c008-167">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="4c008-167">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="4c008-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c008-168">See also</span></span>

[<span data-ttu-id="4c008-169">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c008-169">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4c008-170">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c008-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4c008-171">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="4c008-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
