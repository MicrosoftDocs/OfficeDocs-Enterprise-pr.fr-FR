---
title: Désactiver l’accès aux services lors de l’attribution des licences utilisateur
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Découvrez comment attribuer des licences à des comptes d’utilisateur et à désactiver des plans de service spécifiques en même temps à l’aide d’Office 365 PowerShell.
ms.openlocfilehash: b1fcd8afd9f9fee5b249752821385cd888519a37
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009469"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="d7d2e-103">Désactiver l’accès aux services lors de l’attribution des licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="d7d2e-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="d7d2e-p101">Les abonnements Office 365 sont fournis avec des plans de service pour des services individuels. Les administrateurs d'Office 365 ont souvent besoin de désactiver certains plans lors de l'attribution des licences aux utilisateurs. Avec les instructions fournies dans cet article, vous pouvez attribuer une licence Office 365 tout en désactivant des plans de service spécifiques à l'aide de PowerShell pour un ou plusieurs comptes d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d7d2e-107">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="d7d2e-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d7d2e-108">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="d7d2e-109">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-109">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="d7d2e-110">Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d7d2e-111">Ensuite, compilez une liste de services à activer.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-111">Next, compile a list of services to enable.</span></span> <span data-ttu-id="d7d2e-112">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-112">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="d7d2e-113">Pour le bloc de commande ci-dessous, renseignez le nom d’utilisateur principal du compte d’utilisateur, le numéro de référence SKU et la liste des plans de service pour activer et supprimer \< le texte explicatif, ainsi que les caractères et >.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-113">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="d7d2e-114">Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-114">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d7d2e-115">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d7d2e-116">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="d7d2e-117">Ensuite, exécutez la commande suivante pour afficher vos abonnements en cours :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-117">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="d7d2e-118">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d7d2e-119">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="d7d2e-120">Dans l'affichage de la commande  `Get-MsolAccountSku` :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-120">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="d7d2e-p105">**AccountSkuId** est un abonnement pour votre organisation au format \<OrganizationName>:\<Subscription>. La valeur \<OrganizationName> est fournie lorsque vous vous inscrivez à Office 365 et elle est propre à votre organisation. La valeur \<Subscription> désigne un abonnement spécifique. Par exemple, pour litwareinc:ENTERPRISEPACK, le nom de l’organisation est litwareinc, et le nom de l’abonnement est ENTERPRISEPACK (Office 365 Entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-p105">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="d7d2e-125">**ActiveUnits** représente le nombre de licences que vous avez achetées pour l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-125">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="d7d2e-126">**WarningUnits** représente le nombre de licences dans un abonnement que vous n'avez pas renouvelées et qui expireront après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-126">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="d7d2e-127">**ConsumedUnits** représente le nombre de licences que vous avez affectées à des utilisateurs de l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-127">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="d7d2e-p106">Notez la valeur AccountSkuId pour votre abonnement Office 365 contenant les utilisateurs pour lesquels vous souhaitez obtenir une licence. En outre, assurez-vous qu'il y a suffisamment de licences à attribuer (soustraire **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-p106">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="d7d2e-130">Ensuite, exécutez cette commande pour afficher les détails sur les plans de service Office 365 qui sont disponibles dans tous vos abonnements :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-130">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="d7d2e-131">À partir de l’affichage de cette commande, déterminez les plans de service que vous souhaitez désactiver lorsque vous attribuez des licences aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-131">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="d7d2e-132">Voici une liste partielle des plans de service et de leurs services Office 365 correspondants.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-132">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="d7d2e-133">Le tableau suivant présente les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-133">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="d7d2e-134">La liste de vos plans de services peut être différente.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-134">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="d7d2e-135">**Plan de services**</span><span class="sxs-lookup"><span data-stu-id="d7d2e-135">**Service plan**</span></span>|<span data-ttu-id="d7d2e-136">**Description**</span><span class="sxs-lookup"><span data-stu-id="d7d2e-136">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="d7d2e-137">Sway</span><span class="sxs-lookup"><span data-stu-id="d7d2e-137">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="d7d2e-138">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d7d2e-138">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="d7d2e-139">Yammer</span><span class="sxs-lookup"><span data-stu-id="d7d2e-139">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="d7d2e-140">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="d7d2e-140">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="d7d2e-141">Applications Microsoft 365 pour les entreprises *(précédemment nommé Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="d7d2e-141">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="d7d2e-142">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="d7d2e-142">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="d7d2e-143">Office</span><span class="sxs-lookup"><span data-stu-id="d7d2e-143">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="d7d2e-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d7d2e-144">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="d7d2e-145">Exchange Online (plan 2)</span><span class="sxs-lookup"><span data-stu-id="d7d2e-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="d7d2e-146">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="d7d2e-146">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="d7d2e-147">Maintenant que vous avez le paramètre AccountSkuId et les plans de service à désactiver, vous pouvez attribuer des licences pour un utilisateur ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="d7d2e-148">Pour un utilisateur unique</span><span class="sxs-lookup"><span data-stu-id="d7d2e-148">For a single user</span></span>

<span data-ttu-id="d7d2e-p108">Pour un utilisateur unique, renseignez le nom d'utilisateur principal du compte d'utilisateur, le paramètre AccountSkuId et la liste des plans de service à désactiver, et supprimez le texte explicatif et les caractères \< et >. Ensuite, exécutez les commandes qui en résultent à l'invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-p108">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

<span data-ttu-id="d7d2e-151">Voici un exemple de bloc de commande pour le compte nommé belindan@contoso.com, pour la licence contoso:ENTERPRISEPACK, et les plans de service à désactiver sont RMS_S_ENTERPRISE, SWAY, INTUNE_O365 et YAMMER_ENTERPRISE :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a><span data-ttu-id="d7d2e-152">Pour plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d7d2e-152">For multiple users</span></span>

<span data-ttu-id="d7d2e-p109">Pour effectuer cette tâche d'administration pour plusieurs utilisateurs, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs UserPrincipalName et UsageLocation. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-p109">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="d7d2e-155">Ensuite, remplissez l’emplacement des fichiers CSV d’entrée et de sortie, l’ID de référence du compte et la liste des plans de service à désactiver, puis exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="d7d2e-156">Ce bloc de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="d7d2e-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="d7d2e-157">affiche le nom d’utilisateur principal de chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="d7d2e-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="d7d2e-158">attribue des licences personnalisées à chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="d7d2e-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="d7d2e-159">crée un fichier CSV avec tous les utilisateurs qui ont été traités et affiche l’état de leur licence.</span><span class="sxs-lookup"><span data-stu-id="d7d2e-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d7d2e-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7d2e-160">See also</span></span>

[<span data-ttu-id="d7d2e-161">Désactiver l'accès aux services Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7d2e-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="d7d2e-162">Désactivation de l'accès à Sway avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7d2e-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="d7d2e-163">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7d2e-163">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d7d2e-164">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7d2e-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
