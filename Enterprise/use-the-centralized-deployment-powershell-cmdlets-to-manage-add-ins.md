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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilisez les applets de commande PowerShell de déploiement centralisé pour vous aider à déployer et gérer des compléments Office pour votre organisation Office 365.
ms.openlocfilehash: 72f7ad69f1154c65ee5f6bd608770461ae775257
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030859"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="fc8da-103">Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments</span><span class="sxs-lookup"><span data-stu-id="fc8da-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="fc8da-104">En tant qu’administrateur général Microsoft 365 ou administrateur Exchange, vous pouvez déployer des compléments Office auprès des utilisateurs via la fonctionnalité de déploiement centralisée (consultez la rubrique [Deploy Office Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="fc8da-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="fc8da-105">Outre le déploiement des compléments Office via le centre d’administration Microsoft 365, vous pouvez également utiliser Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc8da-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="fc8da-106">Installez le [module de déploiement de compléments centralisés O365 pour Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="fc8da-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="fc8da-107">Après avoir téléchargé le module, ouvrez une fenêtre Windows PowerShell normale et exécutez l’applet de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fc8da-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="fc8da-108">Se connecter à l’aide de vos informations d’identification d’administrateur</span><span class="sxs-lookup"><span data-stu-id="fc8da-108">Connect using your admin credentials</span></span>

<span data-ttu-id="fc8da-109">Avant de pouvoir utiliser les cmdlets de déploiement centralisé, vous devez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="fc8da-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="fc8da-110">Démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc8da-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="fc8da-111">Connectez-vous à PowerShell à l’aide des informations d’identification d’administrateur de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="fc8da-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="fc8da-112">Exécutez l’applet de commande suivante.</span><span class="sxs-lookup"><span data-stu-id="fc8da-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="fc8da-113">Dans la page **entrer les informations d’identification** , entrez vos informations d’identification d’administrateur global Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc8da-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="fc8da-114">Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fc8da-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="fc8da-115">Exécutez l’applet de commande suivante en spécifiant les informations d’identification d’administrateur de votre entreprise en tant qu’objet PSCredential.</span><span class="sxs-lookup"><span data-stu-id="fc8da-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="fc8da-116">Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="fc8da-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="fc8da-117">Chargement d’un manifeste de complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-117">Upload an add-in manifest</span></span>

<span data-ttu-id="fc8da-118">Exécutez la cmdlet **New-organisationcompléments-in** pour télécharger un manifeste de complément à partir d’un chemin d’accès, qui peut être un emplacement de fichier ou une URL.</span><span class="sxs-lookup"><span data-stu-id="fc8da-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="fc8da-119">L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="fc8da-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="fc8da-120">Vous pouvez également exécuter la cmdlet **New-organisationcompléments-in** pour télécharger un complément et l’attribuer directement à des utilisateurs ou à des groupes à l’aide du paramètre _members_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc8da-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="fc8da-121">Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="fc8da-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="fc8da-122">Télécharger un complément à partir de l’Office Store</span><span class="sxs-lookup"><span data-stu-id="fc8da-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="fc8da-123">Exécutez la cmdlet **New-OrganizationAddIn** pour télécharger un manifeste à partir de l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="fc8da-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="fc8da-124">Dans l’exemple suivant, la cmdlet **New-OrganizationAddIn** spécifie le AssetID pour un complément pour un marché de contenu et de localisation des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="fc8da-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="fc8da-125">Pour déterminer la valeur du paramètre _AssetID_ , vous pouvez le copier à partir de l’URL de la page Web Office Store du complément.</span><span class="sxs-lookup"><span data-stu-id="fc8da-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="fc8da-126">AssetIds commence toujours par « WA » suivi d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="fc8da-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="fc8da-127">Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web de l’Office Store pour [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)le complément :.</span><span class="sxs-lookup"><span data-stu-id="fc8da-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="fc8da-128">Les valeurs des paramètres _locale_ et _ContentMarket_ sont identiques et indiquent le pays/la région à partir duquel vous essayez d’installer le complément.</span><span class="sxs-lookup"><span data-stu-id="fc8da-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="fc8da-129">Le format est en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="fc8da-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="fc8da-130">et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fc8da-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="fc8da-131">Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="fc8da-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="fc8da-132">Obtenir les détails d’un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-132">Get details of an add-in</span></span>

<span data-ttu-id="fc8da-133">Exécutez la cmdlet **Get-OrganizationAddIn** comme indiqué ci-dessous pour obtenir les détails de tous les compléments téléchargés vers le client, en incluant l’ID de produit d’un complément.</span><span class="sxs-lookup"><span data-stu-id="fc8da-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="fc8da-134">Exécutez la cmdlet **Get-OrganizationAddIn** avec une valeur pour le paramètre _ProductID_ afin de spécifier le complément pour lequel vous souhaitez récupérer les détails.</span><span class="sxs-lookup"><span data-stu-id="fc8da-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="fc8da-135">Pour obtenir tous les détails de tous les compléments, ainsi que les utilisateurs et les groupes affectés, redirigez la sortie de la cmdlet **Get-OrganizationAddIn** vers la cmdlet Format-List, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc8da-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="fc8da-136">Activation ou désactivation d’un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="fc8da-137">Pour désactiver un complément de sorte que les utilisateurs et les groupes qui lui sont attribués n’y aient plus accès, exécutez l’applet de commande **Set-OrganizationAddIn** avec le paramètre _ProductID_ et le paramètre `$false` _Enabled_ défini sur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc8da-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="fc8da-138">Pour réactiver un complément, exécutez la même applet de commande avec le paramètre _Enabled_ défini sur `$true`.</span><span class="sxs-lookup"><span data-stu-id="fc8da-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="fc8da-139">Ajouter ou supprimer des utilisateurs d’un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="fc8da-140">Pour ajouter des utilisateurs et des groupes à un complément spécifique, exécutez l’applet de commande **Set-OrganizationAddInAssignments** avec les paramètres _ProductID_, _Add_et _members_ .</span><span class="sxs-lookup"><span data-stu-id="fc8da-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="fc8da-141">Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="fc8da-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="fc8da-142">Pour supprimer des utilisateurs et des groupes, exécutez la même cmdlet à l’aide du paramètre _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="fc8da-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="fc8da-143">Pour affecter un complément à tous les utilisateurs sur le client, exécutez la même cmdlet à l’aide du paramètre _AssignToEveryone_ avec la valeur définie `$true`sur.</span><span class="sxs-lookup"><span data-stu-id="fc8da-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="fc8da-144">Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs et les groupes précédemment affectés, vous pouvez exécuter la même cmdlet et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.</span><span class="sxs-lookup"><span data-stu-id="fc8da-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="fc8da-145">Mettre à jour un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-145">Update an add-in</span></span>

<span data-ttu-id="fc8da-146">Pour mettre à jour un complément à partir d’un manifeste, exécutez la cmdlet **Set-OrganizationAddIn** avec les paramètres _ProductID_, _ManifestPath_et _locale_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc8da-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="fc8da-147">Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="fc8da-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="fc8da-148">Supprimer un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-148">Delete an add-in</span></span>

<span data-ttu-id="fc8da-149">Pour supprimer un complément, exécutez l’applet de commande **Remove-OrganizationAddIn** avec le paramètre _ProductID_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc8da-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="fc8da-150">Personnalisation des compléments Microsoft Store pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="fc8da-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="fc8da-151">Vous devez personnaliser le complément avant de le déployer dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="fc8da-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="fc8da-152">Les compléments antérieurs à la version 1,1 ne sont pas pris en charge par cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="fc8da-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="fc8da-153">Nous vous recommandons de déployer un complément personnalisé pour vous assurer qu’il fonctionne comme prévu avant de le déployer dans l’ensemble de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="fc8da-153">We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.</span></span>

<span data-ttu-id="fc8da-154">Notez également les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc8da-154">Note also the following restrictions:</span></span>
- <span data-ttu-id="fc8da-155">Toutes les URL doivent être absolues (y compris http ou https) et valides.</span><span class="sxs-lookup"><span data-stu-id="fc8da-155">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="fc8da-156">*DisplayName* ne doit pas dépasser 125 caractères</span><span class="sxs-lookup"><span data-stu-id="fc8da-156">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="fc8da-157">*DisplayName*, les *ressources* et les *AppDomains* ne doivent pas inclure les caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="fc8da-157">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="fc8da-158">;</span><span class="sxs-lookup"><span data-stu-id="fc8da-158"></span></span>
    -  =   

<span data-ttu-id="fc8da-159">Si vous souhaitez personnaliser un complément qui a été déployé, vous devez le désinstaller dans le centre d’administration et voir [supprimer un complément du cache local](#remove-an-add-in-from-local-cache) pour connaître les étapes à suivre pour le supprimer de chaque ordinateur sur lequel il a été déployé.</span><span class="sxs-lookup"><span data-stu-id="fc8da-159">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="fc8da-160">Pour personnaliser un complément, exécutez l’applet de commande **Set – OrganizationAddInOverrides** avec le *ProductID* en tant que paramètre, suivi de la balise que vous souhaitez remplacer et de la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="fc8da-160">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="fc8da-161">Pour savoir comment obtenir le *ProductID* , consultez la rubrique [obtenir les détails d’un complément](#get-details-of-an-add-in) dans cet article.</span><span class="sxs-lookup"><span data-stu-id="fc8da-161">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="fc8da-162">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fc8da-162">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
<span data-ttu-id="fc8da-163">Pour personnaliser plusieurs balises pour un complément, ajoutez-les à la ligne de ligne :</span><span class="sxs-lookup"><span data-stu-id="fc8da-163">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="fc8da-164">Vous devez appliquer plusieurs balises personnalisées à un complément en tant que commande unique.</span><span class="sxs-lookup"><span data-stu-id="fc8da-164">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="fc8da-165">Si vous personnalisez les balises une par une, seule la dernière personnalisation sera appliquée.</span><span class="sxs-lookup"><span data-stu-id="fc8da-165">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="fc8da-166">En outre, si vous personnalisez une balise par inadvertance, vous devez supprimer toutes les personnalisations et recommencer.</span><span class="sxs-lookup"><span data-stu-id="fc8da-166">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="fc8da-167">Balises que vous pouvez personnaliser</span><span class="sxs-lookup"><span data-stu-id="fc8da-167">Tags you can customize</span></span>

| <span data-ttu-id="fc8da-168">Tag</span><span class="sxs-lookup"><span data-stu-id="fc8da-168">Tag</span></span>                  | <span data-ttu-id="fc8da-169">Description</span><span class="sxs-lookup"><span data-stu-id="fc8da-169">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="fc8da-170">\<> IconURL</span><span class="sxs-lookup"><span data-stu-id="fc8da-170">\<IconURL></span></span>   </br>| <span data-ttu-id="fc8da-171">URL de l’image utilisée comme icône du complément (dans le centre d’administration).</span><span class="sxs-lookup"><span data-stu-id="fc8da-171">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="fc8da-172">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="fc8da-172">\<DisplayName></span></span>| <span data-ttu-id="fc8da-173">Titre du complément (dans le centre d’administration).</span><span class="sxs-lookup"><span data-stu-id="fc8da-173">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="fc8da-174">\<Hôtes></span><span class="sxs-lookup"><span data-stu-id="fc8da-174">\<Hosts></span></span>| <span data-ttu-id="fc8da-175">Liste des applications qui prendront en charge le complément.</span><span class="sxs-lookup"><span data-stu-id="fc8da-175">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="fc8da-176">\<> SourceLocation</span><span class="sxs-lookup"><span data-stu-id="fc8da-176">\<SourceLocation></span></span> | <span data-ttu-id="fc8da-177">URL source à laquelle le complément se connectera.</span><span class="sxs-lookup"><span data-stu-id="fc8da-177">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="fc8da-178">\<AppDomains></span><span class="sxs-lookup"><span data-stu-id="fc8da-178">\<AppDomains></span></span> | <span data-ttu-id="fc8da-179">Liste des domaines avec lesquels le complément peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="fc8da-179">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="fc8da-180">\<SupportURL,></span><span class="sxs-lookup"><span data-stu-id="fc8da-180">\<SupportURL></span></span>| <span data-ttu-id="fc8da-181">L’URL que les utilisateurs peuvent utiliser pour accéder à l’aide et à la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="fc8da-181">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="fc8da-182">\<Ressources></span><span class="sxs-lookup"><span data-stu-id="fc8da-182">\<Resources></span></span>  | <span data-ttu-id="fc8da-183">Cette balise contient un certain nombre d’éléments, y compris des titres, des info-bulles et des icônes de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="fc8da-183">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="fc8da-184">Personnaliser la balise des ressources</span><span class="sxs-lookup"><span data-stu-id="fc8da-184">Customize Resources tag</span></span>

<span data-ttu-id="fc8da-185">Tout élément dans la <Resources> balise du manifeste peut être personnalisé de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="fc8da-185">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="fc8da-186">Vous devez d’abord vérifier le manifeste pour trouver l’ID de l’élément auquel vous souhaitez affecter une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="fc8da-186">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="fc8da-187">La <Resources> balise se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="fc8da-187">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="fc8da-188">Dans ce cas, l’ID d’élément de l’image est « img16icon » et la valeur qui lui est associée est «<i></i>http://site. <i> </i>com/img. jpg. "</span><span class="sxs-lookup"><span data-stu-id="fc8da-188">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="fc8da-189">Une fois que vous avez identifié les éléments que vous souhaitez personnaliser, utilisez la commande suivante dans PowerShell pour affecter de nouvelles valeurs aux éléments :</span><span class="sxs-lookup"><span data-stu-id="fc8da-189">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="fc8da-190">Vous pouvez personnaliser autant d’éléments à l’aide de la commande que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="fc8da-190">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="fc8da-191">Supprimer la personnalisation d’un complément</span><span class="sxs-lookup"><span data-stu-id="fc8da-191">Remove customization from an add-in</span></span>

<span data-ttu-id="fc8da-192">La seule option actuellement disponible pour la suppression des personnalisations consiste à les supprimer toutes en même temps :</span><span class="sxs-lookup"><span data-stu-id="fc8da-192">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="fc8da-193">Afficher les personnalisations des compléments</span><span class="sxs-lookup"><span data-stu-id="fc8da-193">View add-in customizations</span></span>

<span data-ttu-id="fc8da-194">Pour afficher la liste des personnalisations appliquées, exécutez la cmdlet **Get-OrganizationAddInOverrides** .</span><span class="sxs-lookup"><span data-stu-id="fc8da-194">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="fc8da-195">Si **Get-OrganizationAddInOverrides** est exécuté sans *ProductID* , une liste de tous les compléments avec des substitutions appliquées est renvoyée.</span><span class="sxs-lookup"><span data-stu-id="fc8da-195">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="fc8da-196">Si ProductId est spécifié, une liste de substitutions appliquée à ce complément est renvoyée.</span><span class="sxs-lookup"><span data-stu-id="fc8da-196">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="fc8da-197">Supprimer un complément du cache local</span><span class="sxs-lookup"><span data-stu-id="fc8da-197">Remove an add-in from local cache</span></span>

<span data-ttu-id="fc8da-198">Si un complément a été déployé, il doit être supprimé du cache de chaque ordinateur pour pouvoir être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fc8da-198">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="fc8da-199">Pour remive un complément à partir du cache :</span><span class="sxs-lookup"><span data-stu-id="fc8da-199">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="fc8da-200">Accédez au dossier « utilisateurs » dans C:</span><span class="sxs-lookup"><span data-stu-id="fc8da-200">Navigate to the “Users” folder in C:</span></span>\ 
1. <span data-ttu-id="fc8da-201">Accéder à votre dossier utilisateur</span><span class="sxs-lookup"><span data-stu-id="fc8da-201">Go to your user folder</span></span>
1. <span data-ttu-id="fc8da-202">Accédez à AppData\Local\Microsoft\Office et sélectionnez le dossier associé à votre version d’Office.</span><span class="sxs-lookup"><span data-stu-id="fc8da-202">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="fc8da-203">Dans le dossier *WEF* , supprimez le dossier *Manifests* .</span><span class="sxs-lookup"><span data-stu-id="fc8da-203">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="fc8da-204">Obtenir de l’aide détaillée pour chaque cmdlet</span><span class="sxs-lookup"><span data-stu-id="fc8da-204">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="fc8da-205">Vous pouvez consulter l’aide détaillée pour chaque cmdlet à l’aide de la cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="fc8da-205">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="fc8da-206">Par exemple, l’applet de commande suivante fournit des informations détaillées sur la cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="fc8da-206">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


