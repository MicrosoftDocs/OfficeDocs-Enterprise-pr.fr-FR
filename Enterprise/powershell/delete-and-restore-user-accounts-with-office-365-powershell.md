---
title: Supprimer des comptes d’utilisateurs avec Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Découvrez comment utiliser Office 365 PowerShell pour supprimer des comptes d'utilisateur Office 365.
ms.openlocfilehash: dd7e5052f8933955267302a5d03870017702a7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069040"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="dee32-103">Supprimer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dee32-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="dee32-104">**Résumé:** Découvrez comment utiliser Office 365 PowerShell pour supprimer des comptes d'utilisateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="dee32-104">**Summary:**  Learn how to use Office 365 PowerShell to delete Office 365 user accounts.</span></span>
  
<span data-ttu-id="dee32-105">Vous pouvez utiliser PowerShell Office 365 pour supprimer un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dee32-105">You can use Office 365 PowerShell to delete a user account.</span></span>

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dee32-106">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="dee32-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dee32-107">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="dee32-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="dee32-108">Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d’utilisateur individuel :</span><span class="sxs-lookup"><span data-stu-id="dee32-108">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="dee32-109">Cet exemple supprime le compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dee32-109">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="dee32-110">Le paramètre **- ObjectID** de la cmdlet **Remove-AzureAD** accepte le nom de compte, également appelé Nom d’utilisateur principal, ou l’ID d’objet du compte.</span><span class="sxs-lookup"><span data-stu-id="dee32-110">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="dee32-111">Pour afficher le nom du compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:</span><span class="sxs-lookup"><span data-stu-id="dee32-111">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="dee32-112">Cet exemple affiche le nom du compte de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="dee32-112">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="dee32-113">Pour supprimer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:</span><span class="sxs-lookup"><span data-stu-id="dee32-113">To remove an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="dee32-114">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dee32-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="dee32-p101">Lorsque vous utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell afin de supprimer un compte d’utilisateur, le compte n’est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.</span><span class="sxs-lookup"><span data-stu-id="dee32-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="dee32-117">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dee32-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="dee32-118">Pour supprimer un compte d’utilisateur, utilisez la syntaxe suivante:</span><span class="sxs-lookup"><span data-stu-id="dee32-118">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="dee32-119">Cet exemple supprime le compte d’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dee32-119">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="dee32-120">Pour restaurer un compte d’utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="dee32-120">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="dee32-121">Cet exemple restaure le compte d’utilisateur supprimé BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dee32-121">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="dee32-122">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="dee32-122">**Notes:**</span></span>
  
- <span data-ttu-id="dee32-123">Pour afficher la liste des utilisateurs supprimés dont la restauration est possible, exécutez la commande suivante:</span><span class="sxs-lookup"><span data-stu-id="dee32-123">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="dee32-124">Si le nom d'utilisateur principal d'origine du compte d'utilisateur est utilisé par un autre compte, utilisez le paramètre_NewUserPrincipalName_ à la place de_UserPrincipalName_ pour spécifier un autre nom d'utilisateur principal lorsque vous restaurez le compte.</span><span class="sxs-lookup"><span data-stu-id="dee32-124">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="dee32-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dee32-125">See also</span></span>

[<span data-ttu-id="dee32-126">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dee32-126">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dee32-127">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dee32-127">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dee32-128">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="dee32-128">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

