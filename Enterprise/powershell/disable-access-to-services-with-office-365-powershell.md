---
title: "Désactiver l’accès aux services Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explique comment utiliser Office 365 PowerShell pour ajouter ou supprimer l’accès aux services Office 365 pour les utilisateurs de votre organisation."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Désactiver l’accès aux services Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour ajouter ou supprimer l’accès aux services Office 365 pour les utilisateurs de votre organisation.
  
Lorsqu’un compte Office 365 est affecté une licence à partir d’un plan de gestion des licences, services Office 365 sont accessibles à l’utilisateur de cette licence. Toutefois, vous pouvez contrôler les services Office 365 que l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès à SharePoint Online, vous pouvez désactiver l’accès. En fait, vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès à n’importe quel nombre de services pour :
- un compte individuel ;
    
- un groupe de comptes ;
    
- tous les comptes de votre organisation.
    
 **Contenu :** [La version courte (instructions sans explications)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [La version longue (avec des explications détaillées sur les instructions)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Voir aussi](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Avant de commencer
<a name="RTT"> </a>

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- L’applet de commande **Get-MsolAccountSku** vous permet d’afficher vos plans de gestion des licences disponibles et les services Office 365 disponibles de ces plans. Pour plus d’informations, voir[Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Pour voir l’avant et après les résultats des procédures de cette rubrique, reportez-vous à la section [Afficher les détails de licences et le service de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Un script PowerShell est disponible qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation d’Office 365, y compris de balancement. Pour plus d’informations, consultez [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.
    
## <a name="the-short-version-instructions-without-explanations"></a>La version courte (instructions sans explications)
<a name="ShortVersion"> </a>

Cette section présente les procédures sans explication superflue ou alambiquée. Si vous avez des questions ou que vous souhaitez plus d'informations, vous pouvez lire le reste de la rubrique.
  
Pour désactiver les services Office 365 pour les utilisateurs à partir d’un seul plan de gestion des licences, effectuez les opérations suivantes :
  
1. Identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Cet exemple crée un objet **LicenseOptions** qui désactive les services Office Online et SharePoint Online dans le plan de licence nommé `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilisez l’objet **LicenseOptions** à partir de l’étape 1 sur un ou plusieurs utilisateurs.
    
  - Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    Cet exemple crée un compte pour Allie Bellew qui attribue la licence et désactive les services décrits à l’étape 1.
    
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

  - Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence, spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK** ), puis exécutez les commandes suivantes :
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
  - **Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    Cet exemple désactive les services pour des utilisateurs du service des ventes aux États-Unis.
    
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
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, consultez [désactivation de l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).
  
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

3. Enregistrez le script en tant que `RemoveO365Services.ps1` dans un emplacement facile à trouver. Pour cet exemple, nous allons enregistrer le fichier sous " `C:\\O365 Scripts`«.
    
4. Exécutez le script dans Office 365 PowerShell à l’aide de la commande suivante.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Pour inverser les effets d’une de ces procédures (c'est-à-dire pour réactiver les services désactivés), exécuter la procédure, mais utiliser la valeur de `$null` pour le paramètre _DisabledPlans_ .
  
[Retour au début](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>La version longue (instructions avec des explications détaillées)
<a name="LongVersion"> </a>

Par défaut, tous les services sont activés lorsque vous émettez une licence à l’aide d’Office 365 PowerShell. Et c’est souvent une bonne chose : cela signifie que vous pouvez rapidement et facilement attribuer des licences aux utilisateurs sans avoir à spécifier que chaque service soit activé tout au long du processus.
  
Cela dit, toutefois, il est également vrai que vous pouvez souhaiter restreindre les services disponibles à certains de vos utilisateurs ; par exemple, peut-être que certains utilisateurs doivent accéder à Office Professionnel Plus, Skype pour Business Online et Exchange Online, mais ces mêmes utilisateurs ne devraient pas avoir accès à SharePoint Online ou sur Office Online. Vous pouvez restreindre comptes de cette manière ? En fait, vous pouvez. Pour expliquer comment cela fonctionne, prenons une approche en deux étapes pour la résolution de ce problème :
  
1. Attribuer à l’utilisateur une licence Office 365 qui active automatiquement tous les services.
    
2. Exécutez les deux commandes d’Office 365 PowerShell qui désactivent des services spécifiés pour cet utilisateur.
    
Nous avons déjà prise en charge de l’étape 1 : notre (Belinda Newman) de l’utilisateur possède une licence de Office 365 qui lui permet d’accéder à tous les services d’Office 365. Toutefois, nous voulons modifier les comptes de Belinda afin qu’elle n’a pas accès à SharePoint Online ( `SHAREPOINTENTERPRISE`) ou d’Office Online ( `SHAREPOINTWAC`). Mais comment sommes-nous censés le faire ?
  
Voici comment. Dans un premier temps, nous allons utiliser l’applet de commande **New-MsolLicenseOptions** pour créer un objet **LicenseOption** qui contient les services que nous désactivés. Dans les cas de Belinda, nous voulons désactiver `SHAREPOINTENTERPRISE` et `SHAREPOINTWAC`, de sorte que nous utilisons cette commande :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Voyez comment cela fonctionne ? Vous spécifiez le plan de gestion des licences ( `litwareinc:ENTERPRISEPACK`), puis indiquez chacun des services que vous souhaitez désactivés, la séparation de ces services à l’aide de virgules.
  
> [!NOTE]
> Assurez-vous que vous stockez votre nouvel objet **LicenseOption** dans une variable. Dans l’exemple précédent, nous avons utilisé `$x`, bien que vous pouvez utiliser n’importe quel nom de variable valide de Windows PowerShell. 
  
À ce stade, nous pouvons utiliser la commande suivante pour désactiver l’accès de Belinda à deux services :
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Rien de trop fantaisiste ici, soit : nous il vous suffit d’appeler l’applet de commande **Set-MsolUserLicense** et inclure le paramètre _LicenseOptions_ , ainsi que la variable ( `$x`) contenant les plans que vous souhaitez désactiver. Et ce qui nous maintenant si nous jetons un coup de œil sur les informations de licence de Belinda en exécutant la commande : `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Nous voir ceci :
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Sympa, non ? Et, bien sûr, nous pouvions faire cette même chose à plusieurs utilisateurs si nous le voulions. Par exemple, ces commandes de désactiver les deux mêmes services pour tous les utilisateurs sous licence. Spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK** ), puis les exécuter.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Gardez à l’esprit que Belinda a toujours une licence Office 365 ; Il est qu’à présent elle a accès à moins de services. Avant que nous avons désactivé les deux services, Belinda a eu accès à SharePoint, les OneDrive et les échanges de News en ligne sites :
  
![Utilisateur avec accès à SharePoint.](images/o365_powershell_with_sharepoint.png)
  
Maintenant, elle ne dispose plus de ces options :
  
![Utilisateur sans accès à SharePoint.](images/o365_powershell_without_sharepoint.png)
  
C’est exactement le résultat que nous attendions.
  
Et que se passe-t-il si nous changeons d’avis plus tard : il est possible de réactiver ces services ? Absolument. Pour réactiver tous les services pour un utilisateur, il vous suffit d’utiliser cette commande pour créer l’objet **LicenseOption** suivant :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Que fait cette commande ? Pour commencer, la constante Windows PowerShell `$null` signifie « rien ». (Ou, dans la langue du contact technique légèrement plus, cela signifie une « valeur null ».) Comme vous vous rappelez, lorsque nous utilisons la cmdlet **New-MsolLicenseOptions** nous avons indiquer les services que nous souhaitons que désactivé. Dans ce cas, nous ne voulons pas les services à désactiver. Qui peut vous amener à penser que nous pourrions utiliser une commande similaire à la suivante, une commande où nous ne spécifiez pas de valeur pour le paramètre _DisabledPlans_ :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

Toutefois, qui ne fonctionnera pas. Au lieu de cela, il génère un message d’erreur :
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
Heureusement pour nous, affectant la valeur du paramètre `$null` fonctionne :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Cela signifie simplement que, lorsque nous exécutons l’applet de commande **Set-MsolUserLicense** , nous allons indiquant **Ensemble-MsolUserLicense** que nous ne souhaitez pas Belinda pour que les services désactivés :
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Logiquement, si aucun des services n’est désactivé, cela signifie que tous les services sont activés.
  
Maintenant que vous comprenez comment tout cela fonctionne, nous allons vous montrer comment vous pouvez émettre une licence et désactiver les services spécifiés et avec la même commande. Qui semble assez impressionnant, mais, pour être honnête, il est vraiment très simple : vous suffit de l’ajouter à la fois _AddLicenses_ et les paramètres de _LicenseOptions_ dans la même commande. En d’autres termes, vous créez tout d’abord votre objet **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Et puis, comme indiqué précédemment, vous utilisez à la fois les _AddLicenses_ et les paramètres _LicenseOptions_ dans votre commande :
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Que commande émettra Belinda Newman une nouvelle licence, mais une licence dans le Skype pour Business Online ( `SHAREPOINTWAC`) et SharePoint Online ( `SHAREPOINTENTERPRISE`) sont tous les deux désactivés.
  
[Retour au début](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?
<a name="LongVersion"> </a>

||
|:-----|
|![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les **professionnels de l’informatique et les administrateurs d’Office 365**, proposée par formation de LinkedIn. |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-Content.](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Nouvelle-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Nouvelle-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Ensemble-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[Retour au début](disable-access-to-services-with-office-365-powershell.md#RTT)
  

