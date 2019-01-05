---
title: Afficher les licences et les services avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
description: Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licences, les services et les licences sont disponibles dans votre organisation Office 365.
ms.openlocfilehash: f673ac984e504a740dfac474821366d34de5ccbc
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730329"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="6ea64-103">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ea64-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="6ea64-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licences, les services et les licences sont disponibles dans votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ea64-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="6ea64-105">Chaque abonnement à Office 365 se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6ea64-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="6ea64-p101">**Plans de gestion des licences** Ce sont également appelés plans de licence ou plans Office 365. Plans de licence définissent les services Office 365 qui sont accessibles aux utilisateurs. Votre abonnement Office 365 peut contenir plusieurs plans de gestion des licences. Un plan de gestion des licences exemple serait Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="6ea64-p102">**Services** Ils sont également appelés plans de service. Les services sont les produits Office 365, les fonctionnalités et les capacités qui sont disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Office Professionnel Plus. Les utilisateurs peuvent avoir plusieurs licences assignés à partir de différents plans de licence permettant d’accéder à différents services.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="6ea64-p103">**Licences** Chaque plan de licences contient le nombre de licences que vous avez acheté. Vous attribuez des licences aux utilisateurs afin qu’ils peuvent utiliser les services Office 365 qui sont définies par le plan de gestion des licences. Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences pour pouvoir se connecter à Office 365 et utiliser les services.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="6ea64-p104">Vous pouvez utiliser Office 365 PowerShell pour afficher plus d’informations sur les plans de licence disponibles, les licences et les services dans votre organisation Office 365. Pour plus d’informations sur les produits, les fonctionnalités et les services qui sont disponibles dans les différents abonnements Office 365, voir [Options de Plan Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="6ea64-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6ea64-118">Utilisez Azure Active Directory PowerShell pour le module de graphique</span><span class="sxs-lookup"><span data-stu-id="6ea64-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6ea64-119">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="6ea64-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="6ea64-120">Pour afficher des informations récapitulatives concernant vos plans de gestion des licences en cours et les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea64-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="6ea64-121">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ea64-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="6ea64-p105">**SkuPartNumber :** Affiche les plans de gestion de licences disponibles pour votre organisation. Par exemple, `ENTERPRISEPACK` est le nom du système pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="6ea64-124">**Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ea64-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="6ea64-125">**ConsumedUnits :** Nombre de licences que vous avez affectés aux utilisateurs d’un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ea64-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="6ea64-126">Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans l’ensemble de vos modes de licence, d’abord afficher une liste de vos plans de licence.</span><span class="sxs-lookup"><span data-stu-id="6ea64-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="6ea64-127">Ensuite, stockez les informations de licence des plans dans une variable.</span><span class="sxs-lookup"><span data-stu-id="6ea64-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="6ea64-128">Ensuite, afficher les services dans un plan de licences spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6ea64-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlan
````

<span data-ttu-id="6ea64-129">\<Index > est un entier qui spécifie le numéro de ligne de la licence de planification de l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` command, moins 1.</span><span class="sxs-lookup"><span data-stu-id="6ea64-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="6ea64-130">Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande s’agit-il :</span><span class="sxs-lookup"><span data-stu-id="6ea64-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="6ea64-131">Puis la commande pour afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea64-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlan
````

<span data-ttu-id="6ea64-p106">ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3 - 1) ou 2.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="6ea64-134">Pour une liste complète des plans de licence (également connu sous les noms de produits), leurs plans de service inclus et leurs noms conviviaux correspondants, voir [identificateurs de plan de service de gestion des licences et les noms de produits](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="6ea64-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6ea64-135">Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ea64-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6ea64-136">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6ea64-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="6ea64-p107">Vous trouverez un script PowerShell qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script permet d’afficher et désactiver des services dans votre organisation Office 365, notamment balancement. Pour plus d’informations, voir [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6ea64-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="6ea64-140">Pour afficher des informations récapitulatives concernant vos plans de gestion des licences en cours et les licences disponibles pour chaque plan, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea64-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="6ea64-141">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ea64-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="6ea64-p108">**Éléments AccountSkuId :** Afficher les plans de gestion de licences disponibles pour votre organisation à l’aide de la syntaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ est la valeur que vous avez fournies lorsque vous inscrit dans Office 365 et êtes unique pour votre organisation. Le _<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur `litwareinc:ENTERPRISEPACK`, est le nom de la société `litwareinc`et le nom de plan de gestion des licences `ENTERPRISEPACK`, qui est le nom du système pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="6ea64-146">**ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ea64-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="6ea64-147">**WarningUnits :** Nombre de licences d’un plan de gestion des licences que vous n’avez pas renouvelé, qui va expirer après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="6ea64-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="6ea64-148">**ConsumedUnits :** Nombre de licences que vous avez affectés aux utilisateurs d’un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ea64-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="6ea64-149">Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans l’ensemble de vos modes de licence, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea64-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="6ea64-p109">Le tableau suivant indique les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants. Votre liste des plans de service peut être différent.</span><span class="sxs-lookup"><span data-stu-id="6ea64-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="6ea64-152">**Plan de service**</span><span class="sxs-lookup"><span data-stu-id="6ea64-152">**Service plan**</span></span>|<span data-ttu-id="6ea64-153">**Description**</span><span class="sxs-lookup"><span data-stu-id="6ea64-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="6ea64-154">Sway</span><span class="sxs-lookup"><span data-stu-id="6ea64-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="6ea64-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6ea64-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="6ea64-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="6ea64-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="6ea64-157">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="6ea64-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="6ea64-158">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="6ea64-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="6ea64-159">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="6ea64-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="6ea64-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="6ea64-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="6ea64-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6ea64-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="6ea64-162">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="6ea64-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="6ea64-163">Pour une liste complète des plans de licence (également connu sous les noms de produits), leurs plans de service inclus et leurs noms conviviaux correspondants, voir [identificateurs de plan de service de gestion des licences et les noms de produits](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="6ea64-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="6ea64-164">Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans un plan de gestion des licences spécifique, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="6ea64-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="6ea64-165">Cet exemple montre les services Office 365 qui sont disponibles dans le plan de gestion des licences litwareinc : enterprisepack (Office 365 entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="6ea64-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="6ea64-166">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="6ea64-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="6ea64-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ea64-167">See also</span></span>


[<span data-ttu-id="6ea64-168">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ea64-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6ea64-169">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ea64-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6ea64-170">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="6ea64-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
