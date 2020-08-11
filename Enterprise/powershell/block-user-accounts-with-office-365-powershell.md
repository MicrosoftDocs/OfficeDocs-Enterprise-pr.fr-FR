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
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Cet article explique comment utiliser PowerShell pour bloquer et débloquer l’accès aux comptes Microsoft 365.
ms.openlocfilehash: 1d32554642f29b4548e2525135d20967ba6b0f16
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606430"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Bloquer les comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Le blocage de l’accès à un compte Microsoft 365 empêche quiconque d’utiliser le compte pour se connecter et accéder aux services et données de votre organisation Microsoft 365. Vous pouvez utiliser PowerShell pour bloquer l’accès à un ou plusieurs comptes d’utilisateurs.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
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

Dans les commandes suivantes, le fichier texte de l’exemple est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
  
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
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

Dans les commandes suivantes, le fichier texte de l’exemple est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
    
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
