---
title: Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720410"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="11150-103">Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="11150-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="11150-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.</span><span class="sxs-lookup"><span data-stu-id="11150-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="11150-p101">La Suite de mobilité Enterprise (EMS) Microsoft protège vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="11150-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="11150-p102">Si vous devez appliquer la sécurité au niveau du périphérique, les appareils doit s’inscrire dans Microsoft Intune. Inscription de périphérique non seulement vous aide à gérer les périphériques appartenant à l’organisation, mais également de personnel (BYOD) et des périphériques partagés, en fonction de votre organisation le juridique stratégies.</span><span class="sxs-lookup"><span data-stu-id="11150-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="11150-109">En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et tester les fonctionnalités de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11150-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="11150-110">Phase 1 : Créer votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="11150-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="11150-111">Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="11150-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="11150-112">Phase 2 : Inscrire vos périphériques iOS ou Android</span><span class="sxs-lookup"><span data-stu-id="11150-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="11150-113">Tout d’abord, suivez les instructions fournies dans [installer et se connecter à l’application de portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre environnement de test.</span><span class="sxs-lookup"><span data-stu-id="11150-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="11150-114">Ensuite, suivez les instructions de [configurer l’accès aux ressources de votre société](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) à inscrire un périphérique iOS.</span><span class="sxs-lookup"><span data-stu-id="11150-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="11150-115">Ensuite, suivez les instructions dans [l’inscription de votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.</span><span class="sxs-lookup"><span data-stu-id="11150-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="11150-116">Phase 3 : Gérer vos périphériques iOS ou Android à distance</span><span class="sxs-lookup"><span data-stu-id="11150-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="11150-p103">Intune Microsoft fournit à distance verrouillage et code secret réinitialisation de fonctionnalités. Si une personne perd leur appareil, vous pouvez verrouiller le périphérique à distance. Si une personne oublie son code confidentiel, vous pouvez le réinitialiser à distance.</span><span class="sxs-lookup"><span data-stu-id="11150-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="11150-120">Pour verrouiller une iOS ou un appareil Android à distance :</span><span class="sxs-lookup"><span data-stu-id="11150-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="11150-121">Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="11150-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="11150-122">Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.</span><span class="sxs-lookup"><span data-stu-id="11150-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="11150-123">Cliquez sur **périphériques > tous les périphériques**.</span><span class="sxs-lookup"><span data-stu-id="11150-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="11150-124">Dans la liste des périphériques, cliquez sur un appareil Android ou sur iOS, puis cliquez sur l’action **Verrouiller à distance** .</span><span class="sxs-lookup"><span data-stu-id="11150-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="11150-125">Pour réinitialiser le code secret à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="11150-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="11150-126">Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="11150-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="11150-127">Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.</span><span class="sxs-lookup"><span data-stu-id="11150-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="11150-128">Cliquez sur **périphériques > tous les périphériques**.</span><span class="sxs-lookup"><span data-stu-id="11150-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="11150-p104">Dans la liste des périphériques gérer, cliquez sur un appareil Android ou sur iOS et choisissez **... Plus**. Puis sélectionnez l’action **Supprimer le code secret** périphérique à distance.</span><span class="sxs-lookup"><span data-stu-id="11150-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="11150-131">Pour une expérimentation supplémentaire, voir [actions de périphérique disponible](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="11150-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="11150-132">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="11150-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="11150-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11150-133">See Also</span></span>

[<span data-ttu-id="11150-134">Environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="11150-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="11150-135">Stratégies GAM pour votre environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="11150-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="11150-136">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="11150-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="11150-137">Mobilité d’entreprise + sécurité (EMS)</span><span class="sxs-lookup"><span data-stu-id="11150-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


