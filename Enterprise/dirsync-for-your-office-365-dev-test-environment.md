---
title: Synchronisation d’annuaire pour votre environnement de développement/test d’Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Résumé : Configurer la synchronisation d’annuaire pour votre environnement de développement/test d’Office 365.'
ms.openlocfilehash: 2fd4a9e6ea009e28ce95ff69e5ab03043ed18706
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="7371a-103">Synchronisation d’annuaire pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="7371a-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="7371a-104">**Résumé :** Configurer la synchronisation d’annuaire pour votre environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="7371a-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="7371a-p101">De nombreuses entreprises choisissent d’utiliser Azure Connect de publicité et de la synchronisation d’annuaire à synchroniser l’ensemble des comptes dans leur forêt de Windows Server Active Directory (AD) sur site à l’ensemble des comptes dans Office 365. Cet article explique comment vous pouvez ajouter la synchronisation d’annuaire avec synchronisation de hachage de mot de passe à l’environnement de développement/test Office 365, résultant dans la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="7371a-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![L’environnement de développement/test d’Office 365 avec la synchronisation d’annuaire](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="7371a-108">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="7371a-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="7371a-109">Un abonnement d’évaluation Office 365 E5, qui arrive à expiration 30 jours après sa création.</span><span class="sxs-lookup"><span data-stu-id="7371a-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="7371a-p102">Un intranet d’organisation simplifié connecté à Internet, qui se compose de trois machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1 et CLIENT1). Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine Windows Server AD avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="7371a-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="7371a-112">Les deux phases de configuration de cet environnement de développement/test sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7371a-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="7371a-113">Créez l’environnement de développement/test Office 365 (les machines virtuelles DC1, APP1 et CLIENT1 dans un réseau virtuel Azure avec un abonnement d’évaluation Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="7371a-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="7371a-114">Installez et configurez Azure AD Connect sur APP1.</span><span class="sxs-lookup"><span data-stu-id="7371a-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="7371a-115">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="7371a-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="7371a-116">Phase 1 : création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="7371a-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="7371a-p103">Suivez les instructions affichées dans les étapes 1, 2 et 3 de l’article de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md) . Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="7371a-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="7371a-120">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="7371a-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="7371a-121">Un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="7371a-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="7371a-122">Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="7371a-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="7371a-123">Phase 2 : installation d’Azure AD Connect sur APP1</span><span class="sxs-lookup"><span data-stu-id="7371a-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="7371a-p104">Une fois installé et configuré, Azure AD Connect synchronise l’ensemble de comptes dans le domaine CORP Windows Server AD avec l’ensemble de comptes dans votre abonnement d’évaluation Office 365. La procédure suivante vous guide tout au long de l’installation d’Azure AD Connect sur APP1 et de la vérification de son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="7371a-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="7371a-126">Installer et configurer Azure AD Connect dans APP1</span><span class="sxs-lookup"><span data-stu-id="7371a-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="7371a-127">Dans le [portail Azure](https://portal.azure.com), connectez-vous à APP1 avec le CORP\\compte utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="7371a-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="7371a-128">À partir d’APP1, ouvrez une invite de commande Windows PowerShell de niveau administrateur, puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7371a-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="7371a-129">À partir de la barre des tâches, cliquez sur **Internet Explorer** et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="7371a-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="7371a-130">Sur la page Microsoft Azure Active Directory se connecter, cliquez sur **Télécharger**, puis cliquez sur **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="7371a-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="7371a-131">Dans la page **Bienvenue dans Azure Connect d’Active Directory** , cliquez sur **J’accepte**, puis cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="7371a-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="7371a-132">Dans la page **Paramètres Express** , cliquez sur **utiliser les paramètres express**.</span><span class="sxs-lookup"><span data-stu-id="7371a-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="7371a-133">Sur la page de **connexion à Azure AD** , tapez votre nom de compte administrateur global dans le type de **nom d’utilisateur,** son mot de passe **mot de passe**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="7371a-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7371a-134">Sur la page de **connexion aux services AD DS** , tapez **CORP\\utilisateur1** dans **nom d’utilisateur,** tapez son mot de passe **mot de passe**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="7371a-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="7371a-135">Sur la page de **configuration de connexion AD Azure** , cliquez sur **Continuer sans vérifié tous les domaines**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="7371a-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="7371a-136">Sur la page **Prêt à configurer**, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="7371a-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="7371a-137">Dans la page **Configuration terminée** , cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="7371a-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="7371a-138">Dans Internet Explorer, accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et connectez-vous à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="7371a-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="7371a-139">À partir de la page principale du portail, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="7371a-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="7371a-140">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="7371a-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="7371a-p105">Notez le compte nommé **utilisateur1**. Ce compte est dans le domaine CORP Windows Server Active Directory et la preuve que la synchronisation d’annuaire a travaillé.</span><span class="sxs-lookup"><span data-stu-id="7371a-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="7371a-p106">Cliquez sur le compte **d’utilisateur1** . Pour les licences de produit, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="7371a-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="7371a-p107">Dans **les licences de produit**, sélectionnez votre pays, puis cliquez sur le contrôle **hors** d' **Office 365 entreprise E5** (commutation **on**). Cliquez sur **Enregistrer** en bas de la page, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="7371a-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="7371a-147">Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="7371a-147">This is the resulting configuration.</span></span>
  
![L’environnement de développement/test d’Office 365 avec la synchronisation d’annuaire](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="7371a-149">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="7371a-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="7371a-150">Un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="7371a-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="7371a-p108">Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine CORP Windows Server AD avec Office 365 toutes les 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="7371a-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="7371a-153">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="7371a-153">Next Step</span></span>

<span data-ttu-id="7371a-154">Lorsque vous êtes prêt à déployer la synchronisation d’annuaire de votre organisation, voir [déployer Office 365 la synchronisation d’annuaire dans Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="7371a-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 directory synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7371a-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7371a-155">See Also</span></span>

<span data-ttu-id="7371a-156">[Cloud adoption Guides de laboratoires de Test (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[environnement de développement/test de Configuration de Base de](base-configuration-dev-test-environment.md)
[environnement de développement/test Office 365](office-365-dev-test-environment.md)
[Sécurité d’application Cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md) 
 [ Avancées de protection contre les menaces pour votre environnement de développement/test Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[adoption du nuage et les solutions hybride](cloud-adoption-and-hybrid-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="7371a-156">[Cloud adoption Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)
[Office 365 dev/test environment](office-365-dev-test-environment.md)
[Cloud App Security for your Office 365 dev/test environment](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Advanced Threat Protection for your Office 365 dev/test environment](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud adoption and hybrid solutions](cloud-adoption-and-hybrid-solutions.md)</span></span>




