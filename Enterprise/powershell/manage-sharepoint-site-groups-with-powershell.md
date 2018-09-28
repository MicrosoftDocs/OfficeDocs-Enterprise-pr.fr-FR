---
title: Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : Utilisation de PowerShell Office 365 pour gérer les groupes de sites SharePoint Online.'
ms.openlocfilehash: c68e0905c0abcbea279829be7c841c31409db6cf
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975142"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.
  
Bien que vous pouvez utiliser le centre d’administration Office 365, vous pouvez également utiliser Office 365 PowerShell pour gérer vos groupes de sites SharePoint Online.

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cet article requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Vue SharePoint Online avec Office 365 PowerShell

Le centre d’administration SharePoint Online a certaines méthodes à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe, le `https://litwareinc.sharepoint.com/sites/finance` site. Voici ce que vous devez faire pour :

1. À partir du centre d’administration Office 365, cliquez sur **les ressources** > de**Sites**, puis cliquez sur l’URL du site.
2. Dans la boîte de dialogue Collection de sites, cliquez sur **Accéder à ce site**.
3. Sur la page du site, cliquez sur l’icône **Paramètres** (située dans l’angle supérieur droit de la page), puis cliquez sur **Paramètres du site** :<br/>
![Paramètres du site SharePoint Online](media/spo-site-settings.png)<br/>
4. Dans la page Paramètres du Site, cliquez sur **autorisations des Sites** , sous **utilisateurs et autorisations**.

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

Il existe deux manières d’exécuter cette commande définie dans l’invite de commandes SharePoint Online Management Shell :

- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Lorsque vous le faites, PowerShell s’arrête à un **>>** invite. Appuyez sur ENTRÉE pour exécuter la commande **foreach** .<br/>
- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , puis enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script depuis l’invite de commande SharePoint Online Management Shell en spécifiant son nom de fichier et chemin d’accès. Voici un exemple de commande :

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

Dans les deux cas, quelque chose de ce type doit apparaître :

![Groupes de sites SharePoint Online](media/SPO-site-groups.png)

Il s’agit de tous les groupes qui ont été créés pour le site `https://litwareinc.sharepoint.com/sites/finance`, ainsi que tous les utilisateurs affectés à ces groupes. Les noms de groupe sont en jaune pour vous aider à des noms de groupe distinct à partir de leurs membres.

Autre exemple, Voici un ensemble de commandes qui répertorie les groupes et toutes les appartenances au groupe, pour tous vos sites SharePoint Online.

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

