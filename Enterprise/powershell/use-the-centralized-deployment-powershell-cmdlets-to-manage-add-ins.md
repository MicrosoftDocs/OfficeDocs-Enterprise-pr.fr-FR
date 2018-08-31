---
title: Utilisez les applets de commande PowerShell de déploiement centralisée pour gérer les compléments
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilisez les applets de commande PowerShell de déploiement centralisée pour vous aider à déployer et gérer les compléments Office pour votre organisation Office 365.
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540351"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="0aa0a-103">Utilisez les applets de commande PowerShell de déploiement centralisée pour gérer les compléments</span><span class="sxs-lookup"><span data-stu-id="0aa0a-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="0aa0a-p101">En tant qu’un administrateur Office 365, vous pouvez déployer des compléments Office pour les utilisateurs via le déploiement centralisée fonction (voir [gestion du déploiement des compléments Office 365 dans le centre d’administration Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). En plus du déploiement des compléments Office via le centre d’administration Office 365, vous pouvez également utiliser Microsoft PowerShell. [Télécharger](https://go.microsoft.com/fwlink/p/?linkid=850850) les applets de commande PowerShell de déploiement centralisés à partir du Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="0aa0a-107">Que souhaitez-vous faire ?</span><span class="sxs-lookup"><span data-stu-id="0aa0a-107">What do you want to do?</span></span>

[<span data-ttu-id="0aa0a-108">Se connecter en utilisant vos informations d’identification d’administration</span><span class="sxs-lookup"><span data-stu-id="0aa0a-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="0aa0a-109">Télécharger un manifeste d’application add-in</span><span class="sxs-lookup"><span data-stu-id="0aa0a-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="0aa0a-110">Télécharger un complément à partir de l’Office Store</span><span class="sxs-lookup"><span data-stu-id="0aa0a-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="0aa0a-111">Obtenir des détails d’un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="0aa0a-112">Activer ou désactiver un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="0aa0a-113">Ajouter ou supprimer des utilisateurs d’un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="0aa0a-114">Mettre à jour un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="0aa0a-115">Supprimer un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="0aa0a-116">Obtenir une aide détaillée de chaque applet de commande</span><span class="sxs-lookup"><span data-stu-id="0aa0a-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="0aa0a-117">Se connecter en utilisant vos informations d’identification d’administration</span><span class="sxs-lookup"><span data-stu-id="0aa0a-117">Connect using your admin credentials</span></span>
<span data-ttu-id="0aa0a-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-118"></span></span>

<span data-ttu-id="0aa0a-119">Avant de pouvoir utiliser les applets de commande de déploiement centralisé, vous devez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="0aa0a-120">Démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="0aa0a-p102">Connectez-vous à PowerShell à l’aide de vos informations d’identification d’administration de société. Exécutez la cmdlet suivante.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="0aa0a-p103">Dans la page **Entrez les informations d’identification** , entrez vos informations d’identification administrateur global de Office 365. Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="0aa0a-125">Exécutez la cmdlet suivante spécification de votre société les informations d’identification d’administration en tant qu’objet PSCredential.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="0aa0a-126">Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="0aa0a-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="0aa0a-127">Télécharger un manifeste d’application add-in</span><span class="sxs-lookup"><span data-stu-id="0aa0a-127">Upload an add-in manifest</span></span>
<span data-ttu-id="0aa0a-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-128"></span></span>

<span data-ttu-id="0aa0a-p104">Exécutez la cmdlet New-OrganizationAdd-In pour télécharger un manifeste d’application add-in à partir d’un chemin d’accès, qui peut correspondre à un emplacement de fichier ou une URL. L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="0aa0a-p105">Vous pouvez également exécuter la cmdlet New-OrganizationAdd-In pour charger un complément et les affecter à des utilisateurs ou groupes directement en utilisant le paramètre _Members_ , comme illustré dans l’exemple suivant. Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="0aa0a-133">Télécharger un complément à partir de l’Office Store</span><span class="sxs-lookup"><span data-stu-id="0aa0a-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="0aa0a-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-134"></span></span>

<span data-ttu-id="0aa0a-135">Exécutez l’applet de commande New-OrganizationAddIn pour télécharger le manifeste de l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="0aa0a-136">Dans l’exemple suivant, l’applet de commande New-OrganizationAddIn Spécifie l’AssetId pour un complément pour un marché d’emplacement et le contenu des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="0aa0a-p106">Pour déterminer la valeur du paramètre _AssetId_ , vous pouvez le copier à partir de l’URL de l’Office Store page Web pour le complément AssetIds commencent par « WA » suivi d’un nombre. Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web Office Store pour le complément : [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="0aa0a-p107">Les valeurs pour le paramètre _paramètres régionaux_ et le paramètre _ContentMarket_ sont identiques et indiquent la pays/la région que vous tentez d’installer le complément de. Le format est en-US, fr-FR. et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="0aa0a-143">Compléments téléchargées à partir de l’Office Store mettra à jour automatiquement quelques jours de la dernière mise à jour est disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="0aa0a-144">Obtenir des détails d’un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-144">Get details of an add-in</span></span>
<span data-ttu-id="0aa0a-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-145"></span></span>

<span data-ttu-id="0aa0a-146">Exécutez l’applet de commande Get-OrganizationAddIn comme indiqué ci-dessous pour obtenir des détails de tous les compléments téléchargés vers le client, inclus ID de produit. d’un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="0aa0a-147">Exécutez l’applet de commande Get-OrganizationAddIn avec une valeur pour le paramètre _ProductId_ pour spécifier le complément vous souhaitez récupérer les détails pour.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="0aa0a-148">Pour obtenir tous les détails de tous les compléments ainsi que les utilisateurs et les groupes, redirigez le résultat de l’applet de commande Get-OrganizationAddIn vers la cmdlet Format-List, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="0aa0a-149">Activer ou désactiver un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="0aa0a-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-150"></span></span>

<span data-ttu-id="0aa0a-151">Pour désactiver un complément afin que les utilisateurs et groupes qui lui sont affectés n’aura plus accès, exécutez l’applet de commande Set-OrganizationAddIn avec le paramètre _ProductId_ et le paramètre _Enabled_ la valeur `$false`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="0aa0a-152">Pour réactiver un complément, exécutez la cmdlet même avec le paramètre _Enabled_ défini sur `$true`.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="0aa0a-153">Ajouter ou supprimer des utilisateurs d’un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="0aa0a-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-154"></span></span>

<span data-ttu-id="0aa0a-p108">Pour ajouter des utilisateurs et groupes à un complément spécifique, exécutez l’applet de commande Set-OrganizationAddInAssignments avec les paramètres _ProductId_et _Ajouter_des _membres_ . Séparez les adresses de messagerie des membres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="0aa0a-157">Pour supprimer des utilisateurs et groupes, exécutez la cmdlet même en utilisant le paramètre à _Supprimer_ .</span><span class="sxs-lookup"><span data-stu-id="0aa0a-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="0aa0a-158">Pour assigner un complément à tous les utilisateurs sur le client, exécutez l’applet de commande même à l’aide du paramètre _AssignToEveryone_ avec la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="0aa0a-159">Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs précédemment affectés et les groupes, vous pouvez exécuter l’applet de commande même et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="0aa0a-160">Mettre à jour un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-160">Update an add-in</span></span>
<span data-ttu-id="0aa0a-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-161"></span></span>

<span data-ttu-id="0aa0a-162">Pour mettre à jour un complément à partir d’un manifeste, exécutez l’applet de commande Set-OrganizationAddIn _ProductId_, _ManifestPath_, et les paramètres _régionaux_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="0aa0a-163">Compléments téléchargées à partir de l’Office Store mettra à jour automatiquement quelques jours de la dernière mise à jour est disponible sur l’Office Store.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="0aa0a-164">Supprimer un complément</span><span class="sxs-lookup"><span data-stu-id="0aa0a-164">Delete an add-in</span></span>
<span data-ttu-id="0aa0a-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-165"></span></span>

<span data-ttu-id="0aa0a-166">Pour supprimer une macro complémentaire, exécutez l’applet de commande Remove-OrganizationAddIn avec le paramètre _ProductId_ , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="0aa0a-167">Obtenir une aide détaillée de chaque applet de commande</span><span class="sxs-lookup"><span data-stu-id="0aa0a-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="0aa0a-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="0aa0a-168"></span></span>

<span data-ttu-id="0aa0a-p109">Vous pouvez consulter l’aide détaillée sur chaque applet de commande à l’aide de l’applet de commande Get-help. Par exemple, la cmdlet suivante fournit des informations détaillées sur l’applet de commande Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


