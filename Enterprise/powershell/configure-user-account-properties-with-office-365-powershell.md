---
title: Configuration des propriétés de compte d’utilisateur Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour configurer les propriétés d’un ou de plusieurs comptes d’utilisateur dans votre client Microsoft 365.'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230850"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Configuration des propriétés de compte d’utilisateur Microsoft 365 avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateurs de votre client Microsoft 365, vous pouvez également utiliser PowerShell et effectuer certaines opérations que le centre d’administration Microsoft 365 ne peut pas faire.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Pour configurer les propriétés des comptes d’utilisateur avec le module Azure Active Directory PowerShell pour Graph, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier. 

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -Department "\<department name>"
    
- -DisplayName "\<full user name>"
    
- -FacsimilieTelephoneNumber "<numéro de télécopie>"
    
- -GivenName "<prénom de l'utilisateur>"
    
- -Surname "<nom de famille de l'utilisateur>"
    
- -Mobile "<N° de téléphone portable>"
    
- -JobTitle "\<job title>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<street address>"
    
- -City "\<city name>"
    
- -State "<nom de l'État>"
    
- -PostalCode "\<postal code>
    
- -Country "\<country name>"
    
- -TelephoneNumber "<numéro de téléphone du bureau>"
    
- -UsageLocation " \<2-character country or region code> "
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).


Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux (**sort userPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte (**Sélectionnez userPrincipalName**).

- Afficher un écran à la fois (**Plus**).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), renseignez la variable **$username** ci-dessous (en supprimant les \< and > caractères), puis exécutez les commandes suivantes :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d’utilisateur principal pour le compte l’utilisateur avec Caleb Sills comme nom d’affichage.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
- Définissez la France comme emplacement de l’utilisateur (**Set-AzureADUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
- Recherchez tous les comptes d’utilisateur dont la propriété Department est définie sur « Accounting » (**where {$ _. Department-EQ "Accounting"}**) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définissez la France comme emplacement de l’utilisateur (**Set-AzureADUser-UsageLocation "fr"**).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez la cmdlet **Set-MsolUser** et spécifiez les propriétés à définir ou à modifier. 

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d’un compte d’utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés de définition ou de modification. 

Identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
- -City "\<city name>"
    
- -Country "\<country name>"
    
- -Department "\<department name>"
    
- -DisplayName "\<full user name>"
    
- -Fax "<numéro de fax>"
    
- -FirstName "<prénom de l'utilisateur>"
    
- -LastName "<nom de famille de l'utilisateur>"
    
- -MobilePhone "<numéro de téléphone portable>"
    
- -Office "\<office location>"
    
- -PhoneNumber "<numéro de téléphone du bureau>"
    
- -PostalCode "\<postal code>
    
- -PreferredLanguage "\<language>"
    
- -State "<nom de l'État>"
    
- -StreetAddress "\<street address>"
    
- -Title "<intitulé du poste>"
    
- -UsageLocation " \<2-character country or region code> "
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour obtenir plus de paramètres, voir [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).

Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux (**sort userPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
- Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte (**Sélectionnez userPrincipalName**).
    
- Afficher un écran à la fois (**Plus**).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), renseignez la variable **$username** ci-dessous (en supprimant les \< and > caractères), puis exécutez les commandes suivantes :
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d’affichage. Voici un exemple de définition de l’emplacement d’utilisation de Belinda Newman en France, mais en spécifiant son nom d’affichage plutôt que son nom d’utilisateur principal :
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
- Définissez la France comme emplacement de l’utilisateur (**Set-MsolUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de compte d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where**et **Set-MsolUser** . L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
- Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
- Recherchez tous les comptes d’utilisateur dont la propriété Department est définie sur « Accounting » (**where {$ _. Department-EQ "Accounting"}**) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définissez la France comme emplacement de l’utilisateur (**Set-MsolUser-UsageLocation "fr"**).
    

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
