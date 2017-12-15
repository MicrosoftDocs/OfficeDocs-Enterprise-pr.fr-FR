---
title: "Authentification multifacteur pour votre environnement de développement/test Office 365"
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
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- mar17entnews
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Résumé : Configurer plusieurs facteurs d’authentification à l’aide de messages textuels envoyés sur un téléphone intelligent dans un environnement de développement/test d’Office 365."
ms.openlocfilehash: 87fdcc2ccd910e8da399e14d37fe3d0d1f0a66d4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="749fc-103">Authentification multifacteur pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="749fc-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="749fc-104">**Résumé :** Configurer plusieurs facteurs d’authentification à l’aide de messages textuels envoyés sur un téléphone intelligent dans un environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="749fc-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="749fc-p101">Pour bénéficier d’un niveau supplémentaire de sécurité lors de la connexion à votre abonnement Office 365, vous pouvez activer l’authentification multifacteur Azure, qui exige davantage qu’un simple nom d’utilisateur et mot de passe pour vérifier un compte. Avec l’authentification multifacteur pour Office 365, les utilisateurs sont tenus de confirmer la bonne réception d’un appel téléphonique, de taper un code de vérification envoyé dans un message texte ou de spécifier un mot de passe d’application sur leur smartphone après avoir entré correctement leur mot de passe. Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté. </span><span class="sxs-lookup"><span data-stu-id="749fc-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to verify an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="749fc-108">Cet article décrit comment activer et tester l’authentification basée sur message texte pour un compte Office 365 spécifique.</span><span class="sxs-lookup"><span data-stu-id="749fc-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="749fc-109">Il existe deux phases de configuration de l’authentification multifacteur pour Office 365 dans un environnement de développement/test :</span><span class="sxs-lookup"><span data-stu-id="749fc-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="749fc-110">Créez l’environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="749fc-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="749fc-111">Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.</span><span class="sxs-lookup"><span data-stu-id="749fc-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="749fc-112">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="749fc-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="749fc-113">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="749fc-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="749fc-114">Si vous souhaitez juste tester plusieurs facteurs d’authentification d’une façon légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="749fc-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="749fc-115">Si vous souhaitez tester une authentification multifactorielle dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="749fc-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="749fc-p102">Le test de l’authentification multifacteur ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="749fc-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="749fc-118">Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2</span><span class="sxs-lookup"><span data-stu-id="749fc-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="749fc-119">Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="749fc-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="749fc-120">Ouvrir une autre instance de votre navigateur et accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) puis connectez-vous à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="749fc-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="749fc-121">À partir de la page principale du portail, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="749fc-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="749fc-122">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="749fc-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="749fc-123">Dans le volet utilisateurs actifs, cliquez sur **plus > installation Azure multi-facteurs auth**.</span><span class="sxs-lookup"><span data-stu-id="749fc-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="749fc-124">Dans la liste, cliquez sur le compte de **l’utilisateur 2** .</span><span class="sxs-lookup"><span data-stu-id="749fc-124">In the list, click the **User 2** account.</span></span>
    
6. <span data-ttu-id="749fc-125">Dans la section **2 de l’utilisateur** , sous **étapes rapides**, cliquez sur **Activer**.</span><span class="sxs-lookup"><span data-stu-id="749fc-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="749fc-126">Dans la boîte de dialogue **sur l’activation de plusieurs facteur auth** , cliquez sur **Activer l’authentification de plusieurs facteur**.</span><span class="sxs-lookup"><span data-stu-id="749fc-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="749fc-127">Dans la boîte de dialogue **mise à jour réussie** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="749fc-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="749fc-128">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de compte utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="749fc-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="749fc-129">Fermez l’instance de navigateur.</span><span class="sxs-lookup"><span data-stu-id="749fc-129">Close your browser instance.</span></span>
    
<span data-ttu-id="749fc-130">Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="749fc-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="749fc-131">Ouvrez une nouvelle instance de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="749fc-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="749fc-132">Accédez au portail d’Office 365 ([https://portal.office.com](https://portal.office.com)) et connectez-vous avec le compte d’utilisateur 2 (Utilisateur2 @\<nom de l’organisation >. onmicrosoft.com) et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="749fc-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="749fc-p103">Après l’ouverture de session, vous êtes invité à configurer le compte pour la validation de la sécurité supplémentaires. Cliquez sur **Installer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="749fc-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="749fc-135">Dans la page **vérification de la sécurité supplémentaires** :</span><span class="sxs-lookup"><span data-stu-id="749fc-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="749fc-136">Sélectionnez le pays ou la région.</span><span class="sxs-lookup"><span data-stu-id="749fc-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="749fc-137">Tapez le numéro de téléphone du smartphone qui recevra les SMS.</span><span class="sxs-lookup"><span data-stu-id="749fc-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="749fc-138">Sélectionnez **M’envoyer un code par message texte**.</span><span class="sxs-lookup"><span data-stu-id="749fc-138">Select **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="749fc-139">Cliquez sur **Contact**.</span><span class="sxs-lookup"><span data-stu-id="749fc-139">Click **Contact me**.</span></span>
    
6. <span data-ttu-id="749fc-140">Saisissez le code de vérification dans le message reçu sur votre téléphone intelligent, puis cliquez sur **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="749fc-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="749fc-141">Sur le **étape 3 : conserver vos applications existantes** la page Enregistrer le mot de passe d’application affichée pour le compte de l’utilisateur 2 dans un emplacement sécurisé et puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="749fc-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="749fc-142">Sur la page de connexion, tapez le mot de passe pour le compte de l’utilisateur 2, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="749fc-142">Back on the sign-in page, type the password for the User 2 account and click **Sign in**.</span></span>
    
9. <span data-ttu-id="749fc-143">Saisissez le code de vérification dans le message reçu sur votre téléphone intelligent, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="749fc-143">Enter the verification code from the text message received on your smart phone, and then click **Sign in**.</span></span>
    
10. <span data-ttu-id="749fc-p104">Si c’est la première fois vous connecté avec le compte de l’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe deux fois, puis cliquez sur **mettre à jour le mot de passe et connectez-vous**. Enregistrer le nouveau mot de passe dans un endroit sûr.</span><span class="sxs-lookup"><span data-stu-id="749fc-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="749fc-147">Vous devriez voir le portail Office 365 pour l’utilisateur 2.</span><span class="sxs-lookup"><span data-stu-id="749fc-147">You should see the Office 365 portal for User 2.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="749fc-148">See Also</span><span class="sxs-lookup"><span data-stu-id="749fc-148">See Also</span></span>

[<span data-ttu-id="749fc-149">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="749fc-149">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="749fc-150">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="749fc-150">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="749fc-151">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="749fc-151">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="749fc-152">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="749fc-152">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="749fc-153">Plan d’authentification à plusieurs facteurs pour les déploiements d’Office 365</span><span class="sxs-lookup"><span data-stu-id="749fc-153">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

