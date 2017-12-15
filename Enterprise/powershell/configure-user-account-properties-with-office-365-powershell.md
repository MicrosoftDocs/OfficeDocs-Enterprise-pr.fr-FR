---
title: "Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Résumé : Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell

 **Résumé :** Utiliser Office 365 PowerShell pour configurer les propriétés d’un ou plusieurs comptes d’utilisateur dans le client Office 365.
  
Bien que vous puissiez utiliser le centre d'administration Office 365 pour configurer les propriétés des comptes d'utilisateur de votre client Office 365, vous pouvez également utiliser Office 365 PowerShell et effectuer certaines actions que le centre d'administration Office 365 ne vous permet pas de réaliser.
  
## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d'un compte d'utilisateur spécifique

Pour configurer les propriétés d'un compte d'utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) et spécifiez les propriétés à définir ou modifier. Cet exemple de commande remplace l'emplacement d'utilisation de Belinda Newman par France :
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Vous identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -Ville «\<nom de la ville > »
    
- -Pays »\<nom de pays > »
    
- -Département «\<nom du service > »
    
- DisplayName-«\<nom d’utilisateur complet > »
    
- -Fax "\<numéro de télécopie > »
    
- -Prénom »\<nom utilisateur > »
    
- Nom-«\<nom de l’utilisateur > »
    
- MobilePhone-«\<numéro de téléphone portable > »
    
- -Office »\<emplacement du bureau > »
    
- PhoneNumber-«\<numéro de téléphone professionnel > »
    
- Code postal-«\<code postal > »
    
- PreferredLanguage-«\<langue > »
    
- -L’état «\<nom de l’état > »
    
- StreetAddress-«\<adresse > »
    
- -Le titre «\<nom du titre > »
    
- UsageLocation-«\<code de pays ou de région 2 caractères > »
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour obtenir plus de paramètres, voir [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).
  
Pour afficher les noms d'utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique de la liste des noms principaux d’utilisateur ( **UserPrincipalName de Sort-Object** ) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).
    
- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d’utilisateur Principal d’un compte en fonction de son affichage nom (nom et prénom), remplir la variable **$userName** ci-dessous (suppression de la \< et > caractères), puis exécutez les commandes suivantes :
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d'utilisateur principal de l'utilisateur nommé Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d'utilisateur

Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d'un ensemble spécifique de comptes d'utilisateur

Pour modifier les propriétés d'un ensemble spécifique de comptes d'utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where-Object** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont le service affectée à leur propriété « Comptabilité » ( **Where-Object {$_. Département - eq « Comptabilité »}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Afficher un écran à la fois ( **Plus** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Utilisation du module Azure Active Directory V2 PowerShell pour configurer des propriétés de compte d'utilisateur

Pour configurer les propriétés des comptes d’utilisateurs avec le module PowerShell de Azure Active Directory V2, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés pour définir ou modifier. Mais tout d’abord, vous devez vous connecter à votre abonnement. Pour les instructions, voir [se connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d'un compte d'utilisateur spécifique

Cet exemple de commande remplace l'emplacement d'utilisation de Belinda Newman par France :
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Vous identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -Département «\<nom du service > »
    
- DisplayName-«\<nom d’utilisateur complet > »
    
- FacsimilieTelephoneNumber-«\<numéro de télécopie > »
    
- GivenName-«\<nom utilisateur > »
    
- -Nom de famille "\<nom de l’utilisateur > »
    
- -Mobile »\<numéro de téléphone portable > »
    
- JobTitle-«\<titre > »
    
- PreferredLanguage-«\<langue > »
    
- StreetAddress-«\<adresse > »
    
- -Ville «\<nom de la ville > »
    
- -L’état «\<nom de l’état > »
    
- Code postal-«\<code postal > »
    
- -Pays »\<nom de pays > »
    
- -Numéro de téléphone «\<numéro de téléphone professionnel > »
    
- UsageLocation-«\<code de pays ou de région 2 caractères > »
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Pour afficher le nom d’utilisateur Principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique de la liste des noms principaux d’utilisateur ( **UserPrincipalName de Sort-Object** ) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).
- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d’utilisateur Principal d’un compte en fonction de son affichage nom (nom et prénom), remplir la variable **$userName** ci-dessous (suppression de la \< et > caractères), puis exécutez les commandes suivantes :
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d'utilisateur principal de l'utilisateur nommé Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d'utilisateur

Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d'un ensemble spécifique de comptes d'utilisateur

Pour modifier les propriétés d’un ensemble spécifique de compte d’utilisateur, vous pouvez utiliser la combinaison des applets de commande **Get-AzureADUser**, **où**et **AzureADUser de l’ensemble** . L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service de comptabilité pour la France :
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes d’utilisateurs qui ont leur propriété de service la valeur « Comptable » ( **où {$_. Département - eq « Comptabilité »}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="see-also"></a>See also

#### 

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

