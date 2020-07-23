---
title: Supprimer des comptes d’utilisateur Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Découvrez comment utiliser PowerShell pour Microsoft 365 pour supprimer des comptes d’utilisateurs.
ms.openlocfilehash: 62d9dee2e6b0d2054116e5e5f005b5928112186d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230710"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Supprimer des comptes d’utilisateur Microsoft 365 avec PowerShell

Vous pouvez utiliser PowerShell pour Microsoft 365 pour supprimer un compte d’utilisateur.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d’utilisateur individuel :
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Cet exemple supprime le compte d’utilisateur fabricec@litwareinc.com.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Le paramètre **-ObjectID** de la cmdlet **Remove-AzureADUser** accepte le nom de connexion du compte, également appelé nom d’utilisateur principal, ou l’ID d’objet du compte.
  
Pour afficher le nom du compte à partir du nom de l’utilisateur, utilisez les commandes suivantes :
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom du compte de l’utilisateur nommé Caleb Sills.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour supprimer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Lorsque vous utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell afin de supprimer un compte d’utilisateur, le compte n’est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Pour supprimer un compte d’utilisateur, utilisez la syntaxe suivante :
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Cet exemple supprime le compte d’utilisateur BelindaN@litwareinc.com.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Pour restaurer un compte d’utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Cet exemple restaure le compte d’utilisateur supprimé BelindaN@litwareinc.com.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Remarques :**
  
- Pour afficher la liste des utilisateurs supprimés dont la restauration est possible, exécutez la commande suivante:
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Si le nom d'utilisateur principal d'origine du compte d'utilisateur est utilisé par un autre compte, utilisez le paramètre_NewUserPrincipalName_ à la place de_UserPrincipalName_ pour spécifier un autre nom d'utilisateur principal lorsque vous restaurez le compte.


## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
