---
title: Environnement de développement/test Office 365 et Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Résumé : Utilisez ce guide de laboratoire de test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.'
ms.openlocfilehash: 195e5ab4fd96d1f238c96d47cc7406a45e0e02b1
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915209"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="3aa00-103">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="3aa00-104">**Résumé :** Utilisez ce guide de laboratoire de test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="3aa00-105">Suivez les instructions fournies dans cet article pour ajouter un abonnement à la version d’évaluation de Dynamics 365 à la même organisation que votre environnement de développement/test Office 365, créant ainsi un environnement de développement/test Office 365 et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Environnement de développement/test Office 365 et Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="3aa00-p101">Vous pouvez utiliser un abonnement à la version d’évaluation de Dynamics 365 afin de présenter les fonctionnalités de Dynamics 365. Les solutions suivantes sont comprises dans la version d’évaluation Enterprise Edition de Dynamics 365 Plan 1 :</span><span class="sxs-lookup"><span data-stu-id="3aa00-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="3aa00-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Augmentez vos ventes grâce à l’automatisation et aux outils numériques qui permettent à vos collaborateurs de rester concentrés et de travailler plus efficacement.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p102">[Microsoft Dynamics 365 for Saleshttps://www.microsoft.com/dynamics365/sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="3aa00-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Fidélisez vos agents en leur fournissant l’ensemble des informations et des outils numériques dont ils ont besoin pour proposer un service impeccable.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p103">[Microsoft Dynamics 365 for Customer Servicehttps://www.microsoft.com/dynamics365/customer-service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="3aa00-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Contrôlez les visites de réparation en optimisant vos plannings, en équipant votre personnel d’appareils adaptés et en utilisant des outils de prévision en vue d’augmenter vos bénéfices.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p104">[Microsoft Dynamics 365 for Field Servicehttps://www.microsoft.com/dynamics365/field-service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="3aa00-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/fr-FR/dynamics365/project-service-automation). Menez vos projets à bien et initiez des relations fructueuses grâce à des collaborateurs productifs et des outils intelligents.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p105">[Microsoft Dynamics 365 for Project Service Automationhttps://www.microsoft.com/fr-FR/dynamics365/project-service-automation](https://www.microsoft.com/fr-FR/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="3aa00-117">Vous pouvez explorer l’un des éléments ci-dessus pour votre abonnement à la version d’évaluation de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guides de laboratoire de test dans Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="3aa00-119">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="3aa00-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="3aa00-120">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="3aa00-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="3aa00-121">Si vous souhaitez simplement tester Office 365 et Dynamics 365 avec une configuration minimale, suivez les instructions des étapes 2 et 3 de la rubrique [Environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="3aa00-121">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="3aa00-122">Si vous souhaitez tester Office 365 et Dynamics 365 dans une entreprise simulée, suivez les instructions de la rubrique [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="3aa00-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in Add DirSync to Your Office 365 Dev/Test Environment.</span></span>

![Environnement de développement/test Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="3aa00-p106">La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="3aa00-126">Phase 2 : Ajouter un abonnement à la version d’évaluation de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="3aa00-127">Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Dynamics 365 et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="3aa00-128">Inscription à un abonnement à la version d’évaluation de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="3aa00-129">En utilisant un navigateur sur votre ordinateur de bureau (simplifié) ou sur CLIENT1 (entreprise de simulation), connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide des informations d’identification de votre compte Administrateur général.</span><span class="sxs-lookup"><span data-stu-id="3aa00-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at  https://portal.office.com https://portal.office.com  with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="3aa00-130">Cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="3aa00-131">Sous l’onglet **Centre d’administration Office**, dans le volet de navigation de gauche, cliquez sur **Facturation > Acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-131">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="3aa00-p107">Dans la page **Acheter des services**, recherchez l’élément **Dynamics 365 Plan 1 Enterprise Edition**. Placez le curseur de la souris dessus et cliquez sur **Démarrer l’essai gratuit**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="3aa00-134">Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="3aa00-135">Dans la page **Réception de la commande**, cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-135">On the **Order receipt** page, click **Continue**.</span></span>

![Environnement de développement/test Office 365 et Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="3aa00-p108">L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="3aa00-140">Phase 3 : Attribuer des administrateurs système et des licences Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="3aa00-141">Lors de cette phrase, vous allez affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.</span><span class="sxs-lookup"><span data-stu-id="3aa00-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="3aa00-142">Suivez ces étapes pour affecter des licences Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="3aa00-143">Sous l’onglet **Centre d’administration Office**, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-143">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="3aa00-144">Dans la liste des utilisateurs actifs, sélectionnez votre compte Administrateur général, puis cliquez sur **Modifier** pour **Licences de produits**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="3aa00-145">	Dans le volet *\*Licences de produit*\*, activez la licence de produit pour *\*Dynamics 365 Plan 1 Enterprise Edition** en sélectionnant *\*Activer*\*, cliquez sur *\*Enregistrer*\*, puis cliquez deux fois sur *\*Fermer*\*.</span><span class="sxs-lookup"><span data-stu-id="3aa00-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="3aa00-146">Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="3aa00-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="3aa00-147">Fermez l’onglet **Centre d’administration Office**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-147">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="3aa00-148">Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="3aa00-149">Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-149">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="3aa00-150">Sur l’onglet **Centre d’administration Office**, cliquez sur **Centres d’administration** dans le volet de navigation de gauche, puis sur **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-150">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="3aa00-151">Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.</span><span class="sxs-lookup"><span data-stu-id="3aa00-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="3aa00-152">Sur l’onglet Dynamics 365, cliquez sur **Toutes ces options**, puis sur **Terminer l’installation**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="3aa00-153">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="3aa00-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="3aa00-p109">Une fois l’installation terminée, un tableau de bord Activité de ventes reposant sur des exemples de données inclus dans l’abonnement d’essai est affiché. Visionnez la **vidéo de présentation de l’essai**. Fermez la fenêtre de la vidéo lorsque vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="3aa00-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="3aa00-157">Dans la barre d’outils située en haut de l’écran, cliquez sur la flèche vers le bas en regard de **Ventes**, sur **Paramètres** puis sur **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="3aa00-158">Dans la page **Sécurité**, cliquez sur **Utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="3aa00-159">Dans la liste des utilisateurs, cliquez sur **Utilisateur 2**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="3aa00-160">Dans la barre d’outils, cliquez sur **Gérer les rôles**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="3aa00-161">Dans **Gérer les rôles**, cliquez sur **Administrateur système**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="3aa00-162">Dans la barre d’outils en haut de l’écran, cliquez sur **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="3aa00-163">Répétez les étapes 5 à 8 pour le compte Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="3aa00-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="3aa00-164">Fermez l’onglet **Utilisateur :User3**.</span><span class="sxs-lookup"><span data-stu-id="3aa00-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3aa00-165">Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="3aa00-166">Votre environnement de développement/test Office 365 et Dynamics 365 a maintenant :</span><span class="sxs-lookup"><span data-stu-id="3aa00-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="3aa00-167">Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3aa00-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="3aa00-168">Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser à la fois Office 365 Entreprise E5 et Dynamics 365, et sont également administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3aa00-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="3aa00-169">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="3aa00-169">Next step</span></span>

<span data-ttu-id="3aa00-170">Configurez Office 365 et Dynamics 365, et expliquez comment ils fonctionnent ensemble dans les boîtes aux lettres Exchange Online avec la rubrique relative à l’[intégration à Exchange Online de votre environnement de développement/test Office 365 et Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="3aa00-170">Configure and then demonstrate how  Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3aa00-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aa00-171">See Also</span></span>

[<span data-ttu-id="3aa00-172">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="3aa00-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="3aa00-173">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="3aa00-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="3aa00-174">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="3aa00-175">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="3aa00-176">Gestion des abonnements pour Dynamics 365 (en ligne)</span><span class="sxs-lookup"><span data-stu-id="3aa00-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="3aa00-177">Administration de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3aa00-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


