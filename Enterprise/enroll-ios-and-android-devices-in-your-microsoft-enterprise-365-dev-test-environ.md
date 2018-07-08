---
title: Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188102"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="ec487-103">Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="ec487-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="ec487-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.</span><span class="sxs-lookup"><span data-stu-id="ec487-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="ec487-p101">La Suite de mobilité Enterprise (EMS) Microsoft protège vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="ec487-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="ec487-p102">Si vous devez appliquer la sécurité au niveau du périphérique, les appareils doit s’inscrire dans Microsoft Intune. Inscription de périphérique non seulement vous aide à gérer les périphériques appartenant à l’organisation, mais également de personnel (BYOD) et des périphériques partagés, en fonction de votre organisation le juridique stratégies.</span><span class="sxs-lookup"><span data-stu-id="ec487-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="ec487-109">En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et tester les fonctionnalités de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ec487-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="ec487-110">Phase 1 : Créer votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ec487-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="ec487-111">Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ec487-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="ec487-112">Phase 2 : Inscrire vos périphériques iOS ou Android</span><span class="sxs-lookup"><span data-stu-id="ec487-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="ec487-113">Tout d’abord, suivez les instructions fournies dans [installer et se connecter à l’application de portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre client de développement/test.</span><span class="sxs-lookup"><span data-stu-id="ec487-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="ec487-114">Ensuite, suivez les instructions de [configurer l’accès aux ressources de votre société](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) à inscrire un périphérique iOS.</span><span class="sxs-lookup"><span data-stu-id="ec487-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="ec487-115">Ensuite, suivez les instructions dans [l’inscription de votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.</span><span class="sxs-lookup"><span data-stu-id="ec487-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="ec487-116">Phase 2 : Gérer vos périphériques iOS ou Android à distance</span><span class="sxs-lookup"><span data-stu-id="ec487-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="ec487-p103">Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le supprimer à distance.</span><span class="sxs-lookup"><span data-stu-id="ec487-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="ec487-120">Pour verrouiller un appareil iOS à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec487-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="ec487-121">Ouvrir un nouvel onglet et accédez à http://manage.microsoft.com (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="ec487-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="ec487-122">À partir de la console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans le volet de navigation gauche.</span><span class="sxs-lookup"><span data-stu-id="ec487-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="ec487-123">Dans le volet **Groupes**, ouvrez **Tous les périphériques > Tous les appareils mobiles > Tous les appareils gérés par gestion directe**.</span><span class="sxs-lookup"><span data-stu-id="ec487-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="ec487-124">Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.</span><span class="sxs-lookup"><span data-stu-id="ec487-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="ec487-125">Dans la liste des périphériques, cliquez sur votre appareil iOS. </span><span class="sxs-lookup"><span data-stu-id="ec487-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="ec487-126">À partir de votre appareil iOS, assurez-vous qu’il se trouve sur l’écran principal. </span><span class="sxs-lookup"><span data-stu-id="ec487-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="ec487-p104">À partir de votre ordinateur d’administration, dans la barre des tâches, cliquez sur **Tâches à distance > Verrouiller à distance**. Regardez votre appareil iOS lorsqu’il bascule vers l’écran de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="ec487-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="ec487-129">Pour supprimer le code secret, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec487-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="ec487-130">À partir de votre ordinateur d’administration, dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.</span><span class="sxs-lookup"><span data-stu-id="ec487-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="ec487-p105">Dans la liste, cliquez sur votre appareil iOS. Dans la barre des tâches, cliquez sur **Tâches à distance > Réinitialisation du code d’accès**. Patientez une minute.</span><span class="sxs-lookup"><span data-stu-id="ec487-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="ec487-p106">À partir de votre appareil iOS, déverrouillez-le et constatez qu’il n’y a plus de code secret. Pour modifier à nouveau le code secret, accédez à **Paramètres**, puis **Code secret**.</span><span class="sxs-lookup"><span data-stu-id="ec487-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="ec487-136">Pour verrouiller un appareil Android à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec487-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="ec487-137">À partir de la console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans le volet de navigation gauche.</span><span class="sxs-lookup"><span data-stu-id="ec487-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="ec487-138">Dans le volet **Groupes**, ouvrez **Tous les périphériques > Tous les appareils mobiles > Tous les appareils gérés par gestion directe**.</span><span class="sxs-lookup"><span data-stu-id="ec487-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="ec487-139">Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.</span><span class="sxs-lookup"><span data-stu-id="ec487-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="ec487-140">Dans la liste des périphériques, cliquez sur votre appareil Android. </span><span class="sxs-lookup"><span data-stu-id="ec487-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="ec487-141">À partir de votre appareil Android, assurez-vous qu’il se trouve sur l’écran principal. </span><span class="sxs-lookup"><span data-stu-id="ec487-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="ec487-p107">À partir de votre ordinateur d’administration, dans la barre des tâches, cliquez sur **Tâches à distance > Verrouiller à distance**. Lorsque vous y êtes invité, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="ec487-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="ec487-144">Regardez votre appareil Android lorsqu’il bascule vers l’écran de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="ec487-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="ec487-145">Lorsque vous réinitialisez le mot de passe pour les appareils Android, le portail d’administration Intune génère et configure un mot de passe fort.</span><span class="sxs-lookup"><span data-stu-id="ec487-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="ec487-146">Pour réinitialiser le code secret à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec487-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="ec487-147">À partir de votre ordinateur d’administration, sous l’onglet de la console d’administration Microsoft Intune de votre navigateur, dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur votre appareil Android.</span><span class="sxs-lookup"><span data-stu-id="ec487-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="ec487-148">Dans la barre des tâches, cliquez sur **Tâches à distance > Réinitialisation du code d’accès**.</span><span class="sxs-lookup"><span data-stu-id="ec487-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="ec487-p108">À l’invite **Tâche à distance : réinitialisation du code d’accès**, cliquez sur **Oui**. Patientez une minute.</span><span class="sxs-lookup"><span data-stu-id="ec487-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="ec487-151">Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Afficher les propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ec487-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="ec487-152">Sous **Réinitialisation du code d’accès**, notez le nouveau code secret.</span><span class="sxs-lookup"><span data-stu-id="ec487-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="ec487-153">Dans votre appareil Android, entrez le nouveau code secret à partir de l’écran de verrouillage. </span><span class="sxs-lookup"><span data-stu-id="ec487-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="ec487-154">Pour modifier à nouveau le code secret, accédez à **Paramètres**, appuyez sur **Appareil** et **Écran de verrouillage**, ressaisissez le nouveau mot de passe, appuyez sur **Écran de verrouillage**, puis choisissez le code secret.</span><span class="sxs-lookup"><span data-stu-id="ec487-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="ec487-155">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="ec487-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ec487-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec487-156">See Also</span></span>

[<span data-ttu-id="ec487-157">Environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="ec487-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="ec487-158">Stratégies GAM pour votre environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="ec487-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="ec487-159">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="ec487-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="ec487-160">Mobilité d’entreprise + sécurité (EMS)</span><span class="sxs-lookup"><span data-stu-id="ec487-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


