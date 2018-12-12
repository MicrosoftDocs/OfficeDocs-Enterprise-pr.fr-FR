---
title: Création de comptes d’utilisateurs avec Office 365 PowerShell
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
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365.
ms.openlocfilehash: e5fed572d0b835a42071e77b4aeaf8714f2178bd
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
ms.locfileid: "17553257"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d580f-103">Création de comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d580f-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d580f-104">**Résumé :** Découvrez comment utiliser Office 365 PowerShell pour créer des comptes d'utilisateurs dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="d580f-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="d580f-p101">Office 365 PowerShell vous permet de créer efficacement des comptes d'utilisateurs, en particulier plusieurs à la fois. Lorsque vous créez des comptes d'utilisateurs dans Office 365 PowerShell, certaines propriétés de compte sont toujours requises. D'autres propriétés ne sont pas nécessaires pour la création du compte, mais sont importantes. Ces propriétés sont décrites dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="d580f-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="d580f-109">**Nom de la propriété**</span><span class="sxs-lookup"><span data-stu-id="d580f-109">**Property name**</span></span>|<span data-ttu-id="d580f-110">**Requis ?**</span><span class="sxs-lookup"><span data-stu-id="d580f-110">**Required?**</span></span>|<span data-ttu-id="d580f-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="d580f-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d580f-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="d580f-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="d580f-113">Oui</span><span class="sxs-lookup"><span data-stu-id="d580f-113">Yes</span></span>  <br/> |<span data-ttu-id="d580f-p102">Il s'agit du nom d'affichage qui est utilisé dans les services Office 365. Par exemple, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="d580f-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="d580f-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="d580f-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="d580f-117">Oui</span><span class="sxs-lookup"><span data-stu-id="d580f-117">Yes</span></span>  <br/> |<span data-ttu-id="d580f-p103">Il s'agit du nom de compte utilisé pour se connecter aux services Office 365. Par exemple, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="d580f-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="d580f-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="d580f-120">**FirstName**</span></span> <br/> |<span data-ttu-id="d580f-121">Non</span><span class="sxs-lookup"><span data-stu-id="d580f-121">No</span></span>  <br/> ||
|<span data-ttu-id="d580f-122">**NomFamille**</span><span class="sxs-lookup"><span data-stu-id="d580f-122">**LastName**</span></span> <br/> |<span data-ttu-id="d580f-123">Non</span><span class="sxs-lookup"><span data-stu-id="d580f-123">No</span></span>  <br/> ||
|<span data-ttu-id="d580f-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="d580f-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="d580f-125">Non</span><span class="sxs-lookup"><span data-stu-id="d580f-125">No</span></span>  <br/> |<span data-ttu-id="d580f-p104">Il s'agit du plan de gestion des licences (également appelé plan de licence, plan Office 365 ou référence (SKU)) à partir duquel une licence disponible est affectée au compte d'utilisateur. La licence définit les services Office 365 disponibles pour le compte. Vous n'êtes pas obligé d'affecter une licence à un utilisateur lorsque vous créez le compte, mais le compte nécessite une licence pour accéder aux services Office 365. Vous disposez de 30 jours pour attribuer une licence à un compte d'utilisateur après sa création.</span><span class="sxs-lookup"><span data-stu-id="d580f-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="d580f-p105">Utilisez la cmdlet **Get-MsolAccountSku** pour afficher les plans de gestion des licences ( **AccountSkuId** ) et les licences disponibles dans votre organisation. Pour plus d'informations, consultez la rubrique [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span><span class="sxs-lookup"><span data-stu-id="d580f-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="d580f-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="d580f-132">**Password**</span></span> <br/> |<span data-ttu-id="d580f-133">Non</span><span class="sxs-lookup"><span data-stu-id="d580f-133">No</span></span>  <br/> | <span data-ttu-id="d580f-p106">Si vous n’indiquez pas de mot de passe, un mot de passe aléatoire est affecté au compte d’utilisateur et le mot de passe est visible dans les résultats de la commande. Si vous indiquez un mot de passe, il doit répondre aux exigences de complexité suivantes :</span><span class="sxs-lookup"><span data-stu-id="d580f-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="d580f-136">Entre 8 et 16 caractères de texte ASCII.</span><span class="sxs-lookup"><span data-stu-id="d580f-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="d580f-137">Les caractères doivent être issus des trois types de caractères suivants : lettres minuscules, lettres majuscules, symboles et nombres.</span><span class="sxs-lookup"><span data-stu-id="d580f-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="d580f-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="d580f-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="d580f-139">Non</span><span class="sxs-lookup"><span data-stu-id="d580f-139">No</span></span>  <br/> |<span data-ttu-id="d580f-p107">Il s'agit d'un code de pays valide ISO 3166-1 alpha-2. Par exemple, US pour les États-Unis et FR pour la France. Il est important de fournir cette valeur, car certains services Office 365 ne sont pas disponibles dans certains pays. Par conséquent, vous ne pouvez pas affecter de licence à un compte d'utilisateur, à moins que cette valeur ne soit configurée sur le compte. Pour plus d'informations, reportez-vous à la section [À propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="d580f-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="d580f-144">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="d580f-144">Before you begin</span></span>

<span data-ttu-id="d580f-p108">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d580f-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="d580f-147">Utilisation d'Office 365 PowerShell pour créer des comptes d'utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="d580f-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="d580f-148">Pour créer un compte individuel, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="d580f-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="d580f-149">Cet exemple crée un compte pour l'utilisateur nommé Caleb Sills et situé aux États-Unis, et affecte une licence à partir du plan de gestion des licences  `contoso:ENTERPRISEPACK` (Office 365 Entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="d580f-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="d580f-150">Utilisation d'Office 365 PowerShell pour créer plusieurs comptes d'utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d580f-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="d580f-p109">Créez un fichier CSV (valeurs séparées par des virgules) qui contient les informations de compte d’utilisateur requises. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d580f-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="d580f-153">Les noms de colonne et leur ordre dans la première ligne du fichier CSV sont arbitraires, mais assurez-vous que les données figurant dans le reste du fichier correspondent à l'ordre des noms de colonne, et utilisez les noms de colonne pour les valeurs de paramètre dans la commande Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d580f-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="d580f-154">Utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="d580f-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="d580f-155">Cet exemple crée des comptes d’utilisateurs à partir du fichier nommé C:\My Documents\NewAccounts.csv et enregistre les résultats dans le fichier nommé C:\My Documents\NewAccountResults.csv.</span><span class="sxs-lookup"><span data-stu-id="d580f-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="d580f-p110">Passez en revue le fichier de sortie pour afficher les résultats. Aucun mot de passe n’a été spécifié, de sorte que les mots de passe aléatoires qui ont été générés sont visibles dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d580f-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="d580f-158">Utilisation du module Azure Active Directory V2 PowerShell pour créer des comptes d’utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="d580f-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="d580f-p111">Pour utiliser la cmdlet **New-AzureADUser** à partir du module Azure Active Directory V2 PowerShell, vous devez d'abord vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article [Se connecter au module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="d580f-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="d580f-161">Une fois connecté, utilisez la syntaxe suivante pour créer un compte individuel :</span><span class="sxs-lookup"><span data-stu-id="d580f-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="d580f-162">L’exemple suivant crée un compte pour l’utilisateur américain appelé Caleb Sills :</span><span class="sxs-lookup"><span data-stu-id="d580f-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="d580f-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d580f-163">See also</span></span>

<span data-ttu-id="d580f-164">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="d580f-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d580f-165">Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d580f-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d580f-166">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d580f-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d580f-167">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d580f-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d580f-168">Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d580f-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="d580f-169">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d580f-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d580f-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="d580f-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [<span data-ttu-id="d580f-171">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="d580f-171">Import-Csv</span></span>](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [<span data-ttu-id="d580f-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d580f-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="d580f-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d580f-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="d580f-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="d580f-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

