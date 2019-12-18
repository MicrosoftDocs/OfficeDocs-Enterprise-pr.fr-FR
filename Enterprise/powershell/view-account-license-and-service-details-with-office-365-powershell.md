---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
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
ms.openlocfilehash: d56457f00e63d20b9d87e1f90e0e8d12587fcc1f
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261427"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="be4fb-103">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be4fb-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="be4fb-104">Dans Office 365, les licences des plans de gestion des licences (également appelés « SKU » ou « offres Office 365 ») permettent aux utilisateurs d’accéder aux services Office 365 définis pour ces plans.</span><span class="sxs-lookup"><span data-stu-id="be4fb-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="be4fb-105">Toutefois, un utilisateur ne dispose peut-être pas d’un accès à tous les services disponibles dans une licence qui lui est affectée.</span><span class="sxs-lookup"><span data-stu-id="be4fb-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="be4fb-106">Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="be4fb-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="be4fb-107">Pour plus d’informations sur les plans de licence, les licences et les services, voir [View licenses and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="be4fb-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="be4fb-108">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="be4fb-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="be4fb-109">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="be4fb-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="be4fb-110">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="be4fb-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="be4fb-111">Utilisez ces commandes pour répertorier les services disponibles dans chaque plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="be4fb-111">Use these commands to list the services that are available in each licensing plan.</span></span>

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

<span data-ttu-id="be4fb-112">Utilisez ces commandes pour répertorier les licences qui sont affectées à un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="be4fb-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="be4fb-113">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be4fb-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="be4fb-114">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="be4fb-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="be4fb-115">Ensuite, exécutez cette commande pour répertorier les plans de gestion des licences disponibles dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="be4fb-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="be4fb-116">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="be4fb-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="be4fb-117">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be4fb-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="be4fb-118">Ensuite, exécutez cette commande pour répertorier les services disponibles dans chaque plan de gestion des licences et l’ordre dans lequel ils sont répertoriés (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="be4fb-118">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="be4fb-119">Utilisez cette commande pour répertorier les licences qui sont affectées à un utilisateur et l’ordre dans lequel elles sont répertoriées (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="be4fb-119">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="be4fb-120">Pour afficher les services d’un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="be4fb-120">To view services for a user account</span></span>

<span data-ttu-id="be4fb-121">Pour afficher tous les services Office 365 auxquels un utilisateur a accès, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="be4fb-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="be4fb-122">Cet exemple illustre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès.</span><span class="sxs-lookup"><span data-stu-id="be4fb-122">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="be4fb-123">Ceci affiche les services qui sont associés à toutes les licences attribuées à son compte.</span><span class="sxs-lookup"><span data-stu-id="be4fb-123">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="be4fb-124">Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).</span><span class="sxs-lookup"><span data-stu-id="be4fb-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="be4fb-125">Pour afficher tous les services d’un utilisateur auquel ont été affectées *plusieurs licences*, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="be4fb-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="be4fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be4fb-126">See also</span></span>

[<span data-ttu-id="be4fb-127">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be4fb-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="be4fb-128">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be4fb-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="be4fb-129">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="be4fb-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
