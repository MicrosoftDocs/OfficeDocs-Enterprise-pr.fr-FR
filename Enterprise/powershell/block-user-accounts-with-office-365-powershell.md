---
title: Bloquer des comptes d’utilisateurs avec Office 365 PowerShell
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
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546475"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e0df9-103">Bloquer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0df9-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e0df9-104">**Résumé :**  Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="e0df9-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="e0df9-p101">Bloque l’accès à un compte Office 365 empêche toute personne utilisant le compte pour se connecter et accéder aux services et données de votre organisation Office 365. Vous pouvez utiliser Office 365 PowerShell pour bloquer l’accès aux différents et plusieurs comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e0df9-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e0df9-107">Utilisez Azure Active Directory PowerShell pour le module de graphique</span><span class="sxs-lookup"><span data-stu-id="e0df9-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e0df9-108">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e0df9-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="e0df9-109">Bloquer l’accès aux comptes d’utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="e0df9-109">Block access to individual user accounts</span></span>

<span data-ttu-id="e0df9-110">Pour bloquer un compte d’utilisateur, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="e0df9-111">Le paramètre - ObjectID dans l’applet de commande Set-AzureAD accepte soit le compte nom de connexion, également connu sous le nom d’utilisateur Principal ou ID d’objet. d’un compte</span><span class="sxs-lookup"><span data-stu-id="e0df9-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="e0df9-112">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e0df9-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="e0df9-113">Pour débloquer ce compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="e0df9-114">Pour afficher le compte d’utilisateur QU'UPN basé sur le nom complet de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0df9-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="e0df9-115">Cet exemple montre comment affiche le compte d’utilisateur UPN pour l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="e0df9-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e0df9-116">Pour bloquer un compte basé sur le nom complet de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0df9-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="e0df9-117">À tout moment, vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="e0df9-118">Bloquer l’accès à plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="e0df9-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="e0df9-119">Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte qui contient un seul compte nom de connexion de chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0df9-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="e0df9-p102">Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacer par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e0df9-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="e0df9-122">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="e0df9-123">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e0df9-124">Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0df9-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e0df9-125">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e0df9-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="e0df9-126">Bloquer l’accès aux comptes d’utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="e0df9-126">Block access to individual user accounts</span></span>

<span data-ttu-id="e0df9-127">Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="e0df9-128">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e0df9-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="e0df9-129">Pour débloquer le compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="e0df9-130">À tout moment, vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="e0df9-131">Bloquer l’accès à plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="e0df9-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="e0df9-132">Tout d’abord, créez un fichier texte qui contient un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0df9-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="e0df9-p103">Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacer par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e0df9-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="e0df9-135">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="e0df9-136">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0df9-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="e0df9-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0df9-137">See also</span></span>

[<span data-ttu-id="e0df9-138">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0df9-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e0df9-139">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0df9-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e0df9-140">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="e0df9-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
