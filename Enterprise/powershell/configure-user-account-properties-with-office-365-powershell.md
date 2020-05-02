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
description: "Résumé : Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365."
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004717"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="00aee-103">Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="00aee-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="00aee-104">Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateur de votre client 365 Office, vous pouvez également utiliser Office 365 PowerShell et effectuer quelques opérations que le centre d’administration ne peut pas faire.</span><span class="sxs-lookup"><span data-stu-id="00aee-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="00aee-105">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="00aee-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="00aee-106">Pour configurer les propriétés des comptes d’utilisateur avec le module Azure Active Directory PowerShell pour Graph, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="00aee-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="00aee-107">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="00aee-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="00aee-108">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="00aee-108">Change properties for a specific user account</span></span>

<span data-ttu-id="00aee-p101">Identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="00aee-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="00aee-111">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="00aee-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="00aee-112">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="00aee-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="00aee-113">-FacsimilieTelephoneNumber "\<numéro de télécopie>"</span><span class="sxs-lookup"><span data-stu-id="00aee-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="00aee-114">-GivenName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="00aee-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="00aee-115">-Surname "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="00aee-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="00aee-116">-Mobile "\<N° de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="00aee-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="00aee-117">-JobTitle "\<fonction>"</span><span class="sxs-lookup"><span data-stu-id="00aee-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="00aee-118">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="00aee-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="00aee-119">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="00aee-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="00aee-120">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="00aee-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="00aee-121">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="00aee-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="00aee-122">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="00aee-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="00aee-123">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="00aee-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="00aee-124">-TelephoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="00aee-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="00aee-125">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="00aee-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="00aee-126">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="00aee-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="00aee-127">Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="00aee-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="00aee-128">Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="00aee-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="00aee-129">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-130">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-131">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **sort userPrincipalName** ) et l’envoyer à la commande **|** suivante ().</span><span class="sxs-lookup"><span data-stu-id="00aee-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-132">Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte ( **Sélectionnez userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="00aee-133">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="00aee-p102">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="00aee-136">Cet exemple affiche le nom d’utilisateur principal pour le compte l’utilisateur avec Caleb Sills comme nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="00aee-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="00aee-p103">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="00aee-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="00aee-139">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="00aee-139">Change properties for all user accounts</span></span>

<span data-ttu-id="00aee-p104">Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="00aee-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="00aee-142">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-143">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-144">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="00aee-145">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="00aee-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="00aee-p105">Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="00aee-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="00aee-148">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-149">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-150">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-151">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="00aee-152">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00aee-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="00aee-153">Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez la cmdlet **Set-MsolUser** et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="00aee-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="00aee-154">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="00aee-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="00aee-155">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="00aee-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="00aee-156">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00aee-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="00aee-157">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="00aee-157">Change properties for a specific user account</span></span>

<span data-ttu-id="00aee-158">Pour configurer les propriétés d’un compte d’utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés de définition ou de modification.</span><span class="sxs-lookup"><span data-stu-id="00aee-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="00aee-p107">Identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="00aee-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="00aee-161">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="00aee-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="00aee-162">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="00aee-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="00aee-163">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="00aee-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="00aee-164">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="00aee-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="00aee-165">-Fax "\<numéro de fax>"</span><span class="sxs-lookup"><span data-stu-id="00aee-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="00aee-166">-FirstName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="00aee-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="00aee-167">-LastName "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="00aee-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="00aee-168">-MobilePhone "\<numéro de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="00aee-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="00aee-169">-Office "\<emplacement du bureau>"</span><span class="sxs-lookup"><span data-stu-id="00aee-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="00aee-170">-PhoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="00aee-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="00aee-171">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="00aee-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="00aee-172">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="00aee-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="00aee-173">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="00aee-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="00aee-174">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="00aee-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="00aee-175">-Title "\<intitulé du poste>"</span><span class="sxs-lookup"><span data-stu-id="00aee-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="00aee-176">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="00aee-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="00aee-177">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="00aee-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="00aee-178">Pour obtenir plus de paramètres, voir [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="00aee-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="00aee-179">Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="00aee-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="00aee-180">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-181">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-182">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **sort userPrincipalName** ) et l’envoyer à la commande **|** suivante ().</span><span class="sxs-lookup"><span data-stu-id="00aee-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-183">Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte ( **Sélectionnez userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="00aee-184">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="00aee-p108">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="00aee-187">Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="00aee-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="00aee-p109">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d’affichage. Voici un exemple de définition de l’emplacement d’utilisation de Belinda Newman en France, mais en spécifiant son nom d’affichage plutôt que son nom d’utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="00aee-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="00aee-190">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="00aee-190">Change properties for all user accounts</span></span>

<span data-ttu-id="00aee-p110">Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="00aee-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="00aee-193">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-194">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-195">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="00aee-196">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="00aee-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="00aee-197">Pour modifier les propriétés d’un ensemble spécifique de compte d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where**et **Set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="00aee-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="00aee-198">L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="00aee-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="00aee-199">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00aee-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="00aee-200">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-201">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="00aee-202">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="00aee-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="00aee-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00aee-203">See also</span></span>

[<span data-ttu-id="00aee-204">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="00aee-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="00aee-205">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="00aee-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="00aee-206">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="00aee-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
