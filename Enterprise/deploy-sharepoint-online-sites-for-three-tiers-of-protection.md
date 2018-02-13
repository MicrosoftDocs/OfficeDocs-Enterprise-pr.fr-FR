---
title: "Déploiement de sites SharePoint Online à trois niveaux de protection"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Résumé : Créer et configurer des sites d’équipe SharePoint Online pour différents niveaux de protection des informations."
ms.openlocfilehash: 4e6e70377f27bcd3cf367aefa1a640188abefc50
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="4ef98-103">Déploiement de sites SharePoint Online à trois niveaux de protection</span><span class="sxs-lookup"><span data-stu-id="4ef98-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="4ef98-104">**Résumé :** Créer et configurer des sites d’équipe SharePoint Online pour différents niveaux de protection des informations.</span><span class="sxs-lookup"><span data-stu-id="4ef98-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="4ef98-p101">Utilisez les étapes de cet article pour concevoir et déployer la base, sensibles et hautement confidentielles SharePoint Online sites d’équipe. Pour plus d’informations sur ces trois niveaux de protection, voir les [fichiers et les sites SharePoint Online de la sécuriser](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="4ef98-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="4ef98-107">Sites d’équipe SharePoint Online de référence</span><span class="sxs-lookup"><span data-stu-id="4ef98-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="4ef98-p102">La protection de référence concerne les sites d’équipe publics et privés. Les sites publics peuvent être recherchés par toute personne de l’organisation. Seules ces personnes peuvent y accéder. Les sites privés peuvent uniquement être recherchés par les membres du groupe Office 365 associé au site d’équipe et seuls ces derniers peuvent y accéder. Ces deux types de sites d’équipe autorisent les membres à partager le site avec d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="4ef98-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="4ef98-112">Public</span><span class="sxs-lookup"><span data-stu-id="4ef98-112">Public</span></span>

<span data-ttu-id="4ef98-113">Pour créer un site d’équipe SharePoint Online de référence avec des autorisations et un accès publics, suivez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ef98-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="4ef98-p103">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4ef98-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4ef98-116">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4ef98-117">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4ef98-118">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4ef98-119">Dans la zone **nom du Site**, tapez un nom pour le site d’équipe public.</span><span class="sxs-lookup"><span data-stu-id="4ef98-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="4ef98-120">Dans la **description de site d’équipe**, tapez une description de l’objet du site.</span><span class="sxs-lookup"><span data-stu-id="4ef98-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="4ef98-121">Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4ef98-122">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="4ef98-123">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="4ef98-123">Here is your resulting configuration.</span></span>
  
![Protection de base pour un site d’équipe SharePoint Online public.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="4ef98-125">Privé</span><span class="sxs-lookup"><span data-stu-id="4ef98-125">Private</span></span>

<span data-ttu-id="4ef98-126">Pour créer un site d’équipe SharePoint Online de référence avec des autorisations et un accès privés, suivez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ef98-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="4ef98-p104">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4ef98-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4ef98-129">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4ef98-130">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4ef98-131">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4ef98-132">Dans la zone **nom du Site**, tapez un nom pour le site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="4ef98-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="4ef98-133">Dans la **description de site d’équipe,** tapez une description de l’objet du site.</span><span class="sxs-lookup"><span data-stu-id="4ef98-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="4ef98-134">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4ef98-135">Sur le **qui voulez-vous ajouter ?** volet, dans la zone **Ajouter des membres**, tapez les noms des comptes d’utilisateurs qui ont accès à ce site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="4ef98-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="4ef98-136">Lorsque vous avez terminé l’ajout de l’ensemble initial de membres au site, cliquez sur **Terminer**</span><span class="sxs-lookup"><span data-stu-id="4ef98-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="4ef98-137">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="4ef98-137">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online privé.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="4ef98-139">Sites d’équipe SharePoint Online sensibles</span><span class="sxs-lookup"><span data-stu-id="4ef98-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="4ef98-140">Un site d’équipe SharePoint Online sensible est un site d’équipe isolé. En d’autres termes, les autorisations sont contrôlées selon l’appartenance de l’utilisateur à des groupes SharePoint, et non selon son appartenance au groupe Office 365 associé au site d’équipe.</span><span class="sxs-lookup"><span data-stu-id="4ef98-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="4ef98-141">La création d’un site d’équipe isolé se déroule en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="4ef98-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="4ef98-142">Étape 1 : conception du site isolé</span><span class="sxs-lookup"><span data-stu-id="4ef98-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="4ef98-143">Pour concevoir votre site d’équipe isolé, vous devez choisir :</span><span class="sxs-lookup"><span data-stu-id="4ef98-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="4ef98-144">vos groupes SharePoint et les niveaux d’autorisation ;</span><span class="sxs-lookup"><span data-stu-id="4ef98-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="4ef98-145">les groupes d’accès qui seront membres de vos groupes SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4ef98-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="4ef98-146">Le jeu de groupes d’accès recommandé est un des membres du site, un pour les visiteurs du site affichent et un pour les administrateurs de site.</span><span class="sxs-lookup"><span data-stu-id="4ef98-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="4ef98-147">si vous allez utiliser des groupes imbriqués au sein de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="4ef98-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="4ef98-148">Voici à quoi peuvent ressembler les niveaux d’autorisation et de structure du groupe recommandés :</span><span class="sxs-lookup"><span data-stu-id="4ef98-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="4ef98-149">**Groupe SharePoint**</span><span class="sxs-lookup"><span data-stu-id="4ef98-149">**SharePoint group**</span></span>|<span data-ttu-id="4ef98-150">**Niveau d’autorisation**</span><span class="sxs-lookup"><span data-stu-id="4ef98-150">**Permission level**</span></span>|<span data-ttu-id="4ef98-151">**Groupe d’accès (exemples)**</span><span class="sxs-lookup"><span data-stu-id="4ef98-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4ef98-152">[nom de site] Membres</span><span class="sxs-lookup"><span data-stu-id="4ef98-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="4ef98-153">Modification</span><span class="sxs-lookup"><span data-stu-id="4ef98-153">Edit</span></span>  <br/> |<span data-ttu-id="4ef98-154">[nom de site] Membres</span><span class="sxs-lookup"><span data-stu-id="4ef98-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="4ef98-155">[nom de site] Visiteurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="4ef98-156">Lecture</span><span class="sxs-lookup"><span data-stu-id="4ef98-156">Read</span></span>  <br/> |<span data-ttu-id="4ef98-157">[nom de site] Afficheurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="4ef98-158">[nom de site] Propriétaires</span><span class="sxs-lookup"><span data-stu-id="4ef98-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="4ef98-159">Contrôle total</span><span class="sxs-lookup"><span data-stu-id="4ef98-159">Full control</span></span>  <br/> |<span data-ttu-id="4ef98-160">[nom de site] Administrateurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="4ef98-p105">Les groupes SharePoint et les niveaux d’autorisation sont créés par défaut pour un site d’équipe. Vous devez nommer vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="4ef98-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="4ef98-163">Pour les détails du processus de conception, consultez [conception d’un site d’équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="4ef98-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="4ef98-164">Étape 2 : déploiement du site isolé</span><span class="sxs-lookup"><span data-stu-id="4ef98-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="4ef98-165">Pour déployer votre site isolé, vous devez d’abord :</span><span class="sxs-lookup"><span data-stu-id="4ef98-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="4ef98-166">déterminer les comptes d’utilisateurs et les groupes à ajouter à chacun de vos groupes d’accès ;</span><span class="sxs-lookup"><span data-stu-id="4ef98-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="4ef98-167">créer les groupes d’accès et ajouter les utilisateurs et les membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="4ef98-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="4ef98-168">Pour obtenir la procédure détaillée, voir la **Phase 1** de [déployer un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="4ef98-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="4ef98-169">Ensuite, vous devez créer le site d’équipe SharePoint Online en suivant ces étapes.</span><span class="sxs-lookup"><span data-stu-id="4ef98-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="4ef98-p106">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4ef98-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4ef98-172">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4ef98-173">Dans le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4ef98-174">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4ef98-175">Dans la zone **nom du Site**, tapez un nom pour le site d’équipe privé.</span><span class="sxs-lookup"><span data-stu-id="4ef98-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="4ef98-176">Dans la **description de site d’équipe**, tapez une description facultative.</span><span class="sxs-lookup"><span data-stu-id="4ef98-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="4ef98-177">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4ef98-178">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="4ef98-179">Ensuite, dans le nouveau site d’équipe SharePoint Online, configurez les autorisations en suivant ces étapes.</span><span class="sxs-lookup"><span data-stu-id="4ef98-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="4ef98-p107">Choisissez le Nom d’utilisateur principal (UPN) de l’administrateur informatique ou d’une autre personne qui sera chargée de répondre aux demandes d’accès au site (belindan@contoso.com est un exemple d’UPN). Notez cet UPN ici : _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="4ef98-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="4ef98-182">Dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="4ef98-183">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="4ef98-184">Dans l’onglet **autorisations** de nouveau de votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="4ef98-185">Dans la boîte de dialogue **Paramètres de demandes d’accès** :</span><span class="sxs-lookup"><span data-stu-id="4ef98-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="4ef98-186">Désactivez les cases à cocher **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et de **permettre aux membres de partager le site et les fichiers et dossiers individuels** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="4ef98-187">Dans la zone **Envoyer toutes les demandes d’accès**, tapez le nom UPN de l’administrateur de l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="4ef98-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="4ef98-188">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="4ef98-189">Dans l’onglet **autorisations** de votre navigateur, cliquez sur **membres de [nom de site]** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="4ef98-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="4ef98-190">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="4ef98-191">Dans la boîte de dialogue de **partage** , tapez le nom de votre groupe d’accès de membres de site pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="4ef98-192">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="4ef98-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="4ef98-193">Dans la liste, cliquez sur **[nom de site] propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="4ef98-194">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="4ef98-195">Dans la boîte de dialogue de **partage** , tapez le nom du groupe de l’accès aux administrateurs du site pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="4ef98-196">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="4ef98-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="4ef98-197">Dans la liste, cliquez sur **les visiteurs de [nom de site]** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="4ef98-198">**Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="4ef98-199">Dans la boîte de dialogue de **partage** , tapez le nom du groupe d’accès site visionneuses pour ce site, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="4ef98-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="4ef98-200">Fermez l’onglet **autorisations** de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="4ef98-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="4ef98-201">Voici les résultats que vous devez escompter :</span><span class="sxs-lookup"><span data-stu-id="4ef98-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="4ef98-202">Le groupe SharePoint **propriétaires de [nom de site]** contient le groupe Administrateurs l’accès, dans laquelle tous les membres ont le niveau d’autorisation **contrôle total** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="4ef98-203">Le groupe SharePoint **des membres de [nom de site]** contient le groupe membres de l’accès, dans laquelle tous les membres ont le niveau d’autorisation **Modifier** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="4ef98-204">Le groupe SharePoint **visiteurs de [nom de site]** contient le groupe d’accès site visionneuses, dans lequel tous les membres ont le niveau d’autorisation **lecture** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="4ef98-205">La capacité des membres à inviter d’autres membres est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4ef98-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="4ef98-206">La possibilité pour les États non membres demander l’accès est activée.</span><span class="sxs-lookup"><span data-stu-id="4ef98-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="4ef98-207">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="4ef98-207">Here is your resulting configuration.</span></span>
  
![Protection des données sensibles d’un site d’équipe SharePoint Online isolé.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="4ef98-209">En étant membres de l’un des groupes d’accès, les membres du site peuvent désormais travailler avec les ressources du site en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="4ef98-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="4ef98-210">Sites d’équipe SharePoint Online hautement confidentiels</span><span class="sxs-lookup"><span data-stu-id="4ef98-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="4ef98-211">Un site d’équipe SharePoint Online hautement confidentiel est un site d’équipe isolé. En d’autres termes, les autorisations sont contrôlées selon l’appartenance de l’utilisateur à des groupes SharePoint, et non selon son appartenance au groupe Office 365 associé au site d’équipe.</span><span class="sxs-lookup"><span data-stu-id="4ef98-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="4ef98-212">Pour créer un site d’équipe isolé pour protéger le travail et les informations hautement confidentielles partagées sur le site, vous devez suivre deux étapes.</span><span class="sxs-lookup"><span data-stu-id="4ef98-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="4ef98-213">Étape 1 : conception du site isolé</span><span class="sxs-lookup"><span data-stu-id="4ef98-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="4ef98-214">Pour concevoir votre site d’équipe isolé, vous devez choisir :</span><span class="sxs-lookup"><span data-stu-id="4ef98-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="4ef98-215">vos groupes SharePoint et les niveaux d’autorisation ;</span><span class="sxs-lookup"><span data-stu-id="4ef98-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="4ef98-216">les groupes d’accès qui seront membres de vos groupes SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4ef98-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="4ef98-217">Le jeu de groupes d’accès recommandé est un des membres du site, un pour les visiteurs du site affichent et un pour les administrateurs de site.</span><span class="sxs-lookup"><span data-stu-id="4ef98-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="4ef98-218">si vous allez utiliser des groupes imbriqués au sein de vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="4ef98-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="4ef98-219">Voici à quoi peuvent ressembler les niveaux d’autorisation et de structure du groupe recommandés :</span><span class="sxs-lookup"><span data-stu-id="4ef98-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="4ef98-220">**Groupe SharePoint**</span><span class="sxs-lookup"><span data-stu-id="4ef98-220">**SharePoint group**</span></span>|<span data-ttu-id="4ef98-221">**Niveau d’autorisation**</span><span class="sxs-lookup"><span data-stu-id="4ef98-221">**Permission level**</span></span>|<span data-ttu-id="4ef98-222">**Groupe d’accès (exemples)**</span><span class="sxs-lookup"><span data-stu-id="4ef98-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4ef98-223">[nom de site] Membres</span><span class="sxs-lookup"><span data-stu-id="4ef98-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="4ef98-224">Modification</span><span class="sxs-lookup"><span data-stu-id="4ef98-224">Edit</span></span>  <br/> |<span data-ttu-id="4ef98-225">[nom de site] Membres</span><span class="sxs-lookup"><span data-stu-id="4ef98-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="4ef98-226">[nom de site] Visiteurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="4ef98-227">Lecture</span><span class="sxs-lookup"><span data-stu-id="4ef98-227">Read</span></span>  <br/> |<span data-ttu-id="4ef98-228">[nom de site] Afficheurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="4ef98-229">[nom de site] Propriétaires</span><span class="sxs-lookup"><span data-stu-id="4ef98-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="4ef98-230">Contrôle total</span><span class="sxs-lookup"><span data-stu-id="4ef98-230">Full control</span></span>  <br/> |<span data-ttu-id="4ef98-231">[nom de site] Administrateurs</span><span class="sxs-lookup"><span data-stu-id="4ef98-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="4ef98-p108">Les groupes SharePoint et les niveaux d’autorisation sont créés par défaut pour un site d’équipe. Vous devez nommer vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="4ef98-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="4ef98-234">Pour les détails du processus de conception, consultez [conception d’un site d’équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="4ef98-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="4ef98-235">Étape 2 : déploiement du site isolé</span><span class="sxs-lookup"><span data-stu-id="4ef98-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="4ef98-236">Pour déployer votre site isolé, vous devez d’abord :</span><span class="sxs-lookup"><span data-stu-id="4ef98-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="4ef98-237">déterminer les utilisateurs et les membres du groupe de chacun de vos groupes d’accès ;</span><span class="sxs-lookup"><span data-stu-id="4ef98-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="4ef98-238">créer les groupes d’accès et ajouter les utilisateurs et les membres du groupe ;</span><span class="sxs-lookup"><span data-stu-id="4ef98-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="4ef98-239">créer un site d’équipe isolé qui utilise vos groupes d’accès.</span><span class="sxs-lookup"><span data-stu-id="4ef98-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="4ef98-240">Pour obtenir la procédure détaillée, voir [déploiement d’un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="4ef98-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="4ef98-241">Voici les résultats que vous devez escompter :</span><span class="sxs-lookup"><span data-stu-id="4ef98-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="4ef98-242">Le groupe SharePoint **propriétaires de [nom de site]** contient le groupe Administrateurs l’accès, dans laquelle tous les membres ont le niveau d’autorisation **contrôle total** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="4ef98-243">Le groupe SharePoint **des membres de [nom de site]** contient le groupe membres de l’accès, dans laquelle tous les membres ont le niveau d’autorisation **Modifier** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="4ef98-244">Le groupe SharePoint **visiteurs de [nom de site]** contient le groupe d’accès site visionneuses, dans lequel tous les membres ont le niveau d’autorisation **lecture** .</span><span class="sxs-lookup"><span data-stu-id="4ef98-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="4ef98-245">La capacité des membres à inviter d’autres membres est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4ef98-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="4ef98-246">La possibilité pour les États non membres demander l’accès est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4ef98-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="4ef98-247">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="4ef98-247">Here is your resulting configuration.</span></span>
  
![Protection avec un niveau de confidentialité élevé pour un site d’équipe SharePoint Online isolé.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="4ef98-249">En étant membres de l’un des groupes d’accès, les membres du site peuvent désormais travailler avec les ressources du site en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="4ef98-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="4ef98-250">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="4ef98-250">Next step</span></span>

[<span data-ttu-id="4ef98-251">Protéger les fichiers SharePoint Online avec les étiquettes d’Office 365 et DLP</span><span class="sxs-lookup"><span data-stu-id="4ef98-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="4ef98-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ef98-252">See Also</span></span>

[<span data-ttu-id="4ef98-253">Sécuriser les fichiers et sites SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4ef98-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="4ef98-254">Sécuriser les sites SharePoint Online dans un environnement de développement/test</span><span class="sxs-lookup"><span data-stu-id="4ef98-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="4ef98-255">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="4ef98-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="4ef98-256">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="4ef98-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




