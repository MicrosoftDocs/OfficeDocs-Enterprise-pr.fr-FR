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
ms.openlocfilehash: e62c06981a861580804dde852ad3da7bd729fdbe
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257645"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="052fb-103">Supprimer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="052fb-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="052fb-104">Vous pouvez utiliser PowerShell Office 365 pour supprimer un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="052fb-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="052fb-105">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="052fb-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="052fb-106">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="052fb-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="052fb-107">Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d’utilisateur individuel :</span><span class="sxs-lookup"><span data-stu-id="052fb-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

>[!Note]
><span data-ttu-id="052fb-108">PowerShell Core ne prend pas en charge les applets de commande et le module Microsoft Azure Active Directory pour Windows PowerShell avec **MSOL** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="052fb-108">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="052fb-109">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="052fb-109">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="052fb-110">Cet exemple supprime le compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="052fb-110">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="052fb-111">Le paramètre **- ObjectID** de la cmdlet **Remove-AzureAD** accepte le nom de compte, également appelé Nom d’utilisateur principal, ou l’ID d’objet du compte.</span><span class="sxs-lookup"><span data-stu-id="052fb-111">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="052fb-112">Pour afficher le nom du compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:</span><span class="sxs-lookup"><span data-stu-id="052fb-112">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="052fb-113">Cet exemple affiche le nom du compte de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="052fb-113">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="052fb-114">Pour supprimer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:</span><span class="sxs-lookup"><span data-stu-id="052fb-114">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="052fb-115">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="052fb-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="052fb-p102">Lorsque vous utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell afin de supprimer un compte d’utilisateur, le compte n’est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.</span><span class="sxs-lookup"><span data-stu-id="052fb-p102">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="052fb-118">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="052fb-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="052fb-119">Pour supprimer un compte d’utilisateur, utilisez la syntaxe suivante:</span><span class="sxs-lookup"><span data-stu-id="052fb-119">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="052fb-120">Cet exemple supprime le compte d’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="052fb-120">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="052fb-121">Pour restaurer un compte d’utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="052fb-121">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="052fb-122">Cet exemple restaure le compte d’utilisateur supprimé BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="052fb-122">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="052fb-123">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="052fb-123">**Notes:**</span></span>
  
- <span data-ttu-id="052fb-124">Pour afficher la liste des utilisateurs supprimés dont la restauration est possible, exécutez la commande suivante:</span><span class="sxs-lookup"><span data-stu-id="052fb-124">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="052fb-125">Si le nom d'utilisateur principal d'origine du compte d'utilisateur est utilisé par un autre compte, utilisez le paramètre_NewUserPrincipalName_ à la place de_UserPrincipalName_ pour spécifier un autre nom d'utilisateur principal lorsque vous restaurez le compte.</span><span class="sxs-lookup"><span data-stu-id="052fb-125">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="052fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="052fb-126">See also</span></span>

[<span data-ttu-id="052fb-127">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="052fb-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="052fb-128">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="052fb-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="052fb-129">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="052fb-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

