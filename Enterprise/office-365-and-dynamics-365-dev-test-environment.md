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
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.'
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="5d3d8-103">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="5d3d8-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="5d3d8-105">Suivez les instructions fournies dans cet article pour ajouter un abonnement à la version d’évaluation de Dynamics 365 à la même organisation que votre environnement de développement/test Office 365, créant ainsi un environnement de développement/test Office 365 et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Environnement de développement/test Office 365 et Dynamics 365](images/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="5d3d8-p101">Vous pouvez utiliser un abonnement à la version d’évaluation de Dynamics 365 afin de présenter les fonctionnalités de Dynamics 365. Les solutions suivantes sont comprises dans la version d’évaluation Enterprise Edition de Dynamics 365 Plan 1 :</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="5d3d8-p102">[Microsoft Dynamics 365 pour les ventes](https://www.microsoft.com/dynamics365/sales). Augmenter vos ventes avec automation et aide à la décision numérique aidant à vos commerciaux se concentrer et travailler plus efficacement.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="5d3d8-p103">[Microsoft Dynamics 365 pour le Service clientèle](https://www.microsoft.com/dynamics365/customer-service). Gagnez fidélité en donnant à vos agents les informations complètes et numérique aide à la décision que dont ils ont besoin pour fournir le service transparent.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="5d3d8-p104">[Microsoft Dynamics 365 pour le Service clientèle](https://www.microsoft.com/dynamics365/field-service). Contrôleur de l’appel de service en optimisant vos planifications, équipant votre personnel et à l’aide des outils prédictives pour augmenter la marge.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="5d3d8-p105">[Microsoft Dynamics 365 pour l’automatisation de Service Project](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Se termine correctement vos projets et créer des relations rentables avec les employés productifs et outils intelligents.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="5d3d8-117">Vous pouvez explorer l’un des éléments ci-dessus pour votre abonnement à la version d’évaluation de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guides de laboratoire de test dans Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="5d3d8-119">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="5d3d8-120">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="5d3d8-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="5d3d8-121">Si vous souhaitez uniquement tester Office 365 et Dynamics 365 dans une solution légère avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5d3d8-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5d3d8-122">Si vous souhaitez tester une entreprise simulée Dynamics 365 et Office 365, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5d3d8-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="5d3d8-p106">La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="5d3d8-126">Phase 2 : Ajouter un abonnement à la version d’évaluation de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="5d3d8-127">Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Dynamics 365 et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="5d3d8-128">Inscription à un abonnement à la version d’évaluation de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="5d3d8-129">Via un navigateur soit sur votre ordinateur de bureau (lightweight) ou à partir de CLIENT1 (entreprise en simulation), connectez-vous au portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="5d3d8-130">Cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="5d3d8-131">Dans l’onglet **Centre d’administration Office** , dans la navigation de gauche, cliquez sur **facturation > achat de services**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-131">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="5d3d8-p107">Dans la page **services d’achat** , recherchez l’élément **Dynamics 365 Plan 1 Enterprise Edition** . Placez le pointeur de la souris au-dessus de celle-ci, cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="5d3d8-134">Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="5d3d8-135">Dans la page **Réception de la commande**, cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-135">On the **Order receipt** page, click **Continue**.</span></span>

![Environnement de développement/test Office 365 et Dynamics 365](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="5d3d8-p108">L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="5d3d8-140">Phase 3 : Attribuer des administrateurs système et des licences Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="5d3d8-141">Lors de cette phrase, vous allez affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="5d3d8-142">Suivez ces étapes pour affecter des licences Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="5d3d8-143">Dans l’onglet **Centre d’administration Office** , cliquez sur **utilisateurs > utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-143">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="5d3d8-144">Dans la liste d’utilisateurs actifs, cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="5d3d8-145">Dans le volet de **licences** , activer la licence de produit pour **Dynamics 365 Plan 1 Enterprise Edition** **activé**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="5d3d8-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="5d3d8-146">Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="5d3d8-147">Fermez l’onglet **Centre d’administration Office** .</span><span class="sxs-lookup"><span data-stu-id="5d3d8-147">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="5d3d8-148">Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="5d3d8-149">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="5d3d8-150">Sous l’onglet **Centre d’administration d’Office** , dans la navigation de gauche, cliquez sur **Centre d’administration**, puis cliquez sur **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="5d3d8-151">Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="5d3d8-152">Sous l’onglet Dynamics 365, cliquez sur **tous ces éléments**, puis cliquez sur **le programme d’installation complète.**</span><span class="sxs-lookup"><span data-stu-id="5d3d8-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="5d3d8-153">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="5d3d8-p109">Lorsque le programme d’installation est terminée, il affiche un tableau de bord ventes activité basés sur des données qui fait partie de l’abonnement de piste. Prendre un certain temps pour afficher la **Bienvenue dans la version d’évaluation de votre** vidéo. Fermez la fenêtre vidéo lorsque vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="5d3d8-157">Dans la barre d’outils dans la partie supérieure, cliquez sur la flèche vers le bas en regard de **ventes**, cliquez sur **paramètres**, puis cliquez sur **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="5d3d8-158">Dans la page **sécurité** , cliquez sur **utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="5d3d8-159">Dans la liste des utilisateurs, cliquez sur **utilisateur 2**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="5d3d8-160">Dans la barre d’outils, cliquez sur **Gérer les rôles**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="5d3d8-161">**Gérer les rôles**, cliquez sur **Administrateur système**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="5d3d8-162">Dans la barre d’outils dans la partie supérieure, cliquez sur **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="5d3d8-163">Répétez les étapes 5 à 8 pour le compte Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="5d3d8-164">Fermer la **utilisateur : User3** onglet.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5d3d8-165">Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="5d3d8-166">Votre environnement de développement/test Office 365 et Dynamics 365 a maintenant :</span><span class="sxs-lookup"><span data-stu-id="5d3d8-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="5d3d8-167">Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="5d3d8-168">Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser à la fois Office 365 Entreprise E5 et Dynamics 365, et sont également administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="5d3d8-169">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="5d3d8-169">Next step</span></span>

<span data-ttu-id="5d3d8-170">Configurer et illustrer puis Office 365 et Dynamics 365 fonctionnement conjoint des boîtes aux lettres dans Exchange Online avec [l’intégration Exchange Online pour votre environnement de développement/test Dynamics 365 et Office 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="5d3d8-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d3d8-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d3d8-171">See Also</span></span>

[<span data-ttu-id="5d3d8-172">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="5d3d8-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5d3d8-173">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="5d3d8-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="5d3d8-174">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="5d3d8-175">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="5d3d8-176">Gestion des abonnements pour Dynamics 365 (en ligne)</span><span class="sxs-lookup"><span data-stu-id="5d3d8-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="5d3d8-177">Administration de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d3d8-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


