---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123291"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
  
Gestion des licences des comptes d’utilisateurs dans Office 365 sont important, car les utilisateurs ne peuvent pas utiliser tous les services Office 365 jusqu'à ce que leur compte a été accordé sous licence. Vous pouvez utiliser Office 365 PowerShell assigner des licences à des comptes sans licence, en particulier de plusieurs comptes. 

## <a name="before-you-begin"></a>Avant de commencer
<a name="RTT"> </a>

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Utilisez l’applet de commande **Get-MsolAccountSku** pour afficher les plans de gestion de licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Pour rechercher les comptes sans licence dans votre organisation, exécutez la commande`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Vous pouvez affecter des licences uniquement aux comptes d’utilisateurs dont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, nous pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez la commande `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Pour définir la valeur **UsageLocation** sur un compte, utilisez la syntaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Par exemple, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le `-All` paramètre, seuls les 500 premières comptes sont renvoyés.

## <a name="assigning-licenses-to-user-accounts"></a>Attribution de licences aux comptes d’utilisateurs
    
Pour attribuer une licence à un utilisateur, utilisez la syntaxe suivante dans Office 365 PowerShell :
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple attribue une licence à partir de la `litwareinc:ENTERPRISEPACK` plan de licences (Office 365 entreprise E3) à l’utilisateur sans licence `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à plusieurs utilisateurs sans licence, utilisez la syntaxe suivante :
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Remarques**
  
- Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences.
    
- Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.
    
Cet exemple attribue des licences à partir de la `litwareinc:ENTERPRISEPACK` plan de licences (Office 365 entreprise E3) à tous les utilisateurs sans licence.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

Dans cet exemple, les mêmes licences sont attribuées à des utilisateurs sans licence du département des ventes aux États-Unis.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Créer des comptes d’utilisateur](create-user-accounts-with-office-365-powershell.md)
    
- [Supprimer et restaurer des comptes d’utilisateurs](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer les comptes d’utilisateurs](block-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à partir de comptes d’utilisateurs](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

