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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments

En tant qu’administrateur Office 365, vous pouvez déployer des compléments Office auprès des utilisateurs via la fonctionnalité de déploiement centralisée (consultez la rubrique [Manage Deployment of Office 365 Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Outre le déploiement de compléments Office via le centre d’administration, vous pouvez également utiliser Microsoft PowerShell. [Téléchargez](https://go.microsoft.com/fwlink/p/?linkid=850850) les applets de commande PowerShell de déploiement centralisé à partir du centre de téléchargement Microsoft. 
  
## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

[Se connecter à l’aide de vos informations d’identification d’administrateur](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Chargement d’un manifeste de complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Télécharger un complément à partir de l’Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Obtenir les détails d’un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Activation ou désactivation d’un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Ajouter ou supprimer des utilisateurs d’un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Mettre à jour un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Supprimer un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Obtenir de l’aide détaillée pour chaque cmdlet](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Se connecter à l’aide de vos informations d’identification d’administrateur
<a name="BKMK_Connect"> </a>

Avant de pouvoir utiliser les cmdlets de déploiement centralisé, vous devez vous connecter.
  
1. Démarrez PowerShell.
    
2. Connectez-vous à PowerShell à l’aide des informations d’identification d’administrateur de votre entreprise. Exécutez l’applet de commande suivante.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Dans la page **entrer les informations d’identification** , entrez vos informations d’identification d’administrateur global Office 365. Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande. 
    
    Exécutez l’applet de commande suivante en spécifiant les informations d’identification d’administrateur de votre entreprise en tant qu’objet PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Chargement d’un manifeste de complément
<a name="BKMK_UploadManifest"> </a>

Exécutez la cmdlet New-Organisationcompléments-in pour télécharger un manifeste de complément à partir d’un chemin d’accès, qui peut être un emplacement de fichier ou une URL. L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Vous pouvez également exécuter la cmdlet New-Organisationcompléments-in pour télécharger un complément et l’attribuer directement à des utilisateurs ou à des groupes à l’aide du paramètre _members_ , comme illustré dans l’exemple suivant. Séparez les adresses de messagerie des membres par une virgule. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Télécharger un complément à partir de l’Office Store
<a name="BKMK_UploadAddin"> </a>

Exécutez la cmdlet New-OrganizationAddIn pour télécharger un manifeste à partir de l’Office Store.
  
Dans l’exemple suivant, la cmdlet New-OrganizationAddIn spécifie le AssetId pour un complément pour un marché de contenu et de localisation des États-Unis.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Pour déterminer la valeur du paramètre _AssetID_ , vous pouvez le copier à partir de l’URL de la page Web Office Store du complément. AssetIds commence toujours par « WA » suivi d’un nombre. Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web de l’Office Store pour [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)le complément :.
  
Les valeurs des paramètres _locale_ et _ContentMarket_ sont identiques et indiquent le pays/la région à partir duquel vous essayez d’installer le complément. Le format est en-US, fr-FR. et ainsi de suite. 
  
> [!NOTE]
> Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obtenir les détails d’un complément
<a name="BKMK_GetDetails"> </a>

Exécutez la cmdlet Get-OrganizationAddIn comme indiqué ci-dessous pour obtenir les détails de tous les compléments téléchargés vers le client, en incluant l’ID de produit d’un complément.
  
```
Get-OrganizationAddIn
```

Exécutez la cmdlet Get-OrganizationAddIn avec une valeur pour le paramètre _ProductID_ afin de spécifier le complément pour lequel vous souhaitez récupérer les détails. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Pour obtenir tous les détails de tous les compléments, ainsi que les utilisateurs et les groupes affectés, redirigez la sortie de la cmdlet Get-OrganizationAddIn vers la cmdlet Format-List, comme illustré dans l’exemple suivant.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activation ou désactivation d’un complément
<a name="BKMK_TurnOnOff"> </a>

Pour désactiver un complément de sorte que les utilisateurs et les groupes qui lui sont attribués n’y aient plus accès, exécutez l’applet de commande Set-OrganizationAddIn avec le paramètre _ProductID_ et le paramètre `$false` _Enabled_ défini sur, comme illustré dans l’exemple suivant.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Pour réactiver un complément, exécutez la même applet de commande avec le paramètre _Enabled_ défini sur `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Ajouter ou supprimer des utilisateurs d’un complément
<a name="BKMK_AddRemove"> </a>

Pour ajouter des utilisateurs et des groupes à un complément spécifique, exécutez l’applet de commande Set-OrganizationAddInAssignments avec les paramètres _ProductID_, _Add_et _members_ . Séparez les adresses de messagerie des membres par une virgule. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour supprimer des utilisateurs et des groupes, exécutez la même cmdlet à l’aide du paramètre _Remove_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour affecter un complément à tous les utilisateurs sur le client, exécutez la même cmdlet à l’aide du paramètre _AssignToEveryone_ avec la valeur définie `$true`sur.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs et les groupes précédemment affectés, vous pouvez exécuter la même cmdlet et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Mettre à jour un complément
<a name="BKMK_UpdateAddin"> </a>

Pour mettre à jour un complément à partir d’un manifeste, exécutez la cmdlet Set-OrganizationAddIn avec les paramètres _ProductID_, _ManifestPath_et _locale_ , comme illustré dans l’exemple suivant. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store. 
  
## <a name="delete-an-add-in"></a>Supprimer un complément
<a name="BKMK_Delete"> </a>

Pour supprimer un complément, exécutez l’applet de commande Remove-OrganizationAddIn avec le paramètre _ProductID_ , comme illustré dans l’exemple suivant. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtenir de l’aide détaillée pour chaque cmdlet
<a name="BKMK_GetHelp"> </a>

Vous pouvez consulter l’aide détaillée pour chaque cmdlet à l’aide de la cmdlet Get-Help. Par exemple, l’applet de commande suivante fournit des informations détaillées sur la cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


