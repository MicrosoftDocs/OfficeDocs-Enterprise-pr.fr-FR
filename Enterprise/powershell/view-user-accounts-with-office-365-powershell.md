---
title: "Afficher des comptes d’utilisateur avec Office 365 PowerShell"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Résumé : Permet d’afficher, de liste ou afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell."
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Afficher des comptes d’utilisateur avec Office 365 PowerShell

 **Résumé :** Permet d’afficher, de liste ou afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.
  
Vous pouvez utiliser le centre d’administration d’Office 365 pour afficher les comptes pour vos clients d’Office 365, vous pouvez également utiliser Office 365 PowerShell et faire certaines choses que le centre d’administration d’Office 365 ne peuvent pas.
  
## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Affichage des informations de compte utilisateur Office 365

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante dans l’invite de commande d’Office 365 PowerShell ou l’environnement de Script intégré (ISE) de PowerShell.
  
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

L’applet de commande **Get-MsolUser** a également un jeu de paramètres pour filtrer le jeu de comptes d’utilisateurs s’affiche. Par exemple, pour la liste des utilisateurs sans licence (les utilisateurs qui ont été ajoutés à Office 365 mais qui n’ont pas encore été concédé sous licence pour utiliser les services), vous devez exécuter cette commande.
  
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

Pour plus d’informations sur les paramètres supplémentaires pour filtrer l’affichage de l’ensemble des comptes d’utilisateur s’affiche, consultez [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where-Object** en combinaison avec l’applet de commande **Get-MsolUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « pipe » « | », qui indique à Office 365 PowerShell utilisent les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ). À l’intérieur d’accolades, la commande indique à Office 365 PowerShell uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation compte de propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété **UsageLocation** n'est qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez l’applet de commande **Select-Object** et le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Par exemple, à partir de cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs pour les utilisateurs vivant à Londres :
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de l’applet de commande **Where-Object** présenté dans ces exemples est **Where-Object {$\_.** [nom de propriété de compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [comparaison] est **-eq** pour equals, **ne -** pour non égal à, **lt -** pour moins de **-gt** de plus d’et d’autres > [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), un valeur numérique, ou **$Null** pour non spécifié > Pour plus d’informations, reportez-vous à la section [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Vous pouvez vérifier le statut de blocage d’un compte d’utilisateur avec la commande suivante :
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Sélection des propriétés de compte utilisateur à afficher

L’applet de commande [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) par défaut affiche les trois propriétés de comptes d’utilisateurs :
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si vous avez besoin des propriétés supplémentaires, telles que le département travaille pour et le pays/la région où l’utilisateur utilise les services d’Office 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec l’applet de commande **Select-Object** pour spécifier la liste des comptes d’utilisateur Propriétés. Voici un exemple :
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).
    
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
David Longmuir      Operations                               US
Scott Wallace            Operations
```

L’applet de commande **Select-Object** vous permet de choisir les propriétés à une commande à afficher. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser l’applet de commande **Where-Object** . Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur d’accolades, la commande est demandant uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation de propriété compte Office 365 PowerShell ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
- Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).
    
Les informations affichées devraient être semblables à ce qui suit :
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Utilisation du module Azure Active Directory V2 PowerShell pour afficher des comptes d’utilisateur

Pour afficher les propriétés des comptes d’utilisateurs avec le module PowerShell de Azure Active Directory V2, vous utilisez l’applet de commande [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Mais tout d’abord, vous devez vous connecter à votre abonnement. Pour les instructions, voir[se connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Affichage des informations de compte utilisateur Office 365

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante dans l’invite de commande d’Office 365 PowerShell ou l’environnement de Script intégré (ISE) de PowerShell.
  
```
Get-AzureADUser
```

L’applet de commande **Get-AzureADUser** par défaut affiche les trois propriétés de comptes d’utilisateurs :
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « pipe » « | », qui indique à Office 365 PowerShell utilisent les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ). À l’intérieur d’accolades, la commande indique à Office 365 PowerShell uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation compte de propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
La propriété **UsageLocation** n'est qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez l’applet de commande **Select-Object** et le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique, une page à la fois ( **plusieurs** ). Voici un exemple :
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

Par exemple, la **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs pour les utilisateurs vivant à Londres :
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de l’applet de commande **Where-Object** présenté dans ces exemples est **Where-Object {$\_.** [nom de propriété de compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [comparaison] est **-eq** pour equals, **ne -** pour non égal à, **lt -** pour moins de **-gt** de plus d’et d’autres > [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), un valeur numérique, ou **$Null** pour non spécifié > Pour plus d’informations, reportez-vous à la section[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
### <a name="select-the-user-account-properties-to-display"></a>Sélection des propriétés de compte utilisateur à afficher

L’applet de commande **Get-AzureADUser** par défaut affiche les propriétés des comptes d’utilisateurs de UserPrincipalName, DisplayName et ObjectID. Si vous avez besoin des propriétés supplémentaires, telles que le département travaille pour et le pays/la région où l’utilisateur utilise les services d’Office 365, vous pouvez exécuter **Get-AzureADUser** en combinaison avec l’applet de commande **Select-Object** pour spécifier la liste des utilisateurs Propriétés du compte. Voici un exemple :
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).
    
Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser l’applet de commande **Where-Object** . Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur d’accolades, la commande est demandant uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation de propriété compte Office 365 PowerShell ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).
    
- Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).
    
## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Voir aussi

#### 

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

