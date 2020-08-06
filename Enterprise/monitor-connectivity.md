---
title: Surveiller la connectivité de Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Une fois que vous avez déployé Microsoft 365, vous pouvez maintenir la connectivité de Microsoft 365 à l’aide de certains des outils et techniques ci-dessous. Vous voudrez comprendre les directives officielles en matière de santé et de continuité des services, ainsi que nos meilleures pratiques pour l’utilisation de Microsoft 365 sur un réseau lent.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571007"
---
# <a name="monitor-microsoft-365-connectivity"></a>Surveiller la connectivité de Microsoft 365

Une fois que vous avez déployé Microsoft 365, vous pouvez maintenir la connectivité de Microsoft 365 à l’aide de certains des outils et techniques ci-dessous. Vous voudrez comprendre les directives officielles en matière de [santé et de continuité des services](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) , ainsi que nos [meilleures pratiques pour l’utilisation de Microsoft 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Vous pouvez également récupérer l’application d' [administration de microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) et ajouter un signet à notre [Microsoft 365 pour les entreprises-aide de l’administrateur](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Surveillance de la connectivité de Microsoft 365

|||
|:-----|:-----|
|**Notification des nouveaux points de terminaison Microsoft 365** <br/> |Si vous [gérez des points de terminaison Microsoft 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), vous pouvez recevoir des notifications lors de la publication de nouveaux points de terminaison, vous pouvez vous abonner à notre flux RSS à l’aide de votre lecteur RSS favori. Voici comment [s’abonner via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez vous [Envoyer les mises à jour du flux RSS par courrier électronique](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Utiliser System Center pour surveiller Microsoft 365** <br/> |Si vous utilisez Microsoft System Center, vous pouvez télécharger le [Pack d’administration System Center pour Office 365](https://www.microsoft.com/download/details.aspx?id=43708) afin de commencer la surveillance de Microsoft 365 dès aujourd’hui. Pour obtenir des instructions plus détaillées, reportez-vous au Guide des opérations du pack d’administration ou au billet de blog [Office 365 Monitoring using System Center Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**Surveiller l’état d’Azure ExpressRoute** <br/> |Si vous vous connectez à Microsoft 365 à l’aide d’Azure ExpressRoute pour Microsoft 365, vous devez vous assurer que vous utilisez à la fois le tableau de bord Microsoft 365 service Health et le service Azure de [résolution des problèmes avec Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Utiliser Azure AD Connect Health avec AD FS** <br/> |Si vous utilisez les services ADFS (Active Directory Federation Services) pour l’authentification unique avec Microsoft 365, vous pouvez commencer [à utiliser Azure ad Connect Health pour surveiller votre infrastructure AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).  <br/> |
|**Surveillance par programme de Microsoft 365** <br/> |Consultez nos conseils sur l' [API de gestion de Microsoft 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>Voir aussi

[Configurer les applications et services d’entreprise Microsoft 365](configure-services-and-applications.md)
  
[Préparer votre organisation pour Microsoft 365 entreprise](get-your-organization-ready-for-office-365.md)
  
[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)
  
[Intégration de Microsoft 365 aux environnements locaux](office-365-integration.md)
  
[Gestion des points de terminaison Microsoft 365](managing-office-365-endpoints.md)
