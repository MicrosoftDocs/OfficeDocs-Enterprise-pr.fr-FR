---
title: "Désactiver l’accès aux services Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explique comment utiliser Office 365 PowerShell pour désactiver l’accès aux services Office 365 pour les utilisateurs de votre organisation."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Désactiver l’accès aux services Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour désactiver l’accès aux services Office 365 pour les utilisateurs de votre organisation.
  
Lorsqu’un compte Office 365 est affecté une licence à partir d’un plan de gestion des licences, services Office 365 sont accessibles à l’utilisateur de cette licence. Toutefois, vous pouvez contrôler les services Office 365 que l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès à SharePoint Online, vous pouvez désactiver l’accès. En fait, vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès à n’importe quel nombre de services pour :

- un compte individuel ;
    
- un groupe de comptes ;
    
- tous les comptes de votre organisation.
    
## <a name="before-you-begin"></a>Avant de commencer
<a name="RTT"> </a>

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- L’applet de commande **Get-MsolAccountSku** vous permet d’afficher vos plans de gestion des licences disponibles et les services Office 365 disponibles de ces plans. Pour plus d’informations, voir [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Pour voir l’avant et après les résultats des procédures de cette rubrique, reportez-vous à la section [Afficher les détails de licences et le service de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Un script PowerShell est disponible qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation d’Office 365, y compris de balancement. Pour plus d’informations, consultez [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le paramètre _All_ , seuls les comptes de 500 utilisateur premier sont retournés.
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>Services Office 365 spécifiques pour des utilisateurs spécifiques pour un seul plan de gestion des licences
  
Pour désactiver un ensemble spécifique de services Office 365 pour les utilisateurs à partir d’un seul plan de gestion des licences, effectuez les opérations suivantes :
  
1. Identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office Online et SharePoint Online dans le plan de licence nommé `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilisez l’objet **LicenseOptions** à partir de l’étape 1 sur un ou plusieurs utilisateurs.
    
  - Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    L’exemple suivant crée un nouveau compte pour Allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Pour plus d’informations sur la création de comptes d’utilisateurs dans Office 365 PowerShell, voir [créer les comptes d’utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence, spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK**), puis exécutez les commandes suivantes :
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
  - **Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    L’exemple suivant désactive les services pour les utilisateurs du service des ventes aux États-Unis.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Utilisation d’une liste de comptes spécifiques** Pour ce faire, effectuez les opérations suivantes :
    
1. Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    Dans cet exemple, le fichier texte est C:\\Mes Documents\\Accounts.txt.
    
2. Exécutez la commande suivante :
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, consultez [désactivation de l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>Services Office 365 spécifiques pour les utilisateurs de tous les plans de gestion des licences
  
Pour désactiver des services Office 365 pour les utilisateurs dans tous les plans de gestion des licences disponibles, effectuez les opérations suivantes :
  
1. Copiez et collez ce script dans le bloc-notes.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. Personnalisez les valeurs suivantes pour votre environnement :
    
  -  _<UndesirableService>_Dans cet exemple, nous allons utiliser Office Online et SharePoint Online.
    
  -  _<Account>_Dans cet exemple, nous allons utiliser belindan@litwareinc.com.
    
    Le script personnalisé ressemble à ceci :
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Enregistrez le script en tant que `RemoveO365Services.ps1` dans un emplacement facile à trouver. Pour cet exemple, nous allons enregistrer le fichier sous `C:\\O365 Scripts`.
    
4. Exécutez le script dans Office 365 PowerShell à l’aide de la commande suivante.
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Pour inverser les effets d’une de ces procédures (c'est-à-dire pour réactiver les services désactivés), exécuter la procédure, mais utiliser la valeur de `$null` pour le paramètre _DisabledPlans_ .
  
[Retour au début](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>Tous les services Office 365 pour tous les utilisateurs pour un seul plan de gestion des licences
 
Pour désactiver tous les services Office 365 pour tous les utilisateurs dans un plan de gestion des licences spécifique, spécifiez le nom de plan licence pour $acctSKU (par exemple, **litwareinc:ENTERPRISEPACK**) et puis exécutez ces commandes dans la fenêtre de commande PowerShell :

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-Content.](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Nouvelle-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Ensemble-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

