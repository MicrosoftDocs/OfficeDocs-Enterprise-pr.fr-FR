---
title: Prise en charge des applications clientes Office 365 — authentification moderne
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Prise en charge des applications clientes Office 365 pour l’authentification moderne.
ms.openlocfilehash: 58bcb7e4b2476a9ae87dc2f59d87c1b70c58375b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41849089"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Prise en charge des applications clientes Office 365-authentification moderne

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

L’authentification moderne permet la connexion basée sur la bibliothèque d’authentification Active Directory (ADAL) pour les applications clientes Office sur différentes plateformes. Cela active des fonctionnalités de connexion telles que l’authentification multifacteur (MFA), la carte à puce et l’authentification basée sur les certificats.

En savoir plus sur [l’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) et [l’authentification basée sur les certificats](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateurs Web<sup>1</sup>
 - Android<sup>2</sup>
 - iOS
 - macOS

Pour plus d’informations sur la prise en charge de la plateforme dans Office 365, voir [Configuration requise pour office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les versions les plus récentes des clients suivants prennent en charge l’authentification moderne :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icône Azure](media/o365-azure-64x64.png) <br> [Portail <br> Azure](https://azure.microsoft.com/features/azure-portal/) | ![Icône portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Portail <br> d’entreprise](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icône Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône Flow](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône Forms](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icône Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icône d’administrateur Office 365](media/o365-o365admin-64x64.png) <br> [Administrateur Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Icône de l’objectif](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) 
| ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône planificateur](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icône PowerApp](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icône Project](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icône Skype Entreprise](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> entreprise<sup>1</sup>](https://www.skype.com/business/) | ![Icône StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Icône de pense-bête](media/o365-stickynotes-64x64.png) <br> [Notes du pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icône Stream](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icône Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône action](media/o365-todo-64x64.png) <br> [Action](https://todo.microsoft.com) 
| ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône de tableau blanc](media/o365-whiteboard-64x64.png) <br> [Tableau blanc<sup>1</sup>,<sup>2</sup>](https://whiteboard.microsoft.com/) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Notificateur <br> Yammer](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> la prise en charge du tableau blanc et de Skype entreprise sur le Web App disponible bientôt disponible. <br>
> <sup>2</sup> la prise en charge du tableau blanc sur Android est bientôt disponible.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
