---
title: Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: 'Résumé : utilisez PowerShell pour créer de nouveaux sites SharePoint Online, puis ajoutez des utilisateurs et des groupes à ces sites.'
ms.openlocfilehash: 2791b4de9388e3ff828a665aeeef5ada19627107
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230800"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a><span data-ttu-id="f3b53-103">Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-103">Create SharePoint Online sites and add users with PowerShell</span></span>

<span data-ttu-id="f3b53-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="f3b53-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f3b53-105">Lorsque vous utilisez PowerShell pour Microsoft 365 pour créer des sites SharePoint Online et ajouter des utilisateurs, vous pouvez rapidement et régulièrement exécuter des tâches beaucoup plus rapidement que vous ne pouvez le faire dans le centre d’administration de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f3b53-105">When you use PowerShell for Microsoft 365 to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Microsoft 365 admin center.</span></span> <span data-ttu-id="f3b53-106">Vous pouvez également effectuer des tâches qui ne peuvent pas être effectuées dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f3b53-106">You can also perform tasks that are not possible to perform in the Microsoft 365 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f3b53-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="f3b53-107">Before you begin</span></span>

<span data-ttu-id="f3b53-108">Les procédures décrites dans cette rubrique vous obligent à vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f3b53-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="f3b53-109">Pour obtenir des instructions, consultez la rubrique [connexion à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="f3b53-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-powershell"></a><span data-ttu-id="f3b53-110">Étape 1 : créer des collections de sites à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-110">Step 1: Create new site collections using PowerShell</span></span>

<span data-ttu-id="f3b53-111">Créez plusieurs sites à l’aide de PowerShell et d’un fichier. csv que vous créez à l’aide de l’exemple de code fourni et du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="f3b53-111">Create multiple sites using PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="f3b53-112">Pendant cette procédure, vous allez remplacer les informations de l’espace réservé indiquées entre parenthèses par vos informations propres au site et au client.</span><span class="sxs-lookup"><span data-stu-id="f3b53-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="f3b53-113">Ce processus vous permet de créer un seul fichier et d’exécuter une seule commande PowerShell qui utilise ce fichier.</span><span class="sxs-lookup"><span data-stu-id="f3b53-113">This process lets you create a single file and run a single PowerShell command that uses that file.</span></span> <span data-ttu-id="f3b53-114">Cela rend les actions entreprises à la fois reproductibles et portables et élimine beaucoup, sinon la totalité, des erreurs qui peuvent provenir de la saisie de longues commandes dans SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="f3b53-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="f3b53-115">Cette procédure est en deux parties.</span><span class="sxs-lookup"><span data-stu-id="f3b53-115">There are two parts to this procedure.</span></span> <span data-ttu-id="f3b53-116">Tout d’abord, vous allez créer un fichier. csv, puis vous ferez référence à ce fichier. csv à l’aide de PowerShell, qui utilisera son contenu pour créer les sites.</span><span class="sxs-lookup"><span data-stu-id="f3b53-116">First you’ll create a .csv file, and then you’ll reference that .csv file using PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="f3b53-117">L’applet de commande PowerShell importe le fichier. csv et le canalise en boucle à l’intérieur des accolades qui lit la première ligne du fichier comme en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="f3b53-117">The PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="f3b53-118">L’applet de commande PowerShell parcourt ensuite les enregistrements restants, crée une nouvelle collection de sites pour chaque enregistrement et affecte des propriétés de la collection de sites en fonction des en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="f3b53-118">The PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="f3b53-119">Créer un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="f3b53-119">Create a .csv file</span></span>

1. <span data-ttu-id="f3b53-120">Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f3b53-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="f3b53-121">Où *client* est le nom de votre client, et *propriétaire* le nom d’utilisateur de l’utilisateur sur votre client auquel vous souhaitez accorder le rôle administrateur principal de la collection de sites.</span><span class="sxs-lookup"><span data-stu-id="f3b53-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="f3b53-122">(Vous pouvez appuyer sur Ctrl + H lorsque vous utilisez le bloc-notes pour remplacer les remplacements en bloc plus rapidement.)</span><span class="sxs-lookup"><span data-stu-id="f3b53-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="f3b53-123">Enregistrez le fichier sur votre bureau en tant que **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="f3b53-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="f3b53-124">Avant d’utiliser ce fichier de script. csv ou Windows PowerShell, il est recommandé de s’assurer qu’il n’y a pas de caractères étrangers ou non imprimables.</span><span class="sxs-lookup"><span data-stu-id="f3b53-124">Before you use this or any other .csv or Windows PowerShell script file, it's a good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="f3b53-125">Ouvrez le fichier dans Word et, dans le ruban, cliquez sur l’icône paragraphe pour afficher les caractères non imprimables.</span><span class="sxs-lookup"><span data-stu-id="f3b53-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="f3b53-126">Il ne doit pas y avoir de caractères non imprimables superflus.</span><span class="sxs-lookup"><span data-stu-id="f3b53-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="f3b53-127">Par exemple, il ne doit y avoir aucune marque de paragraphe après la dernière marque à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="f3b53-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="f3b53-128">Exécuter la commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="f3b53-129">À l’invite Windows PowerShell, tapez ou copiez-collez la commande suivante, puis appuyez sur entrée :</span><span class="sxs-lookup"><span data-stu-id="f3b53-129">At the Windows PowerShell prompt, type or copy and paste the following command, and press Enter:</span></span><br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="f3b53-130">Où *MyAlias* est égal à votre alias d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f3b53-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="f3b53-p106">Attendez que l’invite de Windows PowerShell réapparaisse. Cela peut prendre une minute ou deux.</span><span class="sxs-lookup"><span data-stu-id="f3b53-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="f3b53-133">À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="f3b53-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="f3b53-134">Notez les nouvelles collections de sites dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f3b53-134">Note the new site collections in the list.</span></span> <span data-ttu-id="f3b53-135">À l’aide de notre exemple de fichier CSV, vous devriez voir les collections de sites suivantes : **TeamSite01**, **Blog01**, **Projet01**et **Community01**</span><span class="sxs-lookup"><span data-stu-id="f3b53-135">Using our example CSV file, you would see the following site collections: **TeamSite01**, **Blog01**, **Project01**, and **Community01**</span></span>

<span data-ttu-id="f3b53-136">C’est fait.</span><span class="sxs-lookup"><span data-stu-id="f3b53-136">That’s it.</span></span> <span data-ttu-id="f3b53-137">Vous avez créé plusieurs collections de sites à l’aide du fichier. csv que vous avez créé et d’une commande Windows PowerShell unique.</span><span class="sxs-lookup"><span data-stu-id="f3b53-137">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell command.</span></span> <span data-ttu-id="f3b53-138">Vous êtes maintenant prêt à créer et à affecter des utilisateurs à ces sites.</span><span class="sxs-lookup"><span data-stu-id="f3b53-138">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="f3b53-139">Étape 2 : Ajout d’utilisateurs et de groupes</span><span class="sxs-lookup"><span data-stu-id="f3b53-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="f3b53-p109">Vous allez maintenant créer des utilisateurs et les ajouter à un groupe de collections de sites. Vous utiliserez ensuite un fichier .csv pour télécharger en bloc de nouveaux groupes et utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f3b53-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="f3b53-142">Les procédures suivantes continuent à utiliser les exemples de sites TeamSite01, Blog01, Projet01 et Community01.</span><span class="sxs-lookup"><span data-stu-id="f3b53-142">The following procedures continue using the example sites TeamSite01, Blog01, Project01, and Community01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="f3b53-143">Créer des fichiers .csv et .ps1</span><span class="sxs-lookup"><span data-stu-id="f3b53-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="f3b53-144">Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f3b53-144">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="f3b53-145">Où *client* est égal à votre nom de client.</span><span class="sxs-lookup"><span data-stu-id="f3b53-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="f3b53-146">Enregistrez le fichier sur votre bureau en tant que **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="f3b53-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="f3b53-147">Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f3b53-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="f3b53-148">Où *client* est égal à votre nom de client, et *NomUtilisateur* est égal au nom d’utilisateur d’un utilisateur existant.</span><span class="sxs-lookup"><span data-stu-id="f3b53-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="f3b53-149">Enregistrez le fichier sur votre bureau en tant que **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="f3b53-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="f3b53-150">Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f3b53-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="f3b53-151">Où MyAlias est égal au nom d’utilisateur de l’utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="f3b53-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="f3b53-152">Enregistrez le fichier sur votre bureau en tant que **UsersAndGroups.ps1**.</span><span class="sxs-lookup"><span data-stu-id="f3b53-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="f3b53-153">Il s’agit d’un script Windows PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="f3b53-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="f3b53-154">Vous êtes maintenant prêt à exécuter le script UsersAndGroup.ps1 pour ajouter des utilisateurs et des groupes à plusieurs collections de sites.</span><span class="sxs-lookup"><span data-stu-id="f3b53-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="f3b53-155">Exécuter le script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="f3b53-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="f3b53-156">Revenez à SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="f3b53-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="f3b53-157">À l’invite de Windows PowerShell, saisissez ou copiez-collez la ligne suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="f3b53-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="f3b53-158">À l’invite de confirmation, appuyez sur **Y**.</span><span class="sxs-lookup"><span data-stu-id="f3b53-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="f3b53-159">À l’invite de Windows PowerShell, saisissez ou copiez-collez ce qui suit, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="f3b53-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="f3b53-160">Où *MyAlias* est égal à votre nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f3b53-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="f3b53-p111">Attendez le renvoi de l’invite pour continuer. Les groupes s’afficheront d’abord tels qu’ils ont été créés. Ensuite, vous verrez la liste de groupes se répéter au fur et à mesure de l’ajout des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f3b53-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3b53-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3b53-164">See also</span></span>

[<span data-ttu-id="f3b53-165">Connexion à SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="f3b53-166">Gestion des groupes de sites SharePoint Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-166">Manage SharePoint Online site groups with PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="f3b53-167">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b53-167">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f3b53-168">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f3b53-168">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

