---
title: Bloquer les comptes d’utilisateur Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explique comment utiliser PowerShell pour bloquer et débloquer l’accès aux comptes Microsoft 365.
ms.openlocfilehash: c18c0248c51096ab089b16b2e9e31eb0929de443
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230890"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="b5917-103">Bloquer les comptes d’utilisateur Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5917-103">Block Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="b5917-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="b5917-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b5917-105">Le blocage de l’accès à un compte Microsoft 365 empêche quiconque d’utiliser le compte pour se connecter et accéder aux services et données de votre organisation Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b5917-105">Blocking access to a Microsoft 365 account prevents anyone from using the account to sign in and access the services and data in your Microsoft 365 organization.</span></span> <span data-ttu-id="b5917-106">Vous pouvez utiliser PowerShell pour bloquer l’accès à un ou plusieurs comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b5917-106">You can use PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b5917-107">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="b5917-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b5917-108">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b5917-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="b5917-109">Bloquer l’accès à des comptes d’utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="b5917-109">Block access to individual user accounts</span></span>

<span data-ttu-id="b5917-110">Utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :</span><span class="sxs-lookup"><span data-stu-id="b5917-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="b5917-111">Le paramètre-ObjectID de la cmdlet Set-AzureAD accepte le nom de connexion du compte, également appelé nom d’utilisateur principal, ou l’ID d’objet du compte.</span><span class="sxs-lookup"><span data-stu-id="b5917-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="b5917-112">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="b5917-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="b5917-113">Pour débloquer ce compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="b5917-114">Pour afficher l’UPN du compte d’utilisateur en fonction du nom d’affichage de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5917-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="b5917-115">Cet exemple affiche le nom UPN du compte d’utilisateur pour l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="b5917-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b5917-116">Pour bloquer un compte en fonction du nom d’affichage de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5917-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="b5917-117">À tout moment, vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="b5917-118">Bloquer l’accès à plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="b5917-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="b5917-119">Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte contenant un nom de connexion sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="b5917-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="b5917-120">Dans les commandes suivantes, le fichier texte de l’exemple est C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="b5917-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="b5917-121">Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b5917-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="b5917-122">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="b5917-123">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b5917-124">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5917-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b5917-125">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b5917-125">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="b5917-126">Bloquer l’accès à des comptes d’utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="b5917-126">Block access to individual user accounts</span></span>

<span data-ttu-id="b5917-127">Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="b5917-128">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="b5917-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="b5917-129">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5917-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="b5917-130">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="b5917-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="b5917-131">Pour débloquer le compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="b5917-132">À tout moment, vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="b5917-133">Bloquer l’accès à plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="b5917-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="b5917-134">Tout d’abord, créez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="b5917-134">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="b5917-135">Dans les commandes suivantes, le fichier texte de l’exemple est C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="b5917-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="b5917-136">Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b5917-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="b5917-137">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="b5917-138">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b5917-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="b5917-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5917-139">See also</span></span>

[<span data-ttu-id="b5917-140">Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5917-140">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b5917-141">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5917-141">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b5917-142">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b5917-142">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
