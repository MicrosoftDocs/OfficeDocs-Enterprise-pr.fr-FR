---
title: Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Résumé : Utilisation d’Office 365 PowerShell pour attribuer des rôles à des comptes d’utilisateur.'
ms.openlocfilehash: d06b305c348d014ce526448d7f8401c26f4d1c47
ms.sourcegitcommit: 3100813cd7dff8b27b1a30a6d6ed5a7c4765c60f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "34586980"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9d511-103">Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d511-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9d511-104">Vous pouvez rapidement et facilement attribuer des rôles à des comptes d’utilisateur à l’aide d’Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9d511-105">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="9d511-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9d511-106">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) avec un compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="9d511-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="9d511-p101">Ensuite, déterminez le nom de connexion du compte d’utilisateur que vous souhaitez ajouter à un rôle (exemple : fredsm@contoso.com). On l’appelle aussi nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="9d511-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="9d511-109">Ensuite, déterminez le nom du rôle.</span><span class="sxs-lookup"><span data-stu-id="9d511-109">Next, determine the name of the role.</span></span> <span data-ttu-id="9d511-110">Utilisez cette[liste d’autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="9d511-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="9d511-111">Soyez attentif aux notes dans cet article.</span><span class="sxs-lookup"><span data-stu-id="9d511-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="9d511-112">Certains noms de rôle sont différents pour Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="9d511-113">Par exemple, le rôle « Administrateur de SharePoint » dans le Centre d’administration Microsoft 365 est nommé « Administrateur du Service SharePoint » pour Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="9d511-114">Ensuite, renseignez les noms de connexion et de rôle, et exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="9d511-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="9d511-115">Voici un exemple d’un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="9d511-115">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="9d511-116">Pour afficher la liste des noms d’utilisateur pour un rôle spécifique, utilisez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="9d511-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9d511-117">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9d511-118">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) avec un compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="9d511-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="9d511-119">Pour une seule modification de rôle</span><span class="sxs-lookup"><span data-stu-id="9d511-119">For a single role change</span></span>

<span data-ttu-id="9d511-120">Le moyen le plus courant d’un compte d’utilisateur spécifique est son nom d’affichage ou son nom de messagerie, également appelé nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="9d511-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="9d511-121">Noms d’affichage des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="9d511-121">Display names of user accounts</span></span>

<span data-ttu-id="9d511-122">Si vous utilisez les noms d’affichage des comptes d’utilisateur, déterminez ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="9d511-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="9d511-123">Le compte d’utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="9d511-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="9d511-p104">Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9d511-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="9d511-p105">Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="9d511-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="9d511-129">Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="9d511-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="9d511-130">Le rôle que vous souhaitez attribuer.</span><span class="sxs-lookup"><span data-stu-id="9d511-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="9d511-131">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9d511-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="9d511-132">Une fois que vous avez déterminé le nom d’affichage du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :</span><span class="sxs-lookup"><span data-stu-id="9d511-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="9d511-p106">Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$dispName** et **$roleName**, remplacez le texte de description par leurs valeurs, supprimez les caractères \< et > et laissez les guillemets. Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-p106">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="9d511-137">Voici un exemple d’un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="9d511-137">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="9d511-138">Noms de connexion des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="9d511-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="9d511-139">Si vous utilisez le nom de connexion ou l’UPN des comptes d’utilisateur, déterminez les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="9d511-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="9d511-140">Nom d’utilisateur principal du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d511-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="9d511-141">Si vous ne connaissez pas déjà le nom d’utilisateur principal, utilisez la commande suivante:</span><span class="sxs-lookup"><span data-stu-id="9d511-141">If you don't already know the UPN, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="9d511-142">Cette commande répertorie l’UPN de vos comptes d’utilisateur, triés par nom UPN, un écran à la fois.</span><span class="sxs-lookup"><span data-stu-id="9d511-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="9d511-143">Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**.</span><span class="sxs-lookup"><span data-stu-id="9d511-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="9d511-144">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="9d511-144">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="9d511-145">Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="9d511-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="9d511-146">Le rôle que vous souhaitez attribuer.</span><span class="sxs-lookup"><span data-stu-id="9d511-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="9d511-147">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9d511-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="9d511-148">Une fois que vous avez le nom UPN du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte:</span><span class="sxs-lookup"><span data-stu-id="9d511-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="9d511-149">Copiez les commandes et collez-les dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="9d511-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="9d511-150">Pour les variables **$upnName** et **$roleName** , remplacez le texte de description par leurs valeurs, supprimez les \< caractères et >, et laissez les guillemets.</span><span class="sxs-lookup"><span data-stu-id="9d511-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="9d511-151">Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter.</span><span class="sxs-lookup"><span data-stu-id="9d511-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="9d511-152">Vous pouvez également utiliser Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d511-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="9d511-153">Voici un exemple d’un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="9d511-153">Here is an example of a completed command set:</span></span>
  
```
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="9d511-154">Pour plusieurs modifications de rôle</span><span class="sxs-lookup"><span data-stu-id="9d511-154">For multiple role changes</span></span>

<span data-ttu-id="9d511-155">Déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9d511-155">Determine the following:</span></span>
  
- <span data-ttu-id="9d511-156">Les comptes d’utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="9d511-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="9d511-157">Vous pouvez utiliser les méthodes de la section précédente pour collecter le jeu de noms complets ou UPN.</span><span class="sxs-lookup"><span data-stu-id="9d511-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="9d511-158">Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d511-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="9d511-159">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9d511-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="9d511-160">Ensuite, créez un fichier texte au format CSV (valeurs séparées par des virgules) contenant le nom complet ou les champs UPN et nom de rôle.</span><span class="sxs-lookup"><span data-stu-id="9d511-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="9d511-161">Vous pouvez le faire facilement avec Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="9d511-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="9d511-162">Voici un exemple de nom d’affichage:</span><span class="sxs-lookup"><span data-stu-id="9d511-162">Here is an example for display names:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="9d511-163">Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="9d511-164">Voici un exemple pour l’UPN:</span><span class="sxs-lookup"><span data-stu-id="9d511-164">Here is an example for UPNs:</span></span>
  
```
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="9d511-165">Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d511-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="9d511-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d511-166">See also</span></span>

- [<span data-ttu-id="9d511-167">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d511-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="9d511-168">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d511-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="9d511-169">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="9d511-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
