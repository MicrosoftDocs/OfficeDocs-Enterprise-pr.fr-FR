---
title: Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui ont été précédemment attribués aux utilisateurs.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651218"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8db02-103">Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8db02-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8db02-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui ont été précédemment attribués aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8db02-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8db02-105">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="8db02-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8db02-106">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8db02-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="8db02-107">Ensuite, répertoriez les plans de licence pour votre client avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="8db02-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="8db02-108">Ensuite, obtenir le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également connu sous le nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="8db02-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="8db02-109">Enfin, spécifiez les noms de plan de connexion et de licence utilisateur, supprimez les caractères « < » et « > » et exécuter ces commandes.</span><span class="sxs-lookup"><span data-stu-id="8db02-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8db02-110">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8db02-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8db02-111">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8db02-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="8db02-112">Pour afficher les informations de licence plan (**éléments AccountSkuID** ) dans votre organisation, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8db02-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="8db02-113">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8db02-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="8db02-114">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8db02-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="8db02-115">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="8db02-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="8db02-116">Supprimer des licences à partir de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="8db02-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="8db02-117">Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8db02-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="8db02-118">Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) du compte d’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="8db02-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8db02-119">Pour supprimer des licences d’un groupe d’utilisateurs sous licence existants, appliquez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8db02-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="8db02-120">**Filtrer les comptes basées sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8db02-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="8db02-121">Cet exemple supprime le `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) licences de tous les comptes d’utilisateurs du service ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="8db02-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="8db02-122">**Utiliser une liste de comptes spécifiques** Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8db02-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="8db02-123">Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="8db02-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="8db02-124">Utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8db02-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="8db02-125">Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) dans les comptes d’utilisateur défini dans le fichier texte C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="8db02-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="8db02-126">Pour supprimer des licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8db02-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="8db02-127">Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir de tout une licence de comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8db02-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="8db02-p101">Une autre manière pour libérer une licence est en supprimant le compte d’utilisateur. Pour plus d’informations, voir [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8db02-p101">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8db02-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8db02-130">See also</span></span>

[<span data-ttu-id="8db02-131">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8db02-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8db02-132">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8db02-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8db02-133">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="8db02-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="8db02-134">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="8db02-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

