---
title: Attribuer des rôles à des comptes d’utilisateur Microsoft 365 avec PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: Dans cet article, Découvrez comment utiliser rapidement et facilement PowerShell pour Microsoft 365 pour attribuer des rôles à des comptes d’utilisateur.
ms.openlocfilehash: a3e1936dfa685c78f88e4f4333192f9a07de3cec
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606440"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a>Attribuer des rôles à des comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez rapidement et facilement attribuer des rôles à des comptes d’utilisateur à l’aide de PowerShell pour Microsoft 365.

>[!Note]
>Pour attribuer des rôles aux comptes d’utilisateur à l’aide du centre d’administration Microsoft 365, consultez [ces instructions](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) à l’aide d’un compte d’administrateur général.
  
Ensuite, déterminez le nom de connexion du compte d’utilisateur que vous souhaitez ajouter à un rôle (exemple : fredsm@contoso.com). On l’appelle aussi nom d’utilisateur principal (UPN).

Ensuite, déterminez le nom du rôle. Utilisez cette[liste d’autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

>[!Note]
>Soyez attentif aux notes dans cet article. Certains noms de rôle sont différents pour Azure AD PowerShell. Par exemple, le rôle « Administrateur de SharePoint » dans le Centre d’administration Microsoft 365 est nommé « Administrateur du Service SharePoint » pour Azure AD PowerShell.
>

Ensuite, renseignez les noms de connexion et de rôle, et exécutez ces commandes.
  
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

Voici un exemple d’un jeu de commandes terminé qui affecte le rôle d’administrateur de service SharePoint au compte belindan@contoso.com :
  
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

Pour afficher la liste des noms d’utilisateur pour un rôle spécifique, utilisez ces commandes.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) à l’aide d’un compte d’administrateur général.
  
### <a name="for-a-single-role-change"></a>Pour une seule modification de rôle

Le moyen le plus courant de compte d’utilisateur spécifique est son nom d’affichage ou son nom de messagerie, également appelé nom de connexion ou nom d’utilisateur principal (UPN).

#### <a name="display-names-of-user-accounts"></a>Noms d’affichage des comptes d’utilisateur

Si vous utilisez les noms d’affichage des comptes d’utilisateur, déterminez ce qui suit :
  
- Le compte d’utilisateur que vous souhaitez configurer.
    
    Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :

   >[!Note]
   >PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Le rôle que vous souhaitez attribuer.
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous avez déterminé le nom d’affichage du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$dispName** et **$roleName** , remplacez le texte de description par leurs valeurs, supprimez les \< and > caractères et laissez les guillemets. Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.
  
Voici un exemple d’un jeu de commandes terminées :
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Noms de connexion des comptes d’utilisateur

Si vous utilisez le nom de connexion ou l’UPN des comptes d’utilisateur, déterminez les éléments suivants :
  
- Nom d’utilisateur principal du compte d’utilisateur.
    
    Si vous ne connaissez pas déjà le nom d’utilisateur principal, utilisez la commande suivante :
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie l’UPN de vos comptes d’utilisateur, triés par nom UPN, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Le rôle que vous souhaitez attribuer.
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous avez le nom UPN du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$upnName** et **$roleName** , remplacez le texte de description par leurs valeurs, supprimez les \< and > caractères et laissez les guillemets. Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter. Vous pouvez également utiliser Windows PowerShell ISE.
  
Voici un exemple d’un jeu de commandes terminées :
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Plusieurs modifications de rôle

Pour les différentes modifications de rôle, déterminez les éléments suivants :
  
- Les comptes d’utilisateur que vous souhaitez configurer. Vous pouvez utiliser les méthodes de la section précédente pour collecter le jeu de noms complets ou UPN.
    
- Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur.
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ensuite, créez un fichier texte au format CSV (valeurs séparées par des virgules) contenant le nom complet ou les champs UPN et nom de rôle. Vous pouvez le faire facilement avec Microsoft Excel.

Voici un exemple de nom d’affichage :
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Voici un exemple pour l’UPN :
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Voir aussi

- [Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
- [Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
