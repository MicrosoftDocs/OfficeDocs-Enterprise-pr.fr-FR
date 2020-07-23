---
title: Suppression des licences Microsoft 365 des comptes d’utilisateur avec PowerShell
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explique comment utiliser PowerShell pour supprimer des licences Microsoft 365 qui ont été précédemment attribuées à des utilisateurs.
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230390"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Suppression des licences Microsoft 365 des comptes d’utilisateur avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également appelée nom d’utilisateur principal (UPN).

Enfin, spécifiez les noms de connexion et de plan de licence de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Pour supprimer toutes les licences pour un compte d’utilisateur spécifique, spécifiez le nom de connexion de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Pour afficher les informations sur le plan de gestion des licences (**AccountSkuID**) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Afficher les détails de service et de licence de compte avec PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.
    
### <a name="removing-licenses-from-user-accounts"></a>Suppression de licences de comptes d’utilisateurs

Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) du compte d’utilisateur BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Vous ne pouvez pas utiliser l' `Set-MsolUserLicense` applet de commande pour annuler l’affectation des utilisateurs des licences *annulées* . Vous devez effectuer cette opération individuellement pour chaque compte d’utilisateur dans le centre d’administration Microsoft 365.
>

Pour supprimer toutes les licences d’un groupe d’utilisateurs sous licence existants, utilisez l’une des méthodes suivantes :
  
- **Filtrer les comptes en fonction d’un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Cet exemple supprime toutes les licences de tous les comptes d’utilisateur du département des ventes aux États-Unis.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Utiliser une liste de comptes spécifiques pour une licence spécifique** Pour ce faire, procédez comme suit :
    
1. Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilisez la syntaxe suivante :
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) des comptes d’utilisateur définis dans le fichier texte C:\My Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Pour supprimer toutes les licences de tous les comptes d’utilisateur existants, utilisez la syntaxe suivante :
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur. Pour plus d’informations, consultez la rubrique [Delete and Restore User Accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

