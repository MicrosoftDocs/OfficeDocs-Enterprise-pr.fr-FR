---
title: "Création de comptes d’utilisateurs avec Office 365 PowerShell"
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
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365."
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Création de comptes d’utilisateurs avec Office 365 PowerShell

**Résumé :** Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365.
  
Office 365 PowerShell vous permet de créer efficacement des comptes d'utilisateurs, en particulier plusieurs à la fois. Lorsque vous créez des comptes d'utilisateurs dans Office 365 PowerShell, certaines propriétés de compte sont toujours requises. D'autres propriétés ne sont pas nécessaires pour la création du compte, mais sont importantes. Ces propriétés sont décrites dans le tableau suivant :
  
****

|**Nom de la propriété**|**Requis ?**|**Description**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Oui  <br/> |Il s'agit du nom d'affichage qui est utilisé dans les services Office 365. Par exemple, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Oui  <br/> |Il s'agit du nom de compte utilisé pour se connecter aux services Office 365. Par exemple, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Non  <br/> ||
|**NomFamille** <br/> |Non  <br/> ||
|**LicenseAssignment** <br/> |Non  <br/> |Il s'agit du plan de gestion des licences (également appelé plan de licence, plan Office 365 ou référence (SKU)) à partir duquel une licence disponible est affectée au compte d'utilisateur. La licence définit les services Office 365 disponibles pour le compte. Vous n'êtes pas obligé d'affecter une licence à un utilisateur lorsque vous créez le compte, mais le compte nécessite une licence pour accéder aux services Office 365. Vous disposez de 30 jours pour attribuer une licence à un compte d'utilisateur après sa création.<br/> Utilisez la cmdlet **Get-MsolAccountSku** pour afficher les plans de gestion des licences ( **AccountSkuId** ) et les licences disponibles dans votre organisation. Pour plus d'informations, consultez la rubrique [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  <br/> |
|**Password** <br/> |Non  <br/> | Si vous n’indiquez pas de mot de passe, un mot de passe aléatoire est affecté au compte d’utilisateur et le mot de passe est visible dans les résultats de la commande. Si vous indiquez un mot de passe, il doit répondre aux exigences de complexité suivantes : <br/>  Entre 8 et 16 caractères de texte ASCII. <br/>  Les caractères doivent être issus des trois types de caractères suivants : lettres minuscules, lettres majuscules, symboles et nombres. <br/> |
|**UsageLocation** <br/> |Non  <br/> |Il s'agit d'un code de pays valide ISO 3166-1 alpha-2. Par exemple, US pour les États-Unis et FR pour la France. Il est important de fournir cette valeur, car certains services Office 365 ne sont pas disponibles dans certains pays. Par conséquent, vous ne pouvez pas affecter de licence à un compte d'utilisateur, à moins que cette valeur ne soit configurée sur le compte. Pour plus d'informations, reportez-vous à la section [À propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Utilisation d'Office 365 PowerShell pour créer des comptes d'utilisateurs individuels

Pour créer un compte individuel, utilisez la syntaxe suivante :
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

Cet exemple crée un compte pour l'utilisateur nommé Caleb Sills et situé aux États-Unis, et affecte une licence à partir du plan de gestion des licences  `contoso:ENTERPRISEPACK` (Office 365 Entreprise E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Utilisation d'Office 365 PowerShell pour créer plusieurs comptes d'utilisateurs

1. Créez un fichier CSV (valeurs séparées par des virgules) qui contient les informations de compte d’utilisateur requises. Par exemple :
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Les noms de colonne et leur ordre dans la première ligne du fichier CSV sont arbitraires, mais assurez-vous que les données figurant dans le reste du fichier correspondent à l'ordre des noms de colonne, et utilisez les noms de colonne pour les valeurs de paramètre dans la commande Office 365 PowerShell.
    
2. Utilisez la syntaxe suivante :
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

Cet exemple crée des comptes d’utilisateurs à partir du fichier nommé C:\My Documents\NewAccounts.csv et enregistre les résultats dans le fichier nommé C:\My Documents\NewAccountResults.csv.
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Passez en revue le fichier de sortie pour afficher les résultats. Aucun mot de passe n’a été spécifié, de sorte que les mots de passe aléatoires qui ont été générés sont visibles dans le fichier de sortie.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Utilisation du module Azure Active Directory V2 PowerShell pour créer des comptes d’utilisateurs individuels

Pour utiliser la cmdlet **New-AzureADUser** à partir du module Azure Active Directory V2 PowerShell, vous devez d'abord vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article [Se connecter au module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Une fois connecté, utilisez la syntaxe suivante pour créer un compte individuel :
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

L’exemple suivant crée un compte pour l’utilisateur américain appelé Caleb Sills :
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>Voir aussi

Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :
  
- [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquer des comptes d'utilisateurs avec Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

