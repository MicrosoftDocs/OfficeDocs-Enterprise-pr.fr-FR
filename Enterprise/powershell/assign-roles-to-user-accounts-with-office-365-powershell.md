---
title: Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Résumé : Utilisation d’Office 365 PowerShell pour attribuer des rôles à des comptes d’utilisateur.'
ms.openlocfilehash: 8cd3bd27f95c9d4191c24c7febc85c8fb2fb0118
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004737"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1ab63-103">Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ab63-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1ab63-104">Vous pouvez rapidement et facilement attribuer des rôles à des comptes d’utilisateur à l’aide d’Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1ab63-105">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="1ab63-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1ab63-106">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) avec un compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="1ab63-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="1ab63-p101">Ensuite, déterminez le nom de connexion du compte d’utilisateur que vous souhaitez ajouter à un rôle (exemple : fredsm@contoso.com). On l’appelle aussi nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="1ab63-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1ab63-109">Ensuite, déterminez le nom du rôle.</span><span class="sxs-lookup"><span data-stu-id="1ab63-109">Next, determine the name of the role.</span></span> <span data-ttu-id="1ab63-110">Utilisez cette[liste d’autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="1ab63-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="1ab63-111">Soyez attentif aux notes dans cet article.</span><span class="sxs-lookup"><span data-stu-id="1ab63-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="1ab63-112">Certains noms de rôle sont différents pour Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="1ab63-113">Par exemple, le rôle « Administrateur de SharePoint » dans le Centre d’administration Microsoft 365 est nommé « Administrateur du Service SharePoint » pour Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="1ab63-114">Ensuite, renseignez les noms de connexion et de rôle, et exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="1ab63-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
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

<span data-ttu-id="1ab63-115">Voici un exemple d’un jeu de commandes terminé qui affecte le rôle d’administrateur de service SharePoint au compte belindan@contoso.com :</span><span class="sxs-lookup"><span data-stu-id="1ab63-115">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
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

<span data-ttu-id="1ab63-116">Pour afficher la liste des noms d’utilisateur pour un rôle spécifique, utilisez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="1ab63-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1ab63-117">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1ab63-118">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) avec un compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="1ab63-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="1ab63-119">Pour une seule modification de rôle</span><span class="sxs-lookup"><span data-stu-id="1ab63-119">For a single role change</span></span>

<span data-ttu-id="1ab63-120">Le moyen le plus courant de compte d’utilisateur spécifique est son nom d’affichage ou son nom de messagerie, également appelé nom de connexion ou nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="1ab63-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="1ab63-121">Noms d’affichage des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="1ab63-121">Display names of user accounts</span></span>

<span data-ttu-id="1ab63-122">Si vous utilisez les noms d’affichage des comptes d’utilisateur, déterminez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="1ab63-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="1ab63-123">Le compte d’utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="1ab63-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="1ab63-p104">Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="1ab63-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="1ab63-p105">Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="1ab63-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="1ab63-129">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="1ab63-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="1ab63-130">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="1ab63-131">Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="1ab63-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="1ab63-132">Le rôle que vous souhaitez attribuer.</span><span class="sxs-lookup"><span data-stu-id="1ab63-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="1ab63-133">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="1ab63-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="1ab63-134">Une fois que vous avez déterminé le nom d’affichage du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :</span><span class="sxs-lookup"><span data-stu-id="1ab63-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="1ab63-p107">Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$dispName** et **$roleName**, remplacez le texte de description par leurs valeurs, supprimez les caractères \< et > et laissez les guillemets. Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-p107">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="1ab63-139">Voici un exemple d’un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="1ab63-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="1ab63-140">Noms de connexion des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="1ab63-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="1ab63-141">Si vous utilisez le nom de connexion ou l’UPN des comptes d’utilisateur, déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1ab63-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="1ab63-142">Nom d’utilisateur principal du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ab63-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="1ab63-143">Si vous ne connaissez pas déjà le nom d’utilisateur principal, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ab63-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="1ab63-144">Cette commande répertorie l’UPN de vos comptes d’utilisateur, triés par nom UPN, un écran à la fois.</span><span class="sxs-lookup"><span data-stu-id="1ab63-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="1ab63-145">Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**.</span><span class="sxs-lookup"><span data-stu-id="1ab63-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="1ab63-146">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="1ab63-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="1ab63-147">Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».</span><span class="sxs-lookup"><span data-stu-id="1ab63-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="1ab63-148">Le rôle que vous souhaitez attribuer.</span><span class="sxs-lookup"><span data-stu-id="1ab63-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="1ab63-149">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="1ab63-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="1ab63-150">Une fois que vous avez le nom UPN du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :</span><span class="sxs-lookup"><span data-stu-id="1ab63-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="1ab63-151">Copiez les commandes et collez-les dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="1ab63-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="1ab63-152">Pour les variables **$upnName** et **$roleName** , remplacez le texte de description par leurs valeurs, supprimez les \< caractères et > et laissez les guillemets.</span><span class="sxs-lookup"><span data-stu-id="1ab63-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="1ab63-153">Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter.</span><span class="sxs-lookup"><span data-stu-id="1ab63-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="1ab63-154">Vous pouvez également utiliser Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1ab63-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="1ab63-155">Voici un exemple d’un jeu de commandes terminées :</span><span class="sxs-lookup"><span data-stu-id="1ab63-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="1ab63-156">Plusieurs modifications de rôle</span><span class="sxs-lookup"><span data-stu-id="1ab63-156">Multiple role changes</span></span>

<span data-ttu-id="1ab63-157">Pour les différentes modifications de rôle, déterminez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1ab63-157">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="1ab63-158">Les comptes d’utilisateur que vous souhaitez configurer.</span><span class="sxs-lookup"><span data-stu-id="1ab63-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="1ab63-159">Vous pouvez utiliser les méthodes de la section précédente pour collecter le jeu de noms complets ou UPN.</span><span class="sxs-lookup"><span data-stu-id="1ab63-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="1ab63-160">Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ab63-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="1ab63-161">Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="1ab63-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="1ab63-162">Ensuite, créez un fichier texte au format CSV (valeurs séparées par des virgules) contenant le nom complet ou les champs UPN et nom de rôle.</span><span class="sxs-lookup"><span data-stu-id="1ab63-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="1ab63-163">Vous pouvez le faire facilement avec Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="1ab63-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="1ab63-164">Voici un exemple de nom d’affichage :</span><span class="sxs-lookup"><span data-stu-id="1ab63-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="1ab63-165">Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="1ab63-166">Voici un exemple pour l’UPN :</span><span class="sxs-lookup"><span data-stu-id="1ab63-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="1ab63-167">Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab63-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="1ab63-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ab63-168">See also</span></span>

- [<span data-ttu-id="1ab63-169">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ab63-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="1ab63-170">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ab63-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="1ab63-171">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="1ab63-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
