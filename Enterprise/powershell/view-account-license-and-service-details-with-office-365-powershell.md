---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués à des utilisateurs.
ms.openlocfilehash: 53668a69d72cdcbe912d550be2b9e571b7f6c0e0
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747473"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="d5645-103">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5645-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="d5645-104">Dans Office 365, les licences des plans de gestion des licences (également appelés « SKU » ou « offres Office 365 ») permettent aux utilisateurs d’accéder aux services Office 365 définis pour ces plans.</span><span class="sxs-lookup"><span data-stu-id="d5645-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="d5645-105">Toutefois, un utilisateur ne dispose peut-être pas d’un accès à tous les services disponibles dans une licence qui lui est affectée.</span><span class="sxs-lookup"><span data-stu-id="d5645-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="d5645-106">Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5645-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="d5645-107">Pour plus d’informations sur les plans de licence, les licences et les services, voir [View licenses and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d5645-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d5645-108">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="d5645-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d5645-109">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d5645-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="d5645-110">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="d5645-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="d5645-111">Utilisez ces commandes pour répertorier les services disponibles dans chaque plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="d5645-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="d5645-112">Utilisez ces commandes pour répertorier les licences qui sont affectées à un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5645-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d5645-113">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5645-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d5645-114">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d5645-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="d5645-115">Ensuite, exécutez cette commande pour répertorier les plans de gestion des licences disponibles dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="d5645-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```

<span data-ttu-id="d5645-116">Ensuite, exécutez cette commande pour répertorier les services disponibles dans chaque plan de gestion des licences et l’ordre dans lequel ils sont répertoriés (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="d5645-116">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
<span data-ttu-id="d5645-117">Utilisez cette commande pour répertorier les licences qui sont affectées à un utilisateur et l’ordre dans lequel elles sont répertoriées (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="d5645-117">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
><span data-ttu-id="d5645-118">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="d5645-118">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="d5645-119">Pour afficher les services d’un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d5645-119">To view services for a user account</span></span>

<span data-ttu-id="d5645-120">Pour afficher tous les services Office 365 auxquels un utilisateur a accès, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="d5645-120">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="d5645-121">Cet exemple illustre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès.</span><span class="sxs-lookup"><span data-stu-id="d5645-121">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="d5645-122">Ceci affiche les services qui sont associés à toutes les licences attribuées à son compte.</span><span class="sxs-lookup"><span data-stu-id="d5645-122">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="d5645-123">Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).</span><span class="sxs-lookup"><span data-stu-id="d5645-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="d5645-124">Pour afficher tous les services d’un utilisateur auquel ont été affectées *plusieurs licences*, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="d5645-124">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a><span data-ttu-id="d5645-125">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="d5645-125">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="d5645-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5645-126">See also</span></span>

[<span data-ttu-id="d5645-127">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5645-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d5645-128">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5645-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d5645-129">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="d5645-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
