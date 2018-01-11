---
title: "Environnement de développement/test Microsoft Cloud unique"
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test qui inclut toutes les offres en nuage de Microsoft."
ms.openlocfilehash: 2cbfb3e963927f18d2ee46ed1f5076b274a99154
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="7b10c-103">Environnement de développement/test Microsoft Cloud unique</span><span class="sxs-lookup"><span data-stu-id="7b10c-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="7b10c-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test qui inclut toutes les offres en nuage de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7b10c-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="7b10c-p101">Les instructions fournies dans cet article vous permettent de créer un intranet simulé dans les services d’infrastructure de Microsoft Azure, puis d’ajouter des abonnements Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) et Microsoft Dynamics 365. Vous obtenez ainsi une organisation plus simple qui utilise toutes les offres cloud de Microsoft en même temps dans un environnement de développement/test unique. </span><span class="sxs-lookup"><span data-stu-id="7b10c-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="7b10c-108">Vous pouvez utiliser la configuration obtenue pour :</span><span class="sxs-lookup"><span data-stu-id="7b10c-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="7b10c-109">Bénéficier d’une intégration de toutes les offres cloud de Microsoft, telles que l’infrastructure d’identité commune fournies par Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="7b10c-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="7b10c-110">Évaluer des scénarios complets comprenant plusieurs offres Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="7b10c-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="7b10c-111">Créer une démonstration, une preuve de concept ou une configuration de développement/test qui utilise plusieurs offres Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="7b10c-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="7b10c-112">Développer vos compétences sur Microsoft Cloud à des fins de développement professionnel.</span><span class="sxs-lookup"><span data-stu-id="7b10c-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="7b10c-113">Phase 1 : Créer un intranet simulé et y ajouter Office 365</span><span class="sxs-lookup"><span data-stu-id="7b10c-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="7b10c-114">Suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7b10c-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7b10c-115">La figure 1 illustre votre configuration qui en résulte, ce qui inclut Office 365 et un intranet simulé en cours d’exécution dans les services d’infrastructure Azure et la synchronisation d’annuaire à partir d’une forêt de Windows Server Active Directory (AD) sur site.</span><span class="sxs-lookup"><span data-stu-id="7b10c-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="7b10c-116">**Figure 1 : L’intranet simulé dans Azure avec Office 365**</span><span class="sxs-lookup"><span data-stu-id="7b10c-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![Environnement de développement/test d’Office 365 avec DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="7b10c-p102">La version d’essai Azure est de 30 jours. L’abonnement d’évaluation de Office 365 entreprise E5 est de 30 jours, ce qui peut être facilement étendus pour un autre 30 jours. Pour un environnement de développement/test permanent, créer un nouveau payé l’abonnement Azure et un nouvel abonnement Office 365 entreprise E5 payé avec un petit nombre de licences.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="7b10c-121">Phase 2 : Ajouter EMS</span><span class="sxs-lookup"><span data-stu-id="7b10c-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="7b10c-122">Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation EMS et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="7b10c-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="7b10c-123">Avec un navigateur soit sur votre ordinateur de bureau ou à partir de CLIENT1, ouvrez une session sur le portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="7b10c-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="7b10c-124">Cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="7b10c-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="7b10c-125">Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="7b10c-p103">Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="7b10c-128">Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="7b10c-129">Dans la page **reçu de commande** , cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7b10c-p104">L’abonnement à la version d’évaluation d’Enterprise Mobility + Security E5 est de 90 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="7b10c-132">Ensuite, activez la licence Enterprise Mobility + Security E5 pour tous les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b10c-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="7b10c-133">Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="7b10c-134">Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="7b10c-135">Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="7b10c-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="7b10c-136">Pour tous vos autres comptes (Utilisateur 1, Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5), suivez les étapes 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="7b10c-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="7b10c-137">Votre environnement de développement/test comporte maintenant :</span><span class="sxs-lookup"><span data-stu-id="7b10c-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="7b10c-138">Un intranet simulé exécuté dans les services d’infrastructure Azure.</span><span class="sxs-lookup"><span data-stu-id="7b10c-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="7b10c-139">Des abonnements d’évaluation Office 365 E5 Entreprise et EMS qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b10c-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="7b10c-140">Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.</span><span class="sxs-lookup"><span data-stu-id="7b10c-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="7b10c-141">La figure 2 montre la configuration obtenue, qui ajoute EMS.</span><span class="sxs-lookup"><span data-stu-id="7b10c-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="7b10c-142">**Figure 2 : L’intranet simulé dans Azure avec Office 365 et EMS**</span><span class="sxs-lookup"><span data-stu-id="7b10c-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Phase 2 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365 et EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="7b10c-144">Phase 3 : Ajoutez Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="7b10c-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="7b10c-145">Dans cette phase, vous allez souscrire à l’abonnement d’évaluation Dynamics 365 et l’ajouter à la même organisation que vos abonnements d’évaluation Office 365 et EMS.</span><span class="sxs-lookup"><span data-stu-id="7b10c-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="7b10c-146">À l’aide d’un navigateur soit sur votre ordinateur de bureau ou à partir de CLIENT1, connectez-vous au portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="7b10c-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="7b10c-147">Cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="7b10c-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="7b10c-148">Dans l’onglet **Centre admin** , dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="7b10c-p105">Dans la page **services d’achat** , trouver l’élément de **Dynamics 365 Plan 1 Enterprise Edition** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="7b10c-151">Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="7b10c-152">Dans la page **reçu de commande** , cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7b10c-p106">L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="7b10c-156">Procédez comme suit pour affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.</span><span class="sxs-lookup"><span data-stu-id="7b10c-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="7b10c-157">Dans l’onglet **Centre admin** , cliquez sur **les utilisateurs > utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="7b10c-158">Dans la liste d’utilisateurs actifs, cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="7b10c-159">Dans le volet **des licences de produit** , activation de la licence du produit pour **Dynamics 365 Plan 1 Enterprise Edition** **sur**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="7b10c-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="7b10c-160">Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="7b10c-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="7b10c-161">Fermez l’onglet **Centre admin** .</span><span class="sxs-lookup"><span data-stu-id="7b10c-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="7b10c-162">Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="7b10c-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="7b10c-163">Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **Centre d’administration**, puis cliquez sur **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="7b10c-164">Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.</span><span class="sxs-lookup"><span data-stu-id="7b10c-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="7b10c-165">Sous l’onglet Dynamics 365, cliquez sur **tous**, puis cliquez sur **le programme d’installation terminé.**</span><span class="sxs-lookup"><span data-stu-id="7b10c-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="7b10c-166">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="7b10c-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="7b10c-p107">Lorsque l’installation est terminée, il affiche un tableau de bord d’activité de vente basés sur des données qui fait partie de l’abonnement de la piste. Prenez quelques instants pour afficher la **Bienvenue dans votre version d’évaluation** de vidéo. Fermez la fenêtre de la vidéo lorsque vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="7b10c-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="7b10c-170">Dans la barre d’outils en haut, cliquez sur la flèche en regard de **ventes**, cliquez sur **paramètres**, puis cliquez sur **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="7b10c-171">Dans la page **sécurité** , cliquez sur **utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="7b10c-172">Dans la liste des utilisateurs, cliquez sur **utilisateur 2**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="7b10c-173">Dans la barre d’outils, cliquez sur **Gérer les rôles**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="7b10c-174">**Gérer les rôles**, cliquez sur **Administrateur système**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="7b10c-175">Dans la barre d’outils en haut, cliquez sur **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="7b10c-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="7b10c-176">Répétez les étapes 5 à 8 pour le compte Utilisateur 3.</span><span class="sxs-lookup"><span data-stu-id="7b10c-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="7b10c-177">Fermer la **utilisateur : l’util_3** onglet.</span><span class="sxs-lookup"><span data-stu-id="7b10c-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7b10c-178">Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="7b10c-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="7b10c-179">Votre environnement de développement/test comporte maintenant :</span><span class="sxs-lookup"><span data-stu-id="7b10c-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="7b10c-180">Un intranet simulé exécuté dans les services d’infrastructure Azure.</span><span class="sxs-lookup"><span data-stu-id="7b10c-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="7b10c-181">Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise, d’EMS et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b10c-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="7b10c-182">Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.</span><span class="sxs-lookup"><span data-stu-id="7b10c-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="7b10c-183">Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser Dynamics 365, et sont également administrateurs système de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="7b10c-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="7b10c-184">La figure 3 présente la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="7b10c-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="7b10c-185">**Figure 3 : L’intranet simulé dans Azure avec Office 365, EMS et Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="7b10c-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="7b10c-187">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7b10c-187">Next steps</span></span>

<span data-ttu-id="7b10c-p108">Vous pouvez maintenant tester différentes configurations avec votre environnement de développement/test Microsoft Cloud. Voici quelques suggestions pour vous guider :</span><span class="sxs-lookup"><span data-stu-id="7b10c-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="7b10c-190">Configurer des stratégies de management (MAM) d’une application mobile dans EMS pour les applications d’Office 365</span><span class="sxs-lookup"><span data-stu-id="7b10c-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="7b10c-191">Montrer Exchange Online dans Office 365 une intégration avec les contacts de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="7b10c-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="7b10c-192">Créer un réseau simulé coexistence dans les services d’infrastructure Azure pour l’hébergement des charges de travail basé sur serveur</span><span class="sxs-lookup"><span data-stu-id="7b10c-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="7b10c-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b10c-193">See Also</span></span>

[<span data-ttu-id="7b10c-194">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="7b10c-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7b10c-195">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="7b10c-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="7b10c-196">Solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="7b10c-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="7b10c-197">Solutions de sécurité</span><span class="sxs-lookup"><span data-stu-id="7b10c-197">Security solutions</span></span>](security-solutions.md)





