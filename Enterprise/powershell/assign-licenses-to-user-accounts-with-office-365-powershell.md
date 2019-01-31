---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651179"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
  
Les utilisateurs ne peuvent pas utiliser les services Office 365 jusqu'à ce que leur compte a été attribué une licence d’un plan de gestion des licences. Vous pouvez utiliser Office 365 PowerShell pour attribuer des licences rapidement aux comptes sans licence. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ensuite, répertoriez les plans de licence pour votre client avec cette commande.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenir le nom de connexion du compte auquel vous souhaitez ajouter une licence, également connu sous le nom d’utilisateur principal (UPN).

Enfin, spécifiez le nom de connexion utilisateur et le nom de plan de licence et exécuter ces commandes.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Exécutez la commande **Get-MsolAccountSku** pour afficher les plans de gestion de licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
Vous ne pouvez affecter des licences pour les comptes d’utilisateurs dont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, nous pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez cette commande.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Par exemple :

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.

### <a name="assigning-licenses-to-user-accounts"></a>Attribution de licences aux comptes d’utilisateurs
    
Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans Office 365 PowerShell.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple attribue une licence à partir de la **litwareinc : enterprisepack** (Office 365 entreprise E3) de planification de l' utilisateur sans licence **belindan@litwareinc.com**de gestion des licences :
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à de nombreux utilisateurs sans licence, exécutez cette commande.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>Vous ne pouvez pas affecter plusieurs licences à un utilisateur dans le plan de gestion des licences. Si vous n’avez pas suffisamment de licences disponibles, les licences sont attribuées aux utilisateurs dans l’ordre dans lequel ils sont renvoyés par l’applet de commande **Get-MsolUser** jusqu'à épuisement des licences disponibles.
>

Cet exemple attribue des licences à partir du plan de gestion des licences **litwareinc : enterprisepack** (Office 365 entreprise E3) pour tous les utilisateurs sans licence :
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

Cet exemple affecte ces mêmes licences aux utilisateurs sans licence dans le service des ventes aux États-Unis :
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
