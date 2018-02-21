---
title: "Désactiver l’accès aux services Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explique comment utiliser Office 365 PowerShell pour désactiver l’accès aux services Office 365 pour les utilisateurs de votre organisation."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="92777-103">Désactiver l’accès aux services Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="92777-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour désactiver l’accès aux services Office 365 pour les utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="92777-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="92777-p101">Lorsqu’un compte Office 365 est affecté une licence à partir d’un plan de gestion des licences, services Office 365 sont accessibles à l’utilisateur de cette licence. Toutefois, vous pouvez contrôler les services Office 365 que l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès à SharePoint Online, vous pouvez désactiver l’accès. En fait, vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès à n’importe quel nombre de services pour :</span><span class="sxs-lookup"><span data-stu-id="92777-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="92777-109">un compte individuel ;</span><span class="sxs-lookup"><span data-stu-id="92777-109">An individual account.</span></span>
    
- <span data-ttu-id="92777-110">un groupe de comptes ;</span><span class="sxs-lookup"><span data-stu-id="92777-110">A group of accounts.</span></span>
    
- <span data-ttu-id="92777-111">tous les comptes de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="92777-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="92777-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="92777-112">Before you begin</span></span>
<span data-ttu-id="92777-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="92777-113"></span></span>

- <span data-ttu-id="92777-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="92777-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="92777-p103">L’applet de commande **Get-MsolAccountSku** vous permet d’afficher vos plans de gestion des licences disponibles et les services Office 365 disponibles de ces plans. Pour plus d’informations, voir [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="92777-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="92777-118">Pour voir l’avant et après les résultats des procédures de cette rubrique, reportez-vous à la section [Afficher les détails de licences et le service de compte avec Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="92777-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="92777-p104">Un script PowerShell est disponible qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation d’Office 365, y compris de balancement. Pour plus d’informations, consultez [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="92777-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="92777-122">Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le paramètre _All_ , seuls les comptes de 500 utilisateur premier sont retournés.</span><span class="sxs-lookup"><span data-stu-id="92777-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="92777-123">Services Office 365 spécifiques pour des utilisateurs spécifiques pour un seul plan de gestion des licences</span><span class="sxs-lookup"><span data-stu-id="92777-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="92777-124">Pour désactiver un ensemble spécifique de services Office 365 pour les utilisateurs à partir d’un seul plan de gestion des licences, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="92777-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="92777-125">Identifier les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="92777-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="92777-126">L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office Online et SharePoint Online dans le plan de licence nommé `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="92777-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="92777-127">Utilisez l’objet **LicenseOptions** à partir de l’étape 1 sur un ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="92777-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="92777-128">Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="92777-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="92777-129">L’exemple suivant crée un nouveau compte pour Allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="92777-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="92777-130">Pour plus d’informations sur la création de comptes d’utilisateurs dans Office 365 PowerShell, voir [créer les comptes d’utilisateurs avec Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="92777-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="92777-131">Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="92777-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="92777-132">Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="92777-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="92777-133">Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence, spécifiez le nom de votre plan d’Office 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple, **litwareinc:ENTERPRISEPACK**), puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="92777-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="92777-134">Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="92777-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="92777-135">**Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="92777-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="92777-136">L’exemple suivant désactive les services pour les utilisateurs du service des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="92777-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="92777-137">**Utilisation d’une liste de comptes spécifiques** Pour ce faire, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="92777-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="92777-138">Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="92777-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="92777-139">Dans cet exemple, le fichier texte est C:\\Mes Documents\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="92777-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="92777-140">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="92777-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="92777-141">Pour désactiver les services Office 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, consultez [désactivation de l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="92777-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="92777-142">Services Office 365 spécifiques pour les utilisateurs de tous les plans de gestion des licences</span><span class="sxs-lookup"><span data-stu-id="92777-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="92777-143">Pour désactiver des services Office 365 pour les utilisateurs dans tous les plans de gestion des licences disponibles, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="92777-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="92777-144">Copiez et collez ce script dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="92777-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="92777-145">Personnalisez les valeurs suivantes pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="92777-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="92777-146">_<UndesirableService>_Dans cet exemple, nous allons utiliser Office Online et SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="92777-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="92777-147">_<Account>_Dans cet exemple, nous allons utiliser belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="92777-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="92777-148">Le script personnalisé ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="92777-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="92777-p105">Enregistrez le script en tant que `RemoveO365Services.ps1` dans un emplacement facile à trouver. Pour cet exemple, nous allons enregistrer le fichier sous `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="92777-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="92777-151">Exécutez le script dans Office 365 PowerShell à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="92777-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="92777-152">Pour inverser les effets d’une de ces procédures (c'est-à-dire pour réactiver les services désactivés), exécuter la procédure, mais utiliser la valeur de `$null` pour le paramètre _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="92777-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="92777-153">Retour au début</span><span class="sxs-lookup"><span data-stu-id="92777-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="92777-154">Tous les services Office 365 pour tous les utilisateurs pour un seul plan de gestion des licences</span><span class="sxs-lookup"><span data-stu-id="92777-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="92777-155">Pour désactiver tous les services Office 365 pour tous les utilisateurs dans un plan de gestion des licences spécifique, spécifiez le nom de plan licence pour $acctSKU (par exemple, **litwareinc:ENTERPRISEPACK**) et puis exécutez ces commandes dans la fenêtre de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="92777-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="92777-156">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="92777-156">New to Office 365?</span></span>
<span data-ttu-id="92777-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="92777-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="92777-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92777-158">See also</span></span>
<span data-ttu-id="92777-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="92777-159"></span></span>

<span data-ttu-id="92777-160">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="92777-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="92777-161">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="92777-162">Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="92777-163">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="92777-164">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="92777-165">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="92777-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="92777-166">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="92777-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="92777-167">Get-Content.</span><span class="sxs-lookup"><span data-stu-id="92777-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="92777-168">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="92777-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="92777-169">Nouvelle-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="92777-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="92777-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="92777-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="92777-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="92777-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="92777-172">Ensemble-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="92777-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="92777-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="92777-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="92777-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="92777-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

