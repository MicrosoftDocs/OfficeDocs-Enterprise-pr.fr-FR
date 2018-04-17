---
title: Déploiement de sites SharePoint Online à trois niveaux de protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Résumé : Créer et configurer des sites d’équipe SharePoint Online pour différents niveaux de protection des informations.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="07676-103">Déploiement de sites SharePoint Online à trois niveaux de protection</span><span class="sxs-lookup"><span data-stu-id="07676-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="07676-104">**Résumé :** Créer et configurer des sites d’équipe SharePoint Online pour différents niveaux de protection des informations.</span><span class="sxs-lookup"><span data-stu-id="07676-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="07676-p101">Utilisez les étapes de cet article pour concevoir et déployer des sites d’équipe SharePoint Online de base de référence, sensibles et hautement confidentiels. Pour plus d’informations sur ces trois niveaux de protection, consultez [Sécuriser des sites et des fichiers SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="07676-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="07676-107">Sites d’équipe SharePoint Online de base de référence</span><span class="sxs-lookup"><span data-stu-id="07676-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="07676-p102">La protection Base de référence inclut les sites d’équipe publics et privés. Les sites d’équipe publics peuvent être découverts et sont accessibles par toute personne de l’organisation. Les sites privés peuvent être découverts et sont accessibles seulement par les membres du groupe Office 365 associé au site d’équipe. Ces deux types de sites d’équipe permettent aux membres de partager le site avec d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="07676-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="07676-112">Public</span><span class="sxs-lookup"><span data-stu-id="07676-112">Public</span></span>

<span data-ttu-id="07676-113">Pour créer un site d’équipe SharePoint Online de base de référence avec un accès et des autorisations publics, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="07676-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="07676-p103">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="07676-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="07676-116">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="07676-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="07676-117">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="07676-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="07676-118">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="07676-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="07676-119">Dans **Nom du Site**, tapez un nom pour le site d’équipe public.</span><span class="sxs-lookup"><span data-stu-id="07676-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="07676-120">Dans **Description du site d’équipe**, tapez une description de l’objectif du site.</span><span class="sxs-lookup"><span data-stu-id="07676-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="07676-121">Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="07676-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="07676-122">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="07676-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="07676-123">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="07676-123">Here is your resulting configuration.</span></span>
  
![Protection de base pour un site d’équipe SharePoint Online public.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="07676-125">Privé</span><span class="sxs-lookup"><span data-stu-id="07676-125">Private</span></span>

<span data-ttu-id="07676-126">Pour créer un site d’équipe SharePoint Online de base de référence avec un accès et des autorisations privés, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="07676-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="07676-p104">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="07676-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="07676-129">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="07676-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="07676-130">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="07676-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="07676-131">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="07676-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="07676-132">Dans **Nom du site**, tapez un nom pour le site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="07676-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="07676-133">Dans la **description de site d’équipe,** tapez une description de l’objet du site.</span><span class="sxs-lookup"><span data-stu-id="07676-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="07676-134">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="07676-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="07676-135">Dans le volet **Qui voulez-vous ajouter ?**, dans **Ajouter des membres**, tapez les noms des comptes d’utilisateurs qui ont accès à ce site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="07676-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="07676-136">Lorsque vous avez terminé l’ajout de l’ensemble initial de membres au site, cliquez sur **Terminer**</span><span class="sxs-lookup"><span data-stu-id="07676-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="07676-137">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="07676-137">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online privé.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="07676-139">Sites d’équipe SharePoint Online sensibles</span><span class="sxs-lookup"><span data-stu-id="07676-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="07676-140">Un site d’équipe SharePoint Online sensible est un site d’équipe isolé. En d’autres termes, les autorisations sont contrôlées selon l’appartenance de l’utilisateur à des groupes SharePoint, et non selon son appartenance au groupe Office 365 associé au site d’équipe.</span><span class="sxs-lookup"><span data-stu-id="07676-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="07676-141">La création d’un site d’équipe isolé se déroule en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="07676-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="07676-142">Étape 1 : conception du site isolé</span><span class="sxs-lookup"><span data-stu-id="07676-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="07676-143">Pour concevoir votre site d’équipe isolé, vous devez déterminer :</span><span class="sxs-lookup"><span data-stu-id="07676-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="07676-144">vos groupes SharePoint et les niveaux d’autorisation ;</span><span class="sxs-lookup"><span data-stu-id="07676-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="07676-145">les groupes d’accès qui seront membres de vos groupes SharePoint.</span><span class="sxs-lookup"><span data-stu-id="07676-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="07676-146">Le jeu de groupes d’accès recommandé est un des membres du site, un pour les visiteurs du site affichent et un pour les administrateurs de site.</span><span class="sxs-lookup"><span data-stu-id="07676-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="07676-147">Si vous utilisez des groupes imbriqués au sein de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="07676-148">Par exemple, la structure des groupes et les niveaux d’autorisations recommandés se présentent comme ceci :</span><span class="sxs-lookup"><span data-stu-id="07676-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="07676-149">**Groupe SharePoint**</span><span class="sxs-lookup"><span data-stu-id="07676-149">**SharePoint group**</span></span>|<span data-ttu-id="07676-150">**Niveau d’autorisation**</span><span class="sxs-lookup"><span data-stu-id="07676-150">**Permission level**</span></span>|<span data-ttu-id="07676-151">**Groupe d’accès (exemples)**</span><span class="sxs-lookup"><span data-stu-id="07676-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="07676-152">Membres de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="07676-153">Éditer</span><span class="sxs-lookup"><span data-stu-id="07676-153">Edit</span></span>  <br/> |<span data-ttu-id="07676-154">Membres de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="07676-155">Visiteurs de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="07676-156">Lire</span><span class="sxs-lookup"><span data-stu-id="07676-156">Read</span></span>  <br/> |<span data-ttu-id="07676-157">Personnes consultant [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="07676-158">Propriétaires de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="07676-159">Contrôle total</span><span class="sxs-lookup"><span data-stu-id="07676-159">Full control</span></span>  <br/> |<span data-ttu-id="07676-160">Administrateurs de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="07676-p105">Les groupes et les niveaux d’autorisation SharePoint sont créés par défaut pour un site d’équipe. Vous devez déterminer les noms de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="07676-163">Pour plus d’informations sur le processus de conception, consultez [Concevoir un site d’équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="07676-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="07676-164">Étape 2 : Déployer votre site isolé</span><span class="sxs-lookup"><span data-stu-id="07676-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="07676-165">Pour déployer votre site isolé, vous devez d’abord :</span><span class="sxs-lookup"><span data-stu-id="07676-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="07676-166">Déterminer les comptes d’utilisateur et les groupes à ajouter à chacun de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="07676-167">Créer les groupes d’accès, et ajouter les utilisateurs et les groupes membres.</span><span class="sxs-lookup"><span data-stu-id="07676-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="07676-168">Pour la procédure détaillée, consultez **Phase 1** de [Déployer un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="07676-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="07676-169">Ensuite, vous devez créer le site d’équipe SharePoint Online en suivant ces étapes.</span><span class="sxs-lookup"><span data-stu-id="07676-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="07676-p106">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="07676-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="07676-172">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="07676-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="07676-173">Dans le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="07676-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="07676-174">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="07676-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="07676-175">Dans **Nom du site**, tapez un nom pour le site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="07676-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="07676-176">Dans la **description de site d’équipe**, tapez une description facultative.</span><span class="sxs-lookup"><span data-stu-id="07676-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="07676-177">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="07676-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="07676-178">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="07676-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="07676-179">Ensuite, dans le nouveau site d’équipe SharePoint Online, configurez les autorisations en suivant cette procédure.</span><span class="sxs-lookup"><span data-stu-id="07676-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="07676-p107">Choisissez le Nom d’utilisateur principal (UPN) de l’administrateur informatique ou d’une autre personne qui sera chargée de répondre aux demandes d’accès au site (belindan@contoso.com est un exemple d’UPN). Notez cet UPN ici : _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="07676-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="07676-182">Dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="07676-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="07676-183">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="07676-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="07676-184">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="07676-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="07676-185">Dans la boîte de dialogue **Paramètres des demandes d’accès** :</span><span class="sxs-lookup"><span data-stu-id="07676-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="07676-186">Décochez les cases **Autoriser les membres à partager le site, ainsi que des fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site**.</span><span class="sxs-lookup"><span data-stu-id="07676-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="07676-187">Tapez le nom d’utilisateur principal de votre administrateur informatique de l’étape 1 dans **Envoyer toutes les demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="07676-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="07676-188">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07676-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="07676-189">Sous l’onglet **Autorisations** de votre navigateur, cliquez sur **Membres de [nom du site]** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="07676-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="07676-190">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="07676-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="07676-191">Dans la boîte de dialogue de **partage** , tapez le nom de votre groupe d’accès de membres de site pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="07676-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="07676-192">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="07676-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="07676-193">Dans la liste, cliquez sur **[nom de site] propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="07676-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="07676-194">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="07676-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="07676-195">Dans la boîte de dialogue de **partage** , tapez le nom du groupe de l’accès aux administrateurs du site pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="07676-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="07676-196">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="07676-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="07676-197">Dans la liste, cliquez sur **les visiteurs de [nom de site]** .</span><span class="sxs-lookup"><span data-stu-id="07676-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="07676-198">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="07676-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="07676-199">Dans la boîte de dialogue de **partage** , tapez le nom du groupe d’accès site visionneuses pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="07676-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="07676-200">Fermez l’onglet **Autorisations** de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="07676-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="07676-201">Voici les résultats que vous devez escompter :</span><span class="sxs-lookup"><span data-stu-id="07676-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="07676-202">Le groupe SharePoint **Propriétaires de [nom du site]** contient le groupe d’accès Administrateurs du site, dans lequel tous les membres ont le niveau d’autorisation **Contrôle total**.</span><span class="sxs-lookup"><span data-stu-id="07676-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="07676-203">Le groupe SharePoint **Membres de [nom du site]** contient le groupe d’accès Membres du site, dans lequel tous les membres ont le niveau d’autorisation **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="07676-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="07676-204">Le groupe SharePoint **Visiteurs de [nom du site]** contient le groupe d’accès Visiteurs du site, dans lequel tous les membres ont le niveau d’autorisation **Lire**.</span><span class="sxs-lookup"><span data-stu-id="07676-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="07676-205">La possibilité pour les membres d’inviter d’autres membres est désactivée.</span><span class="sxs-lookup"><span data-stu-id="07676-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="07676-206">La possibilité pour les non-membres de demander l’accès est activée.</span><span class="sxs-lookup"><span data-stu-id="07676-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="07676-207">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="07676-207">Here is your resulting configuration.</span></span>
  
![Protection des données sensibles d’un site d’équipe SharePoint Online isolé.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="07676-209">Les membres du site, via l’appartenance à un des groupes d’accès, peuvent désormais collaborer sur les ressources du site de façon sécurisée.</span><span class="sxs-lookup"><span data-stu-id="07676-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="07676-210">Sites d’équipe SharePoint Online hautement confidentiels</span><span class="sxs-lookup"><span data-stu-id="07676-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="07676-211">Un site d’équipe SharePoint Online hautement confidentiel est un site d’équipe isolé, ce qui signifie que les autorisations sont contrôlées via l’appartenance à des groupes SharePoint, au lieu de l’appartenance au groupe Office 365 associé au site d’équipe.</span><span class="sxs-lookup"><span data-stu-id="07676-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="07676-212">Pour créer un site d’équipe isolé pour des informations et une collaboration hautement confidentielles, vous devez procéder en deux étapes principales.</span><span class="sxs-lookup"><span data-stu-id="07676-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="07676-213">Étape 1 : Concevoir votre site isolé</span><span class="sxs-lookup"><span data-stu-id="07676-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="07676-214">Pour concevoir votre site d’équipe isolé, vous devez déterminer :</span><span class="sxs-lookup"><span data-stu-id="07676-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="07676-215">vos groupes SharePoint et les niveaux d’autorisation ;</span><span class="sxs-lookup"><span data-stu-id="07676-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="07676-216">les groupes d’accès qui seront membres de vos groupes SharePoint.</span><span class="sxs-lookup"><span data-stu-id="07676-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="07676-217">Le jeu de groupes d’accès recommandé est un des membres du site, un pour les visiteurs du site affichent et un pour les administrateurs de site.</span><span class="sxs-lookup"><span data-stu-id="07676-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="07676-218">Si vous utilisez des groupes imbriqués au sein de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="07676-219">Par exemple, la structure des groupes et les niveaux d’autorisations recommandés se présentent comme ceci :</span><span class="sxs-lookup"><span data-stu-id="07676-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="07676-220">**Groupe SharePoint**</span><span class="sxs-lookup"><span data-stu-id="07676-220">**SharePoint group**</span></span>|<span data-ttu-id="07676-221">**Niveau d’autorisation**</span><span class="sxs-lookup"><span data-stu-id="07676-221">**Permission level**</span></span>|<span data-ttu-id="07676-222">**Groupe d’accès (exemples)**</span><span class="sxs-lookup"><span data-stu-id="07676-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="07676-223">Membres de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="07676-224">Éditer</span><span class="sxs-lookup"><span data-stu-id="07676-224">Edit</span></span>  <br/> |<span data-ttu-id="07676-225">Membres de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="07676-226">Visiteurs de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="07676-227">Lire</span><span class="sxs-lookup"><span data-stu-id="07676-227">Read</span></span>  <br/> |<span data-ttu-id="07676-228">Personnes consultant [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="07676-229">Propriétaires de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="07676-230">Contrôle total</span><span class="sxs-lookup"><span data-stu-id="07676-230">Full control</span></span>  <br/> |<span data-ttu-id="07676-231">Administrateurs de [nom du site]</span><span class="sxs-lookup"><span data-stu-id="07676-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="07676-p108">Les groupes et les niveaux d’autorisation SharePoint sont créés par défaut pour un site d’équipe. Vous devez déterminer les noms de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="07676-234">Pour plus d’informations sur le processus de conception, consultez [Concevoir un site d’équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="07676-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="07676-235">Étape 2 : Déployer votre site isolé</span><span class="sxs-lookup"><span data-stu-id="07676-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="07676-236">Pour déployer votre site isolé, vous devez d’abord :</span><span class="sxs-lookup"><span data-stu-id="07676-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="07676-237">déterminer les utilisateurs et les membres du groupe de chacun de vos groupes d’accès ;</span><span class="sxs-lookup"><span data-stu-id="07676-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="07676-238">créer les groupes d’accès et ajouter les utilisateurs et les membres du groupe ;</span><span class="sxs-lookup"><span data-stu-id="07676-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="07676-239">créer un site d’équipe isolé qui utilise vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="07676-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="07676-240">Pour la procédure détaillée, consultez [Déployer un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="07676-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="07676-241">Voici les résultats que vous devez escompter :</span><span class="sxs-lookup"><span data-stu-id="07676-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="07676-242">Le groupe SharePoint **Propriétaires de [nom du site]** contient le groupe d’accès Administrateurs du site, dans lequel tous les membres ont le niveau d’autorisation **Contrôle total**.</span><span class="sxs-lookup"><span data-stu-id="07676-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="07676-243">Le groupe SharePoint **Membres de [nom du site]** contient le groupe d’accès Membres du site, dans lequel tous les membres ont le niveau d’autorisation **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="07676-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="07676-244">Le groupe SharePoint **Visiteurs de [nom du site]** contient le groupe d’accès Visiteurs du site, dans lequel tous les membres ont le niveau d’autorisation **Lire**.</span><span class="sxs-lookup"><span data-stu-id="07676-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="07676-245">La possibilité pour les membres d’inviter d’autres membres est désactivée.</span><span class="sxs-lookup"><span data-stu-id="07676-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="07676-246">La possibilité pour les non-membres de demander l’accès est désactivée.</span><span class="sxs-lookup"><span data-stu-id="07676-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="07676-247">Voici le résultat de votre configuration.</span><span class="sxs-lookup"><span data-stu-id="07676-247">Here is your resulting configuration.</span></span>
  
![Protection avec un niveau de confidentialité élevé pour un site d’équipe SharePoint Online isolé.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="07676-249">En étant membres de l’un des groupes d’accès, les membres du site peuvent désormais travailler avec les ressources du site en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="07676-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="07676-250">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="07676-250">Next step</span></span>

[<span data-ttu-id="07676-251">Protéger les fichiers SharePoint Online avec les étiquettes d’Office 365 et DLP</span><span class="sxs-lookup"><span data-stu-id="07676-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="07676-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07676-252">See Also</span></span>

[<span data-ttu-id="07676-253">Sécuriser les fichiers et sites SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="07676-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="07676-254">Sécuriser les sites SharePoint Online dans un environnement de développement/test</span><span class="sxs-lookup"><span data-stu-id="07676-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="07676-255">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="07676-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="07676-256">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="07676-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




