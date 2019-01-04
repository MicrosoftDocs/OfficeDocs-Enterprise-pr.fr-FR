---
title: Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.
ms.openlocfilehash: 0648fae89a45b080bd48561bb079184f0e97dd36
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546505"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.
  
Il se peut que l'intégralité, une partie ou aucune des licences disponibles soit attribuée aux comptes d'utilisateurs de votre organisation Office 365 à partir des plans de gestion des licences disponibles dans votre organisation. Vous pouvez utiliser Office 365 PowerShell pour rechercher rapidement les utilisateurs avec ou sans licence dans votre organisation.


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez Azure Active Directory PowerShell pour le module de graphique

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Pour afficher la liste de tous les comptes d’utilisateurs dans votre organisation qui n’a pas attribué un de vos plans de gestion des licences (les utilisateurs sans licence), exécutez la commande suivante :
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Pour afficher la liste de tous les comptes d’utilisateurs dans votre organisation qui ont été affectés à un de vos plans de gestion des licences (utilisateurs sous licence), exécutez la commande suivante :
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Pour afficher la liste de tous les comptes d'utilisateurs et leur statut de licence dans votre organisation, exécutez la commande suivante dans Office 365 PowerShell :
  
```
Get-MsolUser -All
```

Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
