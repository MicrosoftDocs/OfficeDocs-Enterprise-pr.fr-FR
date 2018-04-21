---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
ms.openlocfilehash: ce8e8c26e929132a8d4beb0f71e18c127064acbe
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
  
Gestionnaire de licences des comptes d’utilisateurs dans Office 365 est important, car les utilisateurs ne peuvent pas utiliser des services Office 365 jusqu'à ce que son compte a été concédé sous licence. Vous pouvez utiliser Office 365 PowerShell à attribuer efficacement des licences à des comptes sans licence, en particulier de plusieurs comptes. 

## <a name="before-you-begin"></a>Avant de commencer
<a name="RTT"> </a>

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- L’applet de commande **Get-MsolAccountSku** permet d’afficher les plans de gestion des licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et les services, reportez-vous à la section [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Pour rechercher les comptes sans licence dans votre organisation, exécutez la commande`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Vous pouvez attribuer des licences qu’aux comptes utilisateurs qui ont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, US pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, consultez [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez la commande `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Pour définir la valeur de **UsageLocation** sur un compte, utilisez la syntaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Par exemple, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le `-All` paramètre, seuls les 500 premiers comptes de sont retournés.
    
## <a name="the-short-version-instructions-without-explanations"></a>La version courte (instructions sans explications)
<a name="ShortVersion"> </a>

Cette section présente les procédures sans explications détaillées. Si vous avez des questions ou souhaitez plus d’informations, vous pouvez lire le reste de la rubrique.
  
Pour attribuer une licence à un utilisateur, utilisez la syntaxe suivante dans Office 365 PowerShell :
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple assigne une licence à partir de la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) le plan licence à l’utilisateur sans licence `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à plusieurs utilisateurs sans licence, utilisez la syntaxe suivante :
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 2^31 (****2 milliards de termes)
  
- Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences.
    
- Si vous n’avez pas assez de licences disponibles, les licences sont attribuées aux utilisateurs dans l’ordre dans lequel ils sont renvoyés par l’applet de commande **Get-MsolUser** jusqu'à épuisement des licences disponibles.
    
Cet exemple affecte les licences à partir de la `litwareinc:ENTERPRISEPACK` plan de gestion des licences (Office 365 entreprise E3) à tous les utilisateurs sans licence.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

Dans cet exemple, les mêmes licences sont attribuées à des utilisateurs sans licence du département des ventes aux États-Unis.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>La version longue (instructions avec des explications détaillées)
<a name="LongVersion"> </a>

Comme indiqué dans l’article [permet d’afficher les utilisateurs sous licence et sans licence avec Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), il est possible que les utilisateurs qui disposent d’un compte utilisateur valide Office 365, mais qui n’ont pas reçu d’une licence d’Office 365. Cela signifie que, compte valide ou aucun compte valide, ces utilisateurs ne sera pas en mesure de se connecter à Office 365. Et si vous ne pouvez pas vous connecter, vous ne pouvez pas tirer parti des services Office 365.
  
L’article susmentionné indique également que nous pouvons renvoyer une liste de comptes d’utilisateurs sans licence en exécutant la commande suivante :
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Cette commande renvoie des informations sur les utilisateurs qui ne sont pas actuellement une licence pour Office 365 :
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Comme vous pouvez le voir, nous avons un utilisateur sans licence : Belinda Newman. Par conséquent, comment nous faire sur l’attribution d’une licence Office 365 Belinda ?
  
Pour commencer, nous allons exécuter l’applet de commande **Get-MsolAccountSku** décrit dans l’article [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):
  
```
Get-MsolAccountSku
```

Cette commande renvoie des données semblables à ceci :
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

Pourquoi nous exécuter **Get-MsolAccountSku** ? (« Référence », dans le cas où vous vous poseriez la question, est abréviation de « unité de stock ». Pour nos besoins, qui est simplement business-parlent de « produit ».) Il existe deux raisons pourquoi nous avons exécuté **Get-MsolAccountSku**. Nous devons tout d’abord, assurez-vous que nous disposons d’une licence pour affecter des Belinda. Nous disposons de toutes les licences que nous pouvons affecter ? Pour déterminer, nous prendre la valeur de propriété **d’ActiveUnits** (25) et de soustraire les valeurs des propriétés de **ConsumedUnits** (24) et **WarningUnits** (0) :
  
 `25 - 0 - 24 = 1`
  
La propriété **ActiveUnits** indique le nombre de licences que nous avons acheté, et que la valeur combinée de **WarningUnits** et de **ConsumedUnits** nous indique de combien de licences est en cours d’utilisation. Il faut soustraire le nombre de licences déjà parlé pour le nombre de licences que nous avons achetés, nous de savoir combien de licences est toujours disponibles. Comme vous avez de la chance, nous avons une licence disponible pour distribution :
  
 `25 - 0 - 24 = 1`
  
La seconde, pour affecter à Belinda une nouvelle licence, nous avons besoin de connaître le nom de notre plan de gestion des licences (autrement dit, nous devons savoir **AccountSkuId** ). Dans ce cas, c’est très simple : nous avons un seul plan de gestion des licences ( `litwareinc:ENTERPRISEPACK`). Notez, toutefois, qu’il est possible qu’une organisation dispose de plusieurs plans de gestion des licences. Dans ce cas, **Get-MsolAccountSku** renvoie différentes deux **AccountSkuIds**, et vous devez choisir le programme de licence approprié lors de l’attribution des licences. Pour le moment, cependant, nous allons Coller avec le cas le plus simple et supposons que nous avons qu’un seul plan de gestion des licences.
  
Alors comment *allons* nous affecter Belinda Newman une nouvelle licence ? Comme ça :
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

C’est également vous faire : il suffit d’appeler l’applet de commande **Set-MsolUserLicense** , assurez-vous que vous spécifiez le paramètre _UserPrincipalName_ pour l’utilisateur et le programme de licence approprié.
  
Lorsque **Set-MsolUserLicense** est terminée, vous verrez quelque chose similaire à celui-ci à l’écran :
  
 `PS C:\windows\system32>`
  
En d’autres termes, il ne s’affiche que quelque chose s’est produit. Pour vérifier qu’une licence a été attribuée à l’utilisateur, exécutez une commande semblable à la suivante :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Si tout fonctionne comme prévu, vous devez voir qu’isLicensed propriété de Belinda est maintenant définie à True :
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Bonne question de sécurité, NOTE] : que se passe-t-il si vous commis une erreur et que vous essayez d’attribuer une licence à un utilisateur qui possède déjà une licence ? Finissent vous donner deux licences pour un seul utilisateur ? > La réponse rapide ? N° ; Office 365 ne vous permettent d’assigner plusieurs licences pour le même utilisateur. (, Plusieurs licences dans le plan de gestion des licences, il s’agit.) Si vous essayez de faire votre commande échouera avec le message d’erreur suivant : > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> certes, ce message d’erreur est un petit peu trompeur : la licence n’est pas vraiment non valide, il est simplement assignée à un utilisateur qui déjà *a* une licence. Toutefois, le message d’erreur, l’important est qu’un utilisateur ne vous retrouver avec plusieurs licences.
  
Comme vous venez de voir, il est très facile à utiliser PowerShell de 365 d’Office pour affecter une seule licence à un utilisateur unique. Et ceci nous mène à une question évidente : il ne serait pas aussi simple, peut-être même plus facile d’utiliser le centre d’administration Office 365 pour attribuer une licence unique pour un seul utilisateur ? Eh bien, peut-être ; qui dépend, en partie, si vous êtes le plus à l’aise en utilisant Windows PowerShell ou plus à l’aise en utilisant le centre d’administration Office 365. Lorsque Windows PowerShell s’avère vraiment utile, cependant, est lorsque vous devez attribuer plusieurs licences à plusieurs utilisateurs. Par exemple, cette commande attribue une licence Office 365 à un de vos utilisateurs n’ayant pas déjà une licence :
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Dans la commande précédente, nous avons utiliser **Get-MsolUser** et le paramètre _UnlicensedUsersOnly_ pour renvoyer une collection de tous les comptes d’utilisateur sans licence. Nous passer ensuite cette collection pour l’applet de commande **Set-MsolUserLicense** ; à son tour, **Ensemble-MsolUserLicense** attribue une licence (pris à partir de la `litwareinc:ENTERPRISEPACK` licence plan) à chaque utilisateur dans la collection.
  
AH, mais que se passe-t-il si vous avez 5 utilisateurs sans licence mais qu’une seule licence disponible ? Dans ce cas **Set-MsolUserLicense** donnera lieu à la licence disponible pour le premier utilisateur renvoyé par **Get-MsolUser**. **Ensemble-MsolUserLicense** loyalement tente alors d’attribuer une licence à quatre autres utilisateurs, mais les quatre de ces tentatives échoue avec le message d’erreur suivant :
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
En d’autres termes, MsolUserLicense de l’ensemble n’échoue pas seulement. Au lieu de cela, il affecte des licences autant que possible. Puis il échouera.
  
Nous allons essayer un autre exemple. Vous souhaitez peut-être attribuer une licence à tous les utilisateurs du service des ventes. Pas de problème :
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Ou, si vous voulez vraiment faire cela selon les règles de l’art et que vous souhaitez réduire les messages d’erreur et le traitement informatique au minimum, attribuez une licence à tous les utilisateurs sans licence du département des ventes :
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Après tout, il n’existe aucun point tente de licences les utilisateurs déjà une licence. Comme nous l’avons déjà vu, qui ne fonctionnera pas.
  
Voici un autre exemple. Vous souhaitez peut-être licence tous les utilisateurs qui n’ont actuellement une licence Office 365 aux États-Unis. Dans ce cas :
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Et ainsi de suite.
  
> [!NOTE]
> Combien de temps faut-il pour exécuter une commande, par exemple, émet des licences pour tous les utilisateurs sans licence ? C’est difficile de dire : elle dépend de fait de tout ce qui est du nombre d’utilisateurs dont vous disposez à la vitesse de votre connexion réseau. Si vous avez quelques centaines d’utilisateurs à licence cela contribuera assez rapidement (autrement dit, il ne devrait pas prendre plus d’une minute ou deux). Si vous avez 10 000 utilisateurs autoriser évidemment prendra un peu plus de temps. Mais, loin de constituer tant que qu’il faudrait pour attribuer des licences à 10 000 utilisateurs en utilisant le centre d’administration Office 365. 
  
Tant que nous sommes sur le sujet, c’est quelque chose que vous devez prendre en compte lorsque l’attribution des licences : si un utilisateur n’a pas une valeur pour la propriété **UsageLocation** vous ne pourrez pas lui attribuer une licence Office 365. À la place, vous obtenez un message d’erreur semblable à celui-ci :
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
De manière quelque peu rond-point, de ce message d’erreur indique que l’utilisateur en question n'a pas été affecté un **UsageLocation**. Comme vous l’avez peut-être deviné, la propriété **UsageLocation** (qui indique la région ou du pays où l’utilisateur utilise généralement Office 365) est extrêmement importante. Pourquoi ? C’est parce que les services disponibles à un utilisateur dépendent non seulement le pack de licence que vous avez acheté mais également sur la résidence de l’utilisateur : règles locales et réglementaires, certains services peut-être pas disponibles pour certains utilisateurs. Si un utilisateur ne possède pas une **UsageLocation**, Office 365 n’a aucun moyen de savoir quels services peuvent légalement être exposés à cet utilisateur. Par conséquent, Office 365 n’offrent pas tous les services à l’utilisateur, au moins pas jusqu'à ce que l' **UsageLocation** a été spécifié.
  
> [!NOTE]
> Lorsque vous configurez un compte d’utilisateur vous savez immédiatement s’il existe des restrictions de licence associées à la partie spécifiée du monde. Par exemple, si vous modifiez **UsageLocation** d’un utilisateur sous licence en Iran ( `IR`), la commande échouera avec le message d’erreur : `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> c’est parce que Office 365 n’est pas actuellement disponible pour les utilisateurs en Iran. Pour plus d’informations, consultez [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidemment, Office 365 utilise les codes de pays à deux lettres produites par l’organisation internationale de normalisation (ISO). Vous pouvez trouver ces codes sur le [site web ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Si vous souhaitez vérifier si un utilisateur donné a une **UsageLocation** , vous pouvez utiliser une commande similaire à celle-ci :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

Sinon, vous pouvez retourner une liste de tous les utilisateurs qui n’ont pas une **UsageLocation** à l’aide de cette commande :
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> Lorsque vous attribuez une licence à un utilisateur utilisateur, par défaut, aura accès à tous les services que votre organisation dispose de l’accès à Office 365. Par exemple, si vous avez acheté des licences pour Office 365 entreprise E3, votre utilisateur nouvellement disposant d’une licence sera automatiquement avoir accès aux services Exchange Online, Skype pour Business Online et SharePoint Online. Si vous préférez limiter l’accès d’un utilisateur à ces services (par exemple, vous souhaitez un utilisateur d’accéder à SharePoint Online, mais *pas* à Exchange Online et Skype pour Business Online) puis consultez l’article [, désactivation de l’accès aux services avec Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Voir aussi
<a name="SeeAlso"> </a>

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Ensemble-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

