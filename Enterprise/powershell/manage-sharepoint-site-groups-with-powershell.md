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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="6c698-103">Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c698-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="6c698-104">**Résumé :** Utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6c698-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="6c698-105">Bien que vous pouvez utiliser le centre d’administration Office 365, vous pouvez également utiliser Office 365 PowerShell pour gérer vos groupes de sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6c698-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="6c698-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="6c698-106">Before you begin</span></span>

<span data-ttu-id="6c698-p101">Les procédures décrites dans cet article requièrent pour se connecter à SharePoint Online. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="6c698-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="6c698-109">Vue SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c698-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="6c698-p102">Le centre d’administration SharePoint Online a certaines méthodes à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe, le https://litwareinc.sharepoint.com/sites/finance site. Voici ce que vous devez faire pour :</span><span class="sxs-lookup"><span data-stu-id="6c698-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="6c698-113">À partir du centre d’administration Office 365, cliquez sur **les ressources** > de**Sites**, puis cliquez sur l’URL du site.</span><span class="sxs-lookup"><span data-stu-id="6c698-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="6c698-114">Dans la boîte de dialogue de collection de sites, cliquez sur **ce site**.</span><span class="sxs-lookup"><span data-stu-id="6c698-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="6c698-115">Dans la page de site, cliquez sur l’icône **paramètres** (située dans l’angle supérieur droit de la page) et puis cliquez sur **paramètres du Site**:</span><span class="sxs-lookup"><span data-stu-id="6c698-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="6c698-116">![Paramètres du site SharePoint Online](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="6c698-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="6c698-117">Dans la page Paramètres du Site, cliquez sur **autorisations des Sites** , sous **utilisateurs et autorisations**.</span><span class="sxs-lookup"><span data-stu-id="6c698-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="6c698-118">Répétez ensuite ce processus pour le prochain site que vous souhaitez consulter.</span><span class="sxs-lookup"><span data-stu-id="6c698-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="6c698-119">Pour obtenir une liste des groupes avec Office 365 PowerShell, vous devez utiliser le jeu de commandes suivant :</span><span class="sxs-lookup"><span data-stu-id="6c698-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="6c698-120">Il existe deux manières d’exécuter cette commande définie dans l’invite de commandes SharePoint Online Management Shell :</span><span class="sxs-lookup"><span data-stu-id="6c698-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>
- <span data-ttu-id="6c698-p103">Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Lorsque vous le faites, PowerShell s’arrête à un >> invite. Appuyez sur ENTRÉE pour exécuter le pour chaque commande.</span><span class="sxs-lookup"><span data-stu-id="6c698-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a >> prompt. Press Enter to execute the for each command.</span></span></br>
- <span data-ttu-id="6c698-p104">Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , puis enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script depuis l’invite de commande SharePoint Online Management Shell en spécifiant son nom de fichier et chemin d’accès. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="6c698-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example:</span></span></br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
<span data-ttu-id="6c698-127">$x = get-SPOSite foreach ($y dans $x) {$y.Url Write-Host - ForegroundColor « jaune » $z = Get-SPOSiteGroup-Site $y.Url foreach ($un $z en) {$b = Get-SPOSiteGroup-$y.Url de sites-groupe $a.Title Write-Host $b.Title - ForegroundColor $b « Cyan » | Select-Object - ExpandProperty utilisateurs Write-Host}}</span><span class="sxs-lookup"><span data-stu-id="6c698-127">$x = Get-SPOSite foreach ($y in $x) { Write-Host $y.Url -ForegroundColor "Yellow" $z = Get-SPOSiteGroup -Site $y.Url foreach ($a in $z) { $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title Write-Host $b.Title -ForegroundColor "Cyan" $b | Select-Object -ExpandProperty Users Write-Host } }</span></span>
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

