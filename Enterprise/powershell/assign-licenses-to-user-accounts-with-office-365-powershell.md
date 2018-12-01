---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123291"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c8452-103">Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8452-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c8452-104">**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="c8452-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="c8452-p101">Gestion des licences des comptes d’utilisateurs dans Office 365 sont important, car les utilisateurs ne peuvent pas utiliser tous les services Office 365 jusqu'à ce que leur compte a été accordé sous licence. Vous pouvez utiliser Office 365 PowerShell assigner des licences à des comptes sans licence, en particulier de plusieurs comptes.</span><span class="sxs-lookup"><span data-stu-id="c8452-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="c8452-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="c8452-107">Before you begin</span></span>
<span data-ttu-id="c8452-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="c8452-108"></span></span>

- <span data-ttu-id="c8452-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c8452-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c8452-p103">Utilisez l’applet de commande **Get-MsolAccountSku** pour afficher les plans de gestion de licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c8452-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c8452-114">Pour rechercher les comptes sans licence dans votre organisation, exécutez la commande`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="c8452-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="c8452-p104">Vous pouvez affecter des licences uniquement aux comptes d’utilisateurs dont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, nous pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="c8452-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="c8452-p105">Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez la commande `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Pour définir la valeur **UsageLocation** sur un compte, utilisez la syntaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Par exemple, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="c8452-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="c8452-122">Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le `-All` paramètre, seuls les 500 premières comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="c8452-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="c8452-123">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c8452-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="c8452-124">Pour attribuer une licence à un utilisateur, utilisez la syntaxe suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c8452-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="c8452-125">Cet exemple attribue une licence à partir de la `litwareinc:ENTERPRISEPACK` plan de licences (Office 365 entreprise E3) à l’utilisateur sans licence `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="c8452-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c8452-126">Pour attribuer une licence à plusieurs utilisateurs sans licence, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="c8452-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="c8452-127">**Remarques**</span><span class="sxs-lookup"><span data-stu-id="c8452-127">**Notes**</span></span>
  
- <span data-ttu-id="c8452-128">Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="c8452-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="c8452-129">Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.</span><span class="sxs-lookup"><span data-stu-id="c8452-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="c8452-130">Cet exemple attribue des licences à partir de la `litwareinc:ENTERPRISEPACK` plan de licences (Office 365 entreprise E3) à tous les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="c8452-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="c8452-131">Dans cet exemple, les mêmes licences sont attribuées à des utilisateurs sans licence du département des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="c8452-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="c8452-132">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="c8452-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="c8452-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8452-133">See also</span></span>
<span data-ttu-id="c8452-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="c8452-134"></span></span>

<span data-ttu-id="c8452-135">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c8452-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c8452-136">Créer des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c8452-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c8452-137">Supprimer et restaurer des comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c8452-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c8452-138">Bloquer les comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c8452-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c8452-139">Supprimer des licences à partir de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="c8452-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c8452-140">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c8452-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c8452-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="c8452-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="c8452-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c8452-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c8452-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="c8452-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="c8452-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c8452-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="c8452-145">Select-Object.</span><span class="sxs-lookup"><span data-stu-id="c8452-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="c8452-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c8452-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

