---
title: "Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell"
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui a été précédemment affectés aux utilisateurs."
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui a été précédemment affectés aux utilisateurs.
  
## <a name="before-you-begin"></a>Avant de commencer

- Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Pour afficher les informations de licence plan ( **AccountSkuID** ) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Afficher les détails de service et de licence de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le _-tous les_ paramètre, seuls les 500 premiers comptes de sont retournés.
    
## <a name="the-short-version-instructions-without-explanations"></a>La version courte (instructions sans explications)
<a name="ShortVersion"> </a>

Cette section présente les procédures sans explication superflue ou alambiquée. Si vous avez des questions ou que vous souhaitez plus d'informations, vous pouvez lire le reste de la rubrique.
  
Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Cet exemple supprime la `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir du compte d’utilisateur BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Pour supprimer des licences d’un groupe d’utilisateurs sous licence existants, appliquez l’une des méthodes suivantes :
  
- **Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Cet exemple supprime la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) des licences de tous les comptes d’utilisateurs dans le service des ventes aux États-Unis.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Utilisation d’une liste de comptes spécifiques** Pour ce faire, effectuez les opérations suivantes :
    
1. Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilisez la syntaxe suivante :
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Cet exemple supprime la `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir des comptes d’utilisateur défini dans le fichier texte C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Pour supprimer des licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Cet exemple supprime la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) licence tout sous licence des comptes d’utilisateurs.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>La version longue (instructions avec des explications détaillées)
<a name="LongVersion"> </a>

Rien ne dure toujours, et qui inclut des licences Office 365 : tôt ou tard, il arrivera un moment lorsque vous devez supprimer une licence d’un compte d’utilisateur. Peut-être que l’utilisateur va sur le congé ; peut-être l’utilisateur n’a plus besoin de la licence ; peut-être - il y a évidemment autant de raisons pourquoi vous pouvez souhaiter supprimer une licence utilisateur.
  
Avant d’aller plus loin qu’il est important de noter que la suppression d’une licence, vous devez, bien, supprimez la licence : la désactivation de tous les services sur une licence n’est pas la même chose que la suppression d’une licence. Par exemple, supposons que nous avons utilisé notre licences Office 365 ; en d’autres termes, nous n’avons pas de licences disponibles que ce soit. Vous décidez de suivre la procédure de [désactivation de l’accès aux services Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) pour désactiver tous les services, par exemple, sur le compte de le de Belinda Newman. Après cela, combien de licences va nous disposons nous ? C’est ça : zéro. Oui, la procédure de cette rubrique va *désactiver* tous les services sur les licences de Belinda, mais il ne désactivera pas (c.-à-d. de supprimer) la licence elle-même. La licence sera toujours valide et elle restera affectée à Belinda Newman. Elle ne sera uniquement en mesure d’utiliser cette licence pour accéder aux services Office 365.
  
Et c’est important : Si vous souhaitez supprimer une licence d’un utilisateur, vous devez *Supprimer* la licence. La désactivation de tous les services empêche l’utilisateur de se connecter à Office 365, mais il ne libérer la licence sa. Si vous souhaitez reprendre une licence qui est actuellement affectée à un utilisateur, que vous devez exécuter une commande semblable à celle-ci, une commande qui utilise le paramètre _RemoveLicenses_ pour supprimer réellement la licence précédemment attribuée à Belinda :
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Exécutez cette commande, et Belinda Newman est n’est plus accordée pour utiliser Office 365.
  
> [!NOTE]
> Comme vous pouvez le voir, lorsque vous utilisez le paramètre _RemoveLicenses_ , que vous devez spécifier le nom de la licence à supprimer. Si vous ne savez pas quel plan de gestion des licences utilisé pour attribuer une licence à l’utilisateur, il suffit d’exécuter une commande comme suit :`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Pour vérifier que la licence a vraiment été supprimée, utilisez la commande Get-MsolUser pour vérifier le compte de l’utilisateur en question :
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Si tout se déroule conformément au plan, propriété **d’isLicensed** de Belinda est maintenant fixée à `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Un autre moyen de libérer une licence est en supprimant le compte utilisateur. Pour plus d’informations, voir [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Voir aussi

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Création de comptes d'utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Get-Content.](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Ensemble-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

||
|:-----|
|![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les [professionnels de l’informatique et les administrateurs d’Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), proposée par formation de LinkedIn. |
   

