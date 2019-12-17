---
title: Bloquer des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes Office 365.
ms.openlocfilehash: 2ebed63de7cddd536b42000028cabd3c71cec31b
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072246"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquer des comptes d’utilisateurs avec Office 365 PowerShell

Le blocage de l’accès à un compte Office 365 empêche quiconque d’utiliser le compte pour se connecter et accéder aux services et données de votre organisation Office 365. Vous pouvez utiliser Office 365 PowerShell pour bloquer l’accès à un ou plusieurs comptes d’utilisateurs.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès à des comptes d’utilisateurs individuels

Utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Le paramètre-ObjectID de la cmdlet Set-AzureAD accepte le nom de connexion du compte, également appelé nom d’utilisateur principal, ou l’ID d’objet du compte. 
  
Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Pour débloquer ce compte, exécutez la commande suivante :
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Pour afficher l’UPN du compte d’utilisateur en fonction du nom d’affichage de l’utilisateur, utilisez les commandes suivantes :
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Cet exemple affiche le nom UPN du compte d’utilisateur pour l’utilisateur nommé Caleb Sills.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour bloquer un compte en fonction du nom d’affichage de l’utilisateur, utilisez les commandes suivantes :
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

À tout moment, vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquer l’accès à plusieurs comptes d’utilisateurs

Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte contenant un nom de connexion sur chaque ligne comme suit :
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
  
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès à des comptes d’utilisateurs individuels

Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Pour débloquer le compte, exécutez la commande suivante :
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

À tout moment, vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquer l’accès à plusieurs comptes d’utilisateurs

Tout d’abord, créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
    
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
