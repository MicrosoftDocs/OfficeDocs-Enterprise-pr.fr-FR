---
title: Support d’application Client Office 365 - authentification moderne
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Prise en charge de l’application cliente Office 365 pour l’authentification moderne.
ms.openlocfilehash: 73827d1e19556a31c9eb3a11c9fa6617bee3f566
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541954"
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

## <a name="supported-clients"></a>Clients pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Entrer l’icône](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Dynamics 365](images/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Icône Excel](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône de flux](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône de formulaires](images/o365-forms-64x64.png) <br> [Formulaires](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | 
| ![Icône Kaizala](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icône d’administration d’Office 365](images/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![Icône Loupe](images/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive entreprise icône](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icône OneNote](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote)
| ![Icône Outlook](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône du planificateur](images/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) | ![Icône PowerBI](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icône PowerPoint](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône de projet](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![Icône SharePoint](images/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Skype pour entreprise icône](images/o365-skypeforbusiness-64x64.png) <br> [Skype pour <br> Business](https://www.skype.com/business/) | ![Icône StaffHub](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Icône de flux de données](images/o365-stream-64x64.png) <br> [Flux](https://stream.microsoft.com) | ![Icône de balancement](images/o365-sway-64x64.png) <br> [Sway](https://sway.com)
| ![Icône d’équipes](images/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône des tâches](images/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Icône Visio](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône de Yammer](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)