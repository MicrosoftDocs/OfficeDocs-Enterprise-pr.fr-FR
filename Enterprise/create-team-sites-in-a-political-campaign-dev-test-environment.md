---
title: Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Résumé : Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans votre environnement de développement/test dans le cadre d’une campagne électorale.'
ms.openlocfilehash: 146632ede567be4bf412304960605e6d87de7657
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="023c3-103">Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale</span><span class="sxs-lookup"><span data-stu-id="023c3-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="023c3-104">**Résumé :** Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans votre environnement de développement/test dans le cadre d’une campagne électorale.</span><span class="sxs-lookup"><span data-stu-id="023c3-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="023c3-p101">Utilisez les instructions fournies dans cet article pour créer un environnement de développement/test qui inclut les quatre différents types de sites d’équipe SharePoint Online pour la solution des [conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et autres organisations souples](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md). Ces sites sont décrits en détail dans la Rubrique 10 intitulée **SharePoint et OneDrive Entreprise**.</span><span class="sxs-lookup"><span data-stu-id="023c3-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="023c3-107">Phase 1 : Création d’un environnement de développement/test dans le cadre d’une campagne électorale</span><span class="sxs-lookup"><span data-stu-id="023c3-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="023c3-108">Tout d’abord, suivez les instructions de [Configurer de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne électorale](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) pour créer vos abonnements, utilisateurs et groupes.</span><span class="sxs-lookup"><span data-stu-id="023c3-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="023c3-109">Phase 2 : Création d’étiquettes Office 365</span><span class="sxs-lookup"><span data-stu-id="023c3-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="023c3-110">Dans cette phase, vous allez créer les étiquettes correspondant aux différents niveaux de sécurité pour les dossiers de document du site d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="023c3-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="023c3-p102">Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur général de votre abonnement d’essai. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="023c3-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="023c3-113">Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="023c3-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="023c3-114">Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration > Sécurité &amp; conformité**.</span><span class="sxs-lookup"><span data-stu-id="023c3-114">From the new Office Admin center tab of your browser, click Admin centers > Security & Compliance.</span></span>
    
4. <span data-ttu-id="023c3-115">Sous le nouvel onglet **Accueil - Sécurité &amp; conformité** de votre navigateur, cliquez sur **Classifications > Étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="023c3-115">From the new Home – Security & Compliance tab of your browser, click Classifications > Labels.</span></span>
    
5. <span data-ttu-id="023c3-116">Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.</span><span class="sxs-lookup"><span data-stu-id="023c3-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="023c3-117">Dans le volet **Nom de l’étiquette**, saisissez **Interne** et cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="023c3-118">Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-119">Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer cette étiquette**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="023c3-120">Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :</span><span class="sxs-lookup"><span data-stu-id="023c3-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="023c3-121">Privé</span><span class="sxs-lookup"><span data-stu-id="023c3-121">Private</span></span>
    
  - <span data-ttu-id="023c3-122">Sensible</span><span class="sxs-lookup"><span data-stu-id="023c3-122">Sensitive</span></span>
    
  - <span data-ttu-id="023c3-123">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="023c3-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="023c3-124">Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="023c3-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="023c3-125">Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.</span><span class="sxs-lookup"><span data-stu-id="023c3-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="023c3-126">Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.</span><span class="sxs-lookup"><span data-stu-id="023c3-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="023c3-127">Cliquez sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="023c3-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="023c3-128">Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="023c3-129">Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="023c3-130">Dans le volet **Nom de votre stratégie**, saisissez **Campagne** dans **Nom**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="023c3-131">Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="023c3-132">Phase 3 : Créer vos sites d’équipe SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="023c3-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="023c3-133">Lors de cette phase, vous allez créer et configurer des sites d’équipe SharePoint Online pour votre campagne électorale correspondant aux quatre types de sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="023c3-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="023c3-134">Site d’équipe de la campagne</span><span class="sxs-lookup"><span data-stu-id="023c3-134">Campaign wide team site</span></span>

<span data-ttu-id="023c3-135">Pour créer une base de référence de site d’équipe SharePoint Online public, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="023c3-136">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="023c3-136">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see Where to sign in to Office 365.</span></span>
    
2. <span data-ttu-id="023c3-137">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="023c3-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="023c3-138">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="023c3-139">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="023c3-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="023c3-140">Dans **Nom du site**, saisissez **Campagne**.</span><span class="sxs-lookup"><span data-stu-id="023c3-140">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="023c3-141">Dans **Description du site d’équipe**, saisissez **Site SharePoint pour l’ensemble de la campagne**.</span><span class="sxs-lookup"><span data-stu-id="023c3-141">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="023c3-142">Dans **Paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-142">In **Privacy settings**, select **Public – anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-143">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="023c3-144">Ensuite, configurez le dossier de documents du site d’équipe de la campagne pour l’étiquette Interne.</span><span class="sxs-lookup"><span data-stu-id="023c3-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="023c3-145">Dans l’onglet **Campagne - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="023c3-145">In the **Campaign wide–Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="023c3-146">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="023c3-147">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="023c3-148">Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Interne**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="023c3-149">Site d’équipe 1 du projet Campagne</span><span class="sxs-lookup"><span data-stu-id="023c3-149">Campaign project 1 team site</span></span>

<span data-ttu-id="023c3-150">Pour créer un site d’équipe SharePoint Online privé de référence pour un projet dans la campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="023c3-151">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="023c3-151">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="023c3-152">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="023c3-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="023c3-153">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="023c3-154">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="023c3-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="023c3-155">Dans **Nom du site**, saisissez **Projet de campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="023c3-155">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="023c3-156">Dans **Description du site d’équipe**, saisissez **Site SharePoint pour le projet de campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="023c3-156">In **Team site description**, type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="023c3-157">Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-157">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-158">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="023c3-159">Ensuite, configurez le dossier de documents du site d’équipe Projet Campagne 1 pour l’étiquette Privé.</span><span class="sxs-lookup"><span data-stu-id="023c3-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="023c3-160">Dans l’onglet **Projet Campagne 1 - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="023c3-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="023c3-161">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="023c3-162">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="023c3-163">Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Privé**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="023c3-164">Site d’équipe marketing de campagne</span><span class="sxs-lookup"><span data-stu-id="023c3-164">Campaign marketing team site</span></span>

<span data-ttu-id="023c3-165">Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources marketing de la campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="023c3-166">En utilisant un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="023c3-166">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="023c3-167">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="023c3-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="023c3-168">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="023c3-169">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="023c3-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="023c3-170">Dans **Nom du site d’équipe**, saisissez **Ressources marketing de la campagne**.</span><span class="sxs-lookup"><span data-stu-id="023c3-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="023c3-171">Dans **Description du site d’équipe**, saisissez **Site SharePoint pour les ressources marketing de la campagne (données sensibles)**.</span><span class="sxs-lookup"><span data-stu-id="023c3-171">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="023c3-172">Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-172">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-173">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="023c3-174">Dans le nouvel onglet **Marketing campagne** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="023c3-175">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="023c3-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="023c3-176">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="023c3-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="023c3-177">Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site, ainsi que des fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site**, saisissez **ITAdmin1@**<your organization name> **.onmicrosoft.com** dans le champ **Envoyer toutes les demandes d’accès à**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-177">In the Access Request Settings dialog box, clear the Allow members to share the site and individual files and folders and Allow members to invite others to the site members group check boxes, type ITAdmin1@<your organization name>.onmicrosoft.com in Send all requests for access, and then click OK.</span></span>
    
13. <span data-ttu-id="023c3-178">Cliquez sur les **membres de l’équipe marketing de la campagne** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="023c3-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="023c3-179">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="023c3-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="023c3-180">Dans la boîte de dialogue **Partager**, saisissez **Personnel senior et stratégique**, sélectionnez-le, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="023c3-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="023c3-181">Répétez les étapes 14 et 15 pour le groupe **Analytics staff** et le compte d’utilisateur **Standard1**.</span><span class="sxs-lookup"><span data-stu-id="023c3-181">Repeat steps 12 and 13 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="023c3-182">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="023c3-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="023c3-183">Cliquez sur **Marketing campagne - Propriétaires** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="023c3-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="023c3-184">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="023c3-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="023c3-185">Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="023c3-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="023c3-186">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="023c3-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="023c3-187">Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Marketing campagne - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="023c3-188">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="023c3-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="023c3-189">Le groupe SharePoint **Marketing campagne - Membres** contient uniquement le groupe **Senior and strategic staff** (qui contient les comptes d’utilisateurs Candidate, ChiefOfStaff et Strategic1), le groupe **Marketing campagne ** (qui contient le compte d’administrateur général), le groupe **Analytics staff** (qui contient le compte d’utilisateur DataScientist1) et le compte d’utilisateur **Regular1**.</span><span class="sxs-lookup"><span data-stu-id="023c3-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="023c3-190">Le groupe SharePoint **Marketing campagne - Propriétaires** contient uniquement le groupe **Équipe informatique** (qui contient uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="023c3-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="023c3-191">Le groupe SharePoint **Marketing campagne - Visiteurs** ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="023c3-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="023c3-192">Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe **Marketing campagne - Propriétaires**).</span><span class="sxs-lookup"><span data-stu-id="023c3-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="023c3-193">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="023c3-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="023c3-194">Ensuite, configurez le dossier de documents du site d’équipe Marketing campagne pour l’étiquette Sensible.</span><span class="sxs-lookup"><span data-stu-id="023c3-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="023c3-195">Dans l’onglet **Marketing campagne - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="023c3-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="023c3-196">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="023c3-197">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="023c3-198">Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Sensible**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="023c3-p103">Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette Sensible à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources du site Marketing campagne.</span><span class="sxs-lookup"><span data-stu-id="023c3-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="023c3-201">Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.</span><span class="sxs-lookup"><span data-stu-id="023c3-201">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="023c3-202">Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-202">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="023c3-203">Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="023c3-204">Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="023c3-205">Dans le volet **Nom de votre stratégie**, saisissez les **sites d’équipe SharePoint Online avec étiquette Sensible** sous **Nom**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="023c3-206">Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="023c3-207">Dans la liste des emplacements, désactivez les emplacements **Messagerie Exchange** et **Comptes OneDrive**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-208">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="023c3-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="023c3-209">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **Étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="023c3-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="023c3-210">Dans le volet **Étiquettes**, cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Sensible**, cliquez sur **Ajouter**, puis sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="023c3-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="023c3-211">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="023c3-212">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="023c3-213">Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="023c3-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="023c3-214">Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="023c3-215">Dans la zone de texte, tapez ou collez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="023c3-p104">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="023c3-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="023c3-219">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="023c3-220">Dans le volet **Que faire en cas de détection d’informations sensibles ?**, désélectionnez la case **Empêcher les utilisateurs de partager un fichier et restreindre l’accès au contenu partagé**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="023c3-221">Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="023c3-222">Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-222">In the **Review your settings** pane, click **Create,** and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="023c3-223">Site d’équipe Stratégie de campagne</span><span class="sxs-lookup"><span data-stu-id="023c3-223">Campaign strategy team site</span></span>

<span data-ttu-id="023c3-224">Pour créer un site d’équipe SharePoint Online isolé hautement confidentiel pour les ressources de stratégie de campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="023c3-225">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="023c3-225">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="023c3-226">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="023c3-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="023c3-227">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="023c3-228">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="023c3-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="023c3-229">Dans **Nom du site d’équipe**, saisissez **Stratégie de campagne**.</span><span class="sxs-lookup"><span data-stu-id="023c3-229">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="023c3-230">Dans **Description du site d’équipe** saisissez **Site SharePoint pour la stratégie de campagne (hautement confidentiel)**.</span><span class="sxs-lookup"><span data-stu-id="023c3-230">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="023c3-231">Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-231">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-232">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="023c3-233">Dans le nouvel onglet **Stratégie de campagne** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="023c3-234">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="023c3-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="023c3-235">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="023c3-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="023c3-236">Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site** (afin que les trois cases à cocher soient désactivées), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="023c3-237">Cliquez sur les **membres de l’équipe Stratégie de campagne** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="023c3-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="023c3-238">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="023c3-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="023c3-239">Dans la boîte de dialogue **Partager**, saisissez **Personnel senior et stratégique**, sélectionnez-le, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="023c3-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="023c3-240">Cliquez sur les **propriétaires de la stratégie de campagne** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="023c3-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="023c3-241">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="023c3-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="023c3-242">Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="023c3-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="023c3-243">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="023c3-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="023c3-244">Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Stratégie de campagne - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.</span><span class="sxs-lookup"><span data-stu-id="023c3-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="023c3-245">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="023c3-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="023c3-246">Le groupe SharePoint **Stratégie de campagne - Membres** contient uniquement le groupe **Senior and strategic staff** (qui contient uniquement les comptes d’utilisateurs Candidate, ChiefOfStaff et Strategic1) et le groupe **Stratégie de campagne** (qui contient uniquement le compte d’administrateur général).
</span><span class="sxs-lookup"><span data-stu-id="023c3-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="023c3-247">Le groupe SharePoint **Stratégie de campagne - Propriétaires** contient uniquement le groupe **Équipe informatique** (qui contient uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="023c3-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="023c3-248">Le groupe SharePoint **Stratégie de campagne - Visiteurs** ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="023c3-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="023c3-249">Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe **Stratégie de campagne - Propriétaires**).</span><span class="sxs-lookup"><span data-stu-id="023c3-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="023c3-p105">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, ni demander l’accès au site. Les autorisations supplémentaires doivent être accordées par l’administrateur général ou par un membre du groupe **Stratégie de campagne - Propriétaires**.</span><span class="sxs-lookup"><span data-stu-id="023c3-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="023c3-252">Ensuite, configurez le dossier de documents du site d’équipe Stratégie de campagne pour l’étiquette Hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="023c3-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="023c3-253">Dans l’onglet **Stratégie de campagne - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="023c3-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="023c3-254">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="023c3-255">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="023c3-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="023c3-256">Dans **Paramètres - Appliquer une étiquette**, sélectionnez **Hautement confidentiel**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="023c3-p106">Ensuite, configurez une stratégie DLP qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Hautement confidentiel. Cette stratégie DLP s’applique aux ressources du site Stratégie de campagne.</span><span class="sxs-lookup"><span data-stu-id="023c3-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="023c3-259">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec un compte disposant du rôle Administrateur de sécurité ou Administrateur de la société.</span><span class="sxs-lookup"><span data-stu-id="023c3-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ( https://portal.office.com https://portal.office.com ) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="023c3-260">Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.</span><span class="sxs-lookup"><span data-stu-id="023c3-260">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
3. <span data-ttu-id="023c3-261">Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-261">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
4. <span data-ttu-id="023c3-262">Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="023c3-263">Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="023c3-264">Dans le volet **Nom de votre stratégie**, saisissez les **sites d’équipe SharePoint Online avec étiquette Hautement confidentiel** sous **Nom**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="023c3-265">Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="023c3-266">Dans la liste des emplacements, désactivez les emplacements **Messagerie Exchange** et **Comptes OneDrive**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="023c3-267">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="023c3-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="023c3-268">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **Étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="023c3-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="023c3-269">Dans le volet **Étiquettes**, cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentiel**, cliquez sur **Ajouter**, puis sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="023c3-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="023c3-270">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="023c3-271">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="023c3-272">Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="023c3-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="023c3-273">Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="023c3-274">Dans la zone de texte, tapez ou collez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="023c3-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="023c3-p107">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="023c3-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="023c3-278">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="023c3-279">Dans le volet **Que faire en cas de détection d’informations sensibles ?**, sélectionnez **Exiger une justification professionnelle pour le remplacement**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="023c3-280">Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="023c3-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="023c3-281">Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="023c3-282">Suivez les instructions contenues dans [Comment activer Azure Rights Management à partir du centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="023c3-282">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="023c3-283">Ensuite, configurez Azure Information Protection avec une nouvelle stratégie délimitée et une sous-étiquette pour la protection et les autorisations en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="023c3-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="023c3-p108">Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="023c3-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="023c3-286">Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="023c3-286">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="023c3-287">Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="023c3-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="023c3-288">Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="023c3-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="023c3-289">Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="023c3-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="023c3-290">Tapez **CampaignStrategy** dans **Nom de la stratégie** et **Étiquette pour les documents dans le site d’équipe Stratégie de campagne** dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="023c3-290">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="023c3-291">Cliquez sur **Sélectionner les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateurs/Groupes**, puis sélectionnez **Personnel senior et stratégique**.</span><span class="sxs-lookup"><span data-stu-id="023c3-291">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="023c3-292">Cliquez sur **Sélectionner > OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="023c3-293">Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.</span><span class="sxs-lookup"><span data-stu-id="023c3-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="023c3-294">Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="023c3-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="023c3-295">Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.</span><span class="sxs-lookup"><span data-stu-id="023c3-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="023c3-296">Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.</span><span class="sxs-lookup"><span data-stu-id="023c3-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="023c3-297">Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.</span><span class="sxs-lookup"><span data-stu-id="023c3-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="023c3-298">Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.</span><span class="sxs-lookup"><span data-stu-id="023c3-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="023c3-299">Dans le volet **Utilisateurs et groupes AAD**, sélectionnez **Personnel senior et stratégique**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="023c3-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="023c3-300">Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="023c3-301">Cliquez deux fois sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="023c3-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="023c3-302">Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="023c3-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="023c3-303">Fermez le panneau de la nouvelle stratégie étendue.</span><span class="sxs-lookup"><span data-stu-id="023c3-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="023c3-304">Dans le panneau **Azure Information Protection – Stratégies délimitées**, cliquez sur **Publier** et sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="023c3-304">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="023c3-305">Vous êtes désormais prêt à créer des documents dans ces quatre sites et à tester l’accès à ces sites avec divers comptes d’utilisateurs disponibles avec votre abonnement à la version d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="023c3-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="023c3-306">Pour protéger un document avec Azure Information Protection et cette nouvelle étiquette, vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur une machine de test, installer Office à partir du portail Office 365, puis vous connecter à partir de Microsoft Word avec un compte du groupe **Personnel senior et stratégique** de votre abonnement d’essai.</span><span class="sxs-lookup"><span data-stu-id="023c3-306">To protect a document with Azure Information Protection and the Highly Confidential label, you must install the Azure Information Protection client on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the C-Suite group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="023c3-307">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="023c3-307">See Also</span></span>

[<span data-ttu-id="023c3-308">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="023c3-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="023c3-309">Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne électorale</span><span class="sxs-lookup"><span data-stu-id="023c3-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="023c3-310">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="023c3-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="023c3-311">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="023c3-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




