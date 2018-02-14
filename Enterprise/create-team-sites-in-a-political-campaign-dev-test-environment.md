---
title: "Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale"
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
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Résumé : Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans votre environnement de développement/test de campagne politique."
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="5fd3e-103">Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale</span><span class="sxs-lookup"><span data-stu-id="5fd3e-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="5fd3e-104">**Résumé :** Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans votre environnement de développement/test de campagne politique.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="5fd3e-p101">Suivez les instructions de cet article pour créer un environnement de développement/test qui inclut les quatre types différents de sites d’équipe SharePoint Online pour connaître les [Conseils Microsoft sur la sécurité pour les campagnes politiques, les organismes sans but lucratif et les autres organisations Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. Ces sites sont décrites en détail dans la rubrique 10, intitulé **SharePoint et OneDrive pour les entreprises**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="5fd3e-107">Phase 1 : Création d’un environnement de développement/test dans le cadre d’une campagne électorale</span><span class="sxs-lookup"><span data-stu-id="5fd3e-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="5fd3e-108">Tout d’abord, suivez les instructions de [configurer les groupes et les utilisateurs d’un environnement de développement/test de campagne politique](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) pour créer des abonnements, des utilisateurs et des groupes.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="5fd3e-109">Phase 2 : Création d’étiquettes Office 365</span><span class="sxs-lookup"><span data-stu-id="5fd3e-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="5fd3e-110">Dans cette phase, vous créez les étiquettes pour les différents niveaux de sécurité pour les dossiers du document site d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="5fd3e-p102">Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="5fd3e-113">À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="5fd3e-114">Dans l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **Centre d’administration > sécurité &amp; la conformité**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="5fd3e-115">À partir du nouveau **maison - sécurité &amp; la conformité** onglet de votre navigateur, cliquez sur **les Classifications > étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="5fd3e-116">À partir de le **Accueil > étiquettes** volet, cliquez sur **créer une étiquette**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="5fd3e-117">Dans le volet **nom de votre étiquette** , type **interne**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5fd3e-118">Dans le volet **paramètres d’étiquette** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-119">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="5fd3e-120">Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="5fd3e-121">Privé</span><span class="sxs-lookup"><span data-stu-id="5fd3e-121">Private</span></span>
    
  - <span data-ttu-id="5fd3e-122">Sensible</span><span class="sxs-lookup"><span data-stu-id="5fd3e-122">Sensitive</span></span>
    
  - <span data-ttu-id="5fd3e-123">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="5fd3e-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="5fd3e-124">À partir de le **Accueil > étiquettes** volet, cliquez sur **publier les étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="5fd3e-125">Dans le volet **Choisir les étiquettes à publier** , cliquez sur **Choisir les étiquettes à publier**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="5fd3e-126">Dans le volet **Choisir étiquettes** , cliquez sur **Ajouter** et sélectionner toutes les étiquettes de quatre.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="5fd3e-127">Cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="5fd3e-128">Dans le volet **Choisir les étiquettes à publier** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="5fd3e-129">Dans le volet **Choisir des emplacements** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="5fd3e-130">Dans le volet **nom de votre stratégie** , type de **campagne** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="5fd3e-131">Dans le volet de **passer en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="5fd3e-132">Phase 3 : Créer vos sites d’équipe SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5fd3e-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="5fd3e-133">Lors de cette phase, vous allez créer et configurer des sites d’équipe SharePoint Online pour votre campagne électorale correspondant aux quatre types de sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="5fd3e-134">Site d’équipe de la campagne</span><span class="sxs-lookup"><span data-stu-id="5fd3e-134">Campaign wide team site</span></span>

<span data-ttu-id="5fd3e-135">Pour créer un site d’équipe SharePoint Online public de référence, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="5fd3e-136">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="5fd3e-137">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="5fd3e-138">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="5fd3e-139">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="5fd3e-140">Dans la zone **nom du Site**, tapez **campagne large**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="5fd3e-141">Dans la **description de site d’équipe**, tapez le **site SharePoint pour toute la campagne**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="5fd3e-142">Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-143">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="5fd3e-144">Ensuite, configurez le dossier de documents du site d’équipe de la campagne pour l’étiquette Interne.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="5fd3e-145">Dans l’onglet **campagne wide-accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="5fd3e-146">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="5fd3e-147">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="5fd3e-148">Dans **Les paramètres à appliquer une étiquette**, sélectionnez **interne**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="5fd3e-149">Site d’équipe 1 du projet Campagne</span><span class="sxs-lookup"><span data-stu-id="5fd3e-149">Campaign project 1 team site</span></span>

<span data-ttu-id="5fd3e-150">Pour créer un site d’équipe SharePoint Online privé de référence pour un projet dans la campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="5fd3e-151">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="5fd3e-152">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="5fd3e-153">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="5fd3e-154">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="5fd3e-155">Dans la zone **nom du Site**, tapez **projet de campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="5fd3e-156">Dans la **description de site d’équipe,** tapez le **site SharePoint pour le projet de campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="5fd3e-157">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-158">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="5fd3e-159">Ensuite, configurez le dossier de documents du site d’équipe Projet Campagne 1 pour l’étiquette Privé.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="5fd3e-160">Dans l’onglet **campagne projet 1-accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="5fd3e-161">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="5fd3e-162">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="5fd3e-163">Dans **Les paramètres à appliquer une étiquette**, sélectionnez **privé**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="5fd3e-164">Site d’équipe marketing de campagne</span><span class="sxs-lookup"><span data-stu-id="5fd3e-164">Campaign marketing team site</span></span>

<span data-ttu-id="5fd3e-165">Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources marketing de la campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="5fd3e-166">À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="5fd3e-167">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="5fd3e-168">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="5fd3e-169">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="5fd3e-170">Dans la zone **nom du site d’équipe**, tapez la **campagne marketing**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="5fd3e-171">Dans la **description de site d’équipe**, tapez le **site SharePoint pour la campagne de commercialisation (la casse)**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="5fd3e-172">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-173">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="5fd3e-174">Dans l’onglet Nouveau de la **campagne marketing** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="5fd3e-175">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="5fd3e-176">Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="5fd3e-177">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @** <your organization name> **. onmicrosoft.com** dans la zone **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="5fd3e-178">Dans la liste, cliquez sur **campagne marketing des membres** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="5fd3e-179">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="5fd3e-180">Dans la boîte de dialogue de **partage** , tapez **Senior et personnel stratégique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="5fd3e-181">Répétez les étapes 14 et 15 pour le groupe **personnel d’Analytique** et le compte d’utilisateur **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="5fd3e-182">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="5fd3e-183">Dans la liste, cliquez sur **campagne marketing propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="5fd3e-184">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="5fd3e-185">Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="5fd3e-186">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="5fd3e-187">Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **Campagne marketing-Accueil** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="5fd3e-188">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="5fd3e-189">Le groupe SharePoint des **Membres de campagne marketing** contient uniquement le **personnel d’encadrement et personnel stratégique** groupe (qui contienne les comptes d’utilisateurs candidats, ChiefOfStaff et Strategic1), le groupe de **campagne marketing** (qui contient le compte d’utilisateur administrateur global), le groupe **personnel d’Analytique** (qui contient le compte d’utilisateur DataScientist1) et le compte d’utilisateur **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="5fd3e-190">Le groupe SharePoint **Propriétaires de marketing de campagne** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="5fd3e-191">Le groupe SharePoint de **Campagne marketing-les visiteurs** ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="5fd3e-192">Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe de **Campagnes marketing-propriétaires** ).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="5fd3e-193">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="5fd3e-194">Ensuite, configurez le dossier de documents du site d’équipe Marketing campagne pour l’étiquette Sensible.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="5fd3e-195">Dans l’onglet **Campagne marketing-Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="5fd3e-196">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="5fd3e-197">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="5fd3e-198">Dans **Les paramètres à appliquer une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="5fd3e-p103">Ensuite, configurez une stratégie de prévention contre la perte données qui avertit les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette sensible à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources dans le site de campagne marketing.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="5fd3e-201">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="5fd3e-202">Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="5fd3e-203">Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="5fd3e-204">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="5fd3e-205">Dans le volet **nom de votre stratégie** , tapez des **sites d’équipe SharePoint Online étiquette sensibles** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5fd3e-206">Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5fd3e-207">Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-208">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="5fd3e-209">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="5fd3e-210">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **sensibles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="5fd3e-211">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="5fd3e-212">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="5fd3e-213">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="5fd3e-214">Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="5fd3e-215">Dans la zone de texte, tapez ou collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="5fd3e-p104">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="5fd3e-219">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="5fd3e-220">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, désactivez la case à cocher **bloquer le partage, des personnes et de restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="5fd3e-221">Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5fd3e-222">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="5fd3e-223">Site d’équipe Stratégie de campagne</span><span class="sxs-lookup"><span data-stu-id="5fd3e-223">Campaign strategy team site</span></span>

<span data-ttu-id="5fd3e-224">Pour créer un site d’équipe SharePoint Online isolé hautement confidentiel pour les ressources de stratégie de campagne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="5fd3e-225">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="5fd3e-226">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="5fd3e-227">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="5fd3e-228">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="5fd3e-229">Dans la zone **nom du site d’équipe**, tapez **stratégie de campagne**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="5fd3e-230">Dans la **description de site d’équipe**, tapez le **site SharePoint pour la stratégie de campagne (hautement confidentiel)**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="5fd3e-231">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-232">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="5fd3e-233">Dans l’onglet **stratégie de campagne** nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="5fd3e-234">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="5fd3e-235">Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="5fd3e-236">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur ** OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="5fd3e-237">Dans la liste, cliquez sur **stratégie de campagne membres** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="5fd3e-238">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="5fd3e-239">Dans la boîte de dialogue de **partage** , tapez **Senior et personnel stratégique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="5fd3e-240">Dans la liste, cliquez sur **stratégie de campagne propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="5fd3e-241">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="5fd3e-242">Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="5fd3e-243">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="5fd3e-244">Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **accueil de la stratégie de la campagne** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="5fd3e-245">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="5fd3e-246">Le groupe SharePoint des **Membres de stratégie de campagne** contient uniquement le groupe **Senior et personnel stratégique** (qui contienne uniquement les comptes d’utilisateurs candidats, ChiefOfStaff et Strategic1) et le groupe de la **stratégie de campagne** (qui contient seul le compte d’administrateur global).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="5fd3e-247">Le groupe SharePoint **Propriétaires de stratégie de campagne** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="5fd3e-248">Le groupe SharePoint **Visiteurs de stratégie de campagne** ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="5fd3e-249">Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de stratégie de campagne** ).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="5fd3e-p105">Autres comptes d’utilisateur ne peut pas accéder au site ou ses ressources ou demander l’accès au site. Des autorisations supplémentaires sur le site doivent être effectuées par l’administrateur global ou par un membre du groupe de **Propriétaires de stratégie de campagne** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="5fd3e-252">Ensuite, configurez le dossier de documents du site d’équipe Stratégie de campagne pour l’étiquette Hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="5fd3e-253">Dans l’onglet **accueil de la stratégie de la campagne** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="5fd3e-254">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="5fd3e-255">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="5fd3e-256">Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Hautement confidentielles**et puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="5fd3e-p106">Configurez ensuite une stratégie DLP qui empêche les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette hautement confidentielles à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources du site stratégie de campagne.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="5fd3e-259">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="5fd3e-260">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="5fd3e-261">Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="5fd3e-262">Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="5fd3e-263">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5fd3e-264">Dans le volet **nom de votre stratégie** , tapez **hautement confidentielles sites d’équipe SharePoint Online étiquette** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5fd3e-265">Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5fd3e-266">Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="5fd3e-267">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="5fd3e-268">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="5fd3e-269">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="5fd3e-270">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="5fd3e-271">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="5fd3e-272">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="5fd3e-273">Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="5fd3e-274">Dans la zone de texte, tapez ou collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="5fd3e-p107">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="5fd3e-278">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="5fd3e-279">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5fd3e-280">Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="5fd3e-281">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="5fd3e-282">Suivez les instructions de [RMS d’Azure activer avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="5fd3e-283">Ensuite, configurez la Protection des informations Azure avec une nouvelle stratégie étendue et une étiquette secondaire pour la protection et d’autorisations avec les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fd3e-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="5fd3e-p108">Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="5fd3e-286">Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="5fd3e-287">Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="5fd3e-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="5fd3e-288">Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="5fd3e-289">Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="5fd3e-290">Dans **nom de la stratégie** et l' **étiquette pour les documents dans le site de l’équipe stratégie campagne** dans la zone **Description**, tapez **CampaignStrategy** .</span><span class="sxs-lookup"><span data-stu-id="5fd3e-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="5fd3e-291">Cliquez sur **Sélectionner les utilisateurs ou les groupes d’obtiennent cette stratégie > groupes d’utilisateurs**, puis sélectionnez **Senior et personnel stratégique**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="5fd3e-292">Cliquez sur **Sélectionner > OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="5fd3e-293">Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="5fd3e-294">Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="5fd3e-295">Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="5fd3e-296">Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="5fd3e-297">Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="5fd3e-298">Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="5fd3e-299">Dans le volet **DAS utilisateurs et des groupes** , sélectionnez **Senior et stratégique personnel**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="5fd3e-300">Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="5fd3e-301">Cliquez deux fois sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="5fd3e-302">Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="5fd3e-303">Fermez le panneau de la nouvelle stratégie étendue.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="5fd3e-304">Sur la lame de **protection des informations de Azure - stratégies étendues** , cliquez sur **Publier**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="5fd3e-305">Vous êtes désormais prêt à créer des documents dans ces quatre sites et à tester l’accès à ces sites avec divers comptes d’utilisateurs disponibles avec votre abonnement à la version d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="5fd3e-306">Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis vous connecter à partir de Microsoft Word avec un compte dans le ** Personnel d’encadrement et personnel stratégique** groupe de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="5fd3e-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5fd3e-307">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fd3e-307">See Also</span></span>

[<span data-ttu-id="5fd3e-308">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="5fd3e-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="5fd3e-309">Configurer des groupes et des utilisateurs pour un environnement de développement/test de campagne politique</span><span class="sxs-lookup"><span data-stu-id="5fd3e-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="5fd3e-310">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="5fd3e-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5fd3e-311">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="5fd3e-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




