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
description: 'Résumé: utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.'
ms.openlocfilehash: a128823ba125342bd1d209ac8a2bf28334da866d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068860"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="8851c-103">Gestion des groupes de sites SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="8851c-104">**Résumé:** Utilisez Office 365 PowerShell pour gérer les groupes de sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8851c-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="8851c-105">Bien que vous puissiez utiliser le centre d’administration Microsoft 365, vous pouvez également utiliser Office 365 PowerShell pour gérer vos groupes de sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8851c-105">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="8851c-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="8851c-106">Before you begin</span></span>

<span data-ttu-id="8851c-107">Les procédures décrites dans cet article vous obligent à vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8851c-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="8851c-108">Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="8851c-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="8851c-109">Afficher SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="8851c-110">Le centre d’administration SharePoint Online propose des méthodes faciles à utiliser pour la gestion des groupes de sites.</span><span class="sxs-lookup"><span data-stu-id="8851c-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="8851c-111">Par exemple, supposons que vous souhaitez consulter les groupes et les membres du groupe pour le `https://litwareinc.sharepoint.com/sites/finance` site.</span><span class="sxs-lookup"><span data-stu-id="8851c-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="8851c-112">Voici ce que vous devez faire :</span><span class="sxs-lookup"><span data-stu-id="8851c-112">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="8851c-113">Dans le centre d’administration Microsoft 365, cliquez sur**sites**de **ressources** > , puis cliquez sur l’URL du site.</span><span class="sxs-lookup"><span data-stu-id="8851c-113">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="8851c-114">Dans la boîte de dialogue Collection de sites, cliquez sur **Accéder à ce site**.</span><span class="sxs-lookup"><span data-stu-id="8851c-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="8851c-115">Sur la page du site, cliquez sur l’icône **Paramètres** (située dans l’angle supérieur droit de la page), puis cliquez sur **Paramètres du site** :</span><span class="sxs-lookup"><span data-stu-id="8851c-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="8851c-116">![Paramètres du site SharePoint Online](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="8851c-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="8851c-117">Dans la page Paramètres du site, cliquez sur **Autorisations de site** sous **Utilisateurs et autorisations**.</span><span class="sxs-lookup"><span data-stu-id="8851c-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="8851c-118">Répétez ensuite ce processus pour le prochain site que vous souhaitez consulter.</span><span class="sxs-lookup"><span data-stu-id="8851c-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="8851c-119">Pour obtenir une liste des groupes avec Office 365 PowerShell, vous devez utiliser le jeu de commandes suivant :</span><span class="sxs-lookup"><span data-stu-id="8851c-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="8851c-120">Il existe deux façons d’exécuter ce jeu de commandes dans l’invite de commandes SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="8851c-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="8851c-121">Copiez les commandes dans le bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$SiteUrl** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="8851c-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="8851c-122">Dans ce cas, PowerShell s’arrête à l' **>>** invite.</span><span class="sxs-lookup"><span data-stu-id="8851c-122">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="8851c-123">Appuyez sur ENTRÉE pour exécuter la commande **foreach**.</span><span class="sxs-lookup"><span data-stu-id="8851c-123">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="8851c-124">Copiez les commandes dans le Bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** et enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié.</span><span class="sxs-lookup"><span data-stu-id="8851c-124">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="8851c-125">Ensuite, exécutez le script à partir de l’invite de commandes SharePoint Online Management Shell en spécifiant son chemin d’accès et son nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="8851c-125">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="8851c-126">Voici un exemple de commande :</span><span class="sxs-lookup"><span data-stu-id="8851c-126">Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="8851c-127">Dans les deux cas, quelque chose de ce type doit apparaître :</span><span class="sxs-lookup"><span data-stu-id="8851c-127">In both cases, you should see something similar to this:</span></span>

![Groupes de sites SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="8851c-129">Il s’agit de tous les groupes qui ont été créés pour `https://litwareinc.sharepoint.com/sites/finance`le site, ainsi que de tous les utilisateurs affectés à ces groupes.</span><span class="sxs-lookup"><span data-stu-id="8851c-129">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="8851c-130">Les noms de groupes apparaissent en jaune pour que vous puissiez distinguer les noms de groupes de leurs membres.</span><span class="sxs-lookup"><span data-stu-id="8851c-130">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="8851c-131">Autre exemple, voici un jeu de commandes qui répertorie les groupes et toutes les appartenances aux groupes de tous vos sites SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8851c-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="8851c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8851c-132">See also</span></span>

[<span data-ttu-id="8851c-133">Connexion à SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="8851c-134">Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="8851c-135">Gestion des utilisateurs et des groupes SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="8851c-136">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8851c-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8851c-137">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="8851c-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

