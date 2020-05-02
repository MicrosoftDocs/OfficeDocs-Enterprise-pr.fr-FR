---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
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
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués à des utilisateurs.
ms.openlocfilehash: 603470be87aea2d58f343511026fb2860e58b688
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004487"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Afficher les détails de service et de licence de compte avec Office 365 PowerShell

Dans Office 365, les licences des plans de gestion des licences (également appelés « SKU » ou « offres Office 365 ») permettent aux utilisateurs d’accéder aux services Office 365 définis pour ces plans. Toutefois, un utilisateur ne dispose peut-être pas d’un accès à tous les services disponibles dans une licence qui lui est affectée. Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur les comptes d’utilisateur. 

Pour plus d’informations sur les plans de licence, les licences et les services, voir [View licenses and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Utilisez ces commandes pour répertorier les services disponibles dans chaque plan de gestion des licences.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Utilisez ces commandes pour répertorier les licences qui sont affectées à un compte d’utilisateur.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, exécutez cette commande pour répertorier les plans de gestion des licences disponibles dans votre organisation. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Ensuite, exécutez cette commande pour répertorier les services disponibles dans chaque plan de gestion des licences et l’ordre dans lequel ils sont répertoriés (le numéro d’index).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Utilisez cette commande pour répertorier les licences qui sont affectées à un utilisateur et l’ordre dans lequel elles sont répertoriées (le numéro d’index).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Pour afficher les services d’un compte d’utilisateur

Pour afficher tous les services Office 365 auxquels un utilisateur a accès, utilisez la syntaxe suivante :
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Cet exemple illustre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Ceci affiche les services qui sont associés à toutes les licences attribuées à son compte.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Pour afficher tous les services d’un utilisateur auquel ont été affectées *plusieurs licences*, utilisez la syntaxe suivante :

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
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

[Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
