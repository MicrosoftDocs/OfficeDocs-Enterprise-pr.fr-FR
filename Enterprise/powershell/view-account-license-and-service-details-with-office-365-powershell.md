---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été affectées aux utilisateurs.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Afficher les détails de service et de licence de compte avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été affectées aux utilisateurs.
  
Dans Office 365, les licences à partir de plans de gestion de licences (également appelé SKU ou Office 365 plans) donner aux utilisateurs d’accéder aux services Office 365 définies pour ces plans. Toutefois, un utilisateur ne peut pas avoir accès à tous les services qui sont disponibles dans une licence qui leur est actuellement assignée. Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur des comptes d’utilisateurs. 

## <a name="before-you-begin"></a>Avant de commencer
<a name="RTT"> </a>

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Utilisez les commandes `Get-MsolAccountSku` et `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` pour trouver les informations suivantes :
    
  - Plans de gestion de licences disponibles dans votre organisation.
    
  - Services disponibles dans chaque plan de gestion de licences et l’ordre dans lequel ils sont répertoriés (numéro d’index).
    
     Pour plus d’informations sur les licences de plans, de licence et de services, voir [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Utilisez la commande `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` pour rechercher les licences attribuées à un utilisateur et l’ordre dans lequel ils sont répertoriés (le numéro d’index).
    
- Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>La version courte (instructions sans explications)

Pour afficher tous les services Office 365 PowerShell auxquelles un utilisateur a accès, utilisez la syntaxe suivante :
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Cet exemple montre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Affiche les services qui sont associés à toutes les licences sont attribuées à son compte.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Pour rechercher tous les utilisateurs sous licence qui ont été activés ou désactivés pour des services spécifiques, utilisez la syntaxe suivante :
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

Ces exemples utilisent les informations suivantes :
  
- La licence qui permet d’accéder aux services Office 365 qui nous intéresse est la première qui est affecté à tous les utilisateurs (le numéro d’index est égal à 0).
    
- Les services Office 365 qui nous intéressent sont Skype pour Business Online et Exchange Online. Pour les licences associées avec le plan de gestion des licences, Skype pour Business Online est le service 6 (le numéro d’index est 5), et Exchange Online est le service 9e répertoriés (le numéro d’index est 8).
    
Cet exemple renvoie tous les titulaires qui sont activés pour Skype pour Business Online et Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Cet exemple retourne tous les utilisateurs sous licence qui ne sont pas activés pour Skype pour Business Online ou Exchange en ligne.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>La version longue (instructions avec des explications détaillées)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Rechercher des services Office 365 PowerShell auxquelles un utilisateur a accès

Il est évidemment important de savoir quels utilisateurs ont été des licences Office 365 et les utilisateurs qui n’ont pas. (Voir l’article [Afficher les utilisateurs sous licence ou non avec Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) pour plus d’informations). Toutefois, simplement disposer d’une licence de Office 365 ne vous indique pas quoi que ce soit sur ce que cet utilisateur peut réellement faire avec Office 365. Il permet de Exchange Online ou Skype pour entreprise en ligne ? Cet utilisateur peut accéder à SharePoint Online ? Il a accès à Office Professionnel Plus ? Disposer d’une licence signifie simplement que l’utilisateur a la possibilité d’accéder à ces services. Toutefois, les fonctionnalités disponibles à un utilisateur dépendent des services qui ont été activées sur la licence sa.
  
Comment pouvons-nous nous déterminer les fonctionnalités d’Office 365 un utilisateur a accès à ? Pour effectuer une opération que nous avons besoin exécuter une commande similaire à celui-ci :
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

Dans cette commande, nous utilisons la cmdlet **Get-MsolUser** pour renvoyer des informations sur le compte BelindaN@litwareinc.com. Une fois que nous avons renvoyé ces informations, nous les données de compte vers la cmdlet **Select-Object** de tuyau et demander **Select-Object** « développer » la valeur de la propriété de **licences** :
  
 `Select-Object -ExpandProperty Licenses`
  
Pourquoi faisons-nous cela ? Ainsi, par défaut les **licences** de propriété uniquement nous indique le nom de la licence pack d'où proviennent les licences de Belinda :
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

« Extension » de la propriété de **licences** nous donne un peu plus d’informations :
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

Et puis en développant la propriété de **l’état du service** nous pouvons obtenir encore plus d’informations :
  
|Plan de service ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
> [!NOTE]
> Vous dites qui est trop tapant ? De même, si vous pouvez placer avec un peu obtuseness de Windows PowerShell, vous pouvez exécuter cette version condensée de la commande à la place : >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
Dans le cas où vous vous poseriez la question, nous pouvons « développer » la propriété **licences** **licences** étant une propriété à valeurs multiples : il s’agit d’une seule propriété qui peut stocker plusieurs valeurs. Nous allons développer une valeur de propriété que nous avons simplement le détail obtenir ces valeurs supplémentaires qui, par défaut, ne sont pas affichées à l’écran.
  
> [!NOTE]
> Comment êtes-vous supposé savoir qu’une valeur est une propriété à valeurs multiples ? Ainsi, pour trouver des, essayez exécutant une commande similaire à celle-ci : > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> la cmdlet **Get-member** renvoie des informations sur l’objet lui-même ; Dans ce cas, les informations sur la propriété valeurs constituant un objet compte d’utilisateur. Voici ce que **Get-Member** a à dire sur la propriété de **licences** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Si la définition de propriété disant quelque chose sur les collections (dans ce cas, `System.Collections.Generic.List`) vous savez que vous avez affaire à une propriété à valeurs multiples. 
  
Ainsi que tout cela signifie-t-il ? Pour répondre à cette question, nous allons tout d’abord examiner une nouvelle les informations retournées par l’applet de commande **Get-MsolUser** :
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

Et également Examinons un un tableau expliquant ce que ces plans de service de façon étrange nommé représentent vraiment :
  
|Plan de service ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Compris ?  `MCOSTANDARD` est simplement un nom de programmation interne de Skype pour Business Online, tandis que `OFFICESUSBCRIPTION` est simplement le nom de programmation interne pour Office Professionnel Plus. Il n’est pas la chose la plus intuitive dans le monde, mais tant que vous gardez cette table pratique vous n’aurez pas beaucoup de problèmes lorsqu’il s’agit de travailler avec les services d’Office 365.
  
Mais attendez : il est plus. Comme nous l’avons appris dans l’article, [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), si la **ProvisioningStatus** est définie sur `Success` qui signifie que le service a été entièrement activé ; par exemple si `MCOSTANDARD` est défini sur `Success` qui signifie que l’utilisateur peut accéder à Skype pour l’activité en ligne. Si la **ProvisioningStatus** est définie sur `PendingInput` qui signifie que Office 365 est toujours traitement de la demande de service ; Toutefois, l’utilisateur peut en général une session et accéder au service, tandis que la demande termine le traitement. ( `YAMMER_ENTERPRISE` sont toujours affichés en tant que `PendingInput`, mais c’est OK : qui n’empêchera pas un utilisateur de se connecter à Yammer).
  
> [!IMPORTANT]
> Les utilisateurs peuvent installer et activer une nouvelle installation d’Office Professionnel Plus lors de la `OFFICESUBSCRIPTION` dans les `PendingInput` état.
  
Et, en soi, est un service est défini sur `Disabled` qui signifie que le service en question n’est pas disponible pour l’utilisateur.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Rechercher les utilisateurs qui ont accès à des services Office 365 PowerShell spécifiques

Dans un autre article, nous avons vu comment vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès utilisateur aux services. (Si vous avez manqué de cet article, reportez-vous à la section [désactiver l’accès aux services Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Qui mène à une question évidente : existe-t-il un moyen pour déterminer quels *utilisateurs* (c'est-à-dire, plusieurs utilisateurs) ont les services activé ou désactivé ?
  
Nous étions en espérant que quelqu'un demande qui. Pour répondre à cette question, examinons le tableau des services que nous avons d’abord étudiés dans l’article [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) pour notre plan de licence disponible uniquement `litwareinc:ENTERPRISEPACK`:
  
|Plan de service ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Comme vous vous en souvenez peut-être, le plan de service n’est rien de plus que le nom de programmation interne pour un produit ; par exemple, `OFFICESUBSCRIPTION`, au nom d’un, est le nom de programmation interne d’Office Professionnel Plus. Si `OFFICESUBSCRIPTION` s’affiche en tant que `SUCCESS` sur le plan de service d’un utilisateur, puis qui signifie que l’utilisateur est autorisé à accéder à Office Professionnel Plus. Si `EXCHANGE_S_ENTERPRISE` est répertorié en tant que `DISABLED` qui signifie que l’utilisateur ne peut pas utiliser Exchange Online.
  
> [!IMPORTANT]
> Les utilisateurs peuvent installer et activer une nouvelle installation d’Office Professionnel Plus lors de la `OFFICESUBSCRIPTION` dans les `PendingInput` état.
  
Est maintenant le moment où l’ordre dans lequel apparaissent les services est extrêmement importante. Windows PowerShell attribue un numéro d’index à chaque entrée de la liste. La première entrée est 0, l’entrée suivante est 1 et ainsi de suite. Les résultats sont expliqués dans le tableau suivant :
  
|Numéro d’index de ***|Plan de service ***|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Comme vous pouvez le voir, `SWAY` est le premier service répertorié, afin qu’il soit affecté de numéro d’index 0.
  
> [!CAUTION]
> Pourquoi 0 et non 1 ? C’est une chose de programmation. Dans les langages de programmation indices indiquent où un élément est « décalage » à partir du début du tableau. Le premier élément *est* le début du tableau, son décalage est donc 0. Le deuxième élément est 1 élément à partir du début du tableau, son décalage est donc 1.
  
Nous allons essayer un exemple. Supposons que nous aimerions une liste de tous les utilisateurs sous licence qui n’ont pas été activé pour Exchange Online. Pour ce faire, nous pouvons utiliser la commande suivante :
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Certes, qui est une aspect énigmatiques petite commande, donc prenez une minute pour expliquer comment il fonctionne. Il s’agit en fait d’une commande de deux parties, et la première partie est très simple : nous utilisons la cmdlet **Get-MsolUser** pour renvoyer une collection de tous les utilisateurs de notre Office 365 (sous licence ou non) :
  
```
Get-MsolUser
```

Cette information est ensuite transmise à la cmdlet **Where-Object** . **Where-Object** passe par tous les comptes d’utilisateur et de recherche pour ces comptes qui répondent aux deux critères suivants :
  
- La propriété **isLicensed** est égale à ( `-eq`) `True` ( `$true`). Qui nous permet d’éliminer les utilisateurs sans licence.
    
- La valeur des licences **[0]. État du service [8]. ProvisioningStatus** propriété est égale à ( `-eq`) `Disabled`. Pour nos besoins immédiats, la partie importante de ce nom de propriété complexe est la suivante :
    
     `ServiceStatus[8]`
    
    Le `[8]` représente le numéro d’index pour Exchange Online. (Nous savons que d’après la table il y a quelques minutes). Que se passe-t-il si nous souhaitons rechercher tous les utilisateurs activés pour Skype pour entreprise en ligne ? Ainsi, le numéro d’index pour Skype pour Business Online est 5, nous utiliserait la syntaxe suivante :
    
     `ServiceStatus[5]`
    
    Etc., etc.
    
    Incidemment, `Licenses[0]` indique le plan de gestion des licences qui nous intéressent. Étant donné que notre domaine de test n’a qu’un seul plan de gestion des licences Cela importe peu. Mais supposons que nous avons un utilisateur qui a été attribué des licences à partir de deux plans de licences différents. Dans ce cas, `Licenses[0]` représenterait le premier plan de gestion des licences, et `Licenses[1]` représenterait le deuxième plan de licence.
    
    Pour rechercher les licences attribuées à un utilisateur et l’ordre dans lequel elles sont répertoriées, exécutez la commande suivante :
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

Vous voyez comment tout cela fonctionne ? Le numéro d’index d’Office Professionnel Plus est 4 ; Par conséquent, cette commande renvoie une liste de tous les utilisateurs qui n’ont pas été activées pour Office Professionnel Plus :
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

Et si nous voulions une liste d’utilisateurs qui ont été *activés* pour Office Professionnel Plus ? Ainsi, si vous avez été activé votre **état du service** sera `PendingInput` ou `Success`; en d’autres termes, votre **état du service** sera *pas* égaux ( `-ne`) `Disabled`. Cela signifie que tout ce que nous devons faire est de prendre notre commande précédente et permuter les `-eq` opérateur pour le `-ne` opérateur :
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Comme on passe, que code ne probablement gagner de nombreux concours de beauté. Et vérité informé, le code peut obtenir encore plus compliquée. Par exemple, supposons que nous voulons rechercher les utilisateurs qui ont été activés pour les deux Skype pour Business Online et Exchange Online :
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Mais ne vous inquiétez pas trop sur comment plus compliqué qui peut se présenter : l’important est que, avec relativement peu d’effort, vous pouvez récupérer ces informations. Ne peut pas obtenir cette même information à l’aide du centre d’administration de l’Office 365 ? En théorie, Oui mais, en pratique, non. Pour obtenir cette même information à l’aide du centre d’administration de l’Office 365, vous devez consulter les informations de licence pour chaque utilisateur, un seul utilisateur à la fois, et puis manuellement effectuer le suivi de qui a été activé pour *X* et qui n’avaient pas. Qui fonctionnent, mais soyons honnêtes : Si vous avez des utilisateurs de plus de 10 ou 11, vous n’allez pas à effectuer cette opération. Il est bien trop longues et laborieuses.
  
Qui, bien sûr, est pourquoi nous devons Windows PowerShell : Windows PowerShell vous économisez des tâches longues et laborieuses que.
  
Voici un exemple de commande pour consulter des informations de service pour un ensemble spécifié de services identifiés par leur index de licences et l’état du service pour un abonnement à Office 365 E5 :
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

Cette commande crée un fichier CSV pour afficher tous les utilisateurs ainsi que leur état de service pour un ensemble spécifié de services (équipes de Yammer, AD RMS, OfficePro, Skype, SharePoint et Exchange).

>[!Note]
>Vous pouvez obtenir la liste des services pour un abonnement à partir de la `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` commande. Dans la sortie, vous commencez la numérotation de l’index de service avec la valeur 0. La commande ci-dessus est qu’un exemple. Les numéros d’index des services peut changer avec le temps.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>Voir aussi

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]