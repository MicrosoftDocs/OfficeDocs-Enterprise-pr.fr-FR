---
title: Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : Utilisation de PowerShell Office 365 pour créer des sites SharePoint Online, puis ajoutez les utilisateurs et les groupes à ces sites.'
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897167"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell

 **Résumé :** Office 365 PowerShell permet de créer des sites SharePoint Online, puis ajoutez les utilisateurs et les groupes à ces sites.

Lorsque vous utilisez Office 365 PowerShell pour créer des sites SharePoint Online et ajouter des utilisateurs, vous pouvez rapidement et à plusieurs reprises effectuer beaucoup plus rapide que vous pouvez dans le centre d’administration Office 356. Vous pouvez également effectuer les tâches qui ne sont pas possibles d’effectuer dans le centre d’administration Office 356. 

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Étape 1 : Création de collections de sites à l’aide d’Office 365 PowerShell

Créer plusieurs sites à l’aide d’Office 365 PowerShell et un fichier .csv que vous créez à l’aide de l’exemple de code fourni et le bloc-notes. Pour exécuter cette procédure, vous allez remplacer les informations d’espace réservé indiquées entre crochets avec vos propres informations spécifiques du site et du client. Ce processus permet de créer un seul fichier et exécutez une commande d’Office 365 PowerShell unique qui utilise ce fichier. Cela rend les actions prises reproductible et portable et élimine un grand nombre, si pas toutes les erreurs qui peuvent provenir de taper des commandes longues dans SharePoint Online Management Shell. Il existe deux parties à cette procédure. Tout d’abord, vous allez créer un fichier .csv, puis vous devez faire référence à ce fichier .csv à l’aide de PowerShell Office 365, qui utilise son contenu pour créer les sites.

La cmdlet Office 365 PowerShell importe le fichier .csv et l’inclut dans une boucle à l’intérieur des accolades à l’aide d’une barre verticale, laquelle boucle lit la première ligne du fichier comme des en-têtes de colonne. La cmdlet Office 365 PowerShell parcourt ensuite les enregistrements restants, crée une nouvelle collection de sites pour chaque enregistrement, puis affecte les propriétés de la collection de sites en fonction des en-têtes de colonne.

### <a name="create-a-csv-file"></a>Créer un fichier CSV

1. Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Où *client* est le nom de votre client, et le *propriétaire* est le nom d’utilisateur de l’utilisateur sur votre client auquel vous souhaitez accorder le rôle d’administrateur de collection de sites principaux.<br/>(Vous pouvez appuyer sur Ctrl + H lorsque vous utilisez le bloc-notes pour en bloc remplacer plus rapidement.)<br/>

2. Enregistrez le fichier sur votre bureau en tant que **SiteCollections.csv**.<br/>

> [!TIP]
> Avant d’utiliser ce ou tout autre .csv ou fichier de script Windows PowerShell, il est judicieux de vous assurer qu’il n’y a pas de caractères étrangers ou non imprimables. Ouvrez le fichier dans Word et dans le ruban, cliquez sur l’icône de paragraphe pour afficher les caractères non imprimables. Il ne doit être aucun des caractères non imprimables superflues. Par exemple, il ne doit être aucune marque de paragraphe au-delà de la dernière à la fin du fichier.

### <a name="run-the-windows-powershell-command"></a>Exécuter la commande Windows PowerShell

1. À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Où *MyAlias* est égale à votre alias de l’utilisateur.<br/>

2. Attendez que l’invite de Windows PowerShell réapparaisse. Cela peut prendre une minute ou deux.<br/>

3. À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Notez les nouvelles collections de sites dans la liste. Vous devez voir les collections de sites suivants : **contosotest**, **TeamSite01**, **Blog01**et **projet01**

C’est fait. Vous avez créé plusieurs collections de sites à l’aide du fichier .csv que vous aviez créé et d’une seule cmdlet Windows PowerShell. Vous êtes maintenant prêt à créer et à affecter des utilisateurs à ces sites.

## <a name="step-2-add-users-and-groups"></a>Étape 2 : Ajout d’utilisateurs et de groupes

Vous allez maintenant créer des utilisateurs et les ajouter à un groupe de collections de sites. Vous utiliserez ensuite un fichier .csv pour télécharger en bloc de nouveaux groupes et utilisateurs.

Les procédures suivantes supposent que vous avez créé les collections de sites contosotest, TeamSite01, Blog01 et Projet01.

### <a name="create-csv-and-ps1-files"></a>Créer des fichiers .csv et .ps1

1. Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>Où *client* correspond au nom de votre client.<br/>

2. Enregistrez le fichier sur votre bureau en tant que **GroupsAndPermissions.csv**.<br/>

3. Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>Où *client* correspond au nom de votre client, et le *nom d’utilisateur* correspond au nom d’un utilisateur existant.<br/>

4. Enregistrez le fichier sur votre bureau en tant que **Users.csv**.<br/>

5. Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Où MyAlias correspond au nom de l’utilisateur actuellement connecté.<br/>

6. Enregistrez le fichier sur votre bureau sous **UsersAndGroups.ps1**. Il s’agit d’un simple script Windows PowerShell.

Vous êtes maintenant prêt à exécuter le script UsersAndGroup.ps1 pour ajouter des utilisateurs et des groupes à plusieurs collections de sites.

### <a name="run-usersandgroupsps1-script"></a>Exécuter le script UsersAndGroups.ps1

1. Revenez à SharePoint Online Management Shell.<br/>
2. À l’invite de Windows PowerShell, saisissez ou copiez-collez la ligne suivante, puis appuyez sur Entrée :<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. À l’invite de confirmation, appuyez sur **Y**.<br/>

4. À l’invite de Windows PowerShell, saisissez ou copiez-collez ce qui suit, puis appuyez sur Entrée :<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Où *MyAlias* correspond à votre nom d’utilisateur.<br/>

5. Attendez le renvoi de l’invite pour continuer. Les groupes s’afficheront d’abord tels qu’ils ont été créés. Ensuite, vous verrez la liste de groupes se répéter au fur et à mesure de l’ajout des utilisateurs.

## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gérer les groupes de sites SharePoint Online Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

