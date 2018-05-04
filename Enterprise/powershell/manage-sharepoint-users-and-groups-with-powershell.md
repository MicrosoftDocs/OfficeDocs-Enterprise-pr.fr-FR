---
title: Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell
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
description: 'Résumé : Utilisation de PowerShell Office 365 pour gérer les utilisateurs, groupes et sites SharePoint Online.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="06166-103">Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="06166-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="06166-104">**Résumé :** Utilisez Office 365 PowerShell pour gérer les utilisateurs, groupes et sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06166-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="06166-105">Si vous êtes un SharePoint Online pour les gérer plus facilement qui fonctionne avec de grandes listes de comptes d’utilisateurs ou des groupes, vous pouvez utiliser Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06166-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="06166-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="06166-106">Before you begin</span></span>

<span data-ttu-id="06166-p101">Les procédures décrites dans cette rubrique requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="06166-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="06166-109">Obtenir une liste de sites, de groupes et d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06166-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="06166-p102">Avant de commencer à gérer les utilisateurs et les groupes, vous devez obtenir les listes de vos sites, groupes et utilisateurs. Vous pouvez ensuite utiliser ces informations pour travailler à partir de l’exemple figurant dans cet article.</span><span class="sxs-lookup"><span data-stu-id="06166-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="06166-112">Obtenir une liste de sites</span><span class="sxs-lookup"><span data-stu-id="06166-112">Get a list of sites</span></span>

<span data-ttu-id="06166-113">Vous pouvez obtenir la liste des sites de votre client avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06166-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="06166-114">Obtenir une liste de groupes</span><span class="sxs-lookup"><span data-stu-id="06166-114">Get a list of groups</span></span>

<span data-ttu-id="06166-115">Vous pouvez obtenir la liste des groupes de votre client avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06166-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="06166-116">Obtenir une liste d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06166-116">Get a list of users</span></span>

<span data-ttu-id="06166-117">Vous pouvez obtenir la liste des utilisateurs de votre client avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06166-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="06166-118">Ajouter un utilisateur au groupe Administrateurs de collection de sites</span><span class="sxs-lookup"><span data-stu-id="06166-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="06166-p103">Vous utilisez la commande **Set-SPOUser** pour ajouter un utilisateur à la liste des administrateurs de Collection de sites dans une collection de sites. Il s’agit de l’aspect de la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="06166-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="06166-121">Cet exemple utilise des variables pour stocker des valeurs et possède des notes dans le script (par exemple «<!--This is the Tenant Name…-->») pour vous aider à comprendre ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="06166-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="06166-122">Par exemple, cet ensemble de commandes ajoute Opalhttp://go.Microsoft.com/fwlink/p/?LinkId=257051 Castillo (opalc de nom d’utilisateur) la liste des administrateurs de Collection de sites sur la collection de sites ContosoTest dans la location contoso1 :</span><span class="sxs-lookup"><span data-stu-id="06166-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="06166-123">Vous pouvez couper et coller ces commandes dans le Bloc-notes, remplacer les valeurs des variables $tenant, $site et $user par des valeurs réelles de votre environnement, puis coller le tout dans votre fenêtre SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="06166-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="06166-124">Ajout d’un utilisateur à d’autres groupes Administrateurs de collection de sites</span><span class="sxs-lookup"><span data-stu-id="06166-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="06166-p104">Dans cette tâche, nous allons utiliser la commande **Add-SPOUser** pour ajouter un utilisateur à un groupe SharePoint sur une collection de sites. Il s’agit de l’aspect de la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="06166-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="06166-127">Par exemple, ajoutons connus pour leurs Glen (glenr nom de l’utilisateur) au groupe de comptes dans la collection de sites ContosoTest dans la location contoso1 :</span><span class="sxs-lookup"><span data-stu-id="06166-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="06166-128">Créer un groupe de collections de sites</span><span class="sxs-lookup"><span data-stu-id="06166-128">Create a site collection group</span></span>

<span data-ttu-id="06166-p105">Vous utilisez la commande **Set-SPOSiteGroup** pour créer un nouveau groupe SharePoint et l’ajouter à la collection de sites ContosoTest. Il s’agit de l’aspect de la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="06166-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="06166-p106">N’importe quelle chaîne par des espaces, mettez-le entre guillemets. Groupes propriétés, telles que des niveaux d’autorisation, peuvent être mis à jour ultérieurement à l’aide de l’applet de commande **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="06166-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="06166-133">Par exemple, ajoutons le groupe de comptes disposant d’autorisations affichage seul à la collection de sites de Contoso Test dans la location contoso1 :</span><span class="sxs-lookup"><span data-stu-id="06166-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="06166-134">Supprimer des utilisateurs d’un groupe</span><span class="sxs-lookup"><span data-stu-id="06166-134">Remove users from a group</span></span>

<span data-ttu-id="06166-p107">Parfois, vous devez supprimer un utilisateur d’un site ou même de tous les sites, par exemple, si l’employé change de service ou quitte l’entreprise. Vous pouvez réaliser cette action facilement dans l’interface utilisateur pour un seul employé, mais déplacer un service complet d’un site à un autre est autrement plus compliqué.</span><span class="sxs-lookup"><span data-stu-id="06166-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="06166-p108">Toutefois, en utilisant les fichiers CSV et de SharePoint Online Management Shell, cela est simple et rapide. Dans cette tâche, vous allez utiliser Windows PowerShell pour supprimer un utilisateur d’un groupe de sécurité de collection de sites. Vous allez utiliser un fichier CSV, puis supprimer de nombreux utilisateurs à partir de différents sites.</span><span class="sxs-lookup"><span data-stu-id="06166-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="06166-p109">Nous allons utiliser la commande **Remove-SPOUser** pour supprimer un utilisateur Office 365 à partir d’un groupe de collection de sites pour nous pouvons voir la syntaxe de la commande. Voici comment la syntaxe de la recherche :</span><span class="sxs-lookup"><span data-stu-id="06166-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="06166-143">Par exemple, nous allons supprimer Bobby Overby du groupe d’auditeurs de collection de sites dans la collection de sites Contoso Test dans la location contoso1 :</span><span class="sxs-lookup"><span data-stu-id="06166-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="06166-p110">Supposons que nous voulions supprimer Bobby de tous les groupes auxquels il appartient actuellement. Voici comment procéder :</span><span class="sxs-lookup"><span data-stu-id="06166-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="06166-p111">Nous souhaitons simplement vous montrer comment faire. Vous ne devez pas exécuter cette commande sauf si vous devez vraiment supprimer un utilisateur de chaque groupe, par exemple si l’utilisateur quitte l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="06166-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="06166-148">Automatiser la gestion des grandes listes d’utilisateurs et de groupes</span><span class="sxs-lookup"><span data-stu-id="06166-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="06166-p112">Pour ajouter un grand nombre de comptes à des sites SharePoint et leur donner des autorisations, vous pouvez utiliser le centre d’administration Office 365, les commandes PowerShell individuelles ou PowerShell un fichier CSV. Ces choix, le fichier CSV est le moyen le plus rapide pour automatiser cette tâche.</span><span class="sxs-lookup"><span data-stu-id="06166-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="06166-p113">Le processus de base consiste à créer un fichier CSV qui comporte des en-têtes (colonnes) qui correspondent aux paramètres dont a besoin le script Windows PowerShell. Vous pouvez facilement créer ce type de liste dans Excel et puis l’exporter dans un fichier CSV. Ensuite, vous utilisez un script Windows PowerShell pour itérer les enregistrements (lignes) dans le fichier CSV, ajout d’utilisateurs aux groupes et les groupes de sites.</span><span class="sxs-lookup"><span data-stu-id="06166-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="06166-p114">Par exemple, créons un fichier CSV pour définir un groupe de collections de sites, des groupes et des autorisations. Puis, nous créerons un fichier CSV pour remplir les groupes avec des utilisateurs. Enfin, nous créerons puis exécuterons un script Windows PowerShell simple qui crée et remplit les groupes.</span><span class="sxs-lookup"><span data-stu-id="06166-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="06166-157">Le premier fichier CSV ajoutera des groupes à des collections de sites et aura la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="06166-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="06166-158">En-tête :</span><span class="sxs-lookup"><span data-stu-id="06166-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="06166-159">Élément :</span><span class="sxs-lookup"><span data-stu-id="06166-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="06166-160">Voici un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="06166-160">Here is an example file:</span></span>

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

<span data-ttu-id="06166-161">Le second fichier CSV ajoutera des utilisateurs à des groupes et aura la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="06166-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="06166-162">En-tête :</span><span class="sxs-lookup"><span data-stu-id="06166-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="06166-163">Élément :</span><span class="sxs-lookup"><span data-stu-id="06166-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="06166-164">Voici un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="06166-164">Here is an example file:</span></span>

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

<span data-ttu-id="06166-p115">Pour la prochaine étape, vous devez avoir enregistré les deux fichiers CSV sur votre lecteur. Voici les commandes qui utilisent les deux fichiers CSV pour ajouter des membres aux groupes et des autorisations :</span><span class="sxs-lookup"><span data-stu-id="06166-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="06166-p116">Le script importe le contenu du fichier CSV et utilise les valeurs dans les colonnes (en gras) pour remplir les paramètres des commandes **New-SPOSiteGroup** et **Add-SPOUser** . Dans notre exemple, nous effectuons l’enregistrement sur le lecteur C, mais vous pouvez l’enregistrer où vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="06166-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="06166-p117">Supprimons maintenant un certain nombre de personnes de plusieurs groupes au sein de différents sites, à l’aide du même fichier CSV. Voici la commande :</span><span class="sxs-lookup"><span data-stu-id="06166-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="06166-171">Générer des rapports sur les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06166-171">Generate user reports</span></span>

<span data-ttu-id="06166-p118">Vous pouvez obtenir un rapport simple pour quelques sites et afficher les utilisateurs de ces sites, leur niveau d’autorisation, ainsi que d’autres propriétés. Voici à quoi ressemble la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="06166-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="06166-p119">Cela récupérer les données pour ces trois sites et les écrire dans un fichier texte sur votre disque local. Notez que le paramètre – Append sera ajouter du contenu à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="06166-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="06166-176">Par exemple, nous allons exécuter un rapport sur les sites ContosoTest, TeamSite01 et Project01 pour la location contoso1 :</span><span class="sxs-lookup"><span data-stu-id="06166-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="06166-p120">Notez que nous devions modifier uniquement la variable **$site** . La variable **$tenant** conserve sa valeur par le biais de toutes les séries de trois de la commande.</span><span class="sxs-lookup"><span data-stu-id="06166-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="06166-p121">Mais que faire si vous souhaitez effectuer cette action pour chaque site ? Vous pouvez le faire sans avoir à entrer tous ces sites web à l’aide de cette commande :</span><span class="sxs-lookup"><span data-stu-id="06166-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="06166-p122">Ce rapport est relativement simple, et vous pouvez ajouter davantage de code pour créer des rapports qui incluent des informations plus détaillées ou des rapports plus spécifiques. Mais cela devrait vous donner une idée de l’utilisation de SharePoint Online Management Shell pour gérer les utilisateurs dans l’environnement SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06166-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="06166-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06166-183">See also</span></span>

[<span data-ttu-id="06166-184">Se connecter à SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="06166-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="06166-185">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="06166-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="06166-186">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="06166-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="06166-187">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="06166-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

