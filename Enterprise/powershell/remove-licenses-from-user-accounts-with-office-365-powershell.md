---
title: Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
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
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 précédemment attribuées à des utilisateurs.
ms.openlocfilehash: f88a8d32616e615ada081af6e7229da57ce3f668
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261537"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="3edab-103">Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3edab-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3edab-104">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="3edab-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3edab-105">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="3edab-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="3edab-106">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="3edab-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="3edab-107">Ensuite, obtenez le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également appelée nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="3edab-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="3edab-108">Enfin, spécifiez les noms de connexion et de plan de licence de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="3edab-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3edab-109">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3edab-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3edab-110">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3edab-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="3edab-111">Pour afficher les informations du plan de gestion des licences (**AccountSkuID** ) dans votre organisation, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3edab-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="3edab-112">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3edab-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="3edab-113">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3edab-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="3edab-114">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="3edab-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="3edab-115">Suppression de licences de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="3edab-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="3edab-116">Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="3edab-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="3edab-117">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="3edab-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="3edab-118">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3edab-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="3edab-119">Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) du compte d’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="3edab-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="3edab-120">Vous ne pouvez pas `Set-MsolUserLicense` utiliser l’applet de commande pour annuler l’affectation des utilisateurs des licences *annulées* .</span><span class="sxs-lookup"><span data-stu-id="3edab-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="3edab-121">Vous devez effectuer cette opération individuellement pour chaque compte d’utilisateur dans le centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3edab-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="3edab-122">Pour supprimer des licences d’un groupe d’utilisateurs sous licence existants, appliquez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3edab-122">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="3edab-123">**Filtrer les comptes en fonction d’un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="3edab-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="3edab-124">Cet exemple supprime les licences **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) de tous les comptes pour les utilisateurs du service des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="3edab-124">This example removes the  **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="3edab-125">**Utiliser une liste de comptes spécifiques** Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3edab-125">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="3edab-126">Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="3edab-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="3edab-127">Utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="3edab-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="3edab-128">Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) des comptes d’utilisateur définis dans le fichier texte C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="3edab-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="3edab-129">Pour supprimer des licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="3edab-129">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="3edab-130">Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) de tous les comptes d’utilisateur sous licence existants.</span><span class="sxs-lookup"><span data-stu-id="3edab-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="3edab-131">Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3edab-131">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="3edab-132">Pour plus d’informations, consultez la rubrique [supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3edab-132">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3edab-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3edab-133">See also</span></span>

[<span data-ttu-id="3edab-134">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3edab-134">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3edab-135">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3edab-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3edab-136">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="3edab-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

