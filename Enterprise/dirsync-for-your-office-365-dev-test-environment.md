---
title: Synchronisation d’annuaires pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Résumé : Configurez la synchronisation d’annuaires pour votre environnement de développement/test Office 365.'
ms.openlocfilehash: c1596b12ab3c6c8feda3063134cc53a5f18919af
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162427"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="c91f8-103">Synchronisation d’annuaires pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="c91f8-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="c91f8-104">**Résumé :** Configurez la synchronisation d’annuaires pour votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="c91f8-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c91f8-p101">De nombreuses organisations utilisent Azure AD Connect et la synchronisation d’annuaires pour synchroniser l’ensemble des comptes dans leur forêt Active Directory Domain Services (AD DS) en local avec l’ensemble des comptes dans Office 365. Cet article explique la procédure d’ajout de la synchronisation d’annuaires avec synchronisation de hachage de mot de passe à l’environnement de développement/test Office 365, ce qui entraîne la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Environnement de développement/test Office 365 avec la synchronisation d’annuaires](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="c91f8-108">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="c91f8-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="c91f8-109">Un abonnement d’évaluation Office 365 E5, qui arrive à expiration 30 jours après sa création.</span><span class="sxs-lookup"><span data-stu-id="c91f8-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="c91f8-p102">Un intranet d’organisation simplifié connecté à Internet, qui se compose de trois machines virtuelles dans un sous-réseau d’un réseau virtuel Azure (DC1, APP1 et CLIENT1). Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine AD DS avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="c91f8-112">Les deux phases de configuration de cet environnement de développement/test sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c91f8-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="c91f8-113">Créez l’environnement de développement/test Office 365 (les machines virtuelles DC1, APP1 et CLIENT1 dans un réseau virtuel Azure avec un abonnement d’évaluation Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="c91f8-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="c91f8-114">Installez et configurez Azure AD Connect sur APP1.</span><span class="sxs-lookup"><span data-stu-id="c91f8-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="c91f8-115">Cliquez sur[ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.</span><span class="sxs-lookup"><span data-stu-id="c91f8-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="c91f8-116">Phase 1 : création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="c91f8-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="c91f8-p103">Suivez les instructions des phases 1, 2 et 3 de l’article relatif à l’[environnement de développement/test Office 365](office-365-dev-test-environment.md). Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Environnement de développement/test Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="c91f8-120">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="c91f8-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="c91f8-121">Un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="c91f8-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="c91f8-122">Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="c91f8-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="c91f8-123">Phase 2 : installation d’Azure AD Connect sur APP1</span><span class="sxs-lookup"><span data-stu-id="c91f8-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="c91f8-124">Une fois installé et configuré, Azure AD Connect synchronise l’ensemble des comptes dans le domaine CORP AD DS avec l’ensemble des comptes dans votre abonnement d’essai Office 365.</span><span class="sxs-lookup"><span data-stu-id="c91f8-124">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription.</span></span> <span data-ttu-id="c91f8-125">La procédure suivante vous guide tout au long de l’installation d’Azure AD Connect sur APP1 et du contrôle de son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="c91f8-125">The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="c91f8-126">Installation et configuration d’Azure AD Connect sur APP1</span><span class="sxs-lookup"><span data-stu-id="c91f8-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="c91f8-127">À partir du [portail Azure](https://portal.azure.com), connectez-vous à APP1 avec le compte CORP\\Utilisateur1.</span><span class="sxs-lookup"><span data-stu-id="c91f8-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="c91f8-128">À partir d’APP1, ouvrez une invite de commande Windows PowerShell de niveau administrateur, puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c91f8-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="c91f8-129">Dans la barre des tâches, cliquez sur **Internet Explorer** et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="c91f8-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="c91f8-130">Sur la page de Microsoft Azure Active Directory Connect, cliquez sur **Télécharger**, puis cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="c91f8-131">Sur la page **Bienvenue dans Azure AD Connect**, cliquez sur **J’accepte**, puis sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="c91f8-132">Sur la page **Configuration rapide**, cliquez sur **Utiliser la configuration rapide**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="c91f8-133">Sur la page **Connexion à Azure AD**, saisissez le nom de votre compte d’administrateur général sous **Nom d’utilisateur** et le mot de passe correspondant sous **Mot de passe**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c91f8-134">Sur la page **Connexion à AD DS**, saisissez **CORP\\Utilisateur** sous **Nom d’utilisateur,** entrez le mot de passe correspondant sous **Mot de passe**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="c91f8-135">Sur la page **Configuration de la connexion à Azure AD**, cliquez sur **Continuer sans aucun domaine vérifié**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="c91f8-136">Sur la page **Prêt à configurer**, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="c91f8-137">Sur la page **Configuration terminée**, cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="c91f8-138">Dans Internet Explorer, accédez au Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) et connectez-vous à votre abonnement d’évaluation Office 365 avec votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="c91f8-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="c91f8-139">Sur la page principale du portail, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="c91f8-140">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="c91f8-p105">Prenez note du compte nommé **Utilisateur1**. Ce compte provient du domaine CORP AD DS et prouve que la synchronisation d’annuaires a fonctionné.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="c91f8-p106">Cliquez sur le compte **Utilisateur1**. Pour les licences de produits, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="c91f8-p107">Dans **Licences de produits**, sélectionnez votre pays, puis cliquez sur le contrôle **Inactif** pour **Office 365 Entreprise E5** (en le définissant sur **Actif**). Cliquez sur **Enregistrer** en bas de la page, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="c91f8-147">Voici la configuration obtenue.</span><span class="sxs-lookup"><span data-stu-id="c91f8-147">This is the resulting configuration.</span></span>
  
![Environnement de développement/test Office 365 avec la synchronisation d’annuaires](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="c91f8-149">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="c91f8-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="c91f8-150">un abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="c91f8-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="c91f8-p108">Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 dans un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute dans APP1 pour synchroniser le domaine CORP AD DS avec Office 365 toutes les 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="c91f8-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="c91f8-153">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="c91f8-153">Next Step</span></span>

<span data-ttu-id="c91f8-154">Lorsque vous êtes prêt à déployer la synchronisation d'annuaires pour votre organisation, consultez la rubrique[Déploiement de la Synchronisation d'annuaires Office 365 dans Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c91f8-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c91f8-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c91f8-155">See Also</span></span>

[<span data-ttu-id="c91f8-156">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="c91f8-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="c91f8-157">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="c91f8-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)

[<span data-ttu-id="c91f8-158">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="c91f8-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="c91f8-159">Protection avancée contre les menaces pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="c91f8-159">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="c91f8-160">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="c91f8-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




