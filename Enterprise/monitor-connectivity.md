---
title: Surveiller la connectivité Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Une fois que vous avez déployé Office 365, vous pouvez maintenir la connectivité d’Office 365 à l’aide de certains des outils et techniques ci-dessous. Vous souhaiterez comprendre les instructions de l’état du Service et la continuité officielles ainsi que nos recommandations d’utilisation d’Office 365 sur un réseau lent. Vous souhaiterez également comprendre comment utiliser l’application Office 365 admin et ajouter un signet sur notre Office 365 pour entreprises -Aide à l’Administrateur.
ms.openlocfilehash: ce307e01a3d7da4a24a06e58d293b9598c684d8f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070050"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="024ca-105">Surveiller la connectivité Office 365</span><span class="sxs-lookup"><span data-stu-id="024ca-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="024ca-p102">Une fois que vous avez déployé Office 365, vous pouvez maintenir la connectivité d’Office 365 à l’aide de certains des outils et techniques ci-dessous. Vous souhaiterez comprendre les instructions [de l’état du Service et la continuité ](https://technet.microsoft.com/library/office-365-service-health.aspx)officielles ainsi que nos [recommandations d’utilisation d’Office 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Vous souhaiterez également comprendre[ comment utiliser l’application d’Office 365 admin](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)et ajouter un signet sur notre[Office 365 pour entreprises-Aide à l’Administrateur](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span><span class="sxs-lookup"><span data-stu-id="024ca-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://technet.microsoft.com/library/office-365-service-health.aspx) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="024ca-109">Surveillance de la connectivité d’Office 365</span><span class="sxs-lookup"><span data-stu-id="024ca-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="024ca-110">**Être informé des nouveaux points de terminaison Office 365**</span><span class="sxs-lookup"><span data-stu-id="024ca-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="024ca-p103">Si vous gérez [les points de terminaison d’Office 365 ](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), vous souhaiterez recevoir des notifications lorsque nous publions de nouveaux points de terminaison, vous pouvez vous abonner à notre flux RSS à l’aide de votre lecteur RSS préféré. Voici comment [vous abonner via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez [recevoir les flux RSS mises à jour et envoyés par courrier électronique](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span><span class="sxs-lookup"><span data-stu-id="024ca-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="024ca-113">**Utiliser System Center pour Surveiller Office 365**</span><span class="sxs-lookup"><span data-stu-id="024ca-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="024ca-p104">Si vous utilisez Microsoft System Center, vous pouvez télécharger le[ Pack de Gestion de Centre pour Office 365](https://www.microsoft.com/download/details.aspx?id=43708) pour commencer à surveiller Office 365 dès aujourd'hui. Pour obtenir des recommandations détaillées, consultez le guide des opérations de pack de gestion ou le billet de blog [surveillance d’Office 365 à l’aide de la Gestion des Opérations du Centre de Système](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span><span class="sxs-lookup"><span data-stu-id="024ca-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="024ca-116">**Surveiller l’état d’Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="024ca-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="024ca-117">En cas de connexion à Office 365 à l’aide d’Azure ExpressRoute pour Office 365, vous souhaiterez vous assurer que vous utilisez le tableau de bord Office 365 Service Health ainsi que l’Azure[réduisant le temps de résolution des problèmes avec Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="024ca-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="024ca-118">**Utiliser Azure AD Connect Health avec AD FS**</span><span class="sxs-lookup"><span data-stu-id="024ca-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="024ca-119">Si vous utilisez AD FS pour authentification unique avec Office 365, vous souhaiterez commencer[utiliser Azure AD Connect Health pour surveiller votre infrastructure AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="024ca-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="024ca-120">**Surveillance par programme d’Office 365**</span><span class="sxs-lookup"><span data-stu-id="024ca-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="024ca-121">Consultez nos recommandations sur la [API gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="024ca-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="024ca-122">Voici un lien que vous pouvez utiliser pour revenir : [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="024ca-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="024ca-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="024ca-123">See also</span></span>

[<span data-ttu-id="024ca-124">Configurer les applications et services Office 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="024ca-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
<span data-ttu-id="024ca-125">[Préparer votre organisation pour Office 365 Entreprise](get-your-organization-ready-for-office-365.md)
</span><span class="sxs-lookup"><span data-stu-id="024ca-125">[Get your organization ready for Office 365 Enterprise](get-your-organization-ready-for-office-365.md)</span></span>
  
[<span data-ttu-id="024ca-126">Planification réseau et optimisation des performances pour Office 365</span><span class="sxs-lookup"><span data-stu-id="024ca-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="024ca-127">Intégration d’Office 365 aux environnements locaux</span><span class="sxs-lookup"><span data-stu-id="024ca-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="024ca-128">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="024ca-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
