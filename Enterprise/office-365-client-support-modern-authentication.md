---
title: Support d’application Client Office 365 - authentification moderne
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Prise en charge de l’application cliente Office 365 pour l’authentification moderne.
ms.openlocfilehash: 9705c70e68ec69dcfdac09342798baf860666535
ms.sourcegitcommit: df40eb730e416f206ca8387ef9e6f559c4e4b8a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "29887621"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Support d’application Client Office 365 - authentification moderne

Fonctionnalité d’authentification moderne de Microsoft permet basée sur Active Directory authentification bibliothèque ADAL reconnectez-vous pour les applications clientes Office sur différentes plateformes. Cela permet de connexion telles que l’authentification multifacteur (MFA), carte à puce et l’authentification par certificat.

En savoir plus sur [l’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) et [l’authentification par certificat](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateur Web
 - Android
 - iOS
 - Mac OS

Pour plus d’informations sur la plateforme prend en charge dans Office 365, voir [Configuration requise pour Office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les dernières versions des clients suivants prennent en charge l’authentification moderne :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> Portal](https://azure.microsoft.com/features/azure-portal/) | ![Icône de portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Société <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Entrer l’icône](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Icône de flux](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône de formulaires](media/o365-forms-64x64.png) <br> [Formulaires](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icône d’administration d’Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![Icône Loupe](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive entreprise icône](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône du planificateur](media/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône de projet](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Skype pour entreprise icône](media/o365-skypeforbusiness-64x64.png) <br> [Skype pour <br> Business](https://www.skype.com/business/) | ![Icône StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Icône de Notes pense-bête](media/o365-stickynotes-64x64.png) <br> [Pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icône de flux de données](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icône de balancement](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône d’équipes](media/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône des tâches](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Icône de Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Icône de Yammer](media/o365-yammer-64x64.png) <br> [Yammer <br> notificateur](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône d’Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)