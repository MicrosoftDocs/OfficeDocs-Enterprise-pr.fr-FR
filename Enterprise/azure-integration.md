---
title: Intégration d’Azure avec Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Votre abonnement Office 365 inclut un abonnement à Azure AD. Intégrez Office 365 avec Azure AD si vous voulez une synchronisation de mot de passe ou une authentification unique avec votre environnement local.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085473"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="86854-104">Intégration d’Azure avec Office 365</span><span class="sxs-lookup"><span data-stu-id="86854-104">Azure integration with Office 365</span></span>

<span data-ttu-id="86854-p102">Office 365 utilise Azure Active Directory (Azure AD) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement Office 365 inclut un abonnement gratuit à Azure AD afin que vous puissiez intégrer Office 365 à Azure AD si vous souhaitez synchroniser les mots de passe ou configurer l'authentification unique avec votre environnement local. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.</span><span class="sxs-lookup"><span data-stu-id="86854-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="86854-108">Azure offre également d'autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser vos abonnements Office 365.</span><span class="sxs-lookup"><span data-stu-id="86854-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="86854-109">Vous pouvez utiliser les conseillers de déploiement Azure AD pour une expérience de configuration et d'installation guidée:</span><span class="sxs-lookup"><span data-stu-id="86854-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="86854-110">Conseiller Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="86854-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="86854-111">Conseiller de déploiement AD FS</span><span class="sxs-lookup"><span data-stu-id="86854-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="86854-112">Assistant Déploiement d'Azure RMS</span><span class="sxs-lookup"><span data-stu-id="86854-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="86854-113">Guide de configuration d'Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="86854-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="86854-114">Gestion des identités Azure AD et Office 365</span><span class="sxs-lookup"><span data-stu-id="86854-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="86854-p103">Si vous disposez d'un abonnement payant à Office 365, vous disposez également d'un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d'utilisateurs et de groupes. Pour activer cet abonnement, vous devez effectuer une inscription unique. Par la suite, vous pouvez accéder à Azure AD à partir de votre portail d'administration Office 365. Pour obtenir des instructions, consultez [la rubrique enregistrer votre abonnement Azure ad gratuit](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="86854-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="86854-p104">Suivez les instructions ci-dessus pour enregistrer l'abonnement Azure AD gratuit fourni avec votre abonnement à Office 365. N'accédez pas directement à azure.microsoft.com pour vous inscrire ou vous obtiendrez une version d'évaluation ou un abonnement payant à Microsoft Azure qui est distinct de votre version gratuite pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="86854-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="86854-122">Avec l'abonnement gratuit, vous pouvez synchroniser avec des annuaires locaux, configurer l'authentification unique et effectuer une synchronisation avec de nombreux logiciels en tant qu'applications de service, telles que Salesforce, DropBox et bien d'autres encore.</span><span class="sxs-lookup"><span data-stu-id="86854-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="86854-p105">Si vous souhaitez améliorer les fonctionnalités AD DS, la synchronisation bidirectionnelle et les autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit vers un abonnement payant payant. Pour plus d'informations, reportez-vous à [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="86854-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="86854-125">Pour plus d'informations sur Office 365 et Azure AD, consultez la rubrique [understandIng Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="86854-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="86854-126">Étendez les capacités de votre client Office 365</span><span class="sxs-lookup"><span data-stu-id="86854-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="86854-127">**Fonctionnalité**</span><span class="sxs-lookup"><span data-stu-id="86854-127">**Feature**</span></span>|<span data-ttu-id="86854-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="86854-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="86854-129">Applications intégrées</span><span class="sxs-lookup"><span data-stu-id="86854-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="86854-p106">Vous pouvez accorder à des applications individuelles l'accès à vos données Office 365, par exemple des courriers, des calendriers, des contacts, des utilisateurs, des groupes, des fichiers et des dossiers. Vous pouvez également autoriser ces applications au niveau de l'administrateur général et les rendre accessibles à votre entreprise entière en enregistrant les applications dans Azure AD. Pour plus d'informations, consultez la rubrique [applications intégrées et Azure AD pour les administrateurs d'Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="86854-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="86854-133">Voir aussi [Galerie d'applications Azure ad et authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="86854-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="86854-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="86854-134">PowerApps</span></span>  <br/> | <span data-ttu-id="86854-p107">Les applications Power sont des applications ciblées pour les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que les listes SharePoint et les autres applications de données. Pour plus d'informations, rePortez-vous à [la page créer un PowerApp pour une liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et les [PowerApp](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="86854-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="86854-137">Pour connaître les autres ressources relatives à Microsoft Cloud et Office 365, consultez les ressources suivantes:</span><span class="sxs-lookup"><span data-stu-id="86854-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="86854-138">Identité cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="86854-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="86854-139">Déployer la synchronisation d’annuaires (DirSync) Office 365 dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="86854-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="86854-140">Pour plus d'informations, consultez la rubrique [applications intégrées et Azure AD pour les administrateurs d'Office 365](integrated-apps-and-azure-ads.md) , ainsi que la [Galerie d'applications Azure ad et l'authentification unique](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="86854-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="86854-141">Applications puissantes</span><span class="sxs-lookup"><span data-stu-id="86854-141">Power Apps</span></span>
<span data-ttu-id="86854-p108">Les applications Power sont des applications ciblées pour les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que les listes SharePoint et les autres applications de données. Pour plus d'informations, rePortez-vous à [la page créer un PowerApp pour une liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et les [PowerApp](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="86854-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>