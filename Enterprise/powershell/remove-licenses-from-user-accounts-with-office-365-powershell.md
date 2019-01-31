---
title: Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui ont été précédemment attribués aux utilisateurs.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651218"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui ont été précédemment attribués aux utilisateurs.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ensuite, répertoriez les plans de licence pour votre client avec cette commande.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenir le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également connu sous le nom d’utilisateur principal (UPN).

Enfin, spécifiez les noms de plan de connexion et de licence utilisateur, supprimez les caractères « < » et « > » et exécuter ces commandes.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

   
Pour afficher les informations de licence plan (**éléments AccountSkuID** ) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Afficher les détails de service et de licence de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.
    
### <a name="removing-licenses-from-user-accounts"></a>Supprimer des licences à partir de comptes d’utilisateurs

Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) du compte d’utilisateur BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Pour supprimer des licences d’un groupe d’utilisateurs sous licence existants, appliquez l’une des méthodes suivantes :
  
- **Filtrer les comptes basées sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Cet exemple supprime le `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) licences de tous les comptes d’utilisateurs du service ventes aux États-Unis.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Utiliser une liste de comptes spécifiques** Pour ce faire, procédez comme suit :
    
1. Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilisez la syntaxe suivante :
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) dans les comptes d’utilisateur défini dans le fichier texte C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Pour supprimer des licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Cet exemple supprime le `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir de tout une licence de comptes d’utilisateurs.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Une autre manière pour libérer une licence est en supprimant le compte d’utilisateur. Pour plus d’informations, voir [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

