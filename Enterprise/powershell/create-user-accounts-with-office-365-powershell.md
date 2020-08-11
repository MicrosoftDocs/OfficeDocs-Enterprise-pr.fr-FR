---
title: Créer des comptes d’utilisateur Microsoft 365 avec PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Dans cet article, Découvrez comment utiliser PowerShell pour créer des comptes d’utilisateurs ou plusieurs comptes d’utilisateur Microsoft 365.
ms.openlocfilehash: 2f4d7b42e68e3bd426ea73c8568e0c603af06dcb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605990"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>Créer des comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 pour créer efficacement des comptes d’utilisateur, notamment plusieurs comptes d’utilisateur. Lorsque vous créez des comptes d’utilisateur dans PowerShell, certaines propriétés de compte sont toujours obligatoires. D'autres propriétés ne sont pas nécessaires pour la création du compte, mais sont importantes. Ces propriétés sont décrites dans le tableau suivant :
  
|**Nom de la propriété**|**Requis ?**|**Description**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Oui  <br/> |Il s’agit du nom complet utilisé dans les services Microsoft 365. Par exemple, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Oui  <br/> |Il s’agit du nom de compte utilisé pour se connecter aux services Microsoft 365. Par exemple, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Non  <br/> ||
|**NomFamille** <br/> |Non  <br/> ||
|**LicenseAssignment** <br/> |Non  <br/> |Il s’agit du plan de gestion des licences (également appelé plan de licence ou SKU) à partir duquel une licence disponible est attribuée au compte d’utilisateur. La licence définit les services Microsoft 365 disponibles pour le compte. Vous n’êtes pas obligé d’attribuer une licence à un utilisateur lorsque vous créez le compte, mais le compte nécessite une licence pour accéder aux services Microsoft 365. Vous disposez de 30 jours pour attribuer une licence à un compte d'utilisateur après sa création. |
|**Password** <br/> |Non  <br/> | Si vous n’indiquez pas de mot de passe, un mot de passe aléatoire est affecté au compte d’utilisateur et le mot de passe est visible dans les résultats de la commande. Si vous spécifiez un mot de passe, il doit être composé de 8 à 16 caractères ASCII de l'un des trois types suivants : lettres minuscules, lettres majuscules, chiffres et symboles. <br/> |
|**UsageLocation** <br/> |Non  <br/> |Il s’agit d’un code ISO 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Il est important de fournir cette valeur, car certains services Microsoft 365 ne sont pas disponibles dans certains pays, de sorte que vous ne pouvez pas attribuer une licence à un compte d’utilisateur sauf si cette valeur est configurée pour le compte. Pour plus d’informations, consultez la rubrique [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Une fois connecté, utilisez la syntaxe suivante pour créer un compte individuel :
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

L’exemple suivant crée un compte pour l’utilisateur américain appelé Caleb Sills :
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Créez un compte d’utilisateur individuel

Pour créer un compte individuel, utilisez la syntaxe suivante :
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour répertorier les noms des plans de gestion des licences disponibles, utilisez la commande suivante :

````powershell
Get-MsolAccountSku
````

Cet exemple crée un compte pour l’utilisateur nommé Caleb Sills et situé aux États-Unis, et affecte une licence à partir du plan de gestion des licences `contoso:ENTERPRISEPACK` (Office 365 Entreprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Créez plusieurs comptes d’utilisateurs

1. Créez un fichier CSV (valeurs séparées par des virgules) qui contient les informations de compte d’utilisateur requises. Par exemple :
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Les noms de colonne et leur ordre dans la première ligne du fichier CSV sont arbitraires, mais assurez-vous que les données dans le reste du fichier correspondent à l’ordre des noms de colonne et utilisez les noms de colonne pour les valeurs de paramètre dans la commande PowerShell pour Microsoft 365.
    
2. Utilisez la syntaxe suivante :
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

Cet exemple crée des comptes d’utilisateurs à partir du fichier nommé C:\My Documents\NewAccounts.csv et enregistre les résultats dans le fichier nommé C:\My Documents\NewAccountResults.csv.
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Passez en revue le fichier de sortie pour afficher les résultats. Les mots de passe ne sont pas spécifiés, de sorte que les mots de passe aléatoires générés par Microsoft 365 sont visibles dans le fichier de sortie.
    
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
