---
title: Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: Découvrez comment afficher, répertorier ou afficher vos comptes d’utilisateur Microsoft 365 de différentes manières avec PowerShell.
ms.openlocfilehash: 56da6bfc7b467b6a85a4bd8c84abd4c2ae05913f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605295"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour afficher les comptes de votre client Microsoft 365, vous pouvez également utiliser PowerShell pour Microsoft 365 et effectuer quelques opérations que le centre d’administration ne peut pas faire.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :
  
```powershell
Get-AzureADUser
```

Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
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

Pour afficher un compte d’utilisateur spécifique, renseignez le nom du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN), supprimez les caractères « < » et « > », puis exécutez la commande suivante :
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Afficher des valeurs de propriétés supplémentaires pour un compte spécifique

Par défaut, la cmdlet **Get-AzureADUser** affiche uniquement les propriétés ObjectId, DisplayName et userPrincipalName des comptes.

Pour être plus sélectif sur la liste des propriétés à afficher, vous pouvez utiliser l’applet de commande **Select** en combinaison avec la cmdlet **Get-AzureADUser** . Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche les DisplayName, Department et UsageLocation pour chaque compte d’utilisateur :
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Sélectionnez DisplayName, Department, UsageLocation** ).
  
Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez l’applet de commande **Select** et le caractère générique (*) pour les afficher tous pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Autre exemple : vous pouvez vérifier l’état activé d’un compte d’utilisateur spécifique à l’aide de la commande suivante :
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Afficher certains comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where** en combinaison avec la cmdlet **Get-AzureADUser** . Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande demande à Azure Active Directory PowerShell pour Graph d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **où {$ \_ . UsageLocation-EQ $Null}** ). À l’intérieur des accolades, la commande demande à PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( ** $ \_ . UsageLocation** ) n’est pas spécifié ( **-EQ $null** ).
    
La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez l’applet de commande **Select** et le caractère générique (*) pour les afficher tous pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where** illustrée dans ces exemples est **where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**. > [opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.  [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour> voir [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) pour plus d’informations.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

La cmdlet **Get-MsolUser** dispose également d’un jeu de paramètres pour filtrer l’ensemble de comptes utilisateur affichés. Par exemple, pour la liste des utilisateurs sans licence (utilisateurs qui ont été ajoutés à Microsoft 365 mais qui n’ont pas encore été concédés sous licence pour utiliser l’un des services), exécutez cette commande.
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Pour plus d’informations sur les paramètres supplémentaires permettant de filtrer l’affichage de l’ensemble des comptes d’utilisateur affichés, consultez la rubrique [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, renseignez le nom de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN), supprimez les caractères « < » et « > », puis exécutez la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Afficher certains comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where** en combinaison avec la cmdlet **Get-MsolUser** . Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à PowerShell de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **où {$ \_ . UsageLocation-EQ $Null}** ). À l’intérieur des accolades, la commande demande à PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( ** $ \_ . UsageLocation** ) n’est pas spécifié ( **-EQ $null** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez l’applet de commande **Select** et le caractère générique (*) pour les afficher tous pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where** illustrée dans ces exemples est **where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**.  [opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.  [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour non spécifié. Pour plus d’informations, consultez la rubrique [Where](https://technet.microsoft.com/library/hh849715.aspx) .
  
Vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Afficher les valeurs des propriétés supplémentaires des comptes

La cmdlet **Get-MsolUser** affiche par défaut trois propriétés des comptes d’utilisateur :
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si vous avez besoin de propriétés supplémentaires, telles que le service pour lequel l’utilisateur travaille pour et le pays/la région où l’utilisateur utilise les services Microsoft 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec l’applet de commande **Select** pour spécifier la liste des propriétés du compte d’utilisateur. Voici un exemple :
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Sélectionnez DisplayName, Department, UsageLocation** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

La cmdlet **Select** vous permet de sélectionner et de sélectionner les propriétés que vous souhaitez afficher pour une commande. Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez le caractère générique (*) pour les afficher tous pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where** . Voici un exemple de commande qui affiche uniquement les comptes utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **où {$ \_ . UsageLocation-EQ $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur des accolades, la commande demande à PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( ** $ \_ . UsageLocation** ) n’est pas spécifié ( **-EQ $null** ).
    
- Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Sélectionnez DisplayName, Department, UsageLocation** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs de Microsoft 365, vous pouvez afficher le compte local à partir duquel un utilisateur Microsoft 365 a été projeté. Les éléments suivants supposent qu’Azure AD Connect a été configuré pour utiliser l’ancre source par défaut d’ObjectGUID (pour plus d’informations sur la configuration d’une ancre source, reportez-vous à la rubrique [Azure ad Connect : Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) et suppose que le module Services de domaine Active Directory pour PowerShell a été installé (voir [outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)) :

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

