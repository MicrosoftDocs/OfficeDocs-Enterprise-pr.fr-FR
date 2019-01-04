---
title: Afficher des comptes d’utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Résumé : Permet d’afficher, de liste ou d’afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.'
ms.openlocfilehash: dc33b64207341576968867fbeea6f211034eeca6
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546525"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Afficher des comptes d’utilisateur avec Office 365 PowerShell

**Résumé :** Afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.
  
Bien que vous pouvez utiliser le centre d’administration d’Office 365 pour afficher les comptes de votre client Office 365, vous pouvez également utiliser Office 365 PowerShell et faire des choses que le centre d’administration d’Office 365 ne peuvent pas.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez Azure Active Directory PowerShell pour le module de graphique

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :
  
```
Get-AzureADUser
```

Les informations affichées devraient être semblables à ce qui suit :
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, renseignez le nom d’utilisateur principal (UPN) du compte d’utilisateur, supprimez le « < » et « > » caractères et exécutez la commande suivante :
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Afficher les valeurs de propriété supplémentaires pour un compte spécifique

Par défaut, l’applet de commande **Get-AzureADUser** affiche uniquement les propriétés UserPrincipalName, DisplayName et ObjectID de comptes.

Pour être plus sélective sur la liste des propriétés à afficher, vous pouvez utiliser la cmdlet **Select-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Windows Azure Active Directory PowerShell graphique prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche le DisplayName, le service et UsageLocation pour chaque compte d’utilisateur :
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).
  
Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Autre exemple, vous pouvez vérifier l’état activé d’un compte d’utilisateur spécifique avec la commande suivante :
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Afficher des comptes basées sur une propriété courantes

Pour être plus sélective sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Windows Azure Active Directory PowerShell graphique prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifié :
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Cette commande indique à Windows Azure Active Directory PowerShell graphique pour :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Les accolades, la commande indique à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
La propriété **UsageLocation** n’existe qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where-Object** indiquée dans ces exemples est **Where-Object {$\_.** [nom de la propriété compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [opérateur de comparaison] est **-eq** pour est égal à, **-ne** pour pas égal à **-lt** pour inférieure à **-gt** pour supérieure et d’autres personnes.  [valeur] est généralement une chaîne (une séquence de lettres, chiffres et autres caractères), une valeur numérique ou **$Null** pour n’est pas spécifié > Pour plus d’informations, consultez [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :
  
```
Get-MsolUser
```

Les informations affichées devraient être semblables à ce qui suit :
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

L’applet de commande **Get-MsolUser** a également un jeu de paramètres pour filtrer l’ensemble des comptes d’utilisateur affiché. Par exemple, la liste des utilisateurs sans licence (les utilisateurs qui ont été ajoutés à Office 365, mais n’ont pas encore été une licence pour utiliser un des services), exécutez cette commande.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Les informations affichées devraient être semblables à ce qui suit :
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Pour plus d’informations sur les paramètres supplémentaires pour filtrer l’affichage de l’ensemble des comptes d’utilisateurs affichés, voir [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, renseignez le nom d’utilisateur principal (UPN) du compte d’utilisateur, supprimez le « < » et « > » caractères et exécutez la commande suivante :
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Afficher des comptes basées sur une propriété courantes

Pour être plus sélective sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec l’applet de commande **Get-MsolUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Office 365 PowerShell pour prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifié :
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Les accolades, la commande indique à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété **UsageLocation** n’existe qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where-Object** indiquée dans ces exemples est **Where-Object {$\_.** [nom de la propriété compte utilisateur] [opérateur de comparaison] [valeur] **}**.  [opérateur de comparaison] est **-eq** pour est égal à **-ne** pour différent, **-lt** pour inférieure à **-gt** pour supérieure et d’autres personnes.  [valeur] est généralement une chaîne (une séquence de lettres, chiffres et autres caractères), une valeur numérique ou **$Null** pour n’est pas spécifié. Pour plus d’informations, voir [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Afficher les valeurs de propriété supplémentaires pour les comptes

L’applet de commande **Get-MsolUser** par défaut affiche trois propriétés des comptes d’utilisateurs :
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si vous avez besoin des propriétés supplémentaires, telles que le service fonctionne de l’utilisateur pour et la pays/la région où l’utilisateur utilise les services Office 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec la cmdlet **Select-Object** pour spécifier la liste du compte d’utilisateur Propriétés. Voici un exemple :
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

La cmdlet **Select-Object** vous permet de choisir les propriétés que vous souhaitez afficher une commande. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Pour être plus sélectif dans la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where-Object**. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). Les accolades, la commande est indiquer à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
- Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs Office 365, vous pouvez afficher le compte local, un utilisateur Office 365 a été prévu à partir de. La procédure suivante suppose que Azure AD Connect a été configuré pour utiliser l’ancre de source par défaut du GUID d’objet (pour plus d’informations sur la configuration d’un point d’ancrage de la source, voir [Azure AD Connect : concepts de conception](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) et de la part du principe que le module d’Active Directory pour powershell a été installée (voir [Outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)) :

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

