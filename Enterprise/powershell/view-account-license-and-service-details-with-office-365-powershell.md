---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués aux utilisateurs.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223106"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Afficher les détails de service et de licence de compte avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués aux utilisateurs.
  
Dans Office 365, les licences de plans de gestion des licences (également appelées références ou Office 365 plans) donner aux utilisateurs l’accès aux services qui sont définies pour les plans Office 365. Toutefois, un utilisateur peut avoir pas accès à tous les services qui sont disponibles dans une licence qui leur est actuellement affectée. Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur les comptes d’utilisateurs. 

## <a name="before-you-begin"></a>Avant de commencer

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Utilisez les commandes `Get-MsolAccountSku` et `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` pour trouver les informations suivantes :
    
  - Plans de gestion de licences disponibles dans votre organisation.
    
  - Services disponibles dans chaque plan de gestion de licences et l’ordre dans lequel ils sont répertoriés (numéro d’index).
    
     Pour plus d’informations sur les licences des plans de licence et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Utilisez la commande `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` pour rechercher les licences sont affectés à un utilisateur et l’ordre dans lequel ils sont répertoriés (le numéro d’index).
    
- Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.
    

## <a name="to-view-services-for-a-user-account"></a>Pour afficher les services pour un compte d’utilisateur

Pour afficher tous les services un utilisateur ayant accès à Office 365, utilisez la syntaxe suivante :
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Cet exemple illustre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Affiche les services qui sont associés à toutes les licences sont attribués à ce compte.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Pour rechercher tous les utilisateurs sous licence qui ont été activés ou désactivés pour des services spécifiques, utilisez la syntaxe suivante :
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

Ces exemples utilisent les informations suivantes :
  
- La licence qui donne accès aux services Office 365 qui nous intéressent est la première qui est affectée à tous les utilisateurs (le numéro d’index est 0).
    
- Les services Office 365 qui nous intéressent sont Skype pour Business Online et Exchange Online. Pour les licences sont associés au plan de gestion des licences, Skype pour Business Online est 6 service répertorié (le numéro d’index est 5), et Exchange Online est le service 9 répertoriés (le numéro d’index est 8).
    
Cet exemple renvoie tous les titulaires qui sont activés pour Skype pour Business Online et Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Cet exemple renvoie tous les utilisateurs sous licence qui ne sont pas activés pour Skype pour Business Online ou Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Pour afficher tous les services d’un utilisateur qui a été affecté *plusieurs licences*, utilisez la syntaxe suivante :

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>Voir aussi

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]