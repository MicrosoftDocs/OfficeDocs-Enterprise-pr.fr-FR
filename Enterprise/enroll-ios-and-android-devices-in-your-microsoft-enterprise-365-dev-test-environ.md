---
title: "Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365"
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques de votre environnement de développement/test Microsoft 365 et de les gérer à distance."
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="98c86-103">Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="98c86-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="98c86-104">**Résumé :** Ce Guide de laboratoire de Test permet d’inscrire des périphériques de votre environnement de développement/test Microsoft 365 et de les gérer à distance.</span><span class="sxs-lookup"><span data-stu-id="98c86-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="98c86-p101">La Suite de mobilité entreprise (EMS) de Microsoft permet à votre personnel gagne en productivité tout en protégeant les données de votre organisation à l’aide de leurs applications favorites et leurs périphériques. Pour plus d’informations, reportez-vous à la section [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="98c86-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="98c86-p102">Si vous avez besoin d’appliquer la sécurité au niveau de l’appareil, vous devez inscrire vos appareils auprès de Microsoft Intune. L’inscription d’appareil vous permet non seulement de gérer les périphériques appartenant à l’entreprise, mais également les périphériques personnels (BYOD) et partagés, en fonction des stratégies juridiques de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="98c86-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="98c86-109">En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et à tester les fonctions de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="98c86-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="98c86-110">Phase 1 : Créer votre environnement de développement/test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="98c86-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="98c86-111">Suivez les instructions dans [l’environnement de développement/test de l’entreprise de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="98c86-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="98c86-112">Phase 2 : Personnalisation de l’application de portail d’entreprise Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="98c86-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="98c86-113">Utilisez ces étapes pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre société fictive :</span><span class="sxs-lookup"><span data-stu-id="98c86-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="98c86-114">Dans un nouvel onglet, ouvrez la console d’administration Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="98c86-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="98c86-115">Cliquez sur **Admin** dans le volet de navigation, puis cliquez sur **Gestion des périphériques mobiles** dans le volet de **l’Administration** .</span><span class="sxs-lookup"><span data-stu-id="98c86-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="98c86-p103">Dans la liste des **tâches** , sélectionnez **l’Autorité de gestion de périphérique Mobile défini**. Assurez-vous qu’elle est définie sur **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="98c86-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="98c86-118">Dans le volet **d’Administration** , cliquez sur **Portail d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="98c86-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="98c86-119">Dans le volet de **Portail d’entreprise** , configurez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="98c86-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="98c86-120">Nom de la société : \<nom de votre société fictive ></span><span class="sxs-lookup"><span data-stu-id="98c86-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="98c86-121">Nom de contact de département informatique : **User5**</span><span class="sxs-lookup"><span data-stu-id="98c86-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="98c86-122">Numéro de téléphone du service informatique : **555-1234**</span><span class="sxs-lookup"><span data-stu-id="98c86-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="98c86-123">Adresse de messagerie du service informatique : **User5 @**\<nom de l’organisation fictive > **. onmicrosoft.com** (l’adresse de messagerie du compte User5)</span><span class="sxs-lookup"><span data-stu-id="98c86-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="98c86-124">Dans une **personnalisation**, sélectionnez **vert** dans la **couleur de thème**.</span><span class="sxs-lookup"><span data-stu-id="98c86-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="98c86-125">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-125">Click **Save**.</span></span>
    
<span data-ttu-id="98c86-126">Ensuite, vous installez l’application de portail d’entreprise Microsoft Intune et inscrivez un appareil iOS ou Android, puis testez les fonctionnalités de gestion de base à partir de la console d’administration Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="98c86-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="98c86-127">Phase 3 (pour les appareils iOS uniquement) : Inscription et gestion d’un appareil iOS</span><span class="sxs-lookup"><span data-stu-id="98c86-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="98c86-128">Pour inscrire un appareil iOS à gérer avec Intune, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="98c86-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="98c86-129">Un appareil iOS, comme un iPad ou iPhone.</span><span class="sxs-lookup"><span data-stu-id="98c86-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="98c86-130">Connaissance du mot de passe du périphérique iOS.</span><span class="sxs-lookup"><span data-stu-id="98c86-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="98c86-p104">Un ID de Apple (un nom de compte et le mot de passe). Si vous n’en avez pas encore, rendez-vous sur le [site Web de Apple ID](https://appleid.apple.com/#!&amp;page=signin) et cliquez sur **créer votre ID d’Apple**. Créer un ID d’Apple correspondant au compte d’administrateur global de votre abonnement à Office 365. Enregistrer votre nouveau nom de compte Apple ID et le mot de passe dans un endroit sûr.</span><span class="sxs-lookup"><span data-stu-id="98c86-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="98c86-p105">Un certificat de services de notifications push Apple (APN) est nécessaire pour qu’Intune puisse gérer les appareils iOS et Mac. Une fois le certificat ajouté à Intune, les utilisateurs peuvent installer l’application de portail d’entreprise Microsoft Intune pour inscrire leurs appareils, ou l’administrateur peut configurer la gestion des appareils iOS appartenant à l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="98c86-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="98c86-p106">Vous avez besoin d’un fichier de demande de signature de certificat pour demander un certificat de relation de confiance à partir du portail de certificats Push Apple. Pour obtenir un fichier de requête de signature de certificat, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="98c86-139">Dans la console d’administration Microsoft Intune, cliquez sur **Admin** dans le volet de navigation.</span><span class="sxs-lookup"><span data-stu-id="98c86-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="98c86-140">Dans le volet **d’Administration** , ouvrez **Gestion des périphériques mobiles > iOS et Mac OS X**, puis cliquez sur **télécharger un certificat de APNs** dans les **tâches**.</span><span class="sxs-lookup"><span data-stu-id="98c86-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="98c86-p107">Dans le volet de **télécharger un certificat de APNs** , cliquez sur **Télécharger la demande de certificat APNs**. Enregistrez le certificat de signature d’un fichier de demande (.csr) localement avec le nom **test-dev**.</span><span class="sxs-lookup"><span data-stu-id="98c86-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="98c86-143">Pour obtenir un certificat de service de notifications Push Apple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="98c86-144">Ouvrir un nouvel onglet, accédez au [Portail de certificats Apple Push](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)et connectez-vous avec votre ID d’Apple.</span><span class="sxs-lookup"><span data-stu-id="98c86-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="98c86-145">Dans la page **Mise en route** , cliquez sur **créer un certificat**.</span><span class="sxs-lookup"><span data-stu-id="98c86-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="98c86-146">Dans la page **Conditions d’utilisation** , sélectionnez **J’ai lu et accepte les conditions d’utilisation**, puis cliquez sur **Accepter**.</span><span class="sxs-lookup"><span data-stu-id="98c86-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="98c86-p108">Sur la page **créer un nouveau certificat de Push** , cliquez sur **Parcourir** et sélectionnez le fichier **test.csr-dev** enregistré dans la procédure précédente, puis cliquez sur **Télécharger**. Lorsque vous êtes invité à ouvrir un fichier json, enregistrez-le dans le même dossier que celui où se trouve le fichier test.csr-dev.</span><span class="sxs-lookup"><span data-stu-id="98c86-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="98c86-149">Ouvrez le [Portail de certificats Apple Push](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) dans un autre onglet et des **certificats de serveurs tiers**, cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="98c86-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="98c86-p109">Lorsque vous êtes invité à ouvrir un fichier .pem, l’enregistrer sous le nom **dev-test.pem** dans le même dossier que celui où se trouve le fichier test.csr-dev. Il s’agit de votre certificat d’APNs.</span><span class="sxs-lookup"><span data-stu-id="98c86-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="98c86-152">Pour charger le certificat APNs dans Intune, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="98c86-153">Sous l’onglet de la console d’administration de Microsoft Intune, sur la page **télécharger un certificat de APNs** , cliquez sur **Télécharger le certificat APNs**.</span><span class="sxs-lookup"><span data-stu-id="98c86-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="98c86-154">Cliquez sur **Parcourir** et indiquez le fichier **dev-test.pem** .</span><span class="sxs-lookup"><span data-stu-id="98c86-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="98c86-p110">Cliquez sur **Ouvrir**, tapez le nom de votre compte Apple ID, puis cliquez sur **Télécharger**. Vous devez voir un message **prêt pour l’inscription** sur la page **iOS et les paramètres de gestion de périphérique MaxOS X Mobile** .</span><span class="sxs-lookup"><span data-stu-id="98c86-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="98c86-157">Avec le certificat APNs installé, Intune peut désormais inscrire et gérer des appareils iOS en plaçant la stratégie sur les appareils mobiles inscrits.</span><span class="sxs-lookup"><span data-stu-id="98c86-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="98c86-158">Pour télécharger l’application de portail d’entreprise Microsoft Intune et inscrire l’appareil iOS, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="98c86-159">À partir de votre appareil iOS, connectez-vous avec votre identifiant Apple.</span><span class="sxs-lookup"><span data-stu-id="98c86-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="98c86-160">Ouvrez l’app **Store d’Apple** .</span><span class="sxs-lookup"><span data-stu-id="98c86-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="98c86-161">Tapez **intune** dans la zone Rechercher, puis cliquez sur **Portail d’entreprise Microsoft Intune**, puis **obtenir**et **installer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="98c86-162">Après l’installation, cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="98c86-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="98c86-163">Sur l’écran **Intune Entreprise Portal** , connectez-vous à votre compte d’administrateur global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="98c86-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="98c86-164">Dans l’écran **Paramètres de société d’accès** , cliquez sur **commencer**et puis cliquez sur **Continuer** .</span><span class="sxs-lookup"><span data-stu-id="98c86-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="98c86-165">Sur le **ce qui vient ensuite ?** de l’écran, cliquez sur **inscrire**.</span><span class="sxs-lookup"><span data-stu-id="98c86-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="98c86-166">Sur le **administrateur de périphérique Activate ?** de l’écran, cliquez sur **Activer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="98c86-167">Dans l’écran **Profil de gestion** , cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="98c86-168">Dans **Entrez le mot de passe**, tapez votre mot de passe de périphérique iOS.</span><span class="sxs-lookup"><span data-stu-id="98c86-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="98c86-169">Dans l’écran **ce qui vient ensuite** , cliquez sur **inscrire**.</span><span class="sxs-lookup"><span data-stu-id="98c86-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="98c86-170">**Installer un profil**, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="98c86-171">Dans la page **Avertissement** , cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="98c86-172">**Gestion à distance**, cliquez sur **Approuver**.</span><span class="sxs-lookup"><span data-stu-id="98c86-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="98c86-173">Cliquez sur **terminé** pour terminer le processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="98c86-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="98c86-174">Lorsque vous êtes invité à **Ouvrir cette page dans « Portail Comp » ?**, cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="98c86-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="98c86-175">Dans l’écran **Paramètres de société d’accès** , cliquez sur **commencer**et appuyez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="98c86-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="98c86-176">Dans l’écran principal de l’application de portail d’entreprise Microsoft Intune, vous devez voir :</span><span class="sxs-lookup"><span data-stu-id="98c86-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="98c86-177">Une bannière verte.</span><span class="sxs-lookup"><span data-stu-id="98c86-177">A green banner.</span></span>
    
  - <span data-ttu-id="98c86-178">Le nom de votre société fictive dans le coin supérieur gauche.</span><span class="sxs-lookup"><span data-stu-id="98c86-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="98c86-179">Le nom du périphérique iOS répertorié dans **Mes périphériques**.</span><span class="sxs-lookup"><span data-stu-id="98c86-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="98c86-180">Dans la section de **support technique** , le **Nom du Contact** **User5** avec le numéro de téléphone **555-1234** et un bouton de **Contact par courrier électronique** .</span><span class="sxs-lookup"><span data-stu-id="98c86-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="98c86-p111">Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le supprimer à distance.</span><span class="sxs-lookup"><span data-stu-id="98c86-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="98c86-184">Pour verrouiller un appareil iOS à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="98c86-185">À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans la navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="98c86-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="98c86-186">Dans le volet **groupes** , ouvrez **tous les périphériques > appareils mobiles tous les > tous les périphériques gérés directement**.</span><span class="sxs-lookup"><span data-stu-id="98c86-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="98c86-187">Dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .</span><span class="sxs-lookup"><span data-stu-id="98c86-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="98c86-188">Dans la liste des périphériques, cliquez sur votre appareil iOS. </span><span class="sxs-lookup"><span data-stu-id="98c86-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="98c86-189">À partir de votre appareil iOS, assurez-vous qu’il se trouve sur l’écran principal. </span><span class="sxs-lookup"><span data-stu-id="98c86-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="98c86-p112">À partir de votre ordinateur d’administration, sur la barre des tâches, cliquez sur **des tâches à distance > verrouillage à distance**. Observez votre périphérique iOS qu’il passe à l’écran de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="98c86-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="98c86-192">Pour supprimer le code secret, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="98c86-193">À partir de votre ordinateur d’administration, dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .</span><span class="sxs-lookup"><span data-stu-id="98c86-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="98c86-p113">Dans la liste, cliquez sur votre périphérique iOS. Dans la barre des tâches, cliquez sur **des tâches à distance > réinitialisation de mot de passe**. Attendez une minute.</span><span class="sxs-lookup"><span data-stu-id="98c86-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="98c86-p114">À partir de votre périphérique iOS, déverrouiller et notez qu’il n’est plus un mot de passe. Pour modifier le code secret de nouveau, allez dans **paramètres**, puis sur **mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="98c86-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="98c86-199">Phase 3 (pour les appareils Android uniquement) : Inscription et gestion d’un appareil Android</span><span class="sxs-lookup"><span data-stu-id="98c86-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="98c86-200">Vous avez besoin des éléments suivants pour inscrire un appareil Android à gérer avec Intune :</span><span class="sxs-lookup"><span data-stu-id="98c86-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="98c86-201">Un appareil Android.</span><span class="sxs-lookup"><span data-stu-id="98c86-201">An Android device.</span></span>
    
- <span data-ttu-id="98c86-202">Connaissance du mot de passe du périphérique.</span><span class="sxs-lookup"><span data-stu-id="98c86-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="98c86-203">Pour télécharger l’application de portail d’entreprise Intune et inscrire l’appareil Android, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="98c86-204">À partir de votre appareil Android, accédez à la **Banque de lecture de Google**et puis cliquez sur **Mise en route**.</span><span class="sxs-lookup"><span data-stu-id="98c86-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="98c86-205">Tapez **intune** dans la zone Rechercher et appuyez sur le **portail d’entreprise intune** dans les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="98c86-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="98c86-206">Cliquez sur l’élément **Intune Entreprise Portal** , puis **installer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="98c86-207">Sur l’écran **pour terminer l’installation compte** , cliquez sur **Continuer**, puis sur **Ignorer**.</span><span class="sxs-lookup"><span data-stu-id="98c86-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="98c86-p115">Dans le **Portail d’entreprise Intune**, cliquez sur **Accepter**. L’installation de l’application.</span><span class="sxs-lookup"><span data-stu-id="98c86-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="98c86-210">Cliquez sur **Ouvrir**, puis **reconnectez-vous**.</span><span class="sxs-lookup"><span data-stu-id="98c86-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="98c86-211">Sur l’écran **Intune Entreprise Portal** , connectez-vous à votre compte d’administrateur global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="98c86-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="98c86-212">Dans l’écran **Paramètres de société d’accès** , cliquer deux fois **commencer**, puis sur **Continuer** .</span><span class="sxs-lookup"><span data-stu-id="98c86-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="98c86-213">Sur le **ce qui vient ensuite ?** de l’écran, cliquez sur **inscrire**.</span><span class="sxs-lookup"><span data-stu-id="98c86-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="98c86-214">Sur le **administrateur de périphérique Activate ?** de l’écran, cliquez sur **Activer.**</span><span class="sxs-lookup"><span data-stu-id="98c86-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="98c86-p116">Sur l’écran de la **Politique de confidentialité** , sélectionnez **J’accepte** et puis cliquez sur **Confirmer**. Attendez la fin du processus d’inscription.</span><span class="sxs-lookup"><span data-stu-id="98c86-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="98c86-217">Dans l’écran **Paramètres de société d’accès** , cliquez sur **Continuer**et appuyez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="98c86-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="98c86-218">Dans l’écran principal de l’application de portail d’entreprise Microsoft Intune, vous devriez voir une bannière verte et le nom de votre société fictive dans le coin supérieur gauche.</span><span class="sxs-lookup"><span data-stu-id="98c86-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="98c86-p117">Cliquez sur **Mes périphériques**. Vous devez voir votre nom appareil Android dans la liste.</span><span class="sxs-lookup"><span data-stu-id="98c86-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="98c86-p118">Cliquez sur **Contact informatique**. Vous devez voir le numéro de téléphone de **555-1234**, un bouton **contacter par e-mail** , et contact de l’informatique de **User5**.</span><span class="sxs-lookup"><span data-stu-id="98c86-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="98c86-p119">Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le réinitialiser à distance.</span><span class="sxs-lookup"><span data-stu-id="98c86-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="98c86-226">Pour verrouiller un appareil Android à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="98c86-227">À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans la navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="98c86-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="98c86-228">Dans le volet **groupes** , ouvrez **tous les périphériques > appareils mobiles tous les > tous les périphériques gérés directement**.</span><span class="sxs-lookup"><span data-stu-id="98c86-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="98c86-229">Dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .</span><span class="sxs-lookup"><span data-stu-id="98c86-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="98c86-230">Dans la liste des périphériques, cliquez sur votre appareil Android. </span><span class="sxs-lookup"><span data-stu-id="98c86-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="98c86-231">À partir de votre appareil Android, assurez-vous qu’il se trouve sur l’écran principal. </span><span class="sxs-lookup"><span data-stu-id="98c86-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="98c86-p120">À partir de votre ordinateur d’administration, sur la barre des tâches, cliquez sur **des tâches à distance > verrouillage à distance**. Lorsque vous y êtes invité, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="98c86-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="98c86-234">Regardez votre appareil Android lorsqu’il bascule vers l’écran de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="98c86-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="98c86-235">Lorsque vous réinitialisez le mot de passe pour des appareils Android, le portail d’administration Intune génère et configure un mot de passe fort.</span><span class="sxs-lookup"><span data-stu-id="98c86-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="98c86-236">Pour réinitialiser le code secret à distance, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="98c86-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="98c86-237">À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, dans le volet **Tous les périphériques gérés Direct** , cliquez sur votre appareil Android.</span><span class="sxs-lookup"><span data-stu-id="98c86-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="98c86-238">Dans la barre des tâches, cliquez sur **des tâches à distance > réinitialisation de mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="98c86-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="98c86-p121">Sur le **tâche à distance : réinitialisation du mot de passe** invite, cliquez sur **Oui**. Attendez une minute.</span><span class="sxs-lookup"><span data-stu-id="98c86-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="98c86-241">Dans le volet **Tous les périphériques gérés Direct** , cliquez sur **Afficher les propriétés**.</span><span class="sxs-lookup"><span data-stu-id="98c86-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="98c86-242">Sous **Réinitialisation de mot de passe**, notez le code secret de nouveau.</span><span class="sxs-lookup"><span data-stu-id="98c86-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="98c86-243">Dans votre appareil Android, entrez le nouveau code secret à partir de l’écran de verrouillage. </span><span class="sxs-lookup"><span data-stu-id="98c86-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="98c86-244">Pour modifier le code précédent, dans **paramètres**, cliquez sur le **périphérique**, cliquez sur **écran de verrouillage**, entrez le nouveau code à nouveau, cliquez sur **verrouillage de l’écran**et votre choix pour le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="98c86-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="98c86-245">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="98c86-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98c86-246">See Also</span><span class="sxs-lookup"><span data-stu-id="98c86-246">See Also</span></span>

[<span data-ttu-id="98c86-247">L’environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="98c86-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="98c86-248">Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="98c86-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="98c86-249">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="98c86-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="98c86-250">Mobilité d’entreprise + sécurité (EMS)</span><span class="sxs-lookup"><span data-stu-id="98c86-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


