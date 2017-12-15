---
title: "Environnement de développement/test Office 365"
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
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour créer un abonnement d’évaluation de Office 365 pour l’évaluation ou de développement/test."
ms.openlocfilehash: 1864043513fc7502ada332ab3b3043ff20a13736
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="8f97a-103">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="8f97a-104">**Résumé :** Utilisez ce Guide de laboratoire de Test pour créer un abonnement d’évaluation de Office 365 pour l’évaluation ou de développement/test.</span><span class="sxs-lookup"><span data-stu-id="8f97a-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="8f97a-p101">Vous pouvez utiliser un abonnement d’évaluation Office 365 et créer un environnement de développement/test Office 365 pour les applications ou faire une démonstration des fonctionnalités d’Office 365. Deux versions sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="8f97a-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="8f97a-107">L’environnement de développement/test Office 365 léger se compose d’un abonnement d’évaluation Office 365 auquel vous accédez depuis votre ordinateur principal.</span><span class="sxs-lookup"><span data-stu-id="8f97a-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="8f97a-p102">Utilisez cet environnement lorsque vous voulez montrer rapidement une fonctionnalité. Pour l’environnement de développement/test Office 365 léger, suivez les instructions des phases 2 et 3 de cet article.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="8f97a-p103">L’environnement de développement/test Office 365 d’entreprise simulé comprend un abonnement d’évaluation Office 365 et un intranet d’organisation simplifié connecté à Internet, qui est hébergé dans les services d’infrastructure de Microsoft Azure. Vous pouvez créer cette configuration entièrement dans le cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="8f97a-p104">Utilisez cet environnement lorsque vous voulez montrer une fonctionnalité ou une application dans un environnement semblable à un réseau d’entreprise classique connecté à Internet, ou pour les fonctionnalités pour lesquelles ce type d’environnement est nécessaire. Pour l’environnement de développement/test Office 365 d’entreprise simulé, suivez les instructions des phases 1, 2 et 3 de cet article.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8f97a-p105">Nous vous recommandons d’imprimer cet article afin de consigner les valeurs spécifiques dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement à la version d’évaluation pour 30 jours de plus. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un petit nombre de licences.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guides de laboratoire de test dans le cloud de Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="8f97a-118">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="8f97a-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="8f97a-119">Phase 1 : création de la configuration de base dans Azure</span><span class="sxs-lookup"><span data-stu-id="8f97a-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="8f97a-120">Suivez les instructions dans [l’environnement de développement/test de Configuration de Base](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="8f97a-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="8f97a-p106">Vous aurez besoin d’un abonnement Azure. Vous pouvez utiliser [Version d’évaluation gratuite de Azure](https://azure.microsoft.com/pricing/free-trial/) pour cette configuration. Si vous avez un abonnement MSDN ou Visual Studio, reportez-vous à la section [crédit mensuel Azure pour les abonnés de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="8f97a-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="8f97a-124">Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="8f97a-124">Here is the resulting configuration.</span></span>
  
![Environnement de développement/test de configuration de base dans Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="8f97a-126">Cette configuration se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="8f97a-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="8f97a-127">Phase 2 : création d’un abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="8f97a-128">Pour démarrer votre abonnement d’évaluation Office 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8f97a-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="8f97a-p107">Nous vous recommandons d’utiliser une variante du nom de la société Contoso pour le nom de votre société, est une société fictive utilisée dans l’exemple de contenu de Microsoft, mais il n’est pas obligatoire. Enregistrer votre nom de la société fictive : ___</span><span class="sxs-lookup"><span data-stu-id="8f97a-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="8f97a-p108">Pour vous inscrire à un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créer un compte avec un nouveau compte de messagerie et une adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="8f97a-133">Indiquer le prénom et le nom de famille utilisés pour votre nouveau compte ici : _______________________________</span><span class="sxs-lookup"><span data-stu-id="8f97a-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="8f97a-134">Indiquer l’adresse du nouveau compte de messagerie ici : _____________________________@outlook.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="8f97a-135">Inscription à un abonnement d’évaluation Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="8f97a-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="8f97a-136">Pour l’environnement de développement/test léger Office 365, ouvrez le navigateur Internet sur votre ordinateur et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="8f97a-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="8f97a-137">Pour l’environnement de développement/test simulées entreprise Office 365 :</span><span class="sxs-lookup"><span data-stu-id="8f97a-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="8f97a-138">À partir du [portail Azure](https://portal.azure.com), se connecter à CLIENT1 avec le CORP\\compte utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="8f97a-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="8f97a-139">Exécutez ces commandes à l’invite de commande Windows PowerShell de niveau administrateur.</span><span class="sxs-lookup"><span data-stu-id="8f97a-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="8f97a-140">Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) pour obtenir un fichier texte qui contient toutes les commandes de PowerShell dans cet article.</span><span class="sxs-lookup"><span data-stu-id="8f97a-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="8f97a-141">À partir de l’écran de démarrage, cliquez sur **Internet Explorer** et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="8f97a-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="8f97a-142">Sur la page **d’accueil, nous allons apprendre à vous connaître** , spécifiez :</span><span class="sxs-lookup"><span data-stu-id="8f97a-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="8f97a-143">votre emplacement physique ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-143">Your physical location</span></span>
    
  - <span data-ttu-id="8f97a-144">le prénom et le nom utilisés pour votre nouveau compte Microsoft ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="8f97a-145">votre nouvelle adresse de compte de messagerie ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-145">Your new email account address</span></span>
    
  - <span data-ttu-id="8f97a-146">un numéro de téléphone professionnel ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-146">A business phone number</span></span>
    
  - <span data-ttu-id="8f97a-147">le nom de votre entreprise fictive ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="8f97a-148">la taille de votre entreprise (250 à 999 personnes).</span><span class="sxs-lookup"><span data-stu-id="8f97a-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="8f97a-149">Cliquez sur **un seul plus l’étape**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="8f97a-150">Sur la page **créer votre nom d’utilisateur** , tapez un nom d’utilisateur en fonction de votre nouvelle adresse e-mail, votre société fictive après le signe @ (supprimer tous les espaces dans le nom), puis un mot de passe (deux fois) pour ce nouveau Office 365 compte.</span><span class="sxs-lookup"><span data-stu-id="8f97a-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="8f97a-151">Enregistrez le mot de passe saisi dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8f97a-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="8f97a-152">Enregistrer le nom de la société fictive d’être désignée sous le **nom de l’organisation**, ici : ___</span><span class="sxs-lookup"><span data-stu-id="8f97a-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="8f97a-153">Cliquez sur **créer mon compte**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="8f97a-p109">Sur le **prouver. Vous êtes. Pas. A robot de.** la page, tapez le numéro de téléphone de votre téléphone prenant en charge de texte, puis cliquez sur **texte me**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="8f97a-156">Tapez le code de vérification dans le message reçu, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8f97a-157">Enregistrez l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ___________________________________________</span><span class="sxs-lookup"><span data-stu-id="8f97a-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="8f97a-158">Enregistrez l’identifiant utilisateur ici (sélectionnez-le et copiez-le) : __________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="8f97a-159">Cette valeur sera dénommée le **nom de l’administrateur global Office 365**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="8f97a-160">Lorsque **vous êtes prêt**, cliquez sur elle.</span><span class="sxs-lookup"><span data-stu-id="8f97a-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="8f97a-161">Sur la page suivante, attendez Office 365 se termine le paramètre des toutes les tuiles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="8f97a-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="8f97a-162">Vous devriez voir la page principale du portail Office 365 à partir de laquelle vous pouvez accéder aux services Office Online et au Centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="8f97a-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="8f97a-163">Pour l’environnement de développement/test Office 365 d’entreprise simulé, voici la configuration que vous obtenez.</span><span class="sxs-lookup"><span data-stu-id="8f97a-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="8f97a-165">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="8f97a-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="8f97a-166">les machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure ;</span><span class="sxs-lookup"><span data-stu-id="8f97a-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="8f97a-167">un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="8f97a-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="8f97a-168">Phase 3 : configuration de votre abonnement d’évaluation Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="8f97a-169">Au cours de cette phase, vous allez configurer votre abonnement Office 365 en y ajoutant des sites d’équipes SharePoint Online et des utilisateurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8f97a-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="8f97a-170">Toute d’abord, ajoutez quatre nouveaux utilisateurs et attribuez-leur des licences E5.</span><span class="sxs-lookup"><span data-stu-id="8f97a-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="8f97a-171">Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell et vous connecter à votre nouvel abonnement Office 365 à partir de :</span><span class="sxs-lookup"><span data-stu-id="8f97a-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="8f97a-172">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="8f97a-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="8f97a-173">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="8f97a-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="8f97a-174">Dans la boîte de dialogue demande d’informations d’identification Windows PowerShell, tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8f97a-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="8f97a-175">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="8f97a-176">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de l’utilisateur 2 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="8f97a-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="8f97a-177">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="8f97a-178">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 3 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="8f97a-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="8f97a-179">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="8f97a-180">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 4 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="8f97a-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="8f97a-181">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="8f97a-182">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte d’utilisateur 5 et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="8f97a-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="8f97a-183">Ensuite, créez trois nouveaux sites d’équipes SharePoint Online pour les services Ventes, Production et Support.</span><span class="sxs-lookup"><span data-stu-id="8f97a-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="8f97a-184">Création de trois nouveaux sites d’équipes SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8f97a-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="8f97a-185">Installer le [Shell de gestion en ligne de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la x64 version).</span><span class="sxs-lookup"><span data-stu-id="8f97a-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="8f97a-186">Cliquez sur **Démarrer**, tapez **sharepoint**, puis cliquez sur **SharePoint Online Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="8f97a-187">Indiquez le nom de votre organisation (exemple : contosotoycompany), puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell pour vous connecter au service SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8f97a-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="8f97a-188">Dans la boîte de dialogue **Microsoft SharePoint Online Management Shell** , tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="8f97a-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="8f97a-189">Pour créer trois nouveaux sites d’équipe (ventes, Production et prise en charge), indiquez le nom d’administrateur global de Office 365 et puis exécutent les commandes suivantes à partir de l’invite du Shell de gestion en ligne de SharePoint :</span><span class="sxs-lookup"><span data-stu-id="8f97a-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="8f97a-190">Exécutez cette commande pour répertorier les URL de ces nouveaux sites :</span><span class="sxs-lookup"><span data-stu-id="8f97a-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="8f97a-191">Dans Internet Explorer, entrez l’URL du site Production pour afficher le site d’équipe SharePoint Online par défaut pour le service Production.</span><span class="sxs-lookup"><span data-stu-id="8f97a-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="8f97a-192">Enregistrez les valeurs, vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="8f97a-192">Record values for future reference</span></span>

<span data-ttu-id="8f97a-193">Enregistrez ces valeurs pour utiliser ou déployer les guides de laboratoire de test dans cet environnement de test :</span><span class="sxs-lookup"><span data-stu-id="8f97a-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="8f97a-194">Nom de l’administrateur général Office 365 : ____________________________________.onmicrosoft.com (indiqué à l’étape 9 de la phase 2)</span><span class="sxs-lookup"><span data-stu-id="8f97a-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="8f97a-195">Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8f97a-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="8f97a-196">Nom de l’organisation de l’abonnement d’évaluation : _______________________________________________ (indiqué à l’étape 4 de la phase 2)</span><span class="sxs-lookup"><span data-stu-id="8f97a-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="8f97a-197">Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="8f97a-198">Enregistrez les noms de compte ici :</span><span class="sxs-lookup"><span data-stu-id="8f97a-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="8f97a-199">Nom du compte Utilisateur 2 : user2@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="8f97a-200">Nom du compte Utilisateur 3 : user3@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="8f97a-201">Nom du compte Utilisateur 4 : user4@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="8f97a-202">Nom du compte Utilisateur 5 : user5@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="8f97a-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="8f97a-203">Enregistrez également les mots de passe de ces comptes dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8f97a-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="8f97a-204">Pour répertorier les URL des sites d’équipes Ventes, Production et Support, exécutez la commande suivante à partir de l’invite SharePoint Online Management Shell :</span><span class="sxs-lookup"><span data-stu-id="8f97a-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="8f97a-205">URL de site de production : https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="8f97a-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="8f97a-206">URL du site Ventes : https://______________________________________________.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="8f97a-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="8f97a-207">URL du site Support : https://______________________________________________.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="8f97a-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="8f97a-208">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8f97a-208">Next steps</span></span>

<span data-ttu-id="8f97a-209">Utilisez ces articles supplémentaires dans votre environnement de développement/test Office 365 :</span><span class="sxs-lookup"><span data-stu-id="8f97a-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="8f97a-210">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-211">Plusieurs facteurs d’authentification pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-212">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-213">Application du nuage sécurité pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-214">Avancées de protection contre les menaces pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-215">E-Discovery avancée pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-216">Protection des fichiers sensibles dans l’environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-217">Environnement de développement/test isolé de SharePoint Online équipe site</span><span class="sxs-lookup"><span data-stu-id="8f97a-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-218">La classification des données et le marquage de l’environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="8f97a-219">Étendez votre environnement de développement/test Office 365 afin d’y inclure des offres cloud supplémentaires de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="8f97a-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="8f97a-220">L’environnement de développement/test Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8f97a-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="8f97a-221">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="8f97a-222">See Also</span><span class="sxs-lookup"><span data-stu-id="8f97a-222">See Also</span></span>

[<span data-ttu-id="8f97a-223">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="8f97a-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="8f97a-224">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="8f97a-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="8f97a-225">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="8f97a-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


