---
title: Désactiver l’accès aux services Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilisez Office 365 PowerShell pour désactiver l’accès aux services 365 Office pour les utilisateurs.
ms.openlocfilehash: 32c43a47e1547e85488cb5158bd7392d79c8a4fb
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781834"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Désactiver l’accès aux services Office 365 PowerShell

**Résumé:** Explique comment utiliser Office 365 PowerShell pour désactiver l’accès aux services 365 Office pour les utilisateurs de votre organisation.
  
Lorsqu’un compte Office 365 est affecté à une licence d’un plan de gestion des licences, les services Office 365 sont mis à la disposition de l’utilisateur à partir de cette licence. Toutefois, vous pouvez contrôler les services Office 365 auxquels l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès au service SharePoint Online, vous pouvez désactiver l’accès à celle-ci. Vous pouvez utiliser PowerShell pour désactiver l’accès à n’importe quel nombre de services pour un plan de gestion des licences spécifique pour:

- un compte individuel ;
    
- un groupe de comptes ;
    
- tous les comptes de votre organisation.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, utilisez cette commande pour afficher vos plans de gestion des licences disponibles, également appelés AccountSkuIds:

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

Pour plus d’informations, voir [afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Pour afficher les résultats avant et après des procédures de cette rubrique, voir [View Account License and service Details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Office 365, y compris Sway. Pour plus d’informations, reportez-vous à la rubrique [désactiver l’accès à Sway avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Désactiver des services Office 365 spécifiques pour des utilisateurs spécifiques pour un plan de gestion des licences spécifique
  
Pour désactiver un ensemble spécifique de services Office 365 pour les utilisateurs pour un plan de gestion de licences spécifique, procédez comme suit:
  
1. Identifiez les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office et SharePoint Online dans le plan de gestion des licences `litwareinc:ENTERPRISEPACK` nommé (Office 365 entreprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilisez l’objet **LicenseOptions** de l’étape 1 sur un ou plusieurs utilisateurs.
    
  - Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  L’exemple suivant crée un nouveau compte pour allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Pour plus d’informations sur la création de comptes d’utilisateurs dans Office 365 PowerShell, consultez la rubrique [Create User Accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence existants, spécifiez le nom de votre plan Office 365 à partir de l’affichage de la cmdlet **Get-MsolAccountSku** (comme **litwareinc: ENTERPRISEPACK**), puis exécutez les commandes suivantes:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le paramètre _All_ , seuls les premiers comptes d’utilisateur 500 sont renvoyés.


  - Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
  - **Filtrer les comptes en fonction d’un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  L’exemple suivant désactive les services pour les utilisateurs du service des ventes aux États-Unis.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Utiliser une liste de comptes spécifiques** Pour ce faire, procédez comme suit:
    
1. Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  Dans cet exemple, le fichier texte est C:\\My documents\\Accounts. txt.
    
2. Exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Si vous souhaitez désactiver l’accès aux services pour plusieurs plans de gestion des licences, répétez les instructions ci-dessus pour chaque plan de gestion des licences, en vous assurant que:

- Le plan de gestion des licences a été attribué aux comptes d’utilisateurs.
- Les services à désactiver sont disponibles dans le plan de gestion des licences.

Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, reportez-vous à la rubrique [désactiver l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
