---
title: Gestion des groupes de sites SharePoint Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: Dans cet article, vous trouverez des procédures pour l’utilisation de PowerShell pour Microsoft 365 afin de gérer les groupes de sites SharePoint Online.
ms.openlocfilehash: 5df2b57db4ac57aaf7905346d090ccde2d96a11c
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605900"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Gestion des groupes de sites SharePoint Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Bien que vous puissiez utiliser le centre d’administration Microsoft 365, vous pouvez également utiliser PowerShell pour Microsoft 365 pour gérer vos groupes de sites SharePoint Online.

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cet article vous obligent à vous connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Afficher SharePoint Online avec PowerShell pour Microsoft 365

Le centre d’administration SharePoint Online propose des méthodes faciles à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe pour le `https://litwareinc.sharepoint.com/sites/finance` site. Voici ce que vous devez faire pour :

1. Dans le centre d’administration SharePoint, cliquez sur **sites actifs**, puis cliquez sur l’URL du site.
2. Sur la page site, cliquez sur l’icône **paramètres** (située dans l’angle supérieur droit de la page), puis cliquez sur **autorisations de site**.

Répétez ensuite ce processus pour le prochain site que vous souhaitez consulter.

Pour obtenir la liste des groupes avec PowerShell pour Microsoft 365, vous pouvez utiliser les commandes suivantes :

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Il existe deux façons d’exécuter ce jeu de commandes dans l’invite de commandes SharePoint Online Management Shell :

- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$SiteUrl** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Dans ce cas, PowerShell s’arrête à l' **>>** invite. Appuyez sur entrée pour exécuter la `foreach` commande.<br/>
- Copiez les commandes dans le Bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** et enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script à partir de l’invite de commandes SharePoint Online Management Shell en spécifiant son chemin d’accès et son nom de fichier. Voici un exemple de commande :

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

Dans les deux cas, quelque chose de ce type doit apparaître :

![Groupes de sites SharePoint Online](media/SPO-site-groups.png)

Il s’agit de tous les groupes qui ont été créés pour le site `https://litwareinc.sharepoint.com/sites/finance` , ainsi que de tous les utilisateurs affectés à ces groupes. Les noms de groupes apparaissent en jaune pour que vous puissiez distinguer les noms de groupes de leurs membres.

Autre exemple, voici un jeu de commandes qui répertorie les groupes et toutes les appartenances aux groupes de tous vos sites SharePoint Online.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

