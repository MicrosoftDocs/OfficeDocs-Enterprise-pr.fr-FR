---
title: Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
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
description: Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 précédemment attribuées à des utilisateurs.
ms.openlocfilehash: 4a99fb115b7c3241beb2cb3b0dd83666622747d5
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208755"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également appelée nom d’utilisateur principal (UPN).

Enfin, spécifiez les noms de connexion et de plan de licence de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
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
   
Pour afficher les informations sur le plan de gestion des licences (**AccountSkuID**) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Afficher les détails de service et de licence de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
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
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId>" }
  ```

Cet exemple supprime la licence **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) des comptes d’utilisateur définis dans le fichier texte C:\My Documents\Accounts.txt.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

Pour supprimer toutes les licences de tous les comptes d’utilisateur existants, utilisez la syntaxe suivante :
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur. Pour plus d’informations, consultez la rubrique [supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Articles associés

[Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

