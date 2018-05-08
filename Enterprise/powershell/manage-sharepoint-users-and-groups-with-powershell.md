---
title: Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : Utilisation de PowerShell Office 365 pour gérer les utilisateurs, groupes et sites SharePoint Online.'
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer les utilisateurs, groupes et sites SharePoint Online.

Si vous êtes un administrateur SharePoint Online pour les gérer plus facilement qui fonctionne avec de grandes listes de comptes d’utilisateurs ou des groupes, vous pouvez utiliser Office 365 PowerShell. 

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Obtenir une liste de sites, de groupes et d’utilisateurs

Avant de commencer à gérer les utilisateurs et les groupes, vous devez obtenir les listes de vos sites, groupes et utilisateurs. Vous pouvez ensuite utiliser ces informations pour travailler à partir de l’exemple figurant dans cet article.

### <a name="get-a-list-of-sites"></a>Obtenir une liste de sites

Vous pouvez obtenir la liste des sites de votre client avec la commande suivante :

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Obtenir une liste de groupes

Vous pouvez obtenir la liste des groupes de votre client avec la commande suivante :

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>Obtenir une liste d’utilisateurs

Vous pouvez obtenir la liste des utilisateurs de votre client avec la commande suivante :

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Ajouter un utilisateur au groupe Administrateurs de collection de sites

Vous utilisez la commande **Set-SPOUser** pour ajouter un utilisateur à la liste des administrateurs de Collection de sites dans une collection de sites. Il s’agit de l’aspect de la syntaxe :

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

Pour utiliser ces commandes, remplacer remplacer tous les éléments entre guillemets, y compris les caractères, avec les noms corrects < et >.

Par exemple, cet ensemble de commandes ajoute Opalhttp://go.Microsoft.com/fwlink/p/?LinkId=257051 Castillo (opalc de nom d’utilisateur) la liste des administrateurs de Collection de sites sur la collection de sites ContosoTest dans la location contoso1 :

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Peut copier et coller ces commandes dans le bloc-notes, modifier les valeurs des variables pour $tenant, $site et $user à des valeurs réelles de votre environnement et puis collez-la dans votre fenêtre de SharePoint Online Management Shell pour les exécuter.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Ajout d’un utilisateur à d’autres groupes Administrateurs de collection de sites

Dans cette tâche, nous allons utiliser la commande **Add-SPOUser** pour ajouter un utilisateur à un groupe SharePoint sur une collection de sites.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Par exemple, ajoutons connus pour leurs Glen (glenr nom de l’utilisateur) au groupe de comptes dans la collection de sites ContosoTest dans la location contoso1 :

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Créer un groupe de collections de sites

Vous utilisez la commande **Set-SPOSiteGroup** pour créer un nouveau groupe SharePoint et l’ajouter à la collection de sites ContosoTest.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
Groupes propriétés, telles que des niveaux d’autorisation, peuvent être mis à jour ultérieurement à l’aide de l’applet de commande **Set-SPOSiteGroup** .

Par exemple, ajoutons le groupe de comptes disposant d’autorisations affichage seul à la collection de sites de Contoso Test dans la location contoso1 :

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Supprimer des utilisateurs d’un groupe

Parfois, vous devez supprimer un utilisateur d’un site ou même de tous les sites, par exemple, si l’employé change de service ou quitte l’entreprise. Vous pouvez réaliser cette action facilement dans l’interface utilisateur pour un seul employé, mais déplacer un service complet d’un site à un autre est autrement plus compliqué.

Toutefois, en utilisant les fichiers CSV et de SharePoint Online Management Shell, cela est simple et rapide. Dans cette tâche, vous allez utiliser Windows PowerShell pour supprimer un utilisateur d’un groupe de sécurité de collection de sites. Vous allez utiliser un fichier CSV, puis supprimer de nombreux utilisateurs à partir de différents sites. 

Nous allons utiliser la commande **Remove-SPOUser** pour supprimer un utilisateur Office 365 à partir d’un groupe de collection de sites pour nous pouvons voir la syntaxe de la commande. Voici comment la syntaxe de la recherche :

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
Par exemple, nous allons supprimer Bobby Overby du groupe d’auditeurs de collection de sites dans la collection de sites Contoso Test dans la location contoso1 :

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Supposons que nous voulions supprimer Bobby de tous les groupes auxquels il appartient actuellement. Voici comment procéder :

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Il s’agit juste d’un exemple. Vous ne devez pas exécuter cette commande, sauf si vous devez supprimer un utilisateur à partir de chaque groupe, par exemple, si l’utilisateur quitte l’entreprise.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatiser la gestion des grandes listes d’utilisateurs et de groupes

Pour ajouter un grand nombre de comptes à des sites SharePoint et leur donner des autorisations, vous pouvez utiliser le centre d’administration Office 365, les commandes PowerShell individuelles ou PowerShell un fichier CSV. Ces choix, le fichier CSV est le moyen le plus rapide pour automatiser cette tâche.

Le processus de base consiste à créer un fichier CSV qui comporte des en-têtes (colonnes) qui correspondent aux paramètres dont a besoin le script Windows PowerShell. Vous pouvez facilement créer ce type de liste dans Excel et puis l’exporter dans un fichier CSV. Ensuite, vous utilisez un script Windows PowerShell pour itérer les enregistrements (lignes) dans le fichier CSV, ajout d’utilisateurs aux groupes et les groupes de sites. 

Par exemple, créons un fichier CSV pour définir un groupe de collections de sites, des groupes et des autorisations. Puis, nous créerons un fichier CSV pour remplir les groupes avec des utilisateurs. Enfin, nous créerons puis exécuterons un script Windows PowerShell simple qui crée et remplit les groupes.

Le premier fichier CSV ajoutera des groupes à des collections de sites et aura la structure suivante :

### <a name="header"></a>En-tête :

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Élément :

```
https://tenant.sharepoint.com/sites/site,group,level
```

Voici un exemple de fichier :

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Le second fichier CSV ajoutera des utilisateurs à des groupes et aura la structure suivante :

### <a name="header"></a>En-tête :

```
Group,LoginName,Site
```

### <a name="item"></a>Élément :

```
group,login,https://tenant.sharepoint.com/sites/site
```

Voici un exemple de fichier :

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

À l’étape suivante, vous devez les deux fichiers CSV enregistrés sur votre disque. Voici des exemples de commandes qui utilisent les deux fichiers CSV et d’ajouter les autorisations et appartenances de groupe :

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Le script importe le contenu du fichier CSV et utilise les valeurs des colonnes pour remplir les paramètres des commandes **New-SPOSiteGroup** et **Add-SPOUser** . Dans notre exemple, nous effectuons ce enregistrement dans le dossier theO365Admin sur le lecteur C, mais vous pouvez l’enregistrer où vous le souhaitez.

À présent, nous allons supprimer un groupe de personnes pour plusieurs groupes dans différents sites en utilisant le même fichier CSV. Voici un exemple de commande :

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Générer des rapports sur les utilisateurs

Vous pouvez obtenir un rapport simple pour quelques sites et afficher les utilisateurs de ces sites, leur niveau d’autorisation, ainsi que d’autres propriétés. Voici à quoi ressemble la syntaxe :

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Cela récupérer les données pour ces trois sites et les écrire dans un fichier texte sur votre disque local. Notez que le paramètre – Append sera ajouter du contenu à un fichier existant.

Par exemple, nous allons exécuter un rapport sur les sites ContosoTest, TeamSite01 et Project01 pour la location contoso1 :

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Notez que nous devions modifier uniquement la variable **$site** . La variable **$tenant** conserve sa valeur par le biais de toutes les séries de trois de la commande.

Mais que faire si vous souhaitez effectuer cette action pour chaque site ? Vous pouvez le faire sans avoir à entrer tous ces sites web à l’aide de cette commande :

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Ce rapport est relativement simple, et vous pouvez ajouter davantage de code pour créer des rapports qui incluent des informations plus détaillées ou des rapports plus spécifiques. Mais cela devrait vous donner une idée de l’utilisation de SharePoint Online Management Shell pour gérer les utilisateurs dans l’environnement SharePoint Online.
   
## <a name="see-also"></a>Voir aussi

[Se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gestion de SharePoint Online avec Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

