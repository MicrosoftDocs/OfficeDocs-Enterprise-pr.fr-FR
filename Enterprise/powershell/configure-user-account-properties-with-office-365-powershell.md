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
ms.openlocfilehash: 3d81a7e5860b086fd411e8e6fcaab44568e890d5
ms.sourcegitcommit: 4d29b00a57c22225f2cdd592064ee8b6e575fceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "37411513"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="18aa0-103">Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="18aa0-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="18aa0-104">**Résumé :** Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="18aa0-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="18aa0-105">Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateur de votre client 365 Office, vous pouvez également utiliser Office 365 PowerShell et effectuer quelques opérations que le centre d’administration ne peut pas faire.</span><span class="sxs-lookup"><span data-stu-id="18aa0-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="18aa0-106">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="18aa0-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="18aa0-107">Pour configurer les propriétés des comptes d’utilisateur avec le module Azure Active Directory PowerShell pour Graph, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="18aa0-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18aa0-108">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="18aa0-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="18aa0-109">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="18aa0-109">Change properties for a specific user account</span></span>

<span data-ttu-id="18aa0-p101">Identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="18aa0-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="18aa0-112">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="18aa0-113">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="18aa0-114">-FacsimilieTelephoneNumber "\<numéro de télécopie>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="18aa0-115">-GivenName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="18aa0-116">-Surname "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="18aa0-117">-Mobile "\<N° de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="18aa0-118">-JobTitle "\<fonction>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="18aa0-119">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="18aa0-120">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="18aa0-121">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="18aa0-122">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="18aa0-123">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="18aa0-124">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="18aa0-125">-TelephoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="18aa0-126">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="18aa0-127">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="18aa0-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="18aa0-128">Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="18aa0-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="18aa0-129">Vous définissez la propriété **mail** avec le paramètre **-OtherMails** .</span><span class="sxs-lookup"><span data-stu-id="18aa0-129">You set the **Mail** property with the **-OtherMails** parameter.</span></span>
>
 
<span data-ttu-id="18aa0-130">Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="18aa0-130">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="18aa0-131">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-131">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-132">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-133">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-133">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-134">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-134">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="18aa0-135">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-135">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="18aa0-p102">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18aa0-138">Cet exemple affiche le nom d’utilisateur principal pour le compte l’utilisateur avec Caleb Sills comme nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="18aa0-138">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18aa0-p103">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="18aa0-141">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="18aa0-141">Change properties for all user accounts</span></span>

<span data-ttu-id="18aa0-p104">Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="18aa0-144">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-144">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-145">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-145">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-146">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-146">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="18aa0-147">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="18aa0-147">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="18aa0-p105">Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="18aa0-150">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-150">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-151">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-151">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-152">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-152">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-153">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-153">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="18aa0-154">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18aa0-154">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="18aa0-155">Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, vous utilisez la cmdlet Set-MsolUser et spécifiez les propriétés à définir ou à modifier.</span><span class="sxs-lookup"><span data-stu-id="18aa0-155">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18aa0-156">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="18aa0-156">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="18aa0-157">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="18aa0-157">Change properties for a specific user account</span></span>

<span data-ttu-id="18aa0-158">Pour configurer les propriétés d’un compte d’utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) et spécifiez les propriétés de définition ou de modification.</span><span class="sxs-lookup"><span data-stu-id="18aa0-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18aa0-p106">Identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="18aa0-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="18aa0-161">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="18aa0-162">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="18aa0-163">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="18aa0-164">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="18aa0-165">-Fax "\<numéro de fax>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="18aa0-166">-FirstName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="18aa0-167">-LastName "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="18aa0-168">-MobilePhone "\<numéro de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="18aa0-169">-Office "\<emplacement du bureau>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="18aa0-170">-PhoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="18aa0-171">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="18aa0-172">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="18aa0-173">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="18aa0-174">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="18aa0-175">-Title "\<intitulé du poste>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="18aa0-176">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="18aa0-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="18aa0-177">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="18aa0-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="18aa0-178">Pour obtenir plus de paramètres, voir [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="18aa0-178">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="18aa0-179">Vous définissez la propriété **mail** avec le paramètre **-AlternateEmailAddresses** .</span><span class="sxs-lookup"><span data-stu-id="18aa0-179">You set the **Mail** property with the **-AlternateEmailAddresses** parameter.</span></span>
>
 
<span data-ttu-id="18aa0-180">Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="18aa0-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="18aa0-181">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-182">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-183">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-184">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="18aa0-185">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="18aa0-p107">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18aa0-188">Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="18aa0-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18aa0-p108">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d’affichage. Voici un exemple de définition de l’emplacement d’utilisation de Belinda Newman en France, mais en spécifiant son nom d’affichage plutôt que son nom d’utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="18aa0-191">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="18aa0-191">Change properties for all user accounts</span></span>

<span data-ttu-id="18aa0-p109">Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="18aa0-194">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-195">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-196">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="18aa0-197">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="18aa0-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="18aa0-p110">Pour modifier les propriétés d'un ensemble spécifique de comptes d'utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where-Object** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="18aa0-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="18aa0-200">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18aa0-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="18aa0-201">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-202">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where-Object {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="18aa0-203">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="18aa0-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="18aa0-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18aa0-204">See also</span></span>

[<span data-ttu-id="18aa0-205">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="18aa0-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="18aa0-206">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="18aa0-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="18aa0-207">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="18aa0-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
