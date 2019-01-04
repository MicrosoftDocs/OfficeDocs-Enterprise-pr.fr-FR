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
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquer des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :**  Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365.
  
Bloque l’accès à un compte Office 365 empêche toute personne utilisant le compte pour se connecter et accéder aux services et données de votre organisation Office 365. Vous pouvez utiliser Office 365 PowerShell pour bloquer l’accès aux différents et plusieurs comptes d’utilisateurs.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez Azure Active Directory PowerShell pour le module de graphique

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès aux comptes d’utilisateurs individuels

Pour bloquer un compte d’utilisateur, utilisez la syntaxe suivante :
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Le paramètre - ObjectID dans l’applet de commande Set-AzureAD accepte soit le compte nom de connexion, également connu sous le nom d’utilisateur Principal ou ID d’objet. d’un compte 
  
Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Pour débloquer ce compte, exécutez la commande suivante :
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Pour afficher le compte d’utilisateur QU'UPN basé sur le nom complet de l’utilisateur, utilisez les commandes suivantes :
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Cet exemple montre comment affiche le compte d’utilisateur UPN pour l’utilisateur nommé Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour bloquer un compte basé sur le nom complet de l’utilisateur, utilisez les commandes suivantes :
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

À tout moment, vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquer l’accès à plusieurs comptes d’utilisateurs

Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte qui contient un seul compte nom de connexion de chaque ligne comme suit :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacer par le chemin d’accès et le nom de votre fichier texte.
  
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès aux comptes d’utilisateurs individuels

Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Pour débloquer le compte, exécutez la commande suivante :
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

À tout moment, vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquer l’accès à plusieurs comptes d’utilisateurs

Tout d’abord, créez un fichier texte qui contient un seul compte sur chaque ligne comme suit :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacer par le chemin d’accès et le nom de votre fichier texte.
    
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
