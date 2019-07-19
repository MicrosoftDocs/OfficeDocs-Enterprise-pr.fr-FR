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
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791249"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments

En tant qu’administrateur général Microsoft 365 ou administrateur Exchange, vous pouvez déployer des compléments Office auprès des utilisateurs via la fonctionnalité de déploiement centralisée (consultez la rubrique [Deploy Office Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Outre le déploiement des compléments Office via le centre d’administration Microsoft 365, vous pouvez également utiliser Microsoft PowerShell. Installez le [module de déploiement de compléments centralisés O365 pour Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Après avoir téléchargé le module, ouvrez une fenêtre Windows PowerShell normale et exécutez l’applet de commande suivante:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Se connecter à l’aide de vos informations d’identification d’administrateur

Avant de pouvoir utiliser les cmdlets de déploiement centralisé, vous devez vous connecter.
  
1. Démarrez PowerShell.
    
2. Connectez-vous à PowerShell à l’aide des informations d’identification d’administrateur de votre entreprise. Exécutez l’applet de commande suivante.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Dans la page **entrer les informations d’identification** , entrez vos informations d’identification d’administrateur global Office 365. Vous pouvez également entrer vos informations d’identification directement dans l’applet de commande. 
    
    Exécutez l’applet de commande suivante en spécifiant les informations d’identification d’administrateur de votre entreprise en tant qu’objet PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Pour plus d’informations sur l’utilisation de PowerShell, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Chargement d’un manifeste de complément

Exécutez la cmdlet **New-organisationcompléments-in** pour télécharger un manifeste de complément à partir d’un chemin d’accès, qui peut être un emplacement de fichier ou une URL. L’exemple suivant montre un emplacement de fichier pour la valeur du paramètre _ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Vous pouvez également exécuter la cmdlet **New-organisationcompléments-in** pour télécharger un complément et l’attribuer directement à des utilisateurs ou à des groupes à l' __ aide du paramètre Members, comme illustré dans l’exemple suivant. Séparez les adresses de messagerie des membres par une virgule. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Télécharger un complément à partir de l’Office Store

Exécutez la cmdlet **New-OrganizationAddIn** pour télécharger un manifeste à partir de l’Office Store.
  
Dans l’exemple suivant, la cmdlet **New-OrganizationAddIn** spécifie le AssetID pour un complément pour un marché de contenu et de localisation des États-Unis.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Pour déterminer la valeur du paramètre _AssetID_ , vous pouvez le copier à partir de l’URL de la page Web Office Store du complément. AssetIds commence toujours par «WA» suivi d’un nombre. Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page Web de l’Office Store pour [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)le complément:.
  
Les valeurs des paramètres _locale_ et _ContentMarket_ sont identiques et indiquent le pays/la région à partir duquel vous essayez d’installer le complément. Le format est en-US, fr-FR. et ainsi de suite. 
  
> [!NOTE]
> Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obtenir les détails d’un complément

Exécutez la cmdlet **Get-OrganizationAddIn** comme indiqué ci-dessous pour obtenir les détails de tous les compléments téléchargés vers le client, en incluant l’ID de produit d’un complément.
  
```powershell
Get-OrganizationAddIn
```

Exécutez la cmdlet **Get-OrganizationAddIn** avec une valeur pour le paramètre _ProductID_ afin de spécifier le complément pour lequel vous souhaitez récupérer les détails. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Pour obtenir tous les détails de tous les compléments, ainsi que les utilisateurs et les groupes affectés, redirigez la sortie de la cmdlet **Get-OrganizationAddIn** vers la cmdlet Format-List, comme illustré dans l’exemple suivant.
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activation ou désactivation d’un complément

Pour désactiver un complément de sorte que les utilisateurs et les groupes qui lui sont attribués n’y aient plus accès, exécutez l’applet de commande **Set-OrganizationAddIn** avec le paramètre _ProductID_ et le paramètre `$false` _Enabled_ défini sur, comme illustré dans l’exemple suivant .
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Pour réactiver un complément, exécutez la même applet de commande avec le paramètre _Enabled_ défini sur `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Ajouter ou supprimer des utilisateurs d’un complément

Pour ajouter des utilisateurs et des groupes à un complément spécifique, exécutez l’applet de commande **Set-OrganizationAddInAssignments** avec les paramètres _ProductID_, _Add_et _members_ . Séparez les adresses de messagerie des membres par une virgule. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour supprimer des utilisateurs et des groupes, exécutez la même cmdlet à l’aide du paramètre _Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour affecter un complément à tous les utilisateurs sur le client, exécutez la même cmdlet à l’aide du paramètre _AssignToEveryone_ avec la valeur définie `$true`sur.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Pour ne pas affecter un complément à tout le monde et rétablir les utilisateurs et les groupes précédemment affectés, vous pouvez exécuter la même cmdlet et désactiver le paramètre _AssignToEveryone_ en définissant sa valeur sur `$false`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Mettre à jour un complément

Pour mettre à jour un complément à partir d’un manifeste, exécutez la cmdlet **Set-OrganizationAddIn** avec les paramètres _ProductID_, _ManifestPath_et _locale_ , comme illustré dans l’exemple suivant. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Les compléments téléchargés à partir de l’Office Store seront automatiquement mis à jour au cours des quelques jours suivant la dernière mise à jour disponible sur l’Office Store. 
  
## <a name="delete-an-add-in"></a>Supprimer un complément

Pour supprimer un complément, exécutez l’applet de commande **Remove-OrganizationAddIn** avec le paramètre _ProductID_ , comme illustré dans l’exemple suivant. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>Personnalisation des compléments Microsoft Store pour votre organisation

Vous devez personnaliser le complément avant de le déployer dans votre organisation. Les compléments antérieurs à la version 1,1 ne sont pas pris en charge par cette fonctionnalité. 

Notez également les restrictions suivantes:
- Toutes les URL doivent être absolues (y compris http ou https) et valides.
- *DisplayName* ne doit pas dépasser 125 caractères 
- *DisplayName*, les *ressources* et les *AppDomains* ne doivent pas inclure les caractères suivants: 
 
    - \<
    -  \>
    -  ;
    -  =   

Si vous souhaitez personnaliser un complément qui a été déployé, vous devez le désinstaller dans le centre d’administration et voir [supprimer un complément du cache local](#remove-an-add-in-from-local-cache) pour connaître les étapes à suivre pour le supprimer de chaque ordinateur sur lequel il a été déployé.

Pour personnaliser un complément, exécutez l’applet de commande **Set – OrganizationAddInOverrides** avec le *ProductID* en tant que paramètre, suivi de la balise que vous souhaitez remplacer et de la nouvelle valeur. Pour savoir comment obtenir le *ProductID* , consultez la rubrique [obtenir les détails d’un complément](#get-details-of-an-add-in) dans cet article. Par exemple :

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
Pour personnaliser plusieurs balises pour un complément, ajoutez-les à la ligne de ligne:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> Vous devez appliquer plusieurs balises personnalisées à un complément en tant que commande unique. Si vous personnalisez les balises une par une, seule la dernière personnalisation sera appliquée. En outre, si vous personnalisez une balise par inadvertance, vous devez supprimer toutes les personnalisations et recommencer.

### <a name="tags-you-can-customize"></a>Balises que vous pouvez personnaliser

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<> IconURL   </br>| URL de l’image utilisée comme icône du complément (dans le centre d’administration). </br> |
| \<DisplayName>| Titre du complément (dans le centre d’administration).|
| \<Hôtes>| Liste des applications qui prendront en charge le complément.|
| \<> SourceLocation | URL source à laquelle le complément se connectera.| 
| \<AppDomains> | Liste des domaines avec lesquels le complément peut se connecter. | 
| \<SupportURL,>| L’URL que les utilisateurs peuvent utiliser pour accéder à l’aide et à la prise en charge. | 
| \<Ressources>  | Cette balise contient un certain nombre d’éléments, y compris des titres, des info-bulles et des icônes de tailles différentes.| 
|
### <a name="customize-resources-tag"></a>Personnaliser la balise des ressources

Tout élément dans la <Resources> balise du manifeste peut être personnalisé de manière dynamique. Vous devez d’abord vérifier le manifeste pour trouver l’ID de l’élément auquel vous souhaitez affecter une nouvelle valeur. La <Resources> balise se présente comme suit:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
Dans ce cas, l’ID d’élément de l’image est «img16icon» et la valeur qui lui est associée est «<i></i>http://site. <i> </i>com/img. jpg. "

Une fois que vous avez identifié les éléments que vous souhaitez personnaliser, utilisez la commande suivante dans PowerShell pour affecter de nouvelles valeurs aux éléments:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

Vous pouvez personnaliser autant d’éléments à l’aide de la commande que vous le souhaitez.

### <a name="remove-customization-from-an-add-in"></a>Supprimer la personnalisation d’un complément

La seule option actuellement disponible pour la suppression des personnalisations consiste à les supprimer toutes en même temps:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>Afficher les personnalisations des compléments

Pour afficher la liste des personnalisations appliquées, exécutez la cmdlet **Get-OrganizationAddInOverrides** . Si **Get-OrganizationAddInOverrides** est exécuté sans *ProductID* , une liste de tous les compléments avec des substitutions appliquées est renvoyée.  

```powershell
Get-OrganizationAddInOverrides 
```
Si ProductId est spécifié, une liste de substitutions appliquée à ce complément est renvoyée. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>Supprimer un complément du cache local

Si un complément a été déployé, il doit être supprimé du cache de chaque ordinateur pour pouvoir être personnalisé. Pour remive un complément à partir du cache:

1. Accédez au dossier «utilisateurs» dans C:\ 
1. Accéder à votre dossier utilisateur
1. Accédez à AppData\Local\Microsoft\Office et sélectionnez le dossier associé à votre version d’Office.
1. Dans le dossier *WEF* , supprimez le dossier *Manifests* .

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtenir de l’aide détaillée pour chaque cmdlet

Vous pouvez consulter l’aide détaillée pour chaque cmdlet à l’aide de la cmdlet Get-Help. Par exemple, l’applet de commande suivante fournit des informations détaillées sur la cmdlet Remove-OrganizationAddIn.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


