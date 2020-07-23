---
title: Désactiver l’accès aux services Microsoft 365 avec PowerShell
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilisez PowerShell pour désactiver l’accès aux services Microsoft 365 pour les utilisateurs.
ms.openlocfilehash: 4e7c59447dae027dffa7fd5ea24d1818d5d64a9a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230680"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Désactiver l’accès aux services Microsoft 365 avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Lorsqu’un compte Microsoft 365 est affecté à une licence d’un plan de gestion des licences, les services Microsoft 365 sont mis à la disposition de l’utilisateur à partir de cette licence. Toutefois, vous pouvez contrôler les services Microsoft 365 auxquels l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès au service SharePoint Online, vous pouvez désactiver l’accès à celle-ci. Vous pouvez utiliser PowerShell pour désactiver l’accès à n’importe quel nombre de services pour un plan de gestion des licences spécifique pour :

- un compte individuel ;
- un groupe de comptes ;
- tous les comptes de votre organisation.

>[!Note]
>Il existe des dépendances de service Microsoft 365 qui peuvent vous empêcher de désactiver un service spécifié lorsque d’autres services dépendent de lui.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, utilisez cette commande pour afficher vos plans de gestion des licences disponibles, également appelés AccountSkuIds :

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour plus d’informations, consultez la rubrique [afficher les licences et les services avec PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Pour afficher les résultats avant et après des procédures de cette rubrique, voir [View Account License and service Details with PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver les services de votre organisation Microsoft 365, y compris Sway. Pour plus d’informations, consultez la rubrique [désactiver l’accès à Sway avec PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de gestion des licences spécifique
  
Pour désactiver un ensemble spécifique de services Microsoft 365 pour les utilisateurs pour un plan de gestion de licences spécifique, procédez comme suit :
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Étape 1 : identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office et SharePoint Online dans le plan de gestion des licences nommé `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Étape 2 : utilisez l’objet **LicenseOptions** de l’étape 1 sur un ou plusieurs utilisateurs.
    
Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

L’exemple suivant crée un nouveau compte pour allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Pour plus d’informations sur la création de comptes d’utilisateur dans PowerShell pour Microsoft 365, voir [Create User Accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).
    
Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence existants, spécifiez le nom de votre plan Microsoft 365 à partir de l’affichage de la cmdlet **Get-MsolAccountSku** (comme **litwareinc : ENTERPRISEPACK**), puis exécutez les commandes suivantes :
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le paramètre _All_ , seuls les premiers comptes d’utilisateur 500 sont renvoyés.

Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
**Méthode 1. Filtrer les comptes en fonction d’un attribut de compte existant** 

Pour ce faire, utilisez la syntaxe suivante :
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

L’exemple suivant désactive les services pour les utilisateurs du service des ventes aux États-Unis.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Méthode 2 : utiliser une liste de comptes spécifiques** 

Pour ce faire, procédez comme suit :
    
1. Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  Dans cet exemple, le fichier texte est C : \\ My Documents \\Accounts.txt.
    
2. Exécutez la commande suivante :
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Si vous souhaitez désactiver l’accès aux services pour plusieurs plans de gestion des licences, répétez les instructions ci-dessus pour chaque plan de gestion des licences, en vous assurant que :

- Le plan de gestion des licences a été attribué aux comptes d’utilisateurs.
- Les services à désactiver sont disponibles dans le plan de gestion des licences.

Pour désactiver les services Microsoft 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, reportez-vous à la rubrique [désactiver l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
