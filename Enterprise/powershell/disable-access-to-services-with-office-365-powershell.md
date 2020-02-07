---
title: Désactiver l’accès aux services Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilisez Office 365 PowerShell pour désactiver l’accès aux services 365 Office pour les utilisateurs.
ms.openlocfilehash: eb6099ce5a41d0ea0d09aba0b737be00912ffbdc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841570"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="ad7be-103">Désactiver l’accès aux services Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad7be-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="ad7be-104">Lorsqu’un compte Office 365 est affecté à une licence d’un plan de gestion des licences, les services Office 365 sont mis à la disposition de l’utilisateur à partir de cette licence.</span><span class="sxs-lookup"><span data-stu-id="ad7be-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="ad7be-105">Toutefois, vous pouvez contrôler les services Office 365 auxquels l’utilisateur peut accéder.</span><span class="sxs-lookup"><span data-stu-id="ad7be-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="ad7be-106">Par exemple, même si la licence autorise l’accès au service SharePoint Online, vous pouvez désactiver l’accès à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="ad7be-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="ad7be-107">Vous pouvez utiliser PowerShell pour désactiver l’accès à n’importe quel nombre de services pour un plan de gestion des licences spécifique pour :</span><span class="sxs-lookup"><span data-stu-id="ad7be-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="ad7be-108">un compte individuel ;</span><span class="sxs-lookup"><span data-stu-id="ad7be-108">An individual account.</span></span>
- <span data-ttu-id="ad7be-109">un groupe de comptes ;</span><span class="sxs-lookup"><span data-stu-id="ad7be-109">A group of accounts.</span></span>
- <span data-ttu-id="ad7be-110">tous les comptes de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="ad7be-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="ad7be-111">Il existe des dépendances de service Office 365 qui peuvent vous empêcher de désactiver un service spécifié lorsque d’autres services dépendent de lui.</span><span class="sxs-lookup"><span data-stu-id="ad7be-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ad7be-112">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad7be-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ad7be-113">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ad7be-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ad7be-114">Ensuite, utilisez cette commande pour afficher vos plans de gestion des licences disponibles, également appelés AccountSkuIds :</span><span class="sxs-lookup"><span data-stu-id="ad7be-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="ad7be-115">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="ad7be-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ad7be-116">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad7be-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="ad7be-117">Pour plus d’informations, voir [afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ad7be-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ad7be-118">Pour afficher les résultats avant et après des procédures de cette rubrique, voir [View Account License and service Details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ad7be-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ad7be-119">Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ad7be-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="ad7be-120">Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Office 365, y compris Sway.</span><span class="sxs-lookup"><span data-stu-id="ad7be-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="ad7be-121">Pour plus d’informations, reportez-vous à la rubrique [désactiver l’accès à Sway avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ad7be-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="ad7be-122">Désactiver des services Office 365 spécifiques pour des utilisateurs spécifiques pour un plan de gestion des licences spécifique</span><span class="sxs-lookup"><span data-stu-id="ad7be-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="ad7be-123">Pour désactiver un ensemble spécifique de services Office 365 pour les utilisateurs pour un plan de gestion de licences spécifique, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ad7be-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="ad7be-124">Étape 1 : identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7be-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="ad7be-125">L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office et SharePoint Online dans le plan de gestion des licences `litwareinc:ENTERPRISEPACK` nommé (Office 365 entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="ad7be-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="ad7be-126">Étape 2 : utilisez l’objet **LicenseOptions** de l’étape 1 sur un ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ad7be-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="ad7be-127">Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7be-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="ad7be-128">L’exemple suivant crée un nouveau compte pour allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="ad7be-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="ad7be-129">Pour plus d’informations sur la création de comptes d’utilisateurs dans Office 365 PowerShell, consultez la rubrique [Create User Accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ad7be-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ad7be-130">Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7be-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="ad7be-131">Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="ad7be-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="ad7be-132">Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence existants, spécifiez le nom de votre plan Office 365 à partir de l’affichage de la cmdlet **Get-MsolAccountSku** (comme **litwareinc : ENTERPRISEPACK**), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad7be-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="ad7be-133">Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le paramètre _All_ , seuls les premiers comptes d’utilisateur 500 sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="ad7be-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="ad7be-134">Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="ad7be-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="ad7be-135">**Méthode 1. Filtrer les comptes en fonction d’un attribut de compte existant**</span><span class="sxs-lookup"><span data-stu-id="ad7be-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="ad7be-136">Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7be-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="ad7be-137">L’exemple suivant désactive les services pour les utilisateurs du service des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="ad7be-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="ad7be-138">**Méthode 2 : utiliser une liste de comptes spécifiques**</span><span class="sxs-lookup"><span data-stu-id="ad7be-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="ad7be-139">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ad7be-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ad7be-140">Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="ad7be-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="ad7be-141">Dans cet exemple, le fichier texte est C :\\My documents\\Accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="ad7be-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="ad7be-142">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7be-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="ad7be-143">Si vous souhaitez désactiver l’accès aux services pour plusieurs plans de gestion des licences, répétez les instructions ci-dessus pour chaque plan de gestion des licences, en vous assurant que :</span><span class="sxs-lookup"><span data-stu-id="ad7be-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="ad7be-144">Le plan de gestion des licences a été attribué aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ad7be-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="ad7be-145">Les services à désactiver sont disponibles dans le plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="ad7be-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="ad7be-146">Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, reportez-vous à la rubrique [désactiver l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="ad7be-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="ad7be-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad7be-147">See also</span></span>

[<span data-ttu-id="ad7be-148">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad7be-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ad7be-149">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad7be-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ad7be-150">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="ad7be-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
