---
title: Prise en charge des applications clientes Office 365 — authentification basée sur les certificats
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
description: Prise en charge des applications clientes Office 365 pour l’authentification basée sur les certificats.
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990913"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Prise en charge des applications clientes Office 365 — authentification basée sur les certificats

L’authentification basée sur les certificats vous permet de vous authentifier auprès d’Azure Active Directory avec un certificat client sur des appareils Windows, Android ou iOS. La configuration de cette fonctionnalité élimine le besoin d’entrer un nom d’utilisateur et un mot de passe dans certains messages et applications Microsoft Office sur votre appareil mobile.

En savoir plus sur [l’authentification basée sur les certificats](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau<sup>2</sup> Windows 10
 - Applications modernes Windows 10
 - Navigateurs Web
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Pour plus d’informations sur la prise en charge de la plateforme dans Office 365, voir [Configuration requise pour office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les versions les plus récentes des clients suivants prennent en charge l’authentification par certificat:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône accès](media/o365-access-64x64.png) <br> [Accès](https://products.office.com/access) | ![Icône Azure](media/o365-azure-64x64.png) <br> [Portail Azure <br> ad](https://azure.microsoft.com/features/azure-portal/) | ![Icône portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Portail <br> d’entreprise](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icône Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [Bord](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône de flux](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône formulaires](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icône d’administrateur Office 365](media/o365-o365admin-64x64.png) <br> [Administrateur Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Icône de l’objectif](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Icône du planificateur](media/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) | ![Icône PowerApp](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône de projet](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![Icône Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icône Skype entreprise](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> entreprise](https://www.skype.com/business/) | ![Icône de pense-bête](media/o365-stickynotes-64x64.png) <br> [Notes du pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icône de flux](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Icône Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône action](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> la prise en charge de OneDrive sur MacOS est bientôt disponible. <br>
> <sup>2</sup> la prise en charge de Yammer sur le bureau Windows et MacOS est bientôt disponible.