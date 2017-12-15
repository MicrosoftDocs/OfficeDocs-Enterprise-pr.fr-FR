---
title: "Bloquer des comptes d’utilisateurs avec Office 365 PowerShell"
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
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365."
ms.openlocfilehash: f22656426e7aa3adf764a3f90adea84cf57a5e89
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquer des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :**  Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365.
  
Bloque l’accès à un compte Office 365, vous empêchez quiconque de se connecter et d’accéder aux services et aux données de votre organisation d’Office 365 à l’aide du compte. Lorsque vous bloquez l’accès au compte, l’utilisateur reçoit le message d’erreur suivant lorsqu’ils tentent de se connecter :
  
![Compte Office 365 bloqué.](images/o365_powershell_account_blocked.png)
  
Vous pouvez utiliser Office 365 PowerShell pour bloquer l’accès aux différents et plusieurs comptes d’utilisateurs.
  
## <a name="before-you-begin"></a>Avant de commencer

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Lorsque vous bloquez un compte d’utilisateur, il peut prendre jusqu'à 24 heures prennent effet sur les périphériques et les clients de tous les utilisateurs.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Utilisation d'Office 365 PowerShell pour bloquer l'accès à des comptes d'utilisateurs individuels

Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Pour débloquer le compte, exécutez la commande suivante :
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

À tout moment, vous pouvez vérifier le statut bloqué d’un compte d’utilisateur avec la commande suivante :
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Office 365 PowerShell permet de bloquer l’accès à plusieurs comptes d’utilisateurs

Tout d’abord, créez un fichier texte qui contient un seul compte sur chaque ligne, comme ceci :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
    
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $true
  ```
Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $false
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Utiliser le module Azure Active Directory V2 PowerShell pour bloquer l’accès à des comptes d’utilisateurs

Pour utiliser la cmdlet **New-AzureADUser** à partir du module Azure Active Directory V2 PowerShell, vous devez d'abord vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article[Se connecter au module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Après vous être connecté, utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Le paramètre - ObjectID de la cmdlet Set-AzureAD accepte le nom de compte, également appelé Nom d’utilisateur principal, ou l’ID d’objet du compte. 
  
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
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Cet exemple affiche le compte d’utilisateur UPN de l’utilisateur nommé Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour bloquer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes :
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

À tout moment, vous pouvez vérifier le statut bloqué d’un compte d’utilisateur avec la commande suivante :
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte qui contient un nom de compte de chaque ligne comme suit :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.
    
Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $true
```

Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $false
```

## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-Content.](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [Nouvelle-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

