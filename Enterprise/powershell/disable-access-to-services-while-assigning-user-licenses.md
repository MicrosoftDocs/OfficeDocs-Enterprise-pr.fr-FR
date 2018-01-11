---
title: "Désactiver l’accès aux services lors de l’attribution des licences utilisateur"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Découvrez comment attribuer des licences à des comptes d’utilisateur et à désactiver des plans de service spécifiques en même temps à l’aide d’Office 365 PowerShell."
ms.openlocfilehash: 96ce12f811ee147a92da6b6928c2f6e3391c9b1f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="7dbf1-103">Désactiver l’accès aux services lors de l’attribution des licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="7dbf1-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="7dbf1-104">**Résumé :** Découvrez comment attribuer des licences à des comptes d’utilisateur et désactiver des plans de service spécifiques en même temps à l’aide d’Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="7dbf1-p101">Les abonnements Office 365 sont fournis avec des plans de service pour des services individuels. Les administrateurs d'Office 365 ont souvent besoin de désactiver certains plans lors de l'attribution des licences aux utilisateurs. Avec les instructions fournies dans cet article, vous pouvez attribuer une licence Office 365 tout en désactivant des plans de service spécifiques à l'aide de PowerShell pour un ou plusieurs comptes d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7dbf1-108">Cet article est basé sur le travail de Siddhartha Parmar, ingénieur support de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="7dbf1-109">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7dbf1-109">Before you begin</span></span>

<span data-ttu-id="7dbf1-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="7dbf1-112">Collecte d’informations sur les abonnements et les plans de service</span><span class="sxs-lookup"><span data-stu-id="7dbf1-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="7dbf1-113">Exécutez cette commande pour afficher vos abonnements en cours :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="7dbf1-114">Dans l'affichage de la commande  `Get-MsolAccountSku` :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="7dbf1-p103">**AccountSkuId** est un abonnement pour votre organisation au format \<OrganizationName>:\<Subscription>. La valeur \<OrganizationName> est fournie lorsque vous vous inscrivez à Office 365 et elle est propre à votre organisation. La valeur \<Subscription> désigne un abonnement spécifique. Par exemple, pour litwareinc:ENTERPRISEPACK, le nom de l’organisation est litwareinc, et le nom de l’abonnement est ENTERPRISEPACK (Office 365 Entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="7dbf1-119">**ActiveUnits** représente le nombre de licences que vous avez achetées pour l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="7dbf1-120">**WarningUnits** représente le nombre de licences dans un abonnement que vous n'avez pas renouvelées et qui expireront après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="7dbf1-121">**ConsumedUnits** représente le nombre de licences que vous avez affectées à des utilisateurs de l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="7dbf1-p104">Notez la valeur AccountSkuId pour votre abonnement Office 365 contenant les utilisateurs pour lesquels vous souhaitez obtenir une licence. En outre, assurez-vous qu'il y a suffisamment de licences à attribuer (soustraire **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="7dbf1-124">Ensuite, exécutez cette commande pour afficher les détails sur les plans de service Office 365 qui sont disponibles dans tous vos abonnements :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="7dbf1-125">À partir de l’affichage de cette commande, déterminez les plans de service que vous souhaitez désactiver lorsque vous attribuez des licences aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="7dbf1-126">Voici une liste partielle des plans de service et de leurs services Office 365 correspondants.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="7dbf1-127">**Plan de service**</span><span class="sxs-lookup"><span data-stu-id="7dbf1-127">**Service plan**</span></span>|<span data-ttu-id="7dbf1-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="7dbf1-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7dbf1-129">SWAY</span><span class="sxs-lookup"><span data-stu-id="7dbf1-129">SWAY</span></span>  <br/> |<span data-ttu-id="7dbf1-130">Sway</span><span class="sxs-lookup"><span data-stu-id="7dbf1-130">Sway</span></span>  <br/> |
|<span data-ttu-id="7dbf1-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="7dbf1-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="7dbf1-132">Gestion des appareils mobiles pour Office 365</span><span class="sxs-lookup"><span data-stu-id="7dbf1-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="7dbf1-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="7dbf1-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="7dbf1-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="7dbf1-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="7dbf1-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="7dbf1-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="7dbf1-136">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="7dbf1-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="7dbf1-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7dbf1-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="7dbf1-138">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="7dbf1-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="7dbf1-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="7dbf1-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="7dbf1-140">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="7dbf1-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="7dbf1-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="7dbf1-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="7dbf1-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="7dbf1-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="7dbf1-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="7dbf1-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="7dbf1-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7dbf1-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="7dbf1-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="7dbf1-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="7dbf1-146">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="7dbf1-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="7dbf1-147">Maintenant que vous avez le paramètre AccountSkuId et les plans de service à désactiver, vous pouvez attribuer des licences pour un utilisateur ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="7dbf1-148">Pour un utilisateur unique</span><span class="sxs-lookup"><span data-stu-id="7dbf1-148">For a single user</span></span>

<span data-ttu-id="7dbf1-p105">Pour un utilisateur unique, renseignez le nom d'utilisateur principal du compte d'utilisateur, le paramètre AccountSkuId et la liste des plans de service à désactiver, et supprimez le texte explicatif et les caractères \< et >. Ensuite, exécutez les commandes qui en résultent à l'invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="7dbf1-151">Voici un exemple de bloc de commande pour le compte nommé belindan@contoso.com, pour la licence contoso:ENTERPRISEPACK, et les plans de service à désactiver sont RMS_S_ENTERPRISE, SWAY, INTUNE_O365 et YAMMER_ENTERPRISE :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="7dbf1-152">Pour plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="7dbf1-152">For multiple users</span></span>

<span data-ttu-id="7dbf1-p106">Pour effectuer cette tâche d'administration pour plusieurs utilisateurs, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs UserPrincipalName et UsageLocation. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="7dbf1-155">Ensuite, remplissez l’emplacement des fichiers CSV d’entrée et de sortie, l’ID de référence du compte et la liste des plans de service à désactiver, puis exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
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
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="7dbf1-156">Ce bloc de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7dbf1-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="7dbf1-157">affiche le nom d’utilisateur principal de chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="7dbf1-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="7dbf1-158">attribue des licences personnalisées à chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="7dbf1-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="7dbf1-159">crée un fichier CSV avec tous les utilisateurs qui ont été traités et affiche l’état de leur licence.</span><span class="sxs-lookup"><span data-stu-id="7dbf1-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7dbf1-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dbf1-160">See also</span></span>

#### 

[<span data-ttu-id="7dbf1-161">Désactiver l'accès aux services Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dbf1-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="7dbf1-162">Désactivation de l'accès à Sway avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dbf1-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="7dbf1-163">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dbf1-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7dbf1-164">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dbf1-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

