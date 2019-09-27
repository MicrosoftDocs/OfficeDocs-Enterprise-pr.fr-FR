---
title: Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: Admin
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
search.appverid:
- MET150
description: Utilisation d’Office 365 PowerShell pour attribuer une licence Office 365 à des utilisateurs sans licence.
ms.openlocfilehash: 1f12c7b55e6766db5b2afc661ee5337448336ba1
ms.sourcegitcommit: 71e6a99fb585b4eb1aea3f215c234688f28d2050
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "37273679"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="dbc0c-103">Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbc0c-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="dbc0c-104">**Résumé :**  Utilisation d’Office 365 PowerShell pour attribuer une licence Office 365 à des utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="dbc0c-105">Les utilisateurs ne peuvent pas utiliser les services Office 365 tant que leur compte n’a pas reçu une licence d’un plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="dbc0c-106">Vous pouvez utiliser Office 365 PowerShell pour affecter rapidement des licences à des comptes sans licence.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="dbc0c-107">Un emplacement doit être attribué aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="dbc0c-108">Vous pouvez effectuer cette opération à partir des propriétés d’un compte d’utilisateur dans le centre d’administration 365 de Microsoft ou à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dbc0c-109">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="dbc0c-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dbc0c-110">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="dbc0c-111">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="dbc0c-112">Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="dbc0c-113">Ensuite, vérifiez que l’emplacement d’utilisation est affecté au compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="dbc0c-114">S’il n’y a pas d’emplacement d’utilisation attribué, vous pouvez en affecter un à l’aide des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="dbc0c-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="dbc0c-115">Enfin, spécifiez le nom de connexion de l’utilisateur et le nom du plan de licence et exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="dbc0c-116">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="dbc0c-117">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="dbc0c-118">Exécutez la commande **Get-MsolAccountSku** pour afficher les plans de gestion des licences disponibles et le nombre de licences disponibles dans chaque plan de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="dbc0c-119">Le nombre de licences disponibles pour chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="dbc0c-120">Pour plus d’informations sur les plans de licence, les licences et les services, voir [View licenses and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="dbc0c-121">Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="dbc0c-122">Vous pouvez uniquement attribuer des licences à des comptes d’utilisateur dont la propriété **UsageLocation** est définie sur un code ISO 3166-1 alpha-2 valide.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="dbc0c-123">Par exemple, US pour les États-Unis et FR pour la France.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="dbc0c-124">Certains services Office 365 ne sont pas disponibles dans certains pays.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="dbc0c-125">Pour plus d’informations, consultez la rubrique [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="dbc0c-126">Pour rechercher les comptes qui n’ont pas de valeur **UsageLocation** , exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="dbc0c-127">Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="dbc0c-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="dbc0c-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="dbc0c-129">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="dbc0c-130">Attribution de licences à des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="dbc0c-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="dbc0c-131">Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="dbc0c-132">Cet exemple attribue une licence du plan de gestion des licences **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) à l’utilisateur sans licence **\@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="dbc0c-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="dbc0c-133">Pour attribuer une licence à un grand nombre d’utilisateurs sans licence, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="dbc0c-134">Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="dbc0c-135">Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="dbc0c-136">Cet exemple attribue des licences à tous les utilisateurs sans licence à partir du plan de gestion des licences **litwareinc : ENTERPRISEPACK** (Office 365 Enterprise E3) :</span><span class="sxs-lookup"><span data-stu-id="dbc0c-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="dbc0c-137">Cet exemple attribue ces mêmes licences aux utilisateurs sans licence du département des ventes aux États-Unis :</span><span class="sxs-lookup"><span data-stu-id="dbc0c-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dbc0c-138">Déplacer un utilisateur vers un autre abonnement (plan de licence) avec le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="dbc0c-138">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dbc0c-139">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-139">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="dbc0c-140">Ensuite, obtenez le nom de connexion du compte d’utilisateur pour lequel vous souhaitez des abonnements de commutateur, également appelé nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-140">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="dbc0c-141">Ensuite, répertoriez les abonnements (plans de licence) de votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-141">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="dbc0c-142">Ensuite, répertoriez les abonnements que le compte d’utilisateur possède actuellement avec ces commandes.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-142">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```
$userUPN=”<user account UPN>”
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="dbc0c-143">Identifiez l’abonnement dont dispose l’utilisateur (abonnement FROM) et l’abonnement que l’utilisateur déplace (l’abonnement à).</span><span class="sxs-lookup"><span data-stu-id="dbc0c-143">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="dbc0c-144">Enfin, spécifiez les noms d’abonnement à et à (numéros de référence SKU) et exécutez ces commandes.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-144">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="dbc0c-145">Vous pouvez vérifier la modification de l’abonnement pour le compte d’utilisateur à l’aide de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="dbc0c-145">You can verify the change in subscription for the user account with these commands.</span></span>

```
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a><span data-ttu-id="dbc0c-146">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="dbc0c-146">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="dbc0c-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbc0c-147">See also</span></span>

[<span data-ttu-id="dbc0c-148">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbc0c-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dbc0c-149">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbc0c-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dbc0c-150">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="dbc0c-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
