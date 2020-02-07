---
title: Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Résumé : Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365."
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841601"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell

Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateur de votre client 365 Office, vous pouvez également utiliser Office 365 PowerShell et effectuer quelques opérations que le centre d’administration ne peut pas faire.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Pour configurer les propriétés des comptes d’utilisateur avec le module Azure Active Directory PowerShell pour Graph, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier. 

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
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
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **sort userPrincipalName** ) et l’envoyer à la commande **|** suivante ().
    
- Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte ( **Sélectionnez userPrincipalName** ).

- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :
  
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

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez la cmdlet **Set-MsolUser** et spécifiez les propriétés à définir ou à modifier. 

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d’un compte d’utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés de définition ou de modification. 

Identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.
  
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
    
Pour obtenir plus de paramètres, voir [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).

Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **sort userPrincipalName** ) et l’envoyer à la commande **|** suivante ().
    
- Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte ( **Sélectionnez userPrincipalName** ).
    
- Afficher un écran à la fois ( **Plus** ).
    
Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :
  
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

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de compte d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where**et **Set-MsolUser** . L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :
  
- Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).
    
- Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
- Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).
    

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
