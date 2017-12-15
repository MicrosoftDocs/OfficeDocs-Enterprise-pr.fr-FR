---
title: "Attribuer des rôles à des comptes d'utilisateur avec Office 365 PowerShell"
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
- DecEntMigration
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "Résumé : Utilisez Office 365 PowerShell et la cmdlet Add-MsolRoleMember pour attribuer des rôles aux comptes d'utilisateur."
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="744a4-103">Attribuer des rôles à des comptes d'utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="744a4-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="744a4-104">**Résumé :** Utiliser Office 365 PowerShell et l’applet de commande **Add-MsolRoleMember** pour assigner des rôles aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="744a4-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="744a4-105">Vous pouvez rapidement et facilement attribuer des rôles aux comptes d’utilisateurs à l’aide d’Office 365 PowerShell en identifiant le nom d’affichage d’un compte utilisateur et le nom de rôle.</span><span class="sxs-lookup"><span data-stu-id="744a4-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="744a4-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="744a4-106">Before you begin</span></span>

<span data-ttu-id="744a4-p101">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell à l'aide d'un compte d'administrateur global. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="744a4-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="744a4-109">Pour une seule modification de rôle</span><span class="sxs-lookup"><span data-stu-id="744a4-109">For a single role change</span></span>

<span data-ttu-id="744a4-110">Déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="744a4-110">Determine the following:</span></span>
  
- <span data-ttu-id="744a4-111">Le compte d'utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="744a4-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="744a4-p102">Pour spécifier le compte d’utilisateur, vous devez déterminer son nom complet. Pour obtenir une liste complète des comptes, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="744a4-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="744a4-p103">Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="744a4-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="744a4-117">Cette commande répertorie uniquement les comptes d'utilisateur dont le nom d'affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="744a4-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="744a4-118">Le rôle que vous souhaitez attribuer.</span><span class="sxs-lookup"><span data-stu-id="744a4-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="744a4-119">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d'utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="744a4-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="744a4-120">Une fois que vous avez déterminé le nom d'affichage du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :</span><span class="sxs-lookup"><span data-stu-id="744a4-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="744a4-p104">Copiez les commandes et les coller dans le bloc-notes. Pour les variables **$dispName** et **$roleName** , remplacez le texte de description par leurs valeurs, supprimez le \< et > caractères et laissez les guillemets. Copier les lignes modifiées et les coller dans votre fenêtre de Windows Azure Active Directory Module pour Windows PowerShell afin de les exécuter. Vous pouvez également utiliser le Windows PowerShell Script environnement intégré (ISE).</span><span class="sxs-lookup"><span data-stu-id="744a4-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="744a4-125">Voici un exemple d'un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="744a4-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="744a4-126">Pour plusieurs modifications de rôle</span><span class="sxs-lookup"><span data-stu-id="744a4-126">For multiple role changes</span></span>

<span data-ttu-id="744a4-127">Déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="744a4-127">Determine the following:</span></span>
  
- <span data-ttu-id="744a4-128">Les comptes d'utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="744a4-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="744a4-p105">Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="744a4-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="744a4-p106">Cette commande répertorie le nom complet de tous les comptes utilisateurs, triées par le nom complet, un écran à la fois. Vous pouvez filtrer la liste à un plus petit ensemble à l’aide de l’applet de commande **où** . Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="744a4-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="744a4-134">Cette commande répertorie uniquement les comptes d'utilisateur dont le nom d'affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="744a4-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="744a4-135">Les rôles que vous souhaitez attribuer à chaque compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="744a4-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="744a4-136">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d'utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="744a4-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="744a4-p107">Ensuite, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs DisplayName et role Name. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="744a4-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="744a4-139">Ensuite, remplissez l'emplacement du fichier CSV et exécutez les commandes qui en résultent à l'invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="744a4-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="744a4-140">See also</span><span class="sxs-lookup"><span data-stu-id="744a4-140">See also</span></span>

#### 

[<span data-ttu-id="744a4-141">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="744a4-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="744a4-142">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="744a4-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="744a4-143">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="744a4-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="744a4-144">Add-MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="744a4-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

