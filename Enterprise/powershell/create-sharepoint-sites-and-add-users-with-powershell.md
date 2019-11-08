---
title: Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : utilisez Office 365 PowerShell pour créer de nouveaux sites SharePoint Online, puis ajoutez des utilisateurs et des groupes à ces sites.'
ms.openlocfilehash: 2262c69af7dce7472257512d215c1f0425f875f0
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031029"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="ec8cb-103">Création de sites SharePoint Online et ajout d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="ec8cb-104">**Résumé :** Utilisez Office 365 PowerShell pour créer de nouveaux sites SharePoint Online, puis ajoutez des utilisateurs et des groupes à ces sites.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="ec8cb-105">Lorsque vous utilisez Office 365 PowerShell pour créer des sites SharePoint Online et ajouter des utilisateurs, vous pouvez rapidement et régulièrement exécuter des tâches beaucoup plus rapidement que vous ne pouvez le faire dans le centre d’administration d’Office 356.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-105">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center.</span></span> <span data-ttu-id="ec8cb-106">Vous pouvez également effectuer des tâches qui ne sont pas possibles dans le centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-106">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="ec8cb-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="ec8cb-107">Before you begin</span></span>

<span data-ttu-id="ec8cb-108">Les procédures décrites dans cette rubrique vous obligent à vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="ec8cb-109">Pour obtenir des instructions, consultez la rubrique [connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="ec8cb-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="ec8cb-110">Étape 1 : Création de collections de sites à l’aide d’Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="ec8cb-111">Créez plusieurs sites à l’aide d’Office 365 PowerShell et un fichier .csv à l’aide de l’exemple de code fourni et du Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-111">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="ec8cb-112">Pendant cette procédure, vous allez remplacer les informations de l’espace réservé indiquées entre parenthèses par vos informations propres au site et au client.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="ec8cb-113">Ce processus vous permet de créer un seul fichier et d’exécuter une seule commande Office 365 PowerShell qui utilise ce fichier.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-113">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="ec8cb-114">Cela rend les actions entreprises à la fois reproductibles et portables et élimine beaucoup, sinon la totalité, des erreurs qui peuvent provenir de la saisie de longues commandes dans SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="ec8cb-115">Cette procédure est en deux parties.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-115">There are two parts to this procedure.</span></span> <span data-ttu-id="ec8cb-116">Tout d’abord, vous devez créer un fichier .csv, puis le référencer à l’aide d’Office 365 PowerShell, qui utilise son contenu pour créer les sites.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-116">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="ec8cb-p104">La cmdlet Office 365 PowerShell importe le fichier .csv et l’inclut dans une boucle à l’intérieur des accolades à l’aide d’une barre verticale, laquelle boucle lit la première ligne du fichier comme des en-têtes de colonne. La cmdlet Office 365 PowerShell parcourt ensuite les enregistrements restants, crée une nouvelle collection de sites pour chaque enregistrement, puis affecte les propriétés de la collection de sites en fonction des en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="ec8cb-119">Créer un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="ec8cb-119">Create a .csv file</span></span>

1. <span data-ttu-id="ec8cb-120">Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="ec8cb-121">Où *client* est le nom de votre client, et *propriétaire* le nom d’utilisateur de l’utilisateur sur votre client auquel vous souhaitez accorder le rôle administrateur principal de la collection de sites.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="ec8cb-122">(Vous pouvez appuyer sur Ctrl + H lorsque vous utilisez le bloc-notes pour remplacer les remplacements en bloc plus rapidement.)</span><span class="sxs-lookup"><span data-stu-id="ec8cb-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="ec8cb-123">Enregistrez le fichier sur votre bureau en tant que **SiteCollections. csv**.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="ec8cb-124">Avant d’utiliser ce fichier .csv, tout autre fichier .csv ou un fichier de script WindowsPowerShell, nous vous recommandons de vérifier qu’il ne contient pas de caractères superflus ou non imprimables.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-124">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="ec8cb-125">Ouvrez le fichier dans Word et, dans le ruban, cliquez sur l’icône paragraphe pour afficher les caractères non imprimables.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="ec8cb-126">Il ne doit pas y avoir de caractères non imprimables superflus.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="ec8cb-127">Par exemple, il ne doit y avoir aucune marque de paragraphe après la dernière marque à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="ec8cb-128">Exécuter la commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="ec8cb-129">À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="ec8cb-130">Où *MyAlias* est égal à votre alias d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="ec8cb-p106">Attendez que l’invite de Windows PowerShell réapparaisse. Cela peut prendre une minute ou deux.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="ec8cb-133">À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="ec8cb-134">Notez les nouvelles collections de sites dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-134">Note the new site collections in the list.</span></span> <span data-ttu-id="ec8cb-135">Les collections de sites suivantes doivent s’afficher : **ContosoTest**, **TeamSite01**, **Blog01**et **Projet01**</span><span class="sxs-lookup"><span data-stu-id="ec8cb-135">You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="ec8cb-p108">C’est fait. Vous avez créé plusieurs collections de sites à l’aide du fichier .csv que vous aviez créé et d’une seule cmdlet Windows PowerShell. Vous êtes maintenant prêt à créer et à affecter des utilisateurs à ces sites.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="ec8cb-139">Étape 2 : Ajout d’utilisateurs et de groupes</span><span class="sxs-lookup"><span data-stu-id="ec8cb-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="ec8cb-p109">Vous allez maintenant créer des utilisateurs et les ajouter à un groupe de collections de sites. Vous utiliserez ensuite un fichier .csv pour télécharger en bloc de nouveaux groupes et utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="ec8cb-142">Les procédures suivantes supposent que vous avez créé les collections de sites contosotest, TeamSite01, Blog01 et Projet01.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="ec8cb-143">Créer des fichiers .csv et .ps1</span><span class="sxs-lookup"><span data-stu-id="ec8cb-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="ec8cb-144">Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="ec8cb-145">Où *client* est égal à votre nom de client.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="ec8cb-146">Enregistrez le fichier sur votre bureau en tant que **GroupsAndPermissions. csv**.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="ec8cb-147">Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="ec8cb-148">Où *client* est égal à votre nom de client, et *NomUtilisateur* est égal au nom d’utilisateur d’un utilisateur existant.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="ec8cb-149">Enregistrez le fichier sur votre bureau en tant que **users. csv**.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="ec8cb-150">Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="ec8cb-151">Où MyAlias est égal au nom d’utilisateur de l’utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="ec8cb-152">Enregistrez le fichier sur votre bureau sous le **UsersAndGroups. ps1**.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="ec8cb-153">Il s’agit d’un script Windows PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="ec8cb-154">Vous êtes maintenant prêt à exécuter le script UsersAndGroup.ps1 pour ajouter des utilisateurs et des groupes à plusieurs collections de sites.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="ec8cb-155">Exécuter le script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="ec8cb-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="ec8cb-156">Revenez à SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="ec8cb-157">À l’invite de Windows PowerShell, saisissez ou copiez-collez la ligne suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="ec8cb-158">À l’invite de confirmation, appuyez sur **Y**.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="ec8cb-159">À l’invite de Windows PowerShell, saisissez ou copiez-collez ce qui suit, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="ec8cb-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="ec8cb-160">Où *MyAlias* est égal à votre nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="ec8cb-p111">Attendez le renvoi de l’invite pour continuer. Les groupes s’afficheront d’abord tels qu’ils ont été créés. Ensuite, vous verrez la liste de groupes se répéter au fur et à mesure de l’ajout des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ec8cb-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec8cb-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec8cb-164">See also</span></span>

[<span data-ttu-id="ec8cb-165">Connexion à SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="ec8cb-166">Gérer les groupes de sites SharePoint Online Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="ec8cb-167">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ec8cb-168">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="ec8cb-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

