---
title: Afficher les détails de service et de licence de compte avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués aux utilisateurs.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223106"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="0545f-103">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="0545f-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été attribués aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0545f-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="0545f-p101">Dans Office 365, les licences de plans de gestion des licences (également appelées références ou Office 365 plans) donner aux utilisateurs l’accès aux services qui sont définies pour les plans Office 365. Toutefois, un utilisateur peut avoir pas accès à tous les services qui sont disponibles dans une licence qui leur est actuellement affectée. Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur les comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0545f-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="0545f-108">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="0545f-108">Before you begin</span></span>

- <span data-ttu-id="0545f-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0545f-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0545f-111">Utilisez les commandes `Get-MsolAccountSku` et `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` pour trouver les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0545f-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="0545f-112">Plans de gestion de licences disponibles dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="0545f-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="0545f-113">Services disponibles dans chaque plan de gestion de licences et l’ordre dans lequel ils sont répertoriés (numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="0545f-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="0545f-114">Pour plus d’informations sur les licences des plans de licence et services, voir [Afficher les licences et les services Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0545f-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0545f-115">Utilisez la commande `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` pour rechercher les licences sont affectés à un utilisateur et l’ordre dans lequel ils sont répertoriés (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="0545f-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="0545f-116">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="0545f-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="0545f-117">Pour afficher les services pour un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="0545f-117">To view services for a user account</span></span>

<span data-ttu-id="0545f-118">Pour afficher tous les services un utilisateur ayant accès à Office 365, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="0545f-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="0545f-p103">Cet exemple illustre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Affiche les services qui sont associés à toutes les licences sont attribués à ce compte.</span><span class="sxs-lookup"><span data-stu-id="0545f-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="0545f-121">Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).</span><span class="sxs-lookup"><span data-stu-id="0545f-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="0545f-122">Pour rechercher tous les utilisateurs sous licence qui ont été activés ou désactivés pour des services spécifiques, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="0545f-122">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="0545f-123">Ces exemples utilisent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0545f-123">These examples use the following information:</span></span>
  
- <span data-ttu-id="0545f-124">La licence qui donne accès aux services Office 365 qui nous intéressent est la première qui est affectée à tous les utilisateurs (le numéro d’index est 0).</span><span class="sxs-lookup"><span data-stu-id="0545f-124">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="0545f-p104">Les services Office 365 qui nous intéressent sont Skype pour Business Online et Exchange Online. Pour les licences sont associés au plan de gestion des licences, Skype pour Business Online est 6 service répertorié (le numéro d’index est 5), et Exchange Online est le service 9 répertoriés (le numéro d’index est 8).</span><span class="sxs-lookup"><span data-stu-id="0545f-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="0545f-127">Cet exemple renvoie tous les titulaires qui sont activés pour Skype pour Business Online et Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0545f-127">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="0545f-128">Cet exemple renvoie tous les utilisateurs sous licence qui ne sont pas activés pour Skype pour Business Online ou Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0545f-128">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="0545f-129">Pour afficher tous les services d’un utilisateur qui a été affecté *plusieurs licences*, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="0545f-129">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="0545f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0545f-130">See also</span></span>

<span data-ttu-id="0545f-131">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0545f-131">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="0545f-132">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-132">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0545f-133">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-133">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0545f-134">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0545f-135">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0545f-136">Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0545f-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="0545f-137">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0545f-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="0545f-138">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="0545f-138">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="0545f-139">Format-List</span><span class="sxs-lookup"><span data-stu-id="0545f-139">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="0545f-140">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0545f-140">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="0545f-141">Select-Object.</span><span class="sxs-lookup"><span data-stu-id="0545f-141">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="0545f-142">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0545f-142">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="0545f-143">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="0545f-143">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]