---
title: Environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour créer un abonnement d’évaluation de Office 365 pour l’évaluation ou de développement/test.'
ms.openlocfilehash: 61c1fc5a997eaa0a524d49e7806fc8bb102ee281
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="13ccf-103">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="13ccf-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour créer un abonnement d’évaluation de Office 365 pour l’évaluation ou de développement/test.</span><span class="sxs-lookup"><span data-stu-id="13ccf-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="13ccf-p101">Vous pouvez utiliser un abonnement d’évaluation Office 365 et créer un environnement de développement/test Office 365 pour les applications ou faire une démonstration des fonctionnalités d’Office 365. Deux versions sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="13ccf-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="13ccf-107">L’environnement de développement/test Office 365 léger se compose d’un abonnement d’évaluation Office 365 auquel vous accédez depuis votre ordinateur principal.</span><span class="sxs-lookup"><span data-stu-id="13ccf-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="13ccf-p102">Utilisez cet environnement lorsque vous voulez démontrer rapidement une fonctionnalité. Pour l’environnement de développement/test léger Office 365, effectuez uniquement les étapes 2 et 3 du présent article.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="13ccf-p103">L’environnement de développement/test Office 365 d’entreprise simulé comprend un abonnement d’évaluation Office 365 et un intranet d’organisation simplifié connecté à Internet, qui est hébergé dans les services d’infrastructure de Microsoft Azure. Vous pouvez créer cette configuration entièrement dans le cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="13ccf-p104">Utilisez cet environnement lorsque vous voulez montrer une fonctionnalité ou une application dans un environnement semblable à un réseau d’entreprise classique connecté à Internet, ou pour les fonctionnalités pour lesquelles ce type d’environnement est nécessaire. Pour l’environnement de développement/test Office 365 d’entreprise simulé, suivez les instructions des phases 1, 2 et 3 de cet article.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="13ccf-p105">Nous vous recommandons d’imprimer cet article afin de consigner les valeurs spécifiques dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement à la version d’évaluation pour 30 jours de plus. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un petit nombre de licences.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guides de laboratoire de test dans le cloud de Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="13ccf-118">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="13ccf-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="13ccf-119">Phase 1 : création de la configuration de base dans Azure</span><span class="sxs-lookup"><span data-stu-id="13ccf-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="13ccf-120">Suivez les instructions dans [l’environnement de développement/test de Configuration de Base](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="13ccf-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="13ccf-p106">Vous aurez besoin d’un abonnement Azure. Vous pouvez utiliser [Version d’évaluation gratuite de Azure](https://azure.microsoft.com/pricing/free-trial/) pour cette configuration. Si vous avez un abonnement MSDN ou Visual Studio, reportez-vous à la section [crédit mensuel Azure pour les abonnés de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="13ccf-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="13ccf-124">Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="13ccf-124">Here is the resulting configuration.</span></span>
  
![Environnement de développement/test de configuration de base dans Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="13ccf-126">Cette configuration se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="13ccf-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="13ccf-127">Phase 2 : création d’un abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="13ccf-128">Pour démarrer votre abonnement d’évaluation Office 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="13ccf-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="13ccf-p107">Nous vous recommandons d’utiliser une variante du nom de la société Contoso pour le nom de votre société, est une société fictive utilisée dans l’exemple de contenu de Microsoft, mais il n’est pas obligatoire. Notez ici le nom de votre société fictive :![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="13ccf-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="13ccf-p108">Pour vous inscrire à un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créez un compte avec un nouveau compte de messagerie et une adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="13ccf-133">Enregistrer le prénom et le nom de votre nouveau compte ici :![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="13ccf-133">Record the first and last name of your new account here: ![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="13ccf-134">Enregistrer la nouveau compte adresse ici : ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-134">Record the new email account address here: ![](./images/Common_Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="13ccf-135">Inscription à un abonnement d’évaluation Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="13ccf-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="13ccf-136">Pour l’environnement de développement/test léger Office 365, ouvrez le navigateur Internet sur votre ordinateur et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="13ccf-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="13ccf-137">L’environnement de développement/test simulées entreprise Office 365, vous connecter à CLIENT1 avec le compte CORP\User1 à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="13ccf-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="13ccf-138">À partir de l’écran de démarrage, exécutez Microsoft Edge et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="13ccf-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="13ccf-139">Sur la page **d’accueil, nous allons apprendre à vous connaître** , spécifiez :</span><span class="sxs-lookup"><span data-stu-id="13ccf-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="13ccf-140">votre emplacement physique ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-140">Your physical location</span></span>
    
  - <span data-ttu-id="13ccf-141">le prénom et le nom utilisés pour votre nouveau compte Microsoft ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="13ccf-142">votre nouvelle adresse de compte de messagerie ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-142">Your new email account address</span></span>
    
  - <span data-ttu-id="13ccf-143">un numéro de téléphone professionnel ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-143">A business phone number</span></span>
    
  - <span data-ttu-id="13ccf-144">le nom de votre entreprise fictive ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="13ccf-145">la taille de votre entreprise (250 à 999 personnes).</span><span class="sxs-lookup"><span data-stu-id="13ccf-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="13ccf-146">Cliquez sur **un seul plus l’étape**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="13ccf-147">Sur la page **créer votre nom d’utilisateur** , tapez un nom d’utilisateur en fonction de votre nouvelle adresse e-mail, votre société fictive après le signe @ (supprimer tous les espaces dans le nom), puis un mot de passe (deux fois) pour ce nouveau Office 365 compte.</span><span class="sxs-lookup"><span data-stu-id="13ccf-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="13ccf-148">Enregistrez le mot de passe saisi dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="13ccf-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="13ccf-149">Enregistrer le nom de la société fictive d’être désignée sous le **nom de l’organisation**, ici :![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="13ccf-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./images/Common_Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="13ccf-150">Cliquez sur **créer mon compte**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="13ccf-p109">Sur le **prouver. Vous êtes. Pas. A robot de.** la page, tapez le numéro de téléphone de votre téléphone prenant en charge de texte, puis cliquez sur **texte me**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="13ccf-153">Tapez le code de vérification dans le message reçu, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13ccf-154">Enregistrer la page de connexion URL ici (sélectionner et copier) :![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="13ccf-154">Record the sign-in page URL here (select and copy): ![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="13ccf-155">Enregistrer le code utilisateur ici (sélectionner et copier) : ![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-155">Record the user ID here (select and copy): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="13ccf-156">Cette valeur sera dénommée le **nom de l’administrateur global Office 365**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="13ccf-157">Lorsque **vous êtes prêt**, cliquez sur elle.</span><span class="sxs-lookup"><span data-stu-id="13ccf-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="13ccf-158">Sur la page suivante, attendez Office 365 se termine le paramètre des toutes les tuiles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="13ccf-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="13ccf-159">Vous devriez voir la page principale du portail Office 365 à partir de laquelle vous pouvez accéder aux services Office Online et au Centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="13ccf-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="13ccf-160">Pour l’environnement de développement/test Office 365 d’entreprise simulé, voici la configuration que vous obtenez.</span><span class="sxs-lookup"><span data-stu-id="13ccf-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="13ccf-162">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="13ccf-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="13ccf-163">les machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure ;</span><span class="sxs-lookup"><span data-stu-id="13ccf-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="13ccf-164">un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="13ccf-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="13ccf-165">Phase 3 : configuration de votre abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="13ccf-166">Au cours de cette phase, vous allez configurer votre abonnement Office 365 en y ajoutant des sites d’équipes SharePoint Online et des utilisateurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="13ccf-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="13ccf-167">Toute d’abord, ajoutez quatre nouveaux utilisateurs et attribuez-leur des licences E5.</span><span class="sxs-lookup"><span data-stu-id="13ccf-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="13ccf-168">Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell et vous connecter à votre nouvel abonnement Office 365 à partir de :</span><span class="sxs-lookup"><span data-stu-id="13ccf-168">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="13ccf-169">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="13ccf-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="13ccf-170">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="13ccf-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="13ccf-171">Dans la boîte de dialogue demande d’informations d’identification Windows PowerShell, tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="13ccf-171">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="13ccf-172">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="13ccf-173">Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) pour obtenir un fichier texte qui contient toutes les commandes de PowerShell dans cet article.</span><span class="sxs-lookup"><span data-stu-id="13ccf-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>

<span data-ttu-id="13ccf-174">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de l’utilisateur 2 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="13ccf-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="13ccf-175">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="13ccf-176">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 3 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="13ccf-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="13ccf-177">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="13ccf-178">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 4 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="13ccf-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="13ccf-179">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="13ccf-180">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 5 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="13ccf-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="13ccf-181">Ensuite, créez trois nouveaux sites d’équipes SharePoint Online pour les services Ventes, Production et Support.</span><span class="sxs-lookup"><span data-stu-id="13ccf-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="13ccf-182">Création de trois nouveaux sites d’équipes SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="13ccf-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="13ccf-183">Installer le [Shell de gestion en ligne de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la x64 version).</span><span class="sxs-lookup"><span data-stu-id="13ccf-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="13ccf-184">Cliquez sur **Démarrer**, tapez **sharepoint**, puis cliquez sur **SharePoint Online Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="13ccf-185">Indiquez le nom de votre organisation (exemple : contosotoycompany), puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell pour vous connecter au service SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="13ccf-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="13ccf-186">Dans la boîte de dialogue **Microsoft SharePoint Online Management Shell** , tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="13ccf-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="13ccf-187">Pour créer trois nouveaux sites d’équipe (ventes, Production et prise en charge), indiquez le nom d’administrateur global de Office 365 et puis exécutent les commandes suivantes à partir de l’invite du Shell de gestion en ligne de SharePoint :</span><span class="sxs-lookup"><span data-stu-id="13ccf-187">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="13ccf-188">Exécutez cette commande pour répertorier les URL de ces nouveaux sites :</span><span class="sxs-lookup"><span data-stu-id="13ccf-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="13ccf-189">Dans Internet Explorer, entrez l’URL du site Production pour afficher le site d’équipe SharePoint Online par défaut pour le service Production.</span><span class="sxs-lookup"><span data-stu-id="13ccf-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="13ccf-190">Enregistrez les valeurs, vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="13ccf-190">Record values for future reference</span></span>

<span data-ttu-id="13ccf-191">Enregistrez ces valeurs pour utiliser ou déployer les guides de laboratoire de test dans cet environnement de test :</span><span class="sxs-lookup"><span data-stu-id="13ccf-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="13ccf-192">Nom de l’administrateur global Office 365 : ![](./images/Common_Images/TableLine.png). onmicrosoft.com (de l’étape 9 de la Phase 2)</span><span class="sxs-lookup"><span data-stu-id="13ccf-192">Office 365 global administrator name: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="13ccf-193">Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="13ccf-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="13ccf-194">Le nom de votre organisation d’essai : ![](./images/Common_Images/TableLine.png) (à partir de l’étape 4 de la Phase 2)</span><span class="sxs-lookup"><span data-stu-id="13ccf-194">Your trial subscription organization name: ![](./images/Common_Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="13ccf-195">Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="13ccf-196">Enregistrez les noms de compte ici :</span><span class="sxs-lookup"><span data-stu-id="13ccf-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="13ccf-197">Nom du compte utilisateur 2 : Utilisateur2 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-197">User 2 account name: user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="13ccf-198">Nom du compte utilisateur 3 : l’util_3 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-198">User 3 account name: user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="13ccf-199">Nom du compte utilisateur 4 : Utilisateur4 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-199">User 4 account name: user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="13ccf-200">Nom du compte utilisateur 5 : user5 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="13ccf-200">User 5 account name: user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="13ccf-201">Enregistrez également les mots de passe de ces comptes dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="13ccf-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="13ccf-202">Pour répertorier les URL des sites d’équipes Ventes, Production et Support, exécutez la commande suivante à partir de l’invite SharePoint Online Management Shell :</span><span class="sxs-lookup"><span data-stu-id="13ccf-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="13ccf-203">URL de site de production : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="13ccf-203">Production site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="13ccf-204">URL du site de vente : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="13ccf-204">Sales site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="13ccf-205">Prise en charge d’URL du site : https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="13ccf-205">Support site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="13ccf-206">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="13ccf-206">Next steps</span></span>

<span data-ttu-id="13ccf-207">Utilisez ces articles supplémentaires dans votre environnement de développement/test Office 365 :</span><span class="sxs-lookup"><span data-stu-id="13ccf-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="13ccf-208">Synchronisation d’annuaire pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-208">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-209">Plusieurs facteurs d’authentification pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-210">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-211">Application du nuage sécurité pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-212">Avancées de protection contre les menaces pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-213">E-Discovery avancée pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-214">Protection des fichiers sensibles dans l’environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-215">Environnement de développement/test isolé de SharePoint Online équipe site</span><span class="sxs-lookup"><span data-stu-id="13ccf-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-216">La classification des données et le marquage de l’environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="13ccf-217">Étendez votre environnement de développement/test Office 365 afin d’y inclure des offres cloud supplémentaires de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="13ccf-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="13ccf-218">L’environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="13ccf-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="13ccf-219">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="13ccf-220">Concepts</span><span class="sxs-lookup"><span data-stu-id="13ccf-220">See Also</span></span>

- [<span data-ttu-id="13ccf-221">Guides de laboratoire de test sur l'adoption du cloud</span><span class="sxs-lookup"><span data-stu-id="13ccf-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="13ccf-222">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="13ccf-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="13ccf-223">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="13ccf-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


