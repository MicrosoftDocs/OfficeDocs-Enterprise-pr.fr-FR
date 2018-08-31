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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Utilisez les applets de commande PowerShell de déploiement centralisée pour gérer les compléments

En tant qu’un administrateur Office 365, vous pouvez déployer des compléments Office pour les utilisateurs via le déploiement centralisée fonction (voir [gestion du déploiement des compléments Office 365 dans le centre d’administration Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). En plus du déploiement des compléments Office via le centre d’administration Office 365, vous pouvez également utiliser Microsoft PowerShell. [Télécharger](https://go.microsoft.com/fwlink/p/?linkid=850850) les applets de commande PowerShell de déploiement centralisés à partir du Microsoft Download Center. 
  
## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

[Se connecter en utilisant vos informations d’identification d’administration](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Télécharger un manifeste d’application add-in](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Télécharger un complément à partir de l’Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Obtenir des détails d’un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Activer ou désactiver un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Ajouter ou supprimer des utilisateurs d’un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Mettre à jour un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Supprimer un complément](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Obtenir une aide détaillée de chaque applet de commande](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Se connecter en utilisant vos informations d’identification d’administration
<a name="BKMK_Connect"> </a>

Avant de pouvoir utiliser les applets de commande de déploiement centralisé, vous devez vous connecter.
  
1. Démarrez PowerShell.
    
2. Connectez-vous à PowerShell à l’aide de vos informations d’identification d’administration de société. Exécutez la cmdlet suivante.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Dans la page **Entrez les informations d’identification** , entrez vos informations d’identification administrateur global de Office 365. Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande. 
    
    Exécutez la cmdlet suivante spécification de votre société les informations d’identification d’administration en tant qu’objet PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Télécharger un manifeste d’application add-in
<a name="BKMK_UploadManifest"> </a>

Exécutez la cmdlet New-OrganizationAdd-In pour télécharger un manifeste d’application add-in à partir d’un chemin d’accès, qui peut correspondre à un emplacement de fichier ou une URL. L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Vous pouvez également exécuter la cmdlet New-OrganizationAdd-In pour charger un complément et les affecter à des utilisateurs ou groupes directement en utilisant le paramètre _Members_ , comme illustré dans l’exemple suivant. Séparez les adresses de messagerie des membres par une virgule. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Télécharger un complément à partir de l’Office Store
<a name="BKMK_UploadAddin"> </a>

Exécutez l’applet de commande New-OrganizationAddIn pour télécharger le manifeste de l’Office Store.
  
Dans l’exemple suivant, l’applet de commande New-OrganizationAddIn Spécifie l’AssetId pour un complément pour un marché d’emplacement et le contenu des États-Unis.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Pour déterminer la valeur du paramètre _AssetId_ , vous pouvez le copier à partir de l’URL de l’Office Store page Web pour le complément AssetIds commencent par « WA » suivi d’un nombre. Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web Office Store pour le complément : [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Les valeurs pour le paramètre _paramètres régionaux_ et le paramètre _ContentMarket_ sont identiques et indiquent la pays/la région que vous tentez d’installer le complément de. Le format est en-US, fr-FR. et ainsi de suite. 
  
> [!NOTE]
> Compléments téléchargées à partir de l’Office Store mettra à jour automatiquement quelques jours de la dernière mise à jour est disponible sur l’Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obtenir des détails d’un complément
<a name="BKMK_GetDetails"> </a>

Exécutez l’applet de commande Get-OrganizationAddIn comme indiqué ci-dessous pour obtenir des détails de tous les compléments téléchargés vers le client, inclus ID de produit. d’un complément
  
```
Get-OrganizationAddIn
```

Exécutez l’applet de commande Get-OrganizationAddIn avec une valeur pour le paramètre _ProductId_ pour spécifier le complément vous souhaitez récupérer les détails pour. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Pour obtenir tous les détails de tous les compléments ainsi que les utilisateurs et les groupes, redirigez le résultat de l’applet de commande Get-OrganizationAddIn vers la cmdlet Format-List, comme illustré dans l’exemple suivant.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activer ou désactiver un complément
<a name="BKMK_TurnOnOff"> </a>

Pour désactiver un complément afin que les utilisateurs et groupes qui lui sont affectés n’aura plus accès, exécutez l’applet de commande Set-OrganizationAddIn avec le paramètre _ProductId_ et le paramètre _Enabled_ la valeur `$false`, comme illustré dans l’exemple suivant.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Pour réactiver un complément, exécutez la cmdlet même avec le paramètre _Enabled_ défini sur `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Ajouter ou supprimer des utilisateurs d’un complément
<a name="BKMK_AddRemove"> </a>

Pour ajouter des utilisateurs et groupes à un complément spécifique, exécutez l’applet de commande Set-OrganizationAddInAssignments avec les paramètres _ProductId_et _Ajouter_des _membres_ . Séparez les adresses de messagerie des membres par une virgule. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour supprimer des utilisateurs et groupes, exécutez la cmdlet même en utilisant le paramètre à _Supprimer_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour assigner un complément à tous les utilisateurs sur le client, exécutez l’applet de commande même à l’aide du paramètre _AssignToEveryone_ avec la valeur `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs précédemment affectés et les groupes, vous pouvez exécuter l’applet de commande même et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Mettre à jour un complément
<a name="BKMK_UpdateAddin"> </a>

Pour mettre à jour un complément à partir d’un manifeste, exécutez l’applet de commande Set-OrganizationAddIn _ProductId_, _ManifestPath_, et les paramètres _régionaux_ , comme illustré dans l’exemple suivant. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Compléments téléchargées à partir de l’Office Store mettra à jour automatiquement quelques jours de la dernière mise à jour est disponible sur l’Office Store. 
  
## <a name="delete-an-add-in"></a>Supprimer un complément
<a name="BKMK_Delete"> </a>

Pour supprimer une macro complémentaire, exécutez l’applet de commande Remove-OrganizationAddIn avec le paramètre _ProductId_ , comme illustré dans l’exemple suivant. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtenir une aide détaillée de chaque applet de commande
<a name="BKMK_GetHelp"> </a>

Vous pouvez consulter l’aide détaillée sur chaque applet de commande à l’aide de l’applet de commande Get-help. Par exemple, la cmdlet suivante fournit des informations détaillées sur l’applet de commande Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


