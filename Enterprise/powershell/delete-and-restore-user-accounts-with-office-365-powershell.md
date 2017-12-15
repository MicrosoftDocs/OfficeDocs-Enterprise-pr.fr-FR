---
title: Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Apprenez à utiliser Office 365 PowerShell pour supprimer et restaurer des comptes d’utilisateurs Office 365."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell

**Résumé :**  Apprenez à utiliser Office 365 PowerShell pour supprimer et restaurer des comptes d’utilisateurs Office 365.
  
Lorsque vous utilisez Office 365 PowerShell pour supprimer un compte d'utilisateur, le compte n'est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.
  
## <a name="before-you-begin"></a>Avant de commencer

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le _-tous les_ paramètre, seuls les 500 premiers comptes de sont retournés.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Utilisation d'Office 365 PowerShell pour bloquer l'accès à des comptes d'utilisateurs individuels
<a name="ShortVersion"> </a>

Pour supprimer un compte d'utilisateur, utilisez la syntaxe suivante :
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

Cet exemple supprime le compte d'utilisateur BelindaN@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Pour restaurer un compte d'utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

Cet exemple restaure le compte d'utilisateur supprimé BelindaN@litwareinc.com.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Remarques :**
  
- Pour afficher la liste des utilisateurs supprimés dont la restauration est possible, exécutez la commande suivante :
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Si le nom d'utilisateur principal d'origine du compte d'utilisateur est utilisé par un autre compte, utilisez le paramètre  _NewUserPrincipalName_ à la place de _UserPrincipalName_ pour spécifier un autre nom d'utilisateur principal lorsque vous restaurez le compte.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Utilisation du module Azure Active Directory V2 PowerShell pour supprimer un compte d'utilisateur
<a name="ShortVersion"> </a>

Pour utiliser l’applet de commande **Remove-AzureADUser** à partir du module PowerShell de Azure Active Directory V2, vous devez d’abord vous connecter à votre abonnement. Pour les instructions, voir [se connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d'utilisateur individuel :
  
```
Remove-AzureADUser -ObjectID <Account>
```

Cet exemple supprime le compte d'utilisateur fabricec@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Le paramètre **- ObjectID** de la cmdlet **Remove-AzureAD** accepte le nom de compte, également appelé Nom d'utilisateur principal, ou l'ID d'objet du compte.
  
Pour afficher le nom du compte à partir du nom de l'utilisateur, utilisez les commandes suivantes :
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom du compte de l'utilisateur nommé Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour supprimer un compte à partir du nom de l'utilisateur, utilisez les commandes suivantes :
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez ces rubriques supplémentaires sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

