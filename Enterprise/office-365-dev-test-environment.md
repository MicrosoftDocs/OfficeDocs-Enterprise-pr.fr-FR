---
title: Environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Résumé : Utilisez ce guide de laboratoire de test pour créer un abonnement d’évaluation Office 365 à des fins d’évaluation ou de développement/test.'
ms.openlocfilehash: 07922965acfbd23f0f48094fda8b18bf0b66ef38
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="5e181-103">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="5e181-104">**Résumé :** Utilisez ce guide de laboratoire de test pour créer un abonnement d’évaluation Office 365 à des fins d’évaluation ou de développement/test.</span><span class="sxs-lookup"><span data-stu-id="5e181-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="5e181-p101">Vous pouvez utiliser un abonnement d’évaluation Office 365 et créer un environnement de développement/test Office 365 pour les applications ou faire une démonstration des fonctionnalités d’Office 365. Deux versions sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="5e181-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="5e181-107">L’environnement de développement/test Office 365 léger se compose d’un abonnement d’évaluation Office 365 auquel vous accédez depuis votre ordinateur principal.</span><span class="sxs-lookup"><span data-stu-id="5e181-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="5e181-p102">Utilisez cet environnement lorsque vous voulez montrer rapidement une fonctionnalité. Pour l’environnement de développement/test Office 365 léger, suivez uniquement les instructions des phases 2 et 3 de cet article.</span><span class="sxs-lookup"><span data-stu-id="5e181-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="5e181-p103">L’environnement de développement/test Office 365 d’entreprise simulé comprend un abonnement d’évaluation Office 365 et un intranet d’organisation simplifié connecté à Internet, qui est hébergé dans les services d’infrastructure de Microsoft Azure. Vous pouvez créer cette configuration entièrement dans le cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e181-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="5e181-p104">Utilisez cet environnement lorsque vous voulez montrer une fonctionnalité ou une application dans un environnement semblable à un réseau d’entreprise classique connecté à Internet, ou pour les fonctionnalités pour lesquelles ce type d’environnement est nécessaire. Pour l’environnement de développement/test Office 365 d’entreprise simulé, suivez les instructions des phases 1, 2 et 3 de cet article.</span><span class="sxs-lookup"><span data-stu-id="5e181-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5e181-p105">Nous vous recommandons d’imprimer cet article afin de consigner les valeurs spécifiques dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement à la version d’évaluation pour 30 jours de plus. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un petit nombre de licences.</span><span class="sxs-lookup"><span data-stu-id="5e181-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guides de laboratoire de test dans Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="5e181-118">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="5e181-118">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="5e181-119">Phase 1 : création de la configuration de base dans Azure</span><span class="sxs-lookup"><span data-stu-id="5e181-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="5e181-120">Suivez les instructions de la rubrique [Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5e181-120">Follow the instructions in [Base Configuration Test Environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5e181-p106">Vous devez posséder un abonnement Azure. Vous pouvez utiliser le [Compte gratuit Azure](https://azure.microsoft.com/pricing/free-trial/) pour cette configuration. Si vous avez un abonnement MSDN ou Visual Studio, reportez-vous à l’article [Crédit Azure mensuel pour les abonnés Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="5e181-p106">You will need an Azure subscription. You can use the [Azure Free Trialhttps://azure.microsoft.com/pricing/free-trial/](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribershttps://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="5e181-124">Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="5e181-124">Here is the resulting configuration.</span></span>
  
![Environnement de développement/test de configuration de base dans Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="5e181-126">Cette configuration se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="5e181-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="5e181-127">Phase 2 : création d’un abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="5e181-128">Pour démarrer votre abonnement d’évaluation Office 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e181-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="5e181-p107">Nous vous recommandons d’utiliser une variante du nom d’entreprise Contoso pour le nom de votre entreprise. Il s’agit d’une entreprise fictive utilisée dans le contenu d’exemple de Microsoft. Toutefois, cette étape n’est pas obligatoire. Indiquer le nom fictif de votre entreprise ici : ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="5e181-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn’t required. Record your fictitious company name here: _____________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="5e181-p108">Pour ouvrir un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créez un compte avec un nouveau compte de messagerie et une nouvelle adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.</span><span class="sxs-lookup"><span data-stu-id="5e181-p108">To sign up for a new Microsoft account, go to  https://outlook.com https://outlook.com  and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="5e181-133">Indiquer le prénom et le nom de famille utilisés pour votre nouveau compte ici : ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="5e181-133">Record the first and last name of your new account here: _______________________________![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="5e181-134">Indiquer l’adresse du nouveau compte de messagerie ici : ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="5e181-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="5e181-135">Inscription à un abonnement d’évaluation Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="5e181-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="5e181-136">Pour l’environnement de développement/test Office 365 léger, ouvrez le navigateur Internet sur votre ordinateur et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="5e181-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to  https://aka.ms/e5trial https://aka.ms/e5trial .</span></span> 
    
    <span data-ttu-id="5e181-137">Pour l’environnement de développement/test Office 365 d’entreprise simulé, connectez-vous à CLIENT1 avec le compte CORP\Utilisateur1 à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="5e181-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="5e181-138">Dans l’écran d’accueil, exécutez Microsoft Edge et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="5e181-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="5e181-139">Sur la page **Bienvenue, nous allons faire connaissance**, indiquez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5e181-139">On the **Welcome, let’s get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="5e181-140">votre emplacement physique ;</span><span class="sxs-lookup"><span data-stu-id="5e181-140">Your physical location</span></span>
    
  - <span data-ttu-id="5e181-141">le prénom et le nom utilisés pour votre nouveau compte Microsoft ;</span><span class="sxs-lookup"><span data-stu-id="5e181-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="5e181-142">votre nouvelle adresse de compte de messagerie ;</span><span class="sxs-lookup"><span data-stu-id="5e181-142">Your new email account address</span></span>
    
  - <span data-ttu-id="5e181-143">un numéro de téléphone professionnel ;</span><span class="sxs-lookup"><span data-stu-id="5e181-143">A business phone number</span></span>
    
  - <span data-ttu-id="5e181-144">le nom de votre entreprise fictive ;</span><span class="sxs-lookup"><span data-stu-id="5e181-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="5e181-145">la taille de votre entreprise (250 à 999 personnes).</span><span class="sxs-lookup"><span data-stu-id="5e181-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="5e181-146">Cliquez sur **Encore une dernière étape**.</span><span class="sxs-lookup"><span data-stu-id="5e181-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="5e181-147">Sur la page **Créer votre identifiant utilisateur**, entrez un nom d’utilisateur dérivé de votre nouvelle adresse de messagerie, le nom de votre entreprise fictive après le signe @ (supprimez tous les espaces dans le nom), puis un mot de passe (deux fois) pour ce nouveau compte Office 365. </span><span class="sxs-lookup"><span data-stu-id="5e181-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="5e181-148">Enregistrez le mot de passe saisi dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="5e181-149">Enregistrez le nom de votre entreprise fictive, ou **nom de l’organisation**, ici : ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="5e181-149">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="5e181-150">Cliquez sur **Créer mon compte**.</span><span class="sxs-lookup"><span data-stu-id="5e181-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="5e181-p109">Sur la page **Prouvez que vous n’êtes pas un robot.**, tapez le numéro de votre téléphone compatible avec du texte, puis cliquez sur **M’envoyer un SMS**.</span><span class="sxs-lookup"><span data-stu-id="5e181-p109">On the **Prove. You’re. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="5e181-153">Saisissez le code de vérification qui vous été envoyé par message, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="5e181-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5e181-154">Enregistrez l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="5e181-154">Record the sign-in page URL here (select and copy): ___________________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="5e181-155">Enregistrez l’identifiant utilisateur ici (sélectionnez-le et copiez-le) : ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e181-155">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="5e181-156">Cette valeur correspond au **nom de l’administrateur général Office 365**.</span><span class="sxs-lookup"><span data-stu-id="5e181-156">This value will  be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="5e181-157">Cliquez sur le lien **Nous sommes prêts** lorsqu’il s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5e181-157">When you see **You’re ready to go**, click it.</span></span>
    
11. <span data-ttu-id="5e181-158">Sur la page suivante, attendez qu’Office 365 termine la configuration et que tous les titres soient visibles.</span><span class="sxs-lookup"><span data-stu-id="5e181-158">On the next page, wait until Office 365 completes setting up and all the tiles under Collaborate with Office Online are visible.</span></span>
    
<span data-ttu-id="5e181-159">Vous devriez voir la page principale du portail Office 365 à partir de laquelle vous pouvez accéder aux services Office Online et au Centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="5e181-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="5e181-160">Pour l’environnement de développement/test Office 365 d’entreprise simulé, voici la configuration que vous obtenez.</span><span class="sxs-lookup"><span data-stu-id="5e181-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="5e181-162">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="5e181-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="5e181-163">les machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure ;</span><span class="sxs-lookup"><span data-stu-id="5e181-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="5e181-164">un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="5e181-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="5e181-165">Phase 3 : configuration de votre abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="5e181-166">Au cours de cette phase, vous allez configurer votre abonnement Office 365 en y ajoutant des sites d’équipes SharePoint Online et des utilisateurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5e181-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="5e181-167">Toute d’abord, ajoutez quatre nouveaux utilisateurs et attribuez-leur des licences E5.</span><span class="sxs-lookup"><span data-stu-id="5e181-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="5e181-168">Utilisez les instructions de l’article [Se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell et vous connecter à votre nouvel abonnement Office 365 à partir de :</span><span class="sxs-lookup"><span data-stu-id="5e181-168">Use the instructions in [Connect to Office 365 PowerShellhttps://technet.microsoft.com/library/dn975125.aspx](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="5e181-169">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="5e181-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="5e181-170">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="5e181-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="5e181-171">Dans la boîte de dialogue Demande d’informations d’identification Windows PowerShell, saisissez le nom de l’administrateur général Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5e181-171">In the Windows PowerShell Credential Request dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="5e181-172">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e181-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="5e181-173">Pour accéder à un fichier texte qui contient toutes les commandes PowerShell décrites dans cet article, cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34).</span><span class="sxs-lookup"><span data-stu-id="5e181-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all of the PowerShell commands in this article.</span></span>

<span data-ttu-id="5e181-174">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 2 et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5e181-175">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e181-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5e181-176">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 3 et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5e181-177">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e181-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5e181-178">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 4 et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5e181-179">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e181-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5e181-180">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 5 et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5e181-181">Ensuite, créez trois nouveaux sites d’équipes SharePoint Online pour les services Ventes, Production et Support.</span><span class="sxs-lookup"><span data-stu-id="5e181-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="5e181-182">Création de trois nouveaux sites d’équipes SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e181-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="5e181-183">Installez [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la version x64).</span><span class="sxs-lookup"><span data-stu-id="5e181-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="5e181-184">Cliquez sur **Démarrer**, saisissez **sharepoint**, puis cliquez sur **SharePoint Online Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="5e181-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="5e181-185">Indiquez le nom de votre organisation (exemple : contosotoycompany), puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell pour vous connecter au service SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5e181-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="5e181-186">Dans la boîte de dialogue **Microsoft SharePoint Online Management Shell**, saisissez le nom de l’administrateur général Office 365 (par exemple, jdoe@contosotoycompany.onmicrosoft.com) et son mot de passe, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="5e181-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="5e181-187">Pour créer trois nouveaux sites d’équipes (Ventes, Production et Support), indiquez le nom de l’administrateur général Office 365, puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell :</span><span class="sxs-lookup"><span data-stu-id="5e181-187">To create three new team sites (Sales, Production, and Support), fill in the Office  365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="5e181-188">Exécutez cette commande pour répertorier les URL de ces nouveaux sites :</span><span class="sxs-lookup"><span data-stu-id="5e181-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="5e181-189">Dans Internet Explorer, entrez l’URL du site Production pour afficher le site d’équipe SharePoint Online par défaut pour le service Production.</span><span class="sxs-lookup"><span data-stu-id="5e181-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="5e181-190">Enregistrez les valeurs, vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="5e181-190">Record values for future reference</span></span>

<span data-ttu-id="5e181-191">Enregistrez ces valeurs pour utiliser ou déployer les guides de laboratoire de test dans cet environnement de test :</span><span class="sxs-lookup"><span data-stu-id="5e181-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="5e181-192">Nom de l’administrateur général Office 365 : ![](./images/Common_Images/TableLine.png).onmicrosoft.com (indiqué à l’étape 9 de la phase 2)</span><span class="sxs-lookup"><span data-stu-id="5e181-192">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="5e181-193">Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="5e181-194">Nom de l’organisation de l’abonnement d’évaluation : ![](./images/Common_Images/TableLine.png) (indiqué à l’étape 4 de la phase 2)</span><span class="sxs-lookup"><span data-stu-id="5e181-194">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="5e181-195">Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e181-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="5e181-196">Enregistrez les noms de compte ici :</span><span class="sxs-lookup"><span data-stu-id="5e181-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="5e181-197">Nom du compte Utilisateur 2 : user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e181-197">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5e181-198">Nom du compte Utilisateur 3 : user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e181-198">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5e181-199">Nom du compte Utilisateur 4 : user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e181-199">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5e181-200">Nom du compte Utilisateur 5 : user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e181-200">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="5e181-201">Enregistrez également les mots de passe de ces comptes dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5e181-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="5e181-202">Pour répertorier les URL des sites d’équipes Ventes, Production et Support, exécutez la commande suivante à partir de l’invite SharePoint Online Management Shell :</span><span class="sxs-lookup"><span data-stu-id="5e181-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="5e181-203">URL du site Production : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="5e181-203">Production site URL:  https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="5e181-204">URL du site Ventes : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="5e181-204">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="5e181-205">URL du site Support : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="5e181-205">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="5e181-206">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5e181-206">Next steps</span></span>

<span data-ttu-id="5e181-207">Utilisez ces articles supplémentaires dans votre environnement de développement/test Office 365 :</span><span class="sxs-lookup"><span data-stu-id="5e181-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="5e181-208">Synchronisation d’annuaires pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-208">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-209">Authentification multifacteur pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-210">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-211">Sécurité des applications cloud pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-212">Protection avancée contre les menaces pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-213">Advanced eDiscovery pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-214">Protection des fichiers sensibles dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-215">Site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-216">Classification et étiquetage des données dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5e181-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="5e181-217">Étendez votre environnement de développement/test Office 365 afin d’y inclure des offres cloud supplémentaires de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="5e181-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="5e181-218">Environnement de développement/test Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="5e181-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="5e181-219">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5e181-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="5e181-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e181-220">See Also</span></span>

- [<span data-ttu-id="5e181-221">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="5e181-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="5e181-222">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5e181-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="5e181-223">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="5e181-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


