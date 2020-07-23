---
title: Attribuer des licences Microsoft 365 à des comptes d’utilisateur avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Comment utiliser PowerShell pour attribuer une licence Microsoft 365 à des utilisateurs sans licence.
ms.openlocfilehash: 25a57158be82f985885a7ceaf89f526f9d522b4d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229830"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Attribuer des licences Microsoft 365 à des comptes d’utilisateur avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Les utilisateurs ne peuvent pas utiliser les services Microsoft 365 tant que leur compte n’a pas reçu une licence d’un plan de gestion des licences. Vous pouvez utiliser PowerShell pour affecter rapidement des licences à des comptes sans licence. 

>[!Note]
>Un emplacement doit être attribué aux comptes d’utilisateurs. Vous pouvez effectuer cette opération à partir des propriétés d’un compte d’utilisateur dans le centre d’administration 365 de Microsoft ou à partir de PowerShell.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).

Ensuite, vérifiez que l’emplacement d’utilisation est affecté au compte d’utilisateur.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

S’il n’y a pas d’emplacement d’utilisation attribué, vous pouvez en affecter un à l’aide des commandes suivantes :

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Enfin, spécifiez le nom de connexion de l’utilisateur et le nom du plan de licence et exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Exécutez la `Get-MsolAccountSku` commande pour afficher les plans de gestion des licences disponibles et le nombre de licences disponibles dans chaque plan de votre organisation. Le nombre de licences disponibles pour chaque plan est **ActiveUnits**  -  **WarningUnits**  -  **ConsumedUnits**. Pour plus d’informations sur les plans de licence, les licences et les services, voir [View licenses and Services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Vous pouvez uniquement attribuer des licences à des comptes d’utilisateur dont la propriété **UsageLocation** est définie sur un code ISO 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Certains services Microsoft 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, consultez la rubrique [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Pour rechercher les comptes qui n’ont pas de valeur **UsageLocation** , exécutez cette commande.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Par exemple :

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.

### <a name="assigning-licenses-to-user-accounts"></a>Attribution de licences à des comptes d’utilisateur
    
Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple attribue une licence du plan de gestion des licences **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) à l’utilisateur sans licence ** \@ litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à tous les utilisateurs sans licence, exécutez cette commande.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences. Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.
>

Cet exemple attribue des licences à tous les utilisateurs sans licence à partir du plan de gestion des licences **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Cet exemple attribue ces mêmes licences aux utilisateurs sans licence du département des ventes aux États-Unis :
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Déplacer un utilisateur vers un autre abonnement (plan de licence) avec le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ensuite, obtenez le nom de connexion du compte d’utilisateur pour lequel vous souhaitez des abonnements de commutateur, également appelé nom d’utilisateur principal (UPN).

Ensuite, répertoriez les abonnements (plans de licence) de votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, répertoriez les abonnements que le compte d’utilisateur possède actuellement avec ces commandes.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifiez l’abonnement dont dispose l’utilisateur (abonnement FROM) et l’abonnement que l’utilisateur déplace (l’abonnement à).

Enfin, spécifiez les noms d’abonnement à et à (numéros de référence SKU) et exécutez ces commandes.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Vous pouvez vérifier la modification de l’abonnement pour le compte d’utilisateur à l’aide de ces commandes.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
