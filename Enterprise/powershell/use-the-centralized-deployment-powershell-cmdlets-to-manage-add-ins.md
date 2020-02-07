---
title: Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilisez les applets de commande PowerShell de déploiement centralisé pour vous aider à déployer et gérer des compléments Office pour votre organisation Office 365.
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844155"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="91559-103">Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments</span><span class="sxs-lookup"><span data-stu-id="91559-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="91559-104">En tant qu’administrateur Office 365, vous pouvez déployer des compléments Office auprès des utilisateurs via la fonctionnalité de déploiement centralisée (consultez la rubrique [Manage Deployment of Office 365 Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="91559-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="91559-105">Outre le déploiement de compléments Office via le centre d’administration, vous pouvez également utiliser Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91559-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="91559-106">[Téléchargez](https://go.microsoft.com/fwlink/p/?linkid=850850) les applets de commande PowerShell de déploiement centralisé à partir du centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="91559-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="91559-107">Que souhaitez-vous faire ?</span><span class="sxs-lookup"><span data-stu-id="91559-107">What do you want to do?</span></span>

[<span data-ttu-id="91559-108">Se connecter à l’aide de vos informations d’identification d’administrateur</span><span class="sxs-lookup"><span data-stu-id="91559-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="91559-109">Chargement d’un manifeste de complément</span><span class="sxs-lookup"><span data-stu-id="91559-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="91559-110">Télécharger un complément à partir de l’Office Store</span><span class="sxs-lookup"><span data-stu-id="91559-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="91559-111">Obtenir les détails d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="91559-112">Activation ou désactivation d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="91559-113">Ajouter ou supprimer des utilisateurs d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="91559-114">Mettre à jour un complément</span><span class="sxs-lookup"><span data-stu-id="91559-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="91559-115">Supprimer un complément</span><span class="sxs-lookup"><span data-stu-id="91559-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="91559-116">Obtenir de l’aide détaillée pour chaque cmdlet</span><span class="sxs-lookup"><span data-stu-id="91559-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="91559-117">Se connecter à l’aide de vos informations d’identification d’administrateur</span><span class="sxs-lookup"><span data-stu-id="91559-117">Connect using your admin credentials</span></span>
<span data-ttu-id="91559-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="91559-119">Avant de pouvoir utiliser les cmdlets de déploiement centralisé, vous devez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="91559-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="91559-120">Démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91559-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="91559-121">Connectez-vous à PowerShell à l’aide des informations d’identification d’administrateur de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="91559-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="91559-122">Exécutez l’applet de commande suivante.</span><span class="sxs-lookup"><span data-stu-id="91559-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="91559-123">Dans la page **entrer les informations d’identification** , entrez vos informations d’identification d’administrateur global Office 365.</span><span class="sxs-lookup"><span data-stu-id="91559-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="91559-124">Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="91559-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="91559-125">Exécutez l’applet de commande suivante en spécifiant les informations d’identification d’administrateur de votre entreprise en tant qu’objet PSCredential.</span><span class="sxs-lookup"><span data-stu-id="91559-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="91559-126">Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="91559-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="91559-127">Chargement d’un manifeste de complément</span><span class="sxs-lookup"><span data-stu-id="91559-127">Upload an add-in manifest</span></span>
<span data-ttu-id="91559-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="91559-129">Exécutez la cmdlet New-Organisationcompléments-in pour télécharger un manifeste de complément à partir d’un chemin d’accès, qui peut être un emplacement de fichier ou une URL.</span><span class="sxs-lookup"><span data-stu-id="91559-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="91559-130">L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="91559-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="91559-131">Vous pouvez également exécuter la cmdlet New-Organisationcompléments-in pour télécharger un complément et l’attribuer directement à des utilisateurs ou à des groupes à l’aide du paramètre _members_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="91559-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="91559-132">Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="91559-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="91559-133">Télécharger un complément à partir de l’Office Store</span><span class="sxs-lookup"><span data-stu-id="91559-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="91559-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="91559-135">Exécutez la cmdlet New-OrganizationAddIn pour télécharger un manifeste à partir de l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="91559-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="91559-136">Dans l’exemple suivant, la cmdlet New-OrganizationAddIn spécifie le AssetId pour un complément pour un marché de contenu et de localisation des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="91559-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="91559-137">Pour déterminer la valeur du paramètre _AssetID_ , vous pouvez le copier à partir de l’URL de la page Web Office Store du complément.</span><span class="sxs-lookup"><span data-stu-id="91559-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="91559-138">AssetIds commence toujours par « WA » suivi d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="91559-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="91559-139">Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web de l’Office Store pour [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)le complément :.</span><span class="sxs-lookup"><span data-stu-id="91559-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="91559-140">Les valeurs des paramètres _locale_ et _ContentMarket_ sont identiques et indiquent le pays/la région à partir duquel vous essayez d’installer le complément.</span><span class="sxs-lookup"><span data-stu-id="91559-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="91559-141">Le format est en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="91559-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="91559-142">et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="91559-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="91559-143">Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="91559-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="91559-144">Obtenir les détails d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-144">Get details of an add-in</span></span>
<span data-ttu-id="91559-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="91559-146">Exécutez la cmdlet Get-OrganizationAddIn comme indiqué ci-dessous pour obtenir les détails de tous les compléments téléchargés vers le client, en incluant l’ID de produit d’un complément.</span><span class="sxs-lookup"><span data-stu-id="91559-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="91559-147">Exécutez la cmdlet Get-OrganizationAddIn avec une valeur pour le paramètre _ProductID_ afin de spécifier le complément pour lequel vous souhaitez récupérer les détails.</span><span class="sxs-lookup"><span data-stu-id="91559-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="91559-148">Pour obtenir tous les détails de tous les compléments, ainsi que les utilisateurs et les groupes affectés, redirigez la sortie de la cmdlet Get-OrganizationAddIn vers la cmdlet Format-List, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="91559-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="91559-149">Activation ou désactivation d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="91559-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="91559-151">Pour désactiver un complément de sorte que les utilisateurs et les groupes qui lui sont attribués n’y aient plus accès, exécutez l’applet de commande Set-OrganizationAddIn avec le paramètre _ProductID_ et le paramètre `$false` _Enabled_ défini sur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="91559-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="91559-152">Pour réactiver un complément, exécutez la même applet de commande avec le paramètre _Enabled_ défini sur `$true`.</span><span class="sxs-lookup"><span data-stu-id="91559-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="91559-153">Ajouter ou supprimer des utilisateurs d’un complément</span><span class="sxs-lookup"><span data-stu-id="91559-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="91559-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="91559-155">Pour ajouter des utilisateurs et des groupes à un complément spécifique, exécutez l’applet de commande Set-OrganizationAddInAssignments avec les paramètres _ProductID_, _Add_et _members_ .</span><span class="sxs-lookup"><span data-stu-id="91559-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="91559-156">Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="91559-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="91559-157">Pour supprimer des utilisateurs et des groupes, exécutez la même cmdlet à l’aide du paramètre _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="91559-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="91559-158">Pour affecter un complément à tous les utilisateurs sur le client, exécutez la même cmdlet à l’aide du paramètre _AssignToEveryone_ avec la valeur définie `$true`sur.</span><span class="sxs-lookup"><span data-stu-id="91559-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="91559-159">Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs et les groupes précédemment affectés, vous pouvez exécuter la même cmdlet et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.</span><span class="sxs-lookup"><span data-stu-id="91559-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="91559-160">Mettre à jour un complément</span><span class="sxs-lookup"><span data-stu-id="91559-160">Update an add-in</span></span>
<span data-ttu-id="91559-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="91559-162">Pour mettre à jour un complément à partir d’un manifeste, exécutez la cmdlet Set-OrganizationAddIn avec les paramètres _ProductID_, _ManifestPath_et _locale_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="91559-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="91559-163">Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="91559-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="91559-164">Supprimer un complément</span><span class="sxs-lookup"><span data-stu-id="91559-164">Delete an add-in</span></span>
<span data-ttu-id="91559-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="91559-166">Pour supprimer un complément, exécutez l’applet de commande Remove-OrganizationAddIn avec le paramètre _ProductID_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="91559-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="91559-167">Obtenir de l’aide détaillée pour chaque cmdlet</span><span class="sxs-lookup"><span data-stu-id="91559-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="91559-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="91559-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="91559-169">Vous pouvez consulter l’aide détaillée pour chaque cmdlet à l’aide de la cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="91559-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="91559-170">Par exemple, l’applet de commande suivante fournit des informations détaillées sur la cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="91559-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


