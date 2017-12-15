---
title: "Désactiver l’accès aux services Office 365 PowerShell"
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explique comment utiliser Office 365 PowerShell pour ajouter ou supprimer l’accès aux services Office 365 pour les utilisateurs de votre organisation."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="593db-103">Désactiver l’accès aux services Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="593db-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour ajouter ou supprimer l’accès aux services Office 365 pour les utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="593db-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="593db-p101">Lorsqu’un compte Office 365 est affecté une licence à partir d’un plan de gestion des licences, services Office 365 sont accessibles à l’utilisateur de cette licence. Toutefois, vous pouvez contrôler les services Office 365 que l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès à SharePoint Online, vous pouvez désactiver l’accès. En fait, vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès à n’importe quel nombre de services pour :</span><span class="sxs-lookup"><span data-stu-id="593db-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="593db-109">un compte individuel ;</span><span class="sxs-lookup"><span data-stu-id="593db-109">An individual account.</span></span>
    
- <span data-ttu-id="593db-110">un groupe de comptes ;</span><span class="sxs-lookup"><span data-stu-id="593db-110">A group of accounts.</span></span>
    
- <span data-ttu-id="593db-111">tous les comptes de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="593db-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="593db-112">**Contenu :** [La version courte (instructions sans explications)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [La version longue (avec des explications détaillées sur les instructions)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Voir aussi](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="593db-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="593db-113">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="593db-113">Before you begin</span></span>
<span data-ttu-id="593db-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="593db-114"></span></span>

- <span data-ttu-id="593db-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="593db-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="593db-p103">L’applet de commande **Get-MsolAccountSku** vous permet d’afficher vos plans de gestion des licences disponibles et les services Office 365 disponibles de ces plans. Pour plus d’informations, voir[Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="593db-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="593db-119">Pour voir l’avant et après les résultats des procédures de cette rubrique, reportez-vous à la section [Afficher les détails de licences et le service de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="593db-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="593db-p104">Un script PowerShell est disponible qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation d’Office 365, y compris de balancement. Pour plus d’informations, consultez [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="593db-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="593db-123">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="593db-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="593db-124">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="593db-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="593db-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="593db-125"></span></span>

<span data-ttu-id="593db-p105">Cette section présente les procédures sans explication superflue ou alambiquée. Si vous avez des questions ou que vous souhaitez plus d'informations, vous pouvez lire le reste de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="593db-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="593db-128">Pour désactiver les services Office 365 pour les utilisateurs à partir d’un seul plan de gestion des licences, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="593db-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="593db-129">Identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="593db-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="593db-130">Cet exemple crée un objet **LicenseOptions** qui désactive les services Office Online et SharePoint Online dans le plan de licence nommé `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="593db-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="593db-131">Utilisez l’objet **LicenseOptions** à partir de l’étape 1 sur un ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="593db-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="593db-132">Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="593db-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="593db-133">Cet exemple crée un compte pour Allie Bellew qui attribue la licence et désactive les services décrits à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="593db-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="593db-134">Pour plus d’informations sur la création de comptes d’utilisateurs dans Office 365 PowerShell, voir [créer les comptes d’utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="593db-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="593db-135">Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="593db-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="593db-136">Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="593db-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="593db-137">Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence, spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK** ), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="593db-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="593db-138">Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="593db-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="593db-139">**Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="593db-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="593db-140">Cet exemple désactive les services pour des utilisateurs du service des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="593db-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="593db-141">**Utilisation d’une liste de comptes spécifiques** Pour ce faire, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="593db-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="593db-142">Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="593db-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="593db-143">Dans cet exemple, le fichier texte est C:\\Mes Documents\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="593db-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="593db-144">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="593db-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="593db-145">Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, consultez [désactivation de l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="593db-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="593db-146">Pour désactiver des services Office 365 pour les utilisateurs dans tous les plans de gestion des licences disponibles, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="593db-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="593db-147">Copiez et collez ce script dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="593db-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="593db-148">Personnalisez les valeurs suivantes pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="593db-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="593db-149">_<UndesirableService>_Dans cet exemple, nous allons utiliser Office Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="593db-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="593db-150">_<Account>_Dans cet exemple, nous allons utiliser belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="593db-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="593db-151">Le script personnalisé ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="593db-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="593db-p106">Enregistrez le script en tant que `RemoveO365Services.ps1` dans un emplacement facile à trouver. Pour cet exemple, nous allons enregistrer le fichier sous " `C:\\O365 Scripts`«.</span><span class="sxs-lookup"><span data-stu-id="593db-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="593db-154">Exécutez le script dans Office 365 PowerShell à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="593db-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="593db-155">Pour inverser les effets d’une de ces procédures (c'est-à-dire pour réactiver les services désactivés), exécuter la procédure, mais utiliser la valeur de `$null` pour le paramètre _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="593db-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="593db-156">Retour au début</span><span class="sxs-lookup"><span data-stu-id="593db-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="593db-157">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="593db-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="593db-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="593db-158"></span></span>

<span data-ttu-id="593db-p107">Par défaut, tous les services sont activés lorsque vous émettez une licence à l’aide d’Office 365 PowerShell. Et c’est souvent une bonne chose : cela signifie que vous pouvez rapidement et facilement attribuer des licences aux utilisateurs sans avoir à spécifier que chaque service soit activé tout au long du processus.</span><span class="sxs-lookup"><span data-stu-id="593db-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="593db-p108">Cela dit, toutefois, il est également vrai que vous pouvez souhaiter restreindre les services disponibles à certains de vos utilisateurs ; par exemple, peut-être que certains utilisateurs doivent accéder à Office Professionnel Plus, Skype pour Business Online et Exchange Online, mais ces mêmes utilisateurs ne devraient pas avoir accès à SharePoint Online ou sur Office Online. Vous pouvez restreindre comptes de cette manière ? En fait, vous pouvez. Pour expliquer comment cela fonctionne, prenons une approche en deux étapes pour la résolution de ce problème :</span><span class="sxs-lookup"><span data-stu-id="593db-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="593db-165">Attribuer à l’utilisateur une licence Office 365 qui active automatiquement tous les services.</span><span class="sxs-lookup"><span data-stu-id="593db-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="593db-166">Exécutez les deux commandes d’Office 365 PowerShell qui désactivent des services spécifiés pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="593db-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="593db-p109">Nous avons déjà prise en charge de l’étape 1 : notre (Belinda Newman) de l’utilisateur possède une licence de Office 365 qui lui permet d’accéder à tous les services d’Office 365. Toutefois, nous voulons modifier les comptes de Belinda afin qu’elle n’a pas accès à SharePoint Online ( `SHAREPOINTENTERPRISE`) ou d’Office Online ( `SHAREPOINTWAC`). Mais comment sommes-nous censés le faire ?</span><span class="sxs-lookup"><span data-stu-id="593db-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="593db-p110">Voici comment. Dans un premier temps, nous allons utiliser l’applet de commande **New-MsolLicenseOptions** pour créer un objet **LicenseOption** qui contient les services que nous désactivés. Dans les cas de Belinda, nous voulons désactiver `SHAREPOINTENTERPRISE` et `SHAREPOINTWAC`, de sorte que nous utilisons cette commande :</span><span class="sxs-lookup"><span data-stu-id="593db-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="593db-p111">Voyez comment cela fonctionne ? Vous spécifiez le plan de gestion des licences ( `litwareinc:ENTERPRISEPACK`), puis indiquez chacun des services que vous souhaitez désactivés, la séparation de ces services à l’aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="593db-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="593db-p112">Assurez-vous que vous stockez votre nouvel objet **LicenseOption** dans une variable. Dans l’exemple précédent, nous avons utilisé `$x`, bien que vous pouvez utiliser n’importe quel nom de variable valide de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="593db-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="593db-177">À ce stade, nous pouvons utiliser la commande suivante pour désactiver l’accès de Belinda à deux services :</span><span class="sxs-lookup"><span data-stu-id="593db-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="593db-p113">Rien de trop fantaisiste ici, soit : nous il vous suffit d’appeler l’applet de commande **Set-MsolUserLicense** et inclure le paramètre _LicenseOptions_ , ainsi que la variable ( `$x`) contenant les plans que vous souhaitez désactiver. Et ce qui nous maintenant si nous jetons un coup de œil sur les informations de licence de Belinda en exécutant la commande : `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Nous voir ceci :</span><span class="sxs-lookup"><span data-stu-id="593db-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="593db-p114">Sympa, non ? Et, bien sûr, nous pouvions faire cette même chose à plusieurs utilisateurs si nous le voulions. Par exemple, ces commandes de désactiver les deux mêmes services pour tous les utilisateurs sous licence. Spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK** ), puis les exécuter.</span><span class="sxs-lookup"><span data-stu-id="593db-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="593db-p115">Gardez à l’esprit que Belinda a toujours une licence Office 365 ; Il est qu’à présent elle a accès à moins de services. Avant que nous avons désactivé les deux services, Belinda a eu accès à SharePoint, les OneDrive et les échanges de News en ligne sites :</span><span class="sxs-lookup"><span data-stu-id="593db-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Utilisateur avec accès à SharePoint.](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="593db-188">Maintenant, elle ne dispose plus de ces options :</span><span class="sxs-lookup"><span data-stu-id="593db-188">Now those options are no longer available to her:</span></span>
  
![Utilisateur sans accès à SharePoint.](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="593db-190">C’est exactement le résultat que nous attendions.</span><span class="sxs-lookup"><span data-stu-id="593db-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="593db-p116">Et que se passe-t-il si nous changeons d’avis plus tard : il est possible de réactiver ces services ? Absolument. Pour réactiver tous les services pour un utilisateur, il vous suffit d’utiliser cette commande pour créer l’objet **LicenseOption** suivant :</span><span class="sxs-lookup"><span data-stu-id="593db-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="593db-p117">Que fait cette commande ? Pour commencer, la constante Windows PowerShell `$null` signifie « rien ». (Ou, dans la langue du contact technique légèrement plus, cela signifie une « valeur null ».) Comme vous vous rappelez, lorsque nous utilisons la cmdlet **New-MsolLicenseOptions** nous avons indiquer les services que nous souhaitons que désactivé. Dans ce cas, nous ne voulons pas les services à désactiver. Qui peut vous amener à penser que nous pourrions utiliser une commande similaire à la suivante, une commande où nous ne spécifiez pas de valeur pour le paramètre _DisabledPlans_ :</span><span class="sxs-lookup"><span data-stu-id="593db-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="593db-p118">Toutefois, qui ne fonctionnera pas. Au lieu de cela, il génère un message d’erreur :</span><span class="sxs-lookup"><span data-stu-id="593db-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="593db-201">Heureusement pour nous, affectant la valeur du paramètre `$null` fonctionne :</span><span class="sxs-lookup"><span data-stu-id="593db-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="593db-202">Cela signifie simplement que, lorsque nous exécutons l’applet de commande **Set-MsolUserLicense** , nous allons indiquant **Ensemble-MsolUserLicense** que nous ne souhaitez pas Belinda pour que les services désactivés :</span><span class="sxs-lookup"><span data-stu-id="593db-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="593db-203">Logiquement, si aucun des services n’est désactivé, cela signifie que tous les services sont activés.</span><span class="sxs-lookup"><span data-stu-id="593db-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="593db-p119">Maintenant que vous comprenez comment tout cela fonctionne, nous allons vous montrer comment vous pouvez émettre une licence et désactiver les services spécifiés et avec la même commande. Qui semble assez impressionnant, mais, pour être honnête, il est vraiment très simple : vous suffit de l’ajouter à la fois _AddLicenses_ et les paramètres de _LicenseOptions_ dans la même commande. En d’autres termes, vous créez tout d’abord votre objet **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="593db-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="593db-207">Et puis, comme indiqué précédemment, vous utilisez à la fois les _AddLicenses_ et les paramètres _LicenseOptions_ dans votre commande :</span><span class="sxs-lookup"><span data-stu-id="593db-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="593db-208">Que commande émettra Belinda Newman une nouvelle licence, mais une licence dans le Skype pour Business Online ( `SHAREPOINTWAC`) et SharePoint Online ( `SHAREPOINTENTERPRISE`) sont tous les deux désactivés.</span><span class="sxs-lookup"><span data-stu-id="593db-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="593db-209">Retour au début</span><span class="sxs-lookup"><span data-stu-id="593db-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="593db-210">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="593db-210">New to Office 365?</span></span>
<span data-ttu-id="593db-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="593db-211"></span></span>

||
|:-----|
|<span data-ttu-id="593db-p120">![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les **professionnels de l’informatique et les administrateurs d’Office 365**, proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="593db-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="593db-214">See also</span><span class="sxs-lookup"><span data-stu-id="593db-214">See also</span></span>
<span data-ttu-id="593db-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="593db-215"></span></span>

<span data-ttu-id="593db-216">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="593db-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="593db-217">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="593db-218">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="593db-219">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="593db-220">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="593db-221">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="593db-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="593db-222">Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="593db-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="593db-223">Get-Content.</span><span class="sxs-lookup"><span data-stu-id="593db-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="593db-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="593db-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="593db-225">Nouvelle-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="593db-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="593db-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="593db-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="593db-227">Nouvelle-MsolUser</span><span class="sxs-lookup"><span data-stu-id="593db-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="593db-228">Ensemble-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="593db-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="593db-229">ForEach-Object.</span><span class="sxs-lookup"><span data-stu-id="593db-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="593db-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="593db-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="593db-231">Retour au début</span><span class="sxs-lookup"><span data-stu-id="593db-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

