---
title: Afficher les utilisateurs titulaires d’une licence et de Microsoft 365 sans licence avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
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
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explique comment utiliser PowerShell pour afficher des comptes d’utilisateurs Microsoft 365 sans licence ou sous licence.
ms.openlocfilehash: 02b1f76bab0e64e4e7e72f5e5556f5047d956d11
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230250"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Afficher les utilisateurs titulaires d’une licence et de Microsoft 365 sans licence avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Les comptes d’utilisateur de votre organisation Microsoft 365 peuvent avoir certaines, toutes ou aucune des licences disponibles qui leur sont attribuées à partir des plans de gestion des licences disponibles dans votre organisation. Vous pouvez utiliser PowerShell pour Microsoft 365 pour trouver rapidement les utilisateurs sous licence et sans licence de votre organisation.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Pour afficher la liste de tous les comptes d’utilisateur de votre organisation auxquels aucun de vos plans de licence n’a été attribué (utilisateurs sans licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation auxquels ont été affectés des plans de gestion des licences (utilisateurs sous licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Pour répertorier tous les utilisateurs de votre abonnement, utilisez la `Get-AzureAdUser -All $true` commande.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Pour afficher la liste de tous les comptes d’utilisateurs et leur statut de licence dans votre organisation, exécutez la commande suivante dans PowerShell :
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
