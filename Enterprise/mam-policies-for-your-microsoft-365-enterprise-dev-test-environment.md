---
title: Stratégies MAM pour votre environnement de développement/test Microsoft 365 pour entreprises
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de gestion (MAM) EMS application mobile à votre environnement de développement/test Microsoft 365.'
ms.openlocfilehash: 1d4ede9b5757d4adce8909586790bcad51f7433f
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="76012-103">Stratégies MAM pour votre environnement de développement/test Microsoft 365 pour entreprises</span><span class="sxs-lookup"><span data-stu-id="76012-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="76012-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de gestion (MAM) EMS application mobile à votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="76012-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="76012-p101">La mobilité d’entreprise Microsoft + la sécurité (EMS) permet de conserver vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="76012-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="76012-107">Avec les instructions de cet article, vous ajoutez des stratégies de gestion (MAM) des applications mobiles pour votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="76012-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="76012-108">Phase 1 : Création de votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="76012-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="76012-109">Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76012-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="76012-110">Phase 2 : Créer et déployer des stratégies de gestion des applications mobiles pour les appareils iOS et Android</span><span class="sxs-lookup"><span data-stu-id="76012-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="76012-111">Dans cette phase, vous créez et déployez deux stratégies de gestion des applications mobiles différentes : une pour les appareils iOS et une pour les appareils Android.</span><span class="sxs-lookup"><span data-stu-id="76012-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="76012-112">Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="76012-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="76012-113">Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure ([https://azure.portal.com](https://azure.portal.com)) et connectez-vous à l’aide de votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="76012-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="76012-114">Sous l’onglet portail Azure dans Internet Explorer, dans le volet de navigation, cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.</span><span class="sxs-lookup"><span data-stu-id="76012-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **All services**, type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="76012-115">Dans le volet de navigation gauche, cliquez sur **Groupes**.</span><span class="sxs-lookup"><span data-stu-id="76012-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="76012-116">Sur le serveur lame **groupes de groupes** , cliquez sur **+ Nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="76012-116">On the **Groups-All groups** blade, click **+ New Group**.</span></span>
    
6. <span data-ttu-id="76012-117">Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **gérées les utilisateurs d’appareils iOS** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**et puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-117">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span> 
    
7. <span data-ttu-id="76012-118">Fermez la lame de **groupe** .</span><span class="sxs-lookup"><span data-stu-id="76012-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="76012-119">Sur le serveur lame **groupes de groupes** , cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="76012-119">On the **Groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="76012-120">Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **utilisateur d’un appareil Android gérés** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-120">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed Android device user** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span>
    
10. <span data-ttu-id="76012-121">Fermez la lame de **groupes de groupes** .</span><span class="sxs-lookup"><span data-stu-id="76012-121">Close the **Groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="76012-122">Dans la lame **Intune** , dans la liste des **tâches rapides** , cliquez sur **créer une stratégie de conformité**.</span><span class="sxs-lookup"><span data-stu-id="76012-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="76012-123">Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="76012-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="76012-p102">Sur le serveur lame **Créer une stratégie** , dans **nom**, tapez **iOS**. Dans la **plateforme**, sélectionnez **iOS**, cliquez sur **OK** dans la **stratégie de conformité iOS** lame, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="76012-126">Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="76012-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="76012-p103">Sur le serveur lame **Créer une stratégie** , dans **nom**, tapez **Android**. Dans la **plateforme**, sélectionnez **Android**, cliquez sur **OK** dans la **stratégie de conformité Android** lame, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="76012-129">Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **Android** .</span><span class="sxs-lookup"><span data-stu-id="76012-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="76012-130">Dans la navigation de gauche de la lame **Android - propriétés** , cliquez sur **les affectations**, puis cliquez sur **Sélectionner des groupes**.</span><span class="sxs-lookup"><span data-stu-id="76012-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="76012-131">Sur le serveur lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils Android géré** , puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="76012-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="76012-132">Cliquez sur **Enregistrer**, puis fermez la lame **Android - affectations** .</span><span class="sxs-lookup"><span data-stu-id="76012-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="76012-133">Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **iOS** .</span><span class="sxs-lookup"><span data-stu-id="76012-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="76012-134">Dans la navigation de gauche de la lame **iOS - propriétés** , cliquez sur **les affectations**, puis cliquez sur **Sélectionner des groupes**.</span><span class="sxs-lookup"><span data-stu-id="76012-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="76012-135">Sur le serveur lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils iOS géré** , puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="76012-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="76012-136">Cliquez sur **Enregistrer**, puis fermez la lame **iOS - affectations** .</span><span class="sxs-lookup"><span data-stu-id="76012-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="76012-137">Fermez la lame de **Profils de stratégie de conformité** .</span><span class="sxs-lookup"><span data-stu-id="76012-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="76012-138">Sur le serveur lame **Intune** , cliquez sur **Gérer les applications** dans le volet de navigation gauche.</span><span class="sxs-lookup"><span data-stu-id="76012-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="76012-139">Sur le serveur lame **Applications Mobile** , cliquez sur **applications**.</span><span class="sxs-lookup"><span data-stu-id="76012-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="76012-140">Dans la liste des applications, cliquez sur **PowerPoint**,</span><span class="sxs-lookup"><span data-stu-id="76012-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="76012-p104">Sur le serveur lame **Présentation PowerPoint** , cliquez sur **affectations > sélectionnez Groupes > périphériques iOS gérés > sélectionnez**. Dans **Type**, sélectionnez **disponible**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="76012-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="76012-143">Répétez l’étape 28 pour les applications suivantes :</span><span class="sxs-lookup"><span data-stu-id="76012-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="76012-144">Outlook pour Android</span><span class="sxs-lookup"><span data-stu-id="76012-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="76012-145">Word pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-145">Word for iOS</span></span>
    
  - <span data-ttu-id="76012-146">Excel pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="76012-147">Outlook pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="76012-148">Microsoft Dynamics CRM sur iPad pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="76012-149">Microsoft Dynamics CRM sur iPhone pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="76012-150">Dynamics CRM pour les téléphones Android</span><span class="sxs-lookup"><span data-stu-id="76012-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="76012-151">Dynamics CRM pour les tablettes Android</span><span class="sxs-lookup"><span data-stu-id="76012-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="76012-152">Excel pour Android</span><span class="sxs-lookup"><span data-stu-id="76012-152">Excel for Android</span></span>
    
  - <span data-ttu-id="76012-153">Word pour Android</span><span class="sxs-lookup"><span data-stu-id="76012-153">Word for Android</span></span>
    
  - <span data-ttu-id="76012-154">OneNote pour iOS</span><span class="sxs-lookup"><span data-stu-id="76012-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="76012-155">Fermez la lame **Applications Mobile - applications** .</span><span class="sxs-lookup"><span data-stu-id="76012-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="76012-156">Sur le serveur lame **Applications Mobile** , cliquez sur **Stratégies de Protection des applications**.</span><span class="sxs-lookup"><span data-stu-id="76012-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="76012-157">Sur le serveur lame de **Stratégies de Protection des applications** , cliquez sur **Ajouter une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="76012-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="76012-158">Sur le serveur lame **Ajouter une stratégie** , tapez **iOS**, puis cliquez sur **Sélectionner les applications nécessaires**.</span><span class="sxs-lookup"><span data-stu-id="76012-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="76012-159">Sur le serveur lame **applications** , cliquez sur **PowerPoint**, **Microsoft Dynamics CRM sur iPhone**, **Excel**, **Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote**, **Outlook**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="76012-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="76012-160">Sur le serveur lame **Ajouter une stratégie** , cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="76012-161">Sur le serveur lame de **Stratégies de Protection des applications** , cliquez sur **Ajouter une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="76012-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="76012-162">Sur le serveur lame **Ajouter une stratégie** , tapez **Android**, sélectionnez **Android** de **plateforme**, puis cliquez sur **Sélectionner les applications requises**.</span><span class="sxs-lookup"><span data-stu-id="76012-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="76012-163">Sur le serveur lame **applications** , cliquez sur **Dynamics CRM pour tablettes**, **PowerPoint**, **Excel**, **Word**, **Outlook**et **Dynamics CRM pour les téléphones**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="76012-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="76012-164">Sur le serveur lame **Ajouter une stratégie** , cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="76012-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="76012-165">Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="76012-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="76012-166">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="76012-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76012-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76012-167">See Also</span></span>

[<span data-ttu-id="76012-168">Environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="76012-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="76012-169">Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="76012-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="76012-170">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="76012-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="76012-171">Mobilité d’entreprise + sécurité (EMS)</span><span class="sxs-lookup"><span data-stu-id="76012-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


