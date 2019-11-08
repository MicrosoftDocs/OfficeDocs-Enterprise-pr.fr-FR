---
title: Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.'
ms.openlocfilehash: 2deaeb2a39b094b828f75a18d4a2c2f06ca79e47
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031739"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.
  
Bien que vous puissiez utiliser le centre d’administration Microsoft 365, vous pouvez également utiliser Office 365 PowerShell pour gérer vos groupes de sites SharePoint Online.

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cet article vous obligent à vous connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Afficher SharePoint Online avec Office 365 PowerShell

Le centre d’administration SharePoint Online propose des méthodes faciles à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe pour le `https://litwareinc.sharepoint.com/sites/finance` site. Voici ce que vous devez faire :

1. Dans le centre d’administration Microsoft 365, cliquez sur**sites**de **ressources** > , puis cliquez sur l’URL du site.
2. Dans la boîte de dialogue Collection de sites, cliquez sur **Accéder à ce site**.
3. Sur la page du site, cliquez sur l’icône **Paramètres** (située dans l’angle supérieur droit de la page), puis cliquez sur **Paramètres du site** :<br/>
![Paramètres du site SharePoint Online](media/spo-site-settings.png)<br/>
4. Dans la page Paramètres du site, cliquez sur **Autorisations de site** sous **Utilisateurs et autorisations**.

Répétez ensuite ce processus pour le prochain site que vous souhaitez consulter.

Pour obtenir une liste des groupes avec Office 365 PowerShell, vous devez utiliser le jeu de commandes suivant :

```
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

- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$SiteUrl** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Dans ce cas, PowerShell s’arrête à l' **>>** invite. Appuyez sur ENTRÉE pour exécuter la commande **foreach**.<br/>
- Copiez les commandes dans le Bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** et enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script à partir de l’invite de commandes SharePoint Online Management Shell en spécifiant son chemin d’accès et son nom de fichier. Voici un exemple de commande :

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

Dans les deux cas, quelque chose de ce type doit apparaître :

![Groupes de sites SharePoint Online](media/SPO-site-groups.png)

Il s’agit de tous les groupes qui ont été créés pour `https://litwareinc.sharepoint.com/sites/finance`le site, ainsi que de tous les utilisateurs affectés à ces groupes. Les noms de groupes apparaissent en jaune pour que vous puissiez distinguer les noms de groupes de leurs membres.

Autre exemple, voici un jeu de commandes qui répertorie les groupes et toutes les appartenances aux groupes de tous vos sites SharePoint Online.

```
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

[Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

