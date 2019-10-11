---
title: Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
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
ms.openlocfilehash: 40d7e78b3fd6c011f6c53b2af433f258b888d5bb
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435348"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="7936f-103">Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7936f-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="7936f-104">**Résumé :** Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="7936f-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="7936f-105">Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateur de votre client 365 Office, vous pouvez également utiliser Office 365 PowerShell et effectuer quelques opérations que le centre d’administration ne peut pas faire.</span><span class="sxs-lookup"><span data-stu-id="7936f-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7936f-106">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="7936f-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7936f-107">Pour configurer les propriétés des comptes d’utilisateur avec le module Azure Active Directory PowerShell pour Graph, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="7936f-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="7936f-108">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="7936f-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="7936f-109">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="7936f-109">Change properties for a specific user account</span></span>

<span data-ttu-id="7936f-p101">Identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="7936f-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="7936f-112">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="7936f-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="7936f-113">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="7936f-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="7936f-114">-FacsimilieTelephoneNumber "\<numéro de télécopie>"</span><span class="sxs-lookup"><span data-stu-id="7936f-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="7936f-115">-GivenName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="7936f-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="7936f-116">-Surname "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="7936f-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="7936f-117">-Mobile "\<N° de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="7936f-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="7936f-118">-JobTitle "\<fonction>"</span><span class="sxs-lookup"><span data-stu-id="7936f-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="7936f-119">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="7936f-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="7936f-120">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="7936f-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="7936f-121">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="7936f-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="7936f-122">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="7936f-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="7936f-123">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="7936f-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="7936f-124">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="7936f-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="7936f-125">-TelephoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="7936f-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="7936f-126">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="7936f-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="7936f-127">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="7936f-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="7936f-128">Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="7936f-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="7936f-129">Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7936f-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="7936f-130">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-131">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-132">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-133">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="7936f-134">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="7936f-p102">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="7936f-137">Cet exemple affiche le nom d’utilisateur principal pour le compte l’utilisateur avec Caleb Sills comme nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="7936f-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="7936f-p103">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="7936f-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="7936f-140">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7936f-140">Change properties for all user accounts</span></span>

<span data-ttu-id="7936f-p104">Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="7936f-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="7936f-143">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-144">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-145">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="7936f-146">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7936f-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="7936f-p105">Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="7936f-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="7936f-149">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-150">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-151">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-152">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7936f-153">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7936f-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7936f-154">Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, vous utilisez la cmdlet Set-MsolUser et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="7936f-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="7936f-155">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7936f-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="7936f-156">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="7936f-156">Change properties for a specific user account</span></span>

<span data-ttu-id="7936f-157">Pour configurer les propriétés d’un compte d’utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) et spécifiez les propriétés de définition ou de modification.</span><span class="sxs-lookup"><span data-stu-id="7936f-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="7936f-p106">Identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="7936f-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="7936f-160">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="7936f-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="7936f-161">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="7936f-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="7936f-162">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="7936f-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="7936f-163">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="7936f-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="7936f-164">-Fax "\<numéro de fax>"</span><span class="sxs-lookup"><span data-stu-id="7936f-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="7936f-165">-FirstName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="7936f-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="7936f-166">-LastName "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="7936f-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="7936f-167">-MobilePhone "\<numéro de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="7936f-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="7936f-168">-Office "\<emplacement du bureau>"</span><span class="sxs-lookup"><span data-stu-id="7936f-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="7936f-169">-PhoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="7936f-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="7936f-170">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="7936f-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="7936f-171">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="7936f-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="7936f-172">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="7936f-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="7936f-173">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="7936f-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="7936f-174">-Title "\<intitulé du poste>"</span><span class="sxs-lookup"><span data-stu-id="7936f-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="7936f-175">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="7936f-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="7936f-176">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="7936f-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="7936f-177">Pour obtenir plus de paramètres, voir [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="7936f-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="7936f-178">Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7936f-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="7936f-179">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-180">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-181">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-182">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="7936f-183">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="7936f-p107">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="7936f-186">Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="7936f-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="7936f-p108">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d’affichage. Voici un exemple de définition de l’emplacement d’utilisation de Belinda Newman en France, mais en spécifiant son nom d’affichage plutôt que son nom d’utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="7936f-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="7936f-189">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7936f-189">Change properties for all user accounts</span></span>

<span data-ttu-id="7936f-p109">Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="7936f-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="7936f-192">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-193">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-194">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="7936f-195">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7936f-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="7936f-p110">Pour modifier les propriétés d'un ensemble spécifique de comptes d'utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where-Object** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="7936f-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="7936f-198">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7936f-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="7936f-199">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-200">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where-Object {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="7936f-201">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="7936f-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="7936f-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7936f-202">See also</span></span>

[<span data-ttu-id="7936f-203">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7936f-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7936f-204">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7936f-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7936f-205">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="7936f-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
