---
title: Déployer Office 365 Entreprise pour votre organisation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: Ces étapes d’aperçu sont conçues pour vous aider à déployer Office 365, à connecter votre annuaire Active Directory, à migrer vos données et à aider les membres de votre organisation à prendre en main la dernière version d’Office 2016.
ms.openlocfilehash: 2530b170c607f635f6f1baebf1d83fa7745d23a6
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102542"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="f8db8-103">Déployer Office 365 Entreprise pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="f8db8-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="f8db8-p101">Êtes-vous prêt à déployer Office 365 Entreprise et à l’intégrer à votre infrastructure locale ? Ces étapes d’aperçu sont conçues pour vous aider à connecter votre annuaire, à migrer vos données et à aider les membres de votre organisation à prendre en main la dernière version d’Office 2016.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="f8db8-106">Ces étapes sont destinées aux entreprises et [associations à but non lucratif](https://go.microsoft.com/fwlink/?LinkId=627221) qui souhaitent commencer avec un déploiement personnalisé d’Office 365 Entreprise.</span><span class="sxs-lookup"><span data-stu-id="f8db8-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="f8db8-p102">Vous n’avez pas Office 365 Entreprise ? Reportez-vous à la rubrique [Configurer Office 365 pour les entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) afin d’obtenir des instructions pour les petites entreprises.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="f8db8-109">Processus guidé de configuration d’Office 365 pour les entreprises avec FastTrack</span><span class="sxs-lookup"><span data-stu-id="f8db8-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="f8db8-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** est la meilleure méthode pour déployer Office 365. FastTrack vous guide dans les configurations de déploiement les plus courantes et peut répondre aux questions tout au long du processus. Si vous voulez procéder en autonomie ou obtenir de l’aide auprès d’un partenaire, utilisez notre [guide de configuration Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa) ou nos [Assistants de configuration Office 365](https://aka.ms/o365fasttrack), ou [trouvez un partenaire qualifié](https://partnercenter.microsoft.com/en-us/pcv/search).</span><span class="sxs-lookup"><span data-stu-id="f8db8-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/en-us/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="f8db8-113">Déploiement en autonomie d’Office 365</span><span class="sxs-lookup"><span data-stu-id="f8db8-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="f8db8-114">Si vous voulez déployer Office 365 sans aide, les étapes de déploiement suivantes sont là pour vous aider.</span><span class="sxs-lookup"><span data-stu-id="f8db8-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="f8db8-p104">**[Préparez le déploiement d’Office 365](get-your-organization-ready-for-office-365.md)**. Ces outils et ressources vous aideront à préparer votre réseau, votre annuaire et vos utilisateurs finaux au déploiement d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="f8db8-117">**Connectez-vous et ajoutez vos domaines Internet à Office 365**.</span><span class="sxs-lookup"><span data-stu-id="f8db8-117">**Sign in and add your internet domain(s) to Office 365**.</span></span> <span data-ttu-id="f8db8-118">Connectez-vous au [Centre d’administration Microsoft 365](https://portal.microsoft.com), cliquez sur **configurer les domaines >**, puis cliquez sur **nouveau domaine**.</span><span class="sxs-lookup"><span data-stu-id="f8db8-118">Sign into the [Microsoft 365 admin center](https://portal.microsoft.com), click **Setup > Domains**, and then click **New domain**.</span></span> <span data-ttu-id="f8db8-119">Ajoutez un ou plusieurs domaines à votre abonnement Office 365 sans ajouter d’utilisateurs ni migrer du courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="f8db8-119">Add one or more domains to your Office 365 subscription without adding users or migrating email.</span></span> 

>[!IMPORTANT] 
><span data-ttu-id="f8db8-120">Les instructions de configuration de base ne fonctionnent pas si vous voulez synchroniser vos utilisateurs d’un annuaire local ou utiliser l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="f8db8-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="f8db8-p106">**[Connectez votre répertoire à Office 365](about-office-365-identity.md)**. Guide des options de configuration d’authentification unique et/ou de synchronisation des identités. Utilisez le [conseiller AAD Connect](https://aka.ms/aadconnectpwsync) et le [guide de configuration Azure AD Premium](https://aka.ms/aadpguidance) pour obtenir des instructions de configuration personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p106">**[Connect your directory to Office 365](about-office-365-identity.md)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="f8db8-p107">**[Configurez les applications et services Office 365](configure-services-and-applications.md)**. Commencez ici pour configurer la messagerie, le partage de fichiers, la messagerie instantanée ou les autres services et applications Office 365.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="f8db8-p108">**[Migrez les données vers Office 365](migrate-data-to-office-365.md)**. Une fois les services configurés, vous pouvez commencer à migrer les données.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="f8db8-p109">**[Encouragez l’utilisation d’Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Aidez les membres de votre organisation à se familiariser à l’utilisation d’Office 365 à l’aide de ces ressources.</span><span class="sxs-lookup"><span data-stu-id="f8db8-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>