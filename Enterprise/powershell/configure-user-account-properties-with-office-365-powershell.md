---
title: "Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell"
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Résumé : Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365."
ms.openlocfilehash: eac568d20d1b33e06c37e920f9fd31582c8bb648
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365.
  
Bien que vous puissiez utiliser le centre d'administration Office 365 pour configurer les propriétés des comptes d'utilisateur de votre client Office 365, vous pouvez également utiliser Office 365 PowerShell et effectuer certaines actions que le centre d'administration Office 365 ne vous permet pas de réaliser.
  
## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d'un compte d'utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) et spécifiez les propriétés à définir ou modifier. Cet exemple de commande remplace l'emplacement d'utilisation de Belinda Newman par France :
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Vous identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -City "\<nom de la ville>"
    
- -Country "\<nom du pays>"
    
- -Department "\<nom du service>"
    
- -DisplayName "\<nom utilisateur complet>"
    
- -Fax "\<numéro de fax>"
    
- -FirstName "\<prénom de l’utilisateur>"
    
- -LastName "\<nom de famille de l’utilisateur>"
    
- -MobilePhone "\<numéro de téléphone portable>"
    
- -Office "\<emplacement du bureau>"
    
- -PhoneNumber "\<numéro de téléphone du bureau>"
    
- -PostalCode "\<code postal>"
    
- -PreferredLanguage "\<langue>"
    
- -State "\<nom de l’État>"
    
- -StreetAddress "\<adresse>"
    
- -Title "\<intitulé du poste>"
    
- -UsageLocation "\<code de région ou de pays à 2 caractères>"
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour obtenir plus de paramètres, voir [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)).
  
Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).
    
- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.
  
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

## <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d'un ensemble spécifique de comptes d'utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where-Object** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where-Object {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Afficher un écran à la fois ( **Plus** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Utilisation du module Azure Active Directory V2 PowerShell pour configurer des propriétés de compte d’utilisateur

Pour configurer les propriétés pour les comptes d'utilisateur avec le module Azure Active Directory V2 PowerShell, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier. Mais tout d'abord, vous devez vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article relatif à la [connexion avec le module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Cet exemple de commande remplace l’emplacement d’utilisation de Belinda Newman par France :
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Vous identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -Department "\<nom du service>"
    
- -DisplayName "\<nom utilisateur complet>"
    
- -FacsimilieTelephoneNumber "\<numéro de télécopie>"
    
- -GivenName "\<prénom de l’utilisateur>"
    
- -Surname "\<nom de famille de l’utilisateur>"
    
- -Mobile "\<N° de téléphone portable>"
    
- -JobTitle "\<fonction>"
    
- -PreferredLanguage "\<langue>"
    
- -StreetAddress "\<adresse>"
    
- -City "\<nom de la ville>"
    
- -State "\<nom de l’État>"
    
- -PostalCode "\<code postal>"
    
- -Country "\<nom du pays>"
    
- -TelephoneNumber "\<numéro de téléphone du bureau>"
    
- -UsageLocation "\<code de région ou de pays à 2 caractères>"
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).
- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.
  
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

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="see-also"></a>Voir aussi

#### 

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

