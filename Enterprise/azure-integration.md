---
title: Intégration d’Azure avec Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Votre abonnement à Office 365 comprend un abonnement Azure AD. Intégrer Office 365 avec Azure AD si vous souhaitez que la synchronisation de mot de passe ou authentification unique avec votre environnement local.
ms.openlocfilehash: 276243b953d18953ef3ea8f1189d1af8292dca6a
ms.sourcegitcommit: b1cd20300a616ebef2f00668f42ba14e8aa5fcab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "23531837"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="a2009-104">Intégration d’Azure avec Office 365</span><span class="sxs-lookup"><span data-stu-id="a2009-104">Azure integration with Office 365</span></span>

<span data-ttu-id="a2009-p102">Office 365 utilise Azure Active Directory (AD Azure) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement à Office 365 comprend un abonnement gratuit à Azure AD afin que vous pouvez intégrer Office 365 avec Azure AD si vous souhaitez synchroniser les mots de passe ou configuration de l’authentification unique avec votre environnement local. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.</span><span class="sxs-lookup"><span data-stu-id="a2009-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="a2009-108">Azure offre également d’autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser vos abonnements Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2009-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="a2009-109">Vous pouvez utiliser les conseillers déploiement Azure AD pour une expérience interactive du programme d’installation et de configuration :</span><span class="sxs-lookup"><span data-stu-id="a2009-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="a2009-110">Gestionnaire de connexion AD Azure</span><span class="sxs-lookup"><span data-stu-id="a2009-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="a2009-111">Gestionnaire de déploiement d’AD FS</span><span class="sxs-lookup"><span data-stu-id="a2009-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="a2009-112">Assistant de déploiement RMS Azure</span><span class="sxs-lookup"><span data-stu-id="a2009-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="a2009-113">Guide de configuration Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="a2009-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="a2009-114">Azure AD éditions et pour la gestion des identités Office 365</span><span class="sxs-lookup"><span data-stu-id="a2009-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="a2009-p103">Si vous disposez d’un abonnement payant à Office 365, vous avez également un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d’utilisateur et groupe. Pour activer cet abonnement, que vous devez effectuer un enregistrement unique. Ensuite, vous pouvez accéder Azure AD à partir de votre portail d’administration d’Office 365. Pour plus d’informations, voir [inscrire votre libre abonnement Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="a2009-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="a2009-p104">Suivez les instructions ci-dessus pour abonnement register Azure AD gratuit qui est fourni avec votre abonnement à Office 365. N’accédez directement à azure.microsoft.com pour vous inscrire ou vous finirez avec un abonnement d’essai ou payant à Microsoft Azure séparé de votre un gratuite pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2009-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="a2009-122">Avec l’abonnement gratuit que vous pouvez synchroniser avec les annuaires locaux, configuration de l’authentification unique et synchroniser avec le logiciel de nombreux comme les applications de service, telles que force de vente, échange et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="a2009-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="a2009-p105">Si vous souhaitez que des fonctionnalités améliorées de domaine Active Directory, la synchronisation bidirectionnelle et autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit à un abonnement payant premium. Pour plus d’informations, consultez [éditions Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="a2009-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="a2009-125">Pour plus d’informations sur Office 365 et Azure AD, voir [identités Office 365 et Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="a2009-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="a2009-126">Étendre les fonctionnalités de votre client Office 365</span><span class="sxs-lookup"><span data-stu-id="a2009-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="a2009-127">**Fonctionnalité**</span><span class="sxs-lookup"><span data-stu-id="a2009-127">**Feature**</span></span>|<span data-ttu-id="a2009-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="a2009-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a2009-129">Applications intégrées</span><span class="sxs-lookup"><span data-stu-id="a2009-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="a2009-p106">Vous pouvez accorder l’accès des applications spécifiques à vos données d’Office 365, tels que la messagerie, calendriers, contacts, les utilisateurs, groupes, fichiers et dossiers. Vous pouvez également autoriser ces applications de niveau administrateur global et les rendre disponibles pour votre ensemble de l’entreprise en enregistrant les applications dans Azure AD. Pour plus d’informations, consultez [applications intégrée et Azure AD pour les administrateurs Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="a2009-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="a2009-133">Voir aussi [Galerie d’applications Azure AD et single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="a2009-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="a2009-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="a2009-134">PowerApps</span></span>  <br/> | <span data-ttu-id="a2009-p107">Power applications sont les applications ciblées pour les appareils mobiles qui peuvent se connecter à vos données sources telles que des listes SharePoint et les autres applications de données. Pour plus d’informations, voir [créer un PowerApp pour obtenir la liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et la [page PowerApps](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="a2009-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="a2009-137">Pour d’autres ressources sur le Cloud Microsoft et Office 365, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2009-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="a2009-138">Identité cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="a2009-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="a2009-139">Déployer la synchronisation d’annuaires (DirSync) Office 365 dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a2009-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="a2009-140">En savoir plus sur les [applications intégrée et Azure AD pour les administrateurs Office 365](integrated-apps-and-azure-ads.md) et [Galerie d’applications Azure AD et single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="a2009-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="a2009-141">Applications d’alimentation</span><span class="sxs-lookup"><span data-stu-id="a2009-141">Power Apps</span></span>
<span data-ttu-id="a2009-p108">Power applications sont les applications ciblées pour les appareils mobiles qui peuvent se connecter à vos données sources telles que des listes SharePoint et les autres applications de données. Pour plus d’informations, voir [créer un PowerApp pour obtenir la liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et la [page PowerApps](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="a2009-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>