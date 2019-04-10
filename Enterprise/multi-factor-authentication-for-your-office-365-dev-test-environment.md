---
title: Authentification multifacteur pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Résumé : Configurer l’authentification multifacteur à l’aide de messages texte envoyés à un Smartphone dans un environnement de développement/test Office 365.'
ms.openlocfilehash: 091b82132b407cfd25b18c3ba8e424e29df58910
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741220"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="10b97-103">Authentification multifacteur pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="10b97-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="10b97-104">**Résumé :** Configurer l’authentification multifacteur à l’aide de messages texte envoyés à un Smartphone dans un environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="10b97-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="10b97-105">Pour un niveau de sécurité supplémentaire pour la connexion à votre abonnement Office 365, vous pouvez activer l'authentification multifacteur Azure, qui nécessite plus qu'un nom d'utilisateur et un mot de passe pour authentifier un compte.</span><span class="sxs-lookup"><span data-stu-id="10b97-105">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account.</span></span> <span data-ttu-id="10b97-106">Avec l’authentification multifacteur pour Office 365, les utilisateurs sont tenus de confirmer la bonne réception d’un appel téléphonique, de taper un code de vérification envoyé dans un message texte ou de spécifier un mot de passe d’application sur leur smartphone après avoir entré correctement leur mot de passe.</span><span class="sxs-lookup"><span data-stu-id="10b97-106">With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords.</span></span> <span data-ttu-id="10b97-107">Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté.</span><span class="sxs-lookup"><span data-stu-id="10b97-107">They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="10b97-108">Cet article décrit comment activer et tester l’authentification basée sur message texte pour un compte Office 365 spécifique.</span><span class="sxs-lookup"><span data-stu-id="10b97-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="10b97-109">Il existe deux phases de configuration de l’authentification multifacteur pour Office 365 dans un environnement de développement/test :</span><span class="sxs-lookup"><span data-stu-id="10b97-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="10b97-110">Créez l’environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="10b97-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="10b97-111">Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.</span><span class="sxs-lookup"><span data-stu-id="10b97-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="10b97-112">Cliquez [ici](http://aka.ms/catlgstack) pour afficher un plan de tous les Articles de la pile de guides de laboratoire de Test Office 365.</span><span class="sxs-lookup"><span data-stu-id="10b97-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="10b97-113">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="10b97-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="10b97-114">Si vous souhaitez simplement tester l'authentification multifacteur de manière légère avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="10b97-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="10b97-115">Si vous souhaitez tester l'authentification multifacteur dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="10b97-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="10b97-116">Le test de l'authentification multifacteur ne nécessite pas l'environnement de développement/test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="10b97-116">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="10b97-117">Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="10b97-117">It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="10b97-118">Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2</span><span class="sxs-lookup"><span data-stu-id="10b97-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="10b97-119">Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="10b97-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="10b97-120">Ouvrez une instance distincte de votre navigateur, accédez au portail Office 365 ([https://www.office.com](https://www.office.com)), puis connectez-vous à votre abonnement d'évaluation Office 365 avec votre compte d'administrateur général.</span><span class="sxs-lookup"><span data-stu-id="10b97-120">Open a separate instance of your browser, go to the Office 365 portal ([https://www.office.com](https://www.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="10b97-121">Sur la page principale du portail, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="10b97-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="10b97-122">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="10b97-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="10b97-123">Dans le volet utilisateurs actifs, cliquez sur **plus d' > d'authentification multifacteur**.</span><span class="sxs-lookup"><span data-stu-id="10b97-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="10b97-124">Dans la liste, sélectionnez le compte **utilisateur 2** .</span><span class="sxs-lookup"><span data-stu-id="10b97-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="10b97-125">Dans la section **Utilisateur 2**, sous **Étapes rapides**, cliquez sur **Activer**.</span><span class="sxs-lookup"><span data-stu-id="10b97-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="10b97-126">Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur**, cliquez sur **Activer Multi-Factor Authentication**.</span><span class="sxs-lookup"><span data-stu-id="10b97-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="10b97-127">Dans la boîte de dialogue **mises à jour réussies** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="10b97-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="10b97-128">Dans l’onglet **Microsoft Office Famille**, cliquez sur l’icône du compte utilisateur en haut à droite, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="10b97-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="10b97-129">Fermez l’instance de navigateur.</span><span class="sxs-lookup"><span data-stu-id="10b97-129">Close your browser instance.</span></span>
    
<span data-ttu-id="10b97-130">Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="10b97-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="10b97-131">Ouvrez une nouvelle instance de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="10b97-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="10b97-132">Accédez au portail Office 365 ([https://www.office.com](https://www.office.com)) et connectez-vous avec le compte utilisateur 2 (utilisateur2 @\<Organization name>. onmicrosoft. com) et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="10b97-132">Go to the Office 365 portal ([https://www.office.com](https://www.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="10b97-p103">Après vous être connecté, vous êtes invité à configurer le compte pour la validation de sécurité supplémentaire. Cliquez sur **Configurer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="10b97-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="10b97-135">Sur la page **Vérification de sécurité supplémentaire** : </span><span class="sxs-lookup"><span data-stu-id="10b97-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="10b97-136">Sélectionnez le pays ou la région.</span><span class="sxs-lookup"><span data-stu-id="10b97-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="10b97-137">Tapez le numéro de téléphone du smartphone qui recevra les SMS.</span><span class="sxs-lookup"><span data-stu-id="10b97-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="10b97-138">dans **méthode**, cliquez sur **m'envoyer un code par message texte**.</span><span class="sxs-lookup"><span data-stu-id="10b97-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="10b97-139">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="10b97-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="10b97-140">Entrez le code de vérification du SMS reçu sur votre smartphone, puis cliquez sur **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="10b97-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="10b97-141">Sur la page **Étape 3 : Conservez la page des applications existantes**, enregistrez le mot de passe de l’application affiché pour le compte d’utilisateur 2 dans un endroit sûr, puis cliquez sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="10b97-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="10b97-p104">Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis cliquez sur **Mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.</span><span class="sxs-lookup"><span data-stu-id="10b97-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="10b97-145">Vous devriez voir le portail Office 365 pour utilisateur 2 sur l'onglet **Accueil Microsoft Office** de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="10b97-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="10b97-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10b97-146">See Also</span></span>

[<span data-ttu-id="10b97-147">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="10b97-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="10b97-148">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="10b97-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="10b97-149">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="10b97-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="10b97-150">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="10b97-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="10b97-151">Offre pour l'authentification multifacteur des déploiements Office 365</span><span class="sxs-lookup"><span data-stu-id="10b97-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

