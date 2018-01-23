---
title: "Afficher les licences et les services avec Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licence, les services et les licences qui sont disponibles dans votre organisation d’Office 365."
ms.openlocfilehash: 7564da2093bdc9de45e239be8196a626214871ba
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="43a8e-103">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="43a8e-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="43a8e-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licence, les services et les licences qui sont disponibles dans votre organisation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="43a8e-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="43a8e-105">Chaque abonnement à Office 365 se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="43a8e-105">Every Office 365 subscription consists of the following elements:</span></span>
- <span data-ttu-id="43a8e-p101">**Plans de gestion de licences** Il s’agit également de plans d’aslicense ou de plans d’Office 365. Plans de gestion des licences définissent les services Office 365 qui sont disponibles pour les utilisateurs. Votre abonnement à Office 365 peut contenir plusieurs plans de gestion des licences. Un plan de gestion des licences exemple serait E3 d’entreprise Office 365.</span><span class="sxs-lookup"><span data-stu-id="43a8e-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="43a8e-p102">**Services** Ce sont également les plans asservice connus. Les services sont les produits Office 365, les fonctionnalités et les fonctionnalités qui sont disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Office Professionnel Plus. Les utilisateurs peuvent avoir plusieurs licences de différents plans de gestion des licences qui accordent l’accès à des services différents.</span><span class="sxs-lookup"><span data-stu-id="43a8e-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="43a8e-p103">**Licences** Chaque plan de licences contient le nombre de licences que vous avez acheté. Vous attribuez des licences aux utilisateurs afin de pouvoir utiliser les services Office 365 qui sont définies par le plan de gestion des licences. Chaque compte d’utilisateur requiert au moins une licence à partir d’un plan de gestion des licences pour pouvoir se connecter à Office 365 et utiliser les services.</span><span class="sxs-lookup"><span data-stu-id="43a8e-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="43a8e-p104">Vous pouvez utiliser Office 365 PowerShell pour afficher plus d’informations sur les plans de gestion des licences disponibles, les licences et les services de votre organisation d’Office 365. Pour plus d’informations sur les produits, les fonctionnalités et les services qui sont disponibles dans les différentes souscriptions d’Office 365, reportez-vous à la section [Options du Plan Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="43a8e-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="43a8e-118">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="43a8e-118">Before you begin</span></span>
<span data-ttu-id="43a8e-119"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="43a8e-119"></span></span>

- <span data-ttu-id="43a8e-p105">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="43a8e-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="43a8e-p106">Un script PowerShell est disponible qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation d’Office 365, y compris de balancement. Pour plus d’informations, consultez [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="43a8e-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="43a8e-125">Afficher les informations sur les plans de licence et sur les licences disponibles</span><span class="sxs-lookup"><span data-stu-id="43a8e-125">View information about licensing plans and the available licenses</span></span>
<span data-ttu-id="43a8e-126"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="43a8e-126"></span></span>

<span data-ttu-id="43a8e-127">Pour afficher des informations récapitulatives sur vos plans de gestion des licences en cours et les licences disponibles pour chaque plan, exécutez la commande suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="43a8e-127">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="43a8e-128">Les résultats contiennent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="43a8e-128">The results contain the following information:</span></span>
  
- <span data-ttu-id="43a8e-p107">**AccountSkuId :** Afficher les plans de gestion des licences disponibles pour votre organisation à l’aide de la syntaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ est la valeur que vous avez fournies lorsque vous inscrit à Office 365 et êtes unique pour votre organisation. Le _<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur de `litwareinc:ENTERPRISEPACK`, le nom de la société est `litwareinc`et le nom du plan licence `ENTERPRISEPACK`, qui est le nom de système pour Office 365 entreprise E3.</span><span class="sxs-lookup"><span data-stu-id="43a8e-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="43a8e-133">**ActiveUnits :** Nombre de licences que vous avez des achats pour un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="43a8e-133">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="43a8e-134">**WarningUnits :** Nombre de licences d’un plan de gestion des licences que vous n’avez pas renouvelé et qui expire après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="43a8e-134">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="43a8e-135">**ConsumedUnits :** Nombre de licences que vous avez affectés aux utilisateurs à partir d’un plan de gestion des licences spécifique.</span><span class="sxs-lookup"><span data-stu-id="43a8e-135">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="43a8e-136">Pour plus d’informations sur les services Office 365 qui sont disponibles dans l’ensemble de vos modes de licence, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="43a8e-136">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="43a8e-p108">Le tableau suivant montre les plans de service d’Office 365 et leurs noms conviviaux pour les services les plus courants. La liste des plans de service peut-être être différente. Pour obtenir une liste complète des services offerts et leurs noms conviviaux, contactez le [Support de l’Office](https://support.office.com/home/contact).</span><span class="sxs-lookup"><span data-stu-id="43a8e-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Office Support](https://support.office.com/home/contact).</span></span>
  
|<span data-ttu-id="43a8e-140">Plan de service \*\*\*</span><span class="sxs-lookup"><span data-stu-id="43a8e-140">****Service plan****</span></span>|<span data-ttu-id="43a8e-141">Description \*\*\*</span><span class="sxs-lookup"><span data-stu-id="43a8e-141">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="43a8e-142">Sway</span><span class="sxs-lookup"><span data-stu-id="43a8e-142">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="43a8e-143">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="43a8e-143">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="43a8e-144">Yammer</span><span class="sxs-lookup"><span data-stu-id="43a8e-144">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="43a8e-145">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="43a8e-145">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="43a8e-146">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="43a8e-146">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="43a8e-147">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="43a8e-147">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="43a8e-148">Office Online</span><span class="sxs-lookup"><span data-stu-id="43a8e-148">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="43a8e-149">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="43a8e-149">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="43a8e-150">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="43a8e-150">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="43a8e-151">Pour plus d’informations sur les services Office 365 qui sont disponibles dans un plan de gestion des licences spécifique, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="43a8e-151">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="43a8e-152">Cet exemple montre les services Office 365 qui sont disponibles dans le plan de gestion des licences litwareinc:ENTERPRISEPACK (Office 365 entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="43a8e-152">This example shows the Office 365 services that are available in the  litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="43a8e-153">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="43a8e-153">New to Office 365?</span></span>
<span data-ttu-id="43a8e-154"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="43a8e-154"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="43a8e-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43a8e-155">See also</span></span>
<span data-ttu-id="43a8e-156"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="43a8e-156"></span></span>

#### 

[<span data-ttu-id="43a8e-157">Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="43a8e-157">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[<span data-ttu-id="43a8e-158">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="43a8e-158">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[<span data-ttu-id="43a8e-159">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="43a8e-159">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

