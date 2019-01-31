---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651179"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1b7bb-103">Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b7bb-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1b7bb-104">**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="1b7bb-p101">Les utilisateurs ne peuvent pas utiliser les services Office 365 jusqu'à ce que leur compte a été attribué une licence d’un plan de gestion des licences. Vous pouvez utiliser Office 365 PowerShell pour attribuer des licences rapidement aux comptes sans licence.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1b7bb-107">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="1b7bb-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1b7bb-108">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="1b7bb-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="1b7bb-109">Ensuite, répertoriez les plans de licence pour votre client avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1b7bb-110">Ensuite, obtenir le nom de connexion du compte auquel vous souhaitez ajouter une licence, également connu sous le nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="1b7bb-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1b7bb-111">Enfin, spécifiez le nom de connexion utilisateur et le nom de plan de licence et exécuter ces commandes.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1b7bb-112">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1b7bb-113">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1b7bb-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1b7bb-p102">Exécutez la commande **Get-MsolAccountSku** pour afficher les plans de gestion de licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1b7bb-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1b7bb-117">Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="1b7bb-p103">Vous ne pouvez affecter des licences pour les comptes d’utilisateurs dont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, nous pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="1b7bb-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="1b7bb-122">Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="1b7bb-123">Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="1b7bb-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1b7bb-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="1b7bb-125">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="1b7bb-126">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1b7bb-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="1b7bb-127">Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="1b7bb-128">Cet exemple attribue une licence à partir de la **litwareinc : enterprisepack** (Office 365 entreprise E3) de planification de l' utilisateur sans licence **belindan@litwareinc.com**de gestion des licences :</span><span class="sxs-lookup"><span data-stu-id="1b7bb-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1b7bb-129">Pour attribuer une licence à de nombreux utilisateurs sans licence, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="1b7bb-p104">Vous ne pouvez pas affecter plusieurs licences à un utilisateur dans le plan de gestion des licences. Si vous n’avez pas suffisamment de licences disponibles, les licences sont attribuées aux utilisateurs dans l’ordre dans lequel ils sont renvoyés par l’applet de commande **Get-MsolUser** jusqu'à épuisement des licences disponibles.</span><span class="sxs-lookup"><span data-stu-id="1b7bb-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="1b7bb-132">Cet exemple attribue des licences à partir du plan de gestion des licences **litwareinc : enterprisepack** (Office 365 entreprise E3) pour tous les utilisateurs sans licence :</span><span class="sxs-lookup"><span data-stu-id="1b7bb-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="1b7bb-133">Cet exemple affecte ces mêmes licences aux utilisateurs sans licence dans le service des ventes aux États-Unis :</span><span class="sxs-lookup"><span data-stu-id="1b7bb-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="1b7bb-134">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="1b7bb-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="1b7bb-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b7bb-135">See also</span></span>

[<span data-ttu-id="1b7bb-136">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b7bb-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1b7bb-137">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b7bb-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1b7bb-138">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="1b7bb-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
