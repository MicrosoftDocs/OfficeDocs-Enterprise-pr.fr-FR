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
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.
  
Bien que vous pouvez utiliser le centre d’administration Office 365, vous pouvez également utiliser Office 365 PowerShell pour gérer vos groupes de sites SharePoint Online.

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cet article requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Vue SharePoint Online avec Office 365 PowerShell

Le centre d’administration SharePoint Online a certaines méthodes à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe, le https://litwareinc.sharepoint.com/sites/finance site. Voici ce que vous devez faire pour :

1. À partir du centre d’administration Office 365, cliquez sur **les ressources** > de**Sites**, puis cliquez sur l’URL du site.
2. Dans la boîte de dialogue de collection de sites, cliquez sur **ce site**.
3. Dans la page de site, cliquez sur l’icône **paramètres** (située dans l’angle supérieur droit de la page) et puis cliquez sur **paramètres du Site**:</br>
![Paramètres du site SharePoint Online](images/spo-site-settings.png)</br>
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
- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Lorsque vous le faites, PowerShell s’arrête à un >> invite. Appuyez sur ENTRÉE pour exécuter le pour chaque commande.</br>
- Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , puis enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script depuis l’invite de commande SharePoint Online Management Shell en spécifiant son nom de fichier et chemin d’accès. Voici un exemple :</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = get-SPOSite foreach ($y dans $x) {$y.Url Write-Host - ForegroundColor « jaune » $z = Get-SPOSiteGroup-Site $y.Url foreach ($un $z en) {$b = Get-SPOSiteGroup-$y.Url de sites-groupe $a.Title Write-Host $b.Title - ForegroundColor $b « Cyan » | Select-Object - ExpandProperty utilisateurs Write-Host}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

