---
title: Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour gérer les utilisateurs, les groupes et les sites SharePoint Online.'
ms.openlocfilehash: ae232766031dade061e79a574efa14e8432ae08c
ms.sourcegitcommit: 7bf52d4277b97d6f1c585da2c83979fbcf061c1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "46542815"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous êtes un administrateur SharePoint Online qui travaille avec de grandes listes de comptes ou de groupes d’utilisateurs et qu’il souhaite un moyen plus facile de les gérer, vous pouvez utiliser PowerShell pour Microsoft 365. 

Avant de commencer, les procédures décrites dans cette rubrique nécessitent que vous vous connectiez à SharePoint Online. Pour obtenir des instructions, consultez la rubrique [connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Obtenir une liste de sites, de groupes et d’utilisateurs

Avant de commencer à gérer les utilisateurs et les groupes, vous devez obtenir les listes de vos sites, groupes et utilisateurs. Vous pouvez ensuite utiliser ces informations pour travailler à partir de l’exemple figurant dans cet article.

Vous pouvez obtenir la liste des sites de votre client avec la commande suivante :

```powershell
Get-SPOSite
```

Vous pouvez obtenir la liste des groupes de votre client avec la commande suivante :

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Vous pouvez obtenir la liste des utilisateurs de votre client avec la commande suivante :

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Ajouter un utilisateur au groupe Administrateurs de collection de sites

Utilisez l’applet de commande `Set-SPOUser` pour ajouter un utilisateur à la liste des administrateurs de collection de sites sur une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Pour utiliser ces commandes, remplacez tous les éléments entre guillemets, y compris les caractères < et >, par les noms corrects.

Par exemple, cet ensemble de commandes ajoute Opal Castillo (nom d’utilisateur opalc) à la liste des administrateurs de collection de sites sur la collection de sites ContosoTest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Vous pouvez copier et coller ces commandes dans le bloc-notes, modifier les valeurs des variables des $tenant, $site et $user en valeurs réelles à partir de votre environnement, puis collez-les dans votre fenêtre SharePoint Online Management Shell pour les exécuter.

## <a name="add-a-user-to-other-site-collection-groups"></a>Ajouter un utilisateur à d’autres groupes de collection de sites

Dans cette tâche, nous allons utiliser l' `Add-SPOUser` applet de commande pour ajouter un utilisateur à un groupe SharePoint sur une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Par exemple, nous allons ajouter Glen Rife (nom d’utilisateur glenr) au groupe auditeurs sur la collection de sites ContosoTest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Créer un groupe de collections de sites

Utilisez l' `New-SPOSiteGroup` applet de commande pour créer un groupe SharePoint et l’ajouter à une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
Les propriétés de groupe, telles que les niveaux d’autorisation, peuvent être mises à jour ultérieurement à l’aide de l’applet de commande `Set-SPOSiteGroup` .

Par exemple, nous allons ajouter le groupe auditeurs avec des autorisations d’affichage seul à la collection de sites ContosoTest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Supprimer des utilisateurs d’un groupe

Parfois, vous devez supprimer un utilisateur d’un site ou même de tous les sites, par exemple, si l’employé change de service ou quitte l’entreprise. Vous pouvez réaliser cette action facilement dans l’interface utilisateur pour un seul employé, mais déplacer un service complet d’un site à un autre est autrement plus compliqué.

Cependant, à l’aide de SharePoint Online Management Shell et des fichiers CSV, cette opération est rapide et facile. Dans cette tâche, vous allez utiliser Windows PowerShell pour supprimer un utilisateur d’un groupe de sécurité de collection de sites. Vous utiliserez ensuite un fichier CSV et supprimerez de nombreux utilisateurs de différents sites. 

Nous allons utiliser la cmdlet « Remove-époux » pour supprimer un seul utilisateur de Microsoft 365 d’un groupe de collection de sites pour pouvoir voir la syntaxe de la commande. Voici à quoi ressemble la syntaxe :

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
Par exemple, nous allons supprimer Bobby Overby du groupe des auditeurs de collection de sites dans la collection de sites ContosoTest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Supposons que nous voulions supprimer Bobby de tous les groupes auxquels il appartient actuellement. Voici comment procéder :

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Ce n’est qu’un exemple. Vous ne devez pas exécuter cette commande sauf si vous devez vraiment supprimer un utilisateur de chaque groupe, par exemple si l’utilisateur quitte l’entreprise.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatiser la gestion des grandes listes d’utilisateurs et de groupes

Pour ajouter un grand nombre de comptes aux sites SharePoint et leur donner des autorisations, vous pouvez utiliser le centre d’administration 365 de Microsoft, des commandes PowerShell individuelles ou PowerShell un fichier CSV. Parmi tous ces choix, le fichier CSV est le moyen le plus rapide d’automatiser cette tâche.

Le processus de base consiste à créer un fichier CSV qui possède des en-têtes (colonnes) correspondant aux paramètres dont le script Windows PowerShell a besoin. Vous pouvez facilement créer une liste de ce type dans Excel, puis l’exporter en tant que fichier CSV. Ensuite, vous utilisez un script Windows PowerShell pour parcourir les enregistrements (lignes) dans le fichier CSV, en ajoutant les utilisateurs à des groupes et les groupes à des sites. 

Par exemple, créons un fichier CSV pour définir un groupe de collections de sites, des groupes et des autorisations. Puis, nous créerons un fichier CSV pour remplir les groupes avec des utilisateurs. Enfin, nous créerons puis exécuterons un script Windows PowerShell simple qui crée et remplit les groupes.

Le premier fichier CSV ajoutera des groupes à des collections de sites et aura la structure suivante :

Tête

```powershell
Site,Group,PermissionLevels
```

Complémentaires

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Voici un exemple de fichier :

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Le second fichier CSV ajoutera des utilisateurs à des groupes et aura la structure suivante :

Tête

```powershell
Group,LoginName,Site
```

Complémentaires

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Voici un exemple de fichier :

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

Pour la prochaine étape, vous devez avoir enregistré les deux fichiers CSV sur votre lecteur. Voici des exemples de commandes qui utilisent des fichiers CSV et pour ajouter des autorisations et l’appartenance à un groupe :

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Le script importe le contenu du fichier CSV et utilise les valeurs des colonnes pour renseigner les paramètres des commandes **New-SPOSiteGroup** et **Add-époux** . Dans notre exemple, nous enregistrons ce fichier dans le dossier theO365Admin sur le lecteur C, mais vous pouvez l’enregistrer où vous le souhaitez.

Supprimons maintenant un certain nombre de personnes de plusieurs groupes au sein de différents sites, à l’aide du même fichier CSV. Voici un exemple de commande :

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Générer des rapports sur les utilisateurs

Vous pouvez obtenir un rapport simple pour quelques sites et afficher les utilisateurs de ces sites, leur niveau d’autorisation, ainsi que d’autres propriétés. Voici à quoi ressemble la syntaxe :

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Cela permet de collecter les données de ces trois sites et de les écrire dans un fichier texte sur votre lecteur local. Notez que le paramètre –Append ajoutera le nouveau contenu à un fichier existant.

Par exemple, nous allons exécuter un rapport sur les sites ContosoTest, TeamSite01 et Project01 pour la location contoso1 :

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Notez que nous devions modifier uniquement la variable **$site** . La variable **$tenant** conserve sa valeur par le biais des trois exécutions de la commande.

Mais que faire si vous souhaitez effectuer cette action pour chaque site ? Vous pouvez le faire sans avoir à entrer tous ces sites web à l’aide de cette commande :

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Ce rapport est assez simple, et vous pouvez ajouter du code pour créer des rapports plus spécifiques ou des rapports qui contiennent des informations plus détaillées. Mais cela doit vous donner une idée de l’utilisation de SharePoint Online Management Shell pour gérer les utilisateurs dans l’environnement SharePoint Online.
   
## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gérer SharePoint Online avec PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
