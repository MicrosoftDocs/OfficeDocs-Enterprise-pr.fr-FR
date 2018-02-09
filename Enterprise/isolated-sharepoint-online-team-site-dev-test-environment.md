---
title: "Environnement de développement/test isolé de SharePoint Online équipe site"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "Résumé : Configuration d’un site d’équipe SharePoint en ligne qui est isolé du reste de l’organisation dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: 997c5cf236a795f4846718cc8864997799a1d966
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="aaa62-103">Environnement de développement/test isolé de SharePoint Online équipe site</span><span class="sxs-lookup"><span data-stu-id="aaa62-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="aaa62-104">**Résumé :** Configurer un site d’équipe SharePoint en ligne qui est isolé du reste de l’organisation dans votre environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="aaa62-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="aaa62-p101">Les sites d’équipe SharePoint Online dans Office 365 sont des emplacements pour la collaboration à l’aide d’une bibliothèque de documents commune, un bloc-notes OneNote et d’autres services. Dans de nombreux cas, vous souhaitez accès étendu et la collaboration entre les départements ou organisations. Toutefois, dans certains cas, vous souhaitez contrôler étroitement l’accès et les autorisations pour la collaboration entre un petit groupe de personnes.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="aaa62-p102">Accès à des sites d’équipe SharePoint Online et à ce que peuvent faire les utilisateurs est contrôlé par les niveaux d’autorisation et des groupes SharePoint. Par défaut, les sites SharePoint Online ont trois niveaux d’accès :</span><span class="sxs-lookup"><span data-stu-id="aaa62-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="aaa62-110">**Membres**, qui peut afficher, créer et modifier des ressources sur le site.</span><span class="sxs-lookup"><span data-stu-id="aaa62-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="aaa62-111">**Propriétaires**, qui ont un contrôle total du site, y compris la possibilité de modifier les autorisations.</span><span class="sxs-lookup"><span data-stu-id="aaa62-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="aaa62-112">**Les visiteurs**, qui peut uniquement afficher des ressources sur le site.</span><span class="sxs-lookup"><span data-stu-id="aaa62-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="aaa62-p103">Les étapes de cet article vous guide dans la configuration d’un site d’équipe SharePoint Online isolé pour un projet de recherche secret nommé ProjectX. Les conditions d’accès sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="aaa62-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="aaa62-115">Seuls les membres du projet peuvent accéder au site et à son contenu (documents, bloc-notes OneNote, pages), avec des niveaux d’autorisation SharePoint pour éditer et afficher contrôlés via l’appartenance au groupe.</span><span class="sxs-lookup"><span data-stu-id="aaa62-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="aaa62-116">Seuls le créateur du site et les membres d’un groupe d’administrateurs du site peuvent effectuer l’administration du site, y compris la modification des autorisations au niveau du site.</span><span class="sxs-lookup"><span data-stu-id="aaa62-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="aaa62-117">Il existe trois phases de configuration d’un site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365 :</span><span class="sxs-lookup"><span data-stu-id="aaa62-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="aaa62-118">Créez l’environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="aaa62-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="aaa62-119">Créez les utilisateurs et groupes pour ProjectX.</span><span class="sxs-lookup"><span data-stu-id="aaa62-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="aaa62-120">Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler.</span><span class="sxs-lookup"><span data-stu-id="aaa62-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="aaa62-121">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="aaa62-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="aaa62-122">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="aaa62-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="aaa62-123">Si vous voulez simplement créer un site d’équipe SharePoint Online isolé de manière légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="aaa62-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="aaa62-124">Si vous souhaitez créer un site d’équipe SharePoint Online isolé dans une configuration d’entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="aaa62-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="aaa62-p104">La création d’un site SharePoint Online isolé ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server AD. Il est proposé comme option dans cet article afin que vous puissiez tester un site SharePoint Online isolé et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="aaa62-127">Phase 2 : Créer des comptes d’utilisateurs et de groupes d’accès</span><span class="sxs-lookup"><span data-stu-id="aaa62-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="aaa62-128">Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour se connecter à votre abonnement à Office 365 piste avec votre compte d’administrateur global à partir de :</span><span class="sxs-lookup"><span data-stu-id="aaa62-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="aaa62-129">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="aaa62-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="aaa62-130">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="aaa62-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="aaa62-131">Pour créer de nouveaux groupes d’accès pour le site d’équipe ProjectX SharePoint Online, exécuter ces commandes à partir de l’invite de Windows Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aaa62-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> <span data-ttu-id="aaa62-132">Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) pour un fichier texte qui contient toutes les commandes de PowerShell dans cet article.</span><span class="sxs-lookup"><span data-stu-id="aaa62-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="aaa62-133">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aaa62-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="aaa62-134">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de conduire le concepteur et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="aaa62-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="aaa62-135">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aaa62-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="aaa62-136">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de conduire l’Organise-notes et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="aaa62-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="aaa62-137">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aaa62-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="aaa62-138">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de vice-président du développement et de l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="aaa62-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="aaa62-139">Ensuite, pour ajouter de nouveaux comptes pour les nouveaux groupes d’accès, exécutez ces commandes PowerShell à partir de l’invite de Windows Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aaa62-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

<span data-ttu-id="aaa62-140">Résultats :</span><span class="sxs-lookup"><span data-stu-id="aaa62-140">Results:</span></span>
  
- <span data-ttu-id="aaa62-141">Le groupe d’accès membres ProjectX contenant les comptes Concepteur de conduire et mener l’Organise-notes</span><span class="sxs-lookup"><span data-stu-id="aaa62-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="aaa62-142">Le groupe d’accès Admins-ProjectX contient le compte d’administrateur global pour votre version d’essai</span><span class="sxs-lookup"><span data-stu-id="aaa62-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="aaa62-143">Le groupe d’accès-visionneuses ProjectX contient le compte d’utilisateur vice-président du développement</span><span class="sxs-lookup"><span data-stu-id="aaa62-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="aaa62-144">La figure 1 illustre l’accès aux groupes et leur appartenance.</span><span class="sxs-lookup"><span data-stu-id="aaa62-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="aaa62-145">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="aaa62-145">**Figure 1**</span></span>

![Groupes Office 365 et leur appartenance pour un site de groupe SharePoint Online isolé](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="aaa62-147">Phase 3 : Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler</span><span class="sxs-lookup"><span data-stu-id="aaa62-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="aaa62-148">Pour créer un site d’équipe SharePoint Online pour ProjectX, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aaa62-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="aaa62-149">En utilisant un navigateur soit sur votre ordinateur local (configuration léger) ou sur CLIENT1 (configuration entreprise simulation), connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="aaa62-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="aaa62-150">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="aaa62-151">Dans l’onglet Nouveau SharePoint dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="aaa62-p105">Dans la zone **nom du site d’équipe**, tapez **ProjectX**. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="aaa62-154">Dans la **description de site d’équipe**, tapez le **site SharePoint pour ProjectX**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="aaa62-155">À **qui voulez-vous ajouter**? volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="aaa62-156">Sur le nouvel onglet **Accueil-ProjectX** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="aaa62-157">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="aaa62-158">Dans la nouvelle **autorisations : projet X** dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="aaa62-159">Dans la boîte de dialogue **Paramètres de demandes d’accès** , désactivez **Autoriser les demandes d’accès** et de **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="aaa62-160">Dans la liste, cliquez sur **Les membres de ProjectX** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="aaa62-161">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="aaa62-162">Dans la boîte de dialogue **partage** , **ProjectX-membres**de type, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="aaa62-163">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="aaa62-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="aaa62-164">Dans la liste, cliquez sur **ProjectX propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="aaa62-165">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="aaa62-166">Dans la boîte de dialogue de **partage** , tapez **Admins-ProjectX**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="aaa62-167">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="aaa62-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="aaa62-168">Dans la liste, cliquez sur **Les visiteurs de ProjectX** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="aaa62-169">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="aaa62-170">Dans la boîte de dialogue **partage** , **ProjectX-visionneuses**de type, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="aaa62-171">Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **Accueil-ProjectX** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="aaa62-172">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="aaa62-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="aaa62-173">Le groupe SharePoint des membres ProjectX contient uniquement le groupe d’accès membres ProjectX (qui contienne uniquement les comptes d’utilisateurs Concepteur de conduire et mener l’Organise-notes) et le groupe ProjectX (qui contient uniquement le compte d’utilisateur administrateur global).</span><span class="sxs-lookup"><span data-stu-id="aaa62-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="aaa62-174">Le groupe SharePoint propriétaires de ProjectX contient uniquement le groupe d’accès Admins-ProjectX (qui contient uniquement le compte d’utilisateur administrateur global).</span><span class="sxs-lookup"><span data-stu-id="aaa62-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="aaa62-175">Le groupe SharePoint visiteurs de ProjectX contient uniquement le groupe d’accès ProjectX-afficheurs (qui contient uniquement le compte d’utilisateur vice-président du développement).</span><span class="sxs-lookup"><span data-stu-id="aaa62-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="aaa62-176">Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe ProjectX-Administrateurs).</span><span class="sxs-lookup"><span data-stu-id="aaa62-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="aaa62-177">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, ni demander l’accès au site.</span><span class="sxs-lookup"><span data-stu-id="aaa62-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="aaa62-178">La figure 2 présente les groupes SharePoint et leur appartenance.</span><span class="sxs-lookup"><span data-stu-id="aaa62-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="aaa62-179">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="aaa62-179">**Figure 2**</span></span>

![Groupes SharePoint Online et leur appartenance pour un site de groupe SharePoint Online isolé](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="aaa62-181">Maintenant illustrons access en utilisant le compte d’utilisateur de conduire le concepteur :</span><span class="sxs-lookup"><span data-stu-id="aaa62-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="aaa62-182">Fermer l’onglet **Accueil-ProjectX** dans votre navigateur, puis cliquez sur l’onglet **d’Accueil de Microsoft Office** dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="aaa62-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="aaa62-183">Cliquez sur le nom de l’administrateur général, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="aaa62-184">Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom de compte de conduire le concepteur et son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="aaa62-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="aaa62-185">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="aaa62-p106">Sur le nouvel onglet **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone de recherche, activez la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour que le site d’équipe ProjectX.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="aaa62-p107">Cliquez sur l’icône Paramètres. Notez qu’il n’existe aucune option pour les **Autorisations du Site**. Cela est correct, car seuls les membres du groupe Administrateurs de le ProjectX peuvent modifier les autorisations sur le site</span><span class="sxs-lookup"><span data-stu-id="aaa62-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="aaa62-191">Ouvrez le bloc-notes ou un éditeur de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="aaa62-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="aaa62-192">Copiez l’URL du site d’équipe ProjectX et le coller dans une nouvelle ligne dans le bloc-notes ou votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="aaa62-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="aaa62-193">Sur le nouvel onglet **Accueil-ProjectX** dans votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="aaa62-194">Copiez l’URL du dossier de documents ProjectX et collez-la dans une nouvelle ligne dans le bloc-notes ou dans votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="aaa62-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="aaa62-195">Dans le nouvel onglet de **ProjectX-Documents** dans votre navigateur, cliquez sur **Nouveau > document Word**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="aaa62-p108">Tapez du texte dans la page **En ligne de Word** , attendez que l’état indiquer **l’enregistrement**et cliquez sur le bouton précédente de votre navigateur, puis actualisez la page. Vous devriez voir un nouveau **Document.docx** dans le dossier **Documents** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="aaa62-198">Cliquez sur le bouton de sélection pour le document **Document.docx** , puis cliquez sur **obtenir un lien**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="aaa62-199">Copiez l’URL dans la boîte de dialogue **partage 'Document.docx'** et collez-le sur une nouvelle ligne dans le bloc-notes ou votre éditeur de texte et puis fermez la boîte de dialogue **partage 'Document.docx'** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="aaa62-200">Fermer les onglets de **Documents ProjectX** et **SharePoint** dans votre navigateur, puis cliquez sur l’onglet **d’Accueil de Microsoft Office** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="aaa62-201">Cliquez sur le nom du **Concepteur de prospect** , puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="aaa62-202">Maintenant nous allons démontrer access en utilisant le compte d’utilisateur vice-président du développement :</span><span class="sxs-lookup"><span data-stu-id="aaa62-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="aaa62-203">Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom de compte de vice-président du développement et de son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="aaa62-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="aaa62-204">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="aaa62-p109">Sur le nouvel onglet **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone de recherche, activez la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour que le site d’équipe ProjectX.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="aaa62-207">Cliquez sur **Documents**, puis cliquez sur le fichier **Document.docx** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="aaa62-p110">Dans l’onglet **Document.docx** dans votre navigateur, essayez de modifier le texte. Vous devriez voir un message indiquant que **ce document est en lecture seule.** Ceci est dû au fait que le compte d’utilisateur vice-président du développement dispose uniquement d’autorisations d’affichage pour le site.</span><span class="sxs-lookup"><span data-stu-id="aaa62-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="aaa62-211">Fermer les onglets **Document.docx**et **ProjectX-Documents** **SharePoint** dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="aaa62-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="aaa62-212">Cliquez sur l’onglet **d’Accueil de Microsoft Office** , cliquez sur le nom du **Directeur de développement** , puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="aaa62-213">Maintenant nous allons démontrer l’accès avec un compte d’utilisateur qui n’est pas autorisé :</span><span class="sxs-lookup"><span data-stu-id="aaa62-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="aaa62-214">Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom du compte utilisateur 3 et son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="aaa62-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="aaa62-215">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="aaa62-p111">Dans l’onglet nouveau **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone Rechercher et puis activer la recherche. Vous devriez voir le message **rien ici correspond à votre recherche.**</span><span class="sxs-lookup"><span data-stu-id="aaa62-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="aaa62-p112">À partir de l’instance ouverte de bloc-notes ou votre éditeur de texte, copiez l’URL du site de ProjectX dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="aaa62-p113">Dans le bloc-notes ou votre éditeur de texte, copiez l’URL du dossier Documents de ProjectX dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="aaa62-p114">Dans le bloc-notes ou votre éditeur de texte, copiez l’URL pour le fichier Documents.docx dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .</span><span class="sxs-lookup"><span data-stu-id="aaa62-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="aaa62-224">Fermer l’onglet **SharePoint** dans votre navigateur, cliquez sur l’onglet **d’Accueil de Microsoft Office** , cliquez sur le nom de **l’utilisateur 3** , puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="aaa62-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="aaa62-225">Votre site SharePoint Online isolé est prêt pour une expérimentation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="aaa62-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="aaa62-226">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="aaa62-226">Next Step</span></span>

<span data-ttu-id="aaa62-227">Lorsque vous souhaitez déployer un site d'équipe SharePoint Online isolé en production, lisez la procédure détaillée dans la rubrique [Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="aaa62-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aaa62-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaa62-228">See Also</span></span>

[<span data-ttu-id="aaa62-229">Sites d'équipe SharePoint Online isolés</span><span class="sxs-lookup"><span data-stu-id="aaa62-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="aaa62-230">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="aaa62-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="aaa62-231">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="aaa62-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="aaa62-232">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="aaa62-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="aaa62-233">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="aaa62-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




