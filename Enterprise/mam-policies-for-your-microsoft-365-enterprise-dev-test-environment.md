---
title: "Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de EMS mobile application management (MAM) à votre environnement de développement/test Microsoft 365."
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="89b07-103">Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="89b07-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="89b07-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de EMS mobile application management (MAM) à votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="89b07-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="89b07-p101">La mobilité d’entreprise Microsoft + sécurité (EMS) permet à votre personnel gagne en productivité tout en protégeant les données de votre organisation à l’aide de leurs applications favorites et leurs périphériques. Pour plus d’informations, reportez-vous à la section [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="89b07-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="89b07-107">Avec les instructions de cet article, vous ajoutez des stratégies de management (MAM) d’application mobile à votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="89b07-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="89b07-108">Phase 1 : Créer votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="89b07-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="89b07-109">Suivez les instructions dans [l’environnement de développement/test de l’entreprise de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="89b07-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="89b07-110">Phase 2 : Créer et déployer des stratégies de gestion des applications mobiles pour les appareils iOS et Android</span><span class="sxs-lookup"><span data-stu-id="89b07-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="89b07-111">Dans cette phase, vous créez et déployez deux stratégies de gestion des applications mobiles différentes : une pour les appareils iOS et une pour les appareils Android.</span><span class="sxs-lookup"><span data-stu-id="89b07-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="89b07-112">Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="89b07-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="89b07-113">Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure ([https://azure.portal.com](https://azure.portal.com)) et connectez-vous en utilisant votre compte d’administrateur global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="89b07-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="89b07-114">Sous l’onglet portail Azure dans Internet Explorer, dans le volet de navigation, cliquez sur **plus de services** (ou sur la flèche vers la droite), tapez **Intune**, puis cliquez sur **Intune**.</span><span class="sxs-lookup"><span data-stu-id="89b07-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="89b07-115">Dans le volet de navigation gauche, cliquez sur **Groupes**.</span><span class="sxs-lookup"><span data-stu-id="89b07-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="89b07-116">Sur la blade **d’utilisateurs et des groupes de groupes** , cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="89b07-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="89b07-117">Sur la lame de **groupe** , tapez **Gestion des utilisateurs de périphériques d’e/s** dans la zone **nom**, sélectionnez **assigné** dans le **type d’abonnement**, sélectionnez **Oui** pour **les fonctionnalités activer Office ?**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="89b07-118">Fermez la lame du **groupe** .</span><span class="sxs-lookup"><span data-stu-id="89b07-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="89b07-119">Sur la blade **d’utilisateurs et des groupes de groupes** , cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="89b07-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="89b07-120">Sur la lame de **groupe** , tapez **utilisateurs de périphériques gérés Android** dans la zone **nom**, sélectionnez **assigné** dans le **type d’abonnement**, sélectionnez **Oui** pour **les fonctionnalités activer Office ?**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="89b07-121">Fermez la blade **d’utilisateurs et des groupes de groupes** .</span><span class="sxs-lookup"><span data-stu-id="89b07-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="89b07-122">Sur la lame **Intune** , dans la liste des **tâches rapides** , cliquez sur **créer une stratégie de conformité**.</span><span class="sxs-lookup"><span data-stu-id="89b07-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="89b07-123">Sur la lame de **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="89b07-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="89b07-p102">Sur la lame de **Créer une stratégie** , dans la zone **nom**, tapez **iOS**. Dans la **plate-forme**, sélectionnez **iOS**, cliquez sur **OK** sur la lame de la **stratégie de conformité d’e/s** , puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="89b07-126">Sur la lame de **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="89b07-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="89b07-p103">Sur la lame de **Créer une stratégie** , dans la zone **nom**, tapez **Android**. Dans la **plate-forme**, sélectionnez **Android**, cliquez sur **OK** sur la lame de la **stratégie de conformité Android** et puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="89b07-129">La lame de **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **Android** .</span><span class="sxs-lookup"><span data-stu-id="89b07-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="89b07-130">Dans la navigation gauche de la lame **Android - propriétés** , cliquez sur **affectations**, puis cliquez sur **Sélectionner des groupes**.</span><span class="sxs-lookup"><span data-stu-id="89b07-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="89b07-131">Sur la lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs de périphériques gérés Android** , puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="89b07-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="89b07-132">Cliquez sur **Enregistrer**et fermez la lame **Android - affectations** .</span><span class="sxs-lookup"><span data-stu-id="89b07-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="89b07-133">La lame de **Profils de stratégie de conformité** , cliquez sur le nom de la stratégie **e/s** .</span><span class="sxs-lookup"><span data-stu-id="89b07-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="89b07-134">Dans la navigation gauche de la lame **d’iOS - propriétés** , cliquez sur **affectations**, puis cliquez sur **Sélectionner des groupes**.</span><span class="sxs-lookup"><span data-stu-id="89b07-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="89b07-135">Sur la lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils iOS gérés** , puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="89b07-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="89b07-136">Cliquez sur **Enregistrer**et fermez la lame **iOS - affectations** .</span><span class="sxs-lookup"><span data-stu-id="89b07-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="89b07-137">Fermez la lame de **Profils de stratégie de conformité** .</span><span class="sxs-lookup"><span data-stu-id="89b07-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="89b07-138">Sur la lame **Intune** , cliquez sur **Gérer les applications** de la navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="89b07-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="89b07-139">Sur la blade **d’Applications Mobile** , cliquez sur **applications**.</span><span class="sxs-lookup"><span data-stu-id="89b07-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="89b07-140">Dans la liste des applications, cliquez sur **PowerPoint**,</span><span class="sxs-lookup"><span data-stu-id="89b07-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="89b07-p104">Sur la lame de **Présentation de PowerPoint** , cliquez sur **les affectations > sélectionnez Groupes > périphériques d’e/s gérés > sélectionnez**. Dans **Type**, sélectionnez **disponible**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="89b07-143">Répétez l’étape 28 pour les applications suivantes :</span><span class="sxs-lookup"><span data-stu-id="89b07-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="89b07-144">Outlook pour Android</span><span class="sxs-lookup"><span data-stu-id="89b07-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="89b07-145">Word pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-145">Word for iOS</span></span>
    
  - <span data-ttu-id="89b07-146">Excel pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="89b07-147">Outlook pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="89b07-148">Microsoft Dynamics CRM sur iPad pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="89b07-149">Microsoft Dynamics CRM sur iPhone pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="89b07-150">Dynamics CRM pour les téléphones Android</span><span class="sxs-lookup"><span data-stu-id="89b07-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="89b07-151">Dynamics CRM pour les tablettes Android</span><span class="sxs-lookup"><span data-stu-id="89b07-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="89b07-152">Excel pour Android</span><span class="sxs-lookup"><span data-stu-id="89b07-152">Excel for Android</span></span>
    
  - <span data-ttu-id="89b07-153">Word pour Android</span><span class="sxs-lookup"><span data-stu-id="89b07-153">Word for Android</span></span>
    
  - <span data-ttu-id="89b07-154">OneNote pour iOS</span><span class="sxs-lookup"><span data-stu-id="89b07-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="89b07-155">Fermez la lame **Mobile Apps - applications** .</span><span class="sxs-lookup"><span data-stu-id="89b07-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="89b07-156">Sur la blade **d’Applications Mobile** , cliquez sur **Stratégies de Protection d’application**.</span><span class="sxs-lookup"><span data-stu-id="89b07-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="89b07-157">Sur la lame de **Stratégies de Protection d’application** , cliquez sur **Ajouter une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="89b07-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="89b07-158">Sur la blade **d’Ajouter une stratégie** , tapez **e/s**, puis cliquez sur **Sélectionner les applications requises**.</span><span class="sxs-lookup"><span data-stu-id="89b07-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="89b07-159">Sur la blade **d’applications** , cliquez sur **PowerPoint**, **De Microsoft Dynamics CRM sur iPhone**, **Excel**, **De Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote**, **Outlook**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="89b07-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="89b07-160">Sur la blade **d’Ajouter une stratégie** , cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="89b07-161">Sur la lame de **Stratégies de Protection d’application** , cliquez sur **Ajouter une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="89b07-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="89b07-162">Sur la blade **d’Ajouter une stratégie** , tapez **Android**, sélectionnez **Android** dans la **plate-forme**, puis cliquez sur **Sélectionnez les applications requises**.</span><span class="sxs-lookup"><span data-stu-id="89b07-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="89b07-163">Sur la blade **d’applications** , cliquez sur **Dynamics CRM pour tablette**, **PowerPoint**, **Excel**, **Word**, **Outlook**et **Dynamics CRM pour les téléphones**et puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="89b07-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="89b07-164">Sur la blade **d’Ajouter une stratégie** , cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="89b07-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="89b07-165">Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="89b07-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="89b07-166">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="89b07-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89b07-167">See Also</span><span class="sxs-lookup"><span data-stu-id="89b07-167">See Also</span></span>

[<span data-ttu-id="89b07-168">L’environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="89b07-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="89b07-169">Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="89b07-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="89b07-170">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="89b07-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="89b07-171">Mobilité d’entreprise + sécurité (EMS)</span><span class="sxs-lookup"><span data-stu-id="89b07-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


