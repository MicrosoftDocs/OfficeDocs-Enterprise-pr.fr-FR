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
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="3eeaa-103">Configurer les propriétés des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eeaa-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="3eeaa-104">**Résumé :** Utilisez Office 365 PowerShell pour configurer les propriétés d'un ou de plusieurs comptes d'utilisateur dans votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="3eeaa-105">Bien que vous puissiez utiliser le centre d'administration Office 365 pour configurer les propriétés des comptes d'utilisateur de votre client Office 365, vous pouvez également utiliser Office 365 PowerShell et effectuer certaines actions que le centre d'administration Office 365 ne vous permet pas de réaliser.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="3eeaa-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3eeaa-106">Before you begin</span></span>

<span data-ttu-id="3eeaa-p101">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="3eeaa-109">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="3eeaa-109">Change properties for a specific user account</span></span>

<span data-ttu-id="3eeaa-p102">Pour configurer les propriétés d'un compte d'utilisateur spécifique, vous utilisez la cmdlet [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) et spécifiez les propriétés à définir ou modifier. Cet exemple de commande remplace l'emplacement d'utilisation de Belinda Newman par France :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p102">To configure properties for a specific user account, you use the [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-p103">Vous identifiez le compte avec le paramètre **-UserPrincipalName** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="3eeaa-114">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="3eeaa-115">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="3eeaa-116">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="3eeaa-117">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="3eeaa-118">-Fax "\<numéro de fax>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="3eeaa-119">-FirstName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="3eeaa-120">-LastName "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="3eeaa-121">-MobilePhone "\<numéro de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="3eeaa-122">-Office "\<emplacement du bureau>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="3eeaa-123">-PhoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="3eeaa-124">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="3eeaa-125">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="3eeaa-126">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="3eeaa-127">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="3eeaa-128">-Title "\<intitulé du poste>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="3eeaa-129">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="3eeaa-130">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="3eeaa-131">Pour obtenir plus de paramètres, voir [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-131">See [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) for additional parameters.</span></span>
  
<span data-ttu-id="3eeaa-132">Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="3eeaa-133">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-134">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-135">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-136">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="3eeaa-137">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="3eeaa-p104">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3eeaa-140">Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3eeaa-p105">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="3eeaa-143">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3eeaa-143">Change properties for all user accounts</span></span>

<span data-ttu-id="3eeaa-p106">Pour modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-146">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-147">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-148">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="3eeaa-149">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3eeaa-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="3eeaa-p107">Pour modifier les propriétés d'un ensemble spécifique de comptes d'utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-MsolUser**, **Where-Object** et **Set-MsolUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-152">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-153">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-154">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where-Object {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-155">Définir la France comme emplacement de l'utilisateur ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="3eeaa-156">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="3eeaa-157">Utilisation du module Azure Active Directory V2 PowerShell pour configurer des propriétés de compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3eeaa-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="3eeaa-p108">Pour configurer les propriétés pour les comptes d'utilisateur avec le module Azure Active Directory V2 PowerShell, vous utilisez la cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier. Mais tout d'abord, vous devez vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article relatif à la [connexion avec le module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="3eeaa-161">Modification des propriétés d’un compte d’utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="3eeaa-161">Change properties for a specific user account</span></span>

<span data-ttu-id="3eeaa-162">Cet exemple de commande remplace l’emplacement d’utilisation de Belinda Newman par France :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-p109">Vous identifiez le compte avec le paramètre **-ObjectID** et définissez ou modifiez des propriétés spécifiques à l'aide de paramètres supplémentaires. Voici la liste des principaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="3eeaa-165">-Department "\<nom du service>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="3eeaa-166">-DisplayName "\<nom utilisateur complet>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="3eeaa-167">-FacsimilieTelephoneNumber "\<numéro de télécopie>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="3eeaa-168">-GivenName "\<prénom de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="3eeaa-169">-Surname "\<nom de famille de l’utilisateur>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="3eeaa-170">-Mobile "\<N° de téléphone portable>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="3eeaa-171">-JobTitle "\<fonction>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="3eeaa-172">-PreferredLanguage "\<langue>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="3eeaa-173">-StreetAddress "\<adresse>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="3eeaa-174">-City "\<nom de la ville>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="3eeaa-175">-State "\<nom de l’État>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="3eeaa-176">-PostalCode "\<code postal>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="3eeaa-177">-Country "\<nom du pays>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="3eeaa-178">-TelephoneNumber "\<numéro de téléphone du bureau>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="3eeaa-179">-UsageLocation "\<code de région ou de pays à 2 caractères>"</span><span class="sxs-lookup"><span data-stu-id="3eeaa-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="3eeaa-180">Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="3eeaa-181">Pour consulter des paramètres supplémentaires, reportez-vous à [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="3eeaa-182">Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="3eeaa-183">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-184">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-185">Trier par ordre alphabétique la liste des noms d’utilisateur principaux ( **Sort-Object UserPrincipalName** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-186">Afficher uniquement la propriété Nom d'utilisateur principal pour chaque compte ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="3eeaa-187">Afficher un écran à la fois ( **Plus** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="3eeaa-p110">Cette commande répertorie tous vos comptes. Si vous souhaitez afficher le nom d'utilisateur principal d'un compte en fonction de son nom d'affichage (prénom et nom), insérez la variable **$userName** ci-dessous (supprimez les caractères \< et >), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3eeaa-190">Cet exemple affiche le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="3eeaa-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3eeaa-p111">En utilisant une variable **$upn**, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple de définition de l'emplacement d'utilisation de Belinda Newman en France, mais en spécifiant son nom d'affichage plutôt que son nom d'utilisateur principal :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="3eeaa-193">Modification des propriétés de tous les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3eeaa-193">Change properties for all user accounts</span></span>

<span data-ttu-id="3eeaa-p112">Afin de modifier les propriétés pour tous les utilisateurs, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser**. L'exemple suivant modifie l'emplacement d'utilisation pour tous les utilisateurs et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-196">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-197">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-198">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="3eeaa-199">Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3eeaa-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="3eeaa-p113">Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser la combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser**. L’exemple suivant modifie l’emplacement d’utilisation pour tous les utilisateurs du service Accounting et définit la France comme nouvel emplacement :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="3eeaa-202">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eeaa-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3eeaa-203">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-204">Rechercher tous les comptes utilisateurs dont la propriété Department est définie sur « Accounting » ( **Where {$_.Department -eq "Accounting"}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3eeaa-205">Définir la France comme emplacement de l’utilisateur ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3eeaa-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3eeaa-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eeaa-206">See also</span></span>

#### 

[<span data-ttu-id="3eeaa-207">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eeaa-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3eeaa-208">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eeaa-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3eeaa-209">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="3eeaa-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

