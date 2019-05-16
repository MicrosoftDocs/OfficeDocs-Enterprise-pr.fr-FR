---
title: Création de comptes d'utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365.
ms.openlocfilehash: 846dafb842b87f119670f44848152a99341939e7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069060"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8d793-103">Création de comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d793-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8d793-104">**Résumé :** Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d793-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="8d793-p101">Office 365 PowerShell vous permet de créer efficacement des comptes d'utilisateurs, en particulier plusieurs à la fois. Lorsque vous créez des comptes d'utilisateurs dans Office 365 PowerShell, certaines propriétés de compte sont toujours requises. D'autres propriétés ne sont pas nécessaires pour la création du compte, mais sont importantes. Ces propriétés sont décrites dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="8d793-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="8d793-109">**Nom de la propriété**</span><span class="sxs-lookup"><span data-stu-id="8d793-109">**Property name**</span></span>|<span data-ttu-id="8d793-110">**Requis ?**</span><span class="sxs-lookup"><span data-stu-id="8d793-110">**Required?**</span></span>|<span data-ttu-id="8d793-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="8d793-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8d793-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="8d793-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="8d793-113">Oui</span><span class="sxs-lookup"><span data-stu-id="8d793-113">Yes</span></span>  <br/> |<span data-ttu-id="8d793-p102">Il s'agit du nom d'affichage qui est utilisé dans les services Office 365. Par exemple, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="8d793-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="8d793-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="8d793-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="8d793-117">Oui</span><span class="sxs-lookup"><span data-stu-id="8d793-117">Yes</span></span>  <br/> |<span data-ttu-id="8d793-p103">Il s'agit du nom de compte utilisé pour se connecter aux services Office 365. Par exemple, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="8d793-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="8d793-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="8d793-120">**FirstName**</span></span> <br/> |<span data-ttu-id="8d793-121">Non</span><span class="sxs-lookup"><span data-stu-id="8d793-121">No</span></span>  <br/> ||
|<span data-ttu-id="8d793-122">**NomFamille**</span><span class="sxs-lookup"><span data-stu-id="8d793-122">**LastName**</span></span> <br/> |<span data-ttu-id="8d793-123">Non</span><span class="sxs-lookup"><span data-stu-id="8d793-123">No</span></span>  <br/> ||
|<span data-ttu-id="8d793-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="8d793-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="8d793-125">Non</span><span class="sxs-lookup"><span data-stu-id="8d793-125">No</span></span>  <br/> |<span data-ttu-id="8d793-p104">Il s'agit du plan de gestion des licences (également appelé plan de licence, plan Office 365 ou référence (SKU)) à partir duquel une licence disponible est affectée au compte d'utilisateur. La licence définit les services Office 365 disponibles pour le compte. Vous n'êtes pas obligé d'affecter une licence à un utilisateur lorsque vous créez le compte, mais le compte nécessite une licence pour accéder aux services Office 365. Vous disposez de 30 jours pour attribuer une licence à un compte d'utilisateur après sa création.</span><span class="sxs-lookup"><span data-stu-id="8d793-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="8d793-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="8d793-130">**Password**</span></span> <br/> |<span data-ttu-id="8d793-131">Non</span><span class="sxs-lookup"><span data-stu-id="8d793-131">No</span></span>  <br/> | <span data-ttu-id="8d793-p105">Si vous n’indiquez pas de mot de passe, un mot de passe aléatoire est affecté au compte d’utilisateur et le mot de passe est visible dans les résultats de la commande. Si vous spécifiez un mot de passe, il doit être composé de 8 à 16 caractères ASCII de l'un des trois types suivants : lettres minuscules, lettres majuscules, chiffres et symboles.</span><span class="sxs-lookup"><span data-stu-id="8d793-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="8d793-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="8d793-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="8d793-135">Non</span><span class="sxs-lookup"><span data-stu-id="8d793-135">No</span></span>  <br/> |<span data-ttu-id="8d793-p106">Il s'agit d'un code de pays valide ISO 3166-1 alpha-2. Par exemple, US pour les États-Unis et FR pour la France. Il est important de fournir cette valeur, car certains services Office 365 ne sont pas disponibles dans certains pays. Par conséquent, vous ne pouvez pas affecter de licence à un compte d'utilisateur, à moins que cette valeur ne soit configurée sur le compte. Pour plus d'informations, reportez-vous à la section [À propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="8d793-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8d793-140">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="8d793-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8d793-141">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8d793-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="8d793-142">Une fois connecté, utilisez la syntaxe suivante pour créer un compte individuel :</span><span class="sxs-lookup"><span data-stu-id="8d793-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="8d793-143">L’exemple suivant crée un compte pour l’utilisateur américain appelé Caleb Sills :</span><span class="sxs-lookup"><span data-stu-id="8d793-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8d793-144">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d793-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8d793-145">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8d793-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="8d793-146">Créez un compte d’utilisateur individuel</span><span class="sxs-lookup"><span data-stu-id="8d793-146">Create an individual user account</span></span>

<span data-ttu-id="8d793-147">Pour créer un compte individuel, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8d793-147">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="8d793-148">Pour répertorier les noms des plans de gestion des licences disponibles, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8d793-148">To list the available licensing plan names, use this command:</span></span>

````
Get-MsolAccountSku
````

<span data-ttu-id="8d793-149">Cet exemple crée un compte pour l’utilisateur nommé Caleb Sills et situé aux États-Unis, et affecte une licence à partir du plan de gestion des licences `contoso:ENTERPRISEPACK` (Office 365 Entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="8d793-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="8d793-150">Créez plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="8d793-150">Create multiple user accounts</span></span>

1. <span data-ttu-id="8d793-p107">Créez un fichier CSV (valeurs séparées par des virgules) qui contient les informations de compte d’utilisateur requises. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8d793-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="8d793-153">Les noms de colonne et leur ordre dans la première ligne du fichier CSV sont arbitraires, mais assurez-vous que les données figurant dans le reste du fichier correspondent à l'ordre des noms de colonne, et utilisez les noms de colonne pour les valeurs de paramètre dans la commande Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d793-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="8d793-154">Utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8d793-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="8d793-155">Cet exemple crée des comptes d’utilisateurs à partir du fichier nommé C:\My Documents\NewAccounts.csv et enregistre les résultats dans le fichier nommé C:\My Documents\NewAccountResults.csv.</span><span class="sxs-lookup"><span data-stu-id="8d793-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="8d793-p108">Passez en revue le fichier de sortie pour afficher les résultats. Aucun mot de passe n’a été spécifié, de sorte que les mots de passe aléatoires qui ont été générés par Office 365 sont visibles dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="8d793-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8d793-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d793-158">See also</span></span>

[<span data-ttu-id="8d793-159">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d793-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8d793-160">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d793-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8d793-161">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="8d793-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
