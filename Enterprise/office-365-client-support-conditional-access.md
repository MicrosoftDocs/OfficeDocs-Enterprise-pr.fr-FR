---
title: Prise en charge des applications Office 365 Client - accès conditionnel
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
description: Comprendre la prise en charge des application client Office 365 pour l’accès conditionnel
ms.openlocfilehash: c03d7f1cc2f1a80abb7227a40eb606a3f40cd214
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "29771103"
---
# <a name="office-365-client-app-support---conditional-access"></a>Prise en charge des applications Office 365 Client - accès conditionnel

Dans l’espace de travail moderne, les utilisateurs peuvent accéder à des ressources de votre organisation à l’aide d’une variété de périphériques et d’applications à partir de n’importe quel emplacement. Par conséquent, juste en mettant l’accent sur qui peut accéder à une ressource ne suffit pas plus. Votre organisation doit également en charge comment et où une ressource est effectuée dans votre infrastructure de contrôle d’accès. Avec Azure AD périphérique, l’emplacement et accès conditionnel authentification multifacteur, vous pouvez vous réunir cette nouvelle exigence. Accès conditionnel est une fonctionnalité d’Azure Active Directory qui vous permet d’appliquer des contrôles de l’accès aux applications dans votre environnement, tout en fonction de conditions spécifiques et gérés à partir d’un emplacement central. 

Pour plus d’informations sur [l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateur Web
 - Android
 - iOS
 - Mac OS

## <a name="supported-clients"></a>Clients pris en charge

Les dernières versions des clients suivants prennent en charge l’accès conditionnel :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Entrer l’icône](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Edge](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône de flux](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône de formulaires](media/o365-forms-64x64.png) <br> [Formulaires](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) |
| ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icône d’administration d’Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive entreprise icône](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Icône du planificateur](media/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône de projet](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) 
| ![Skype pour entreprise icône](media/o365-skypeforbusiness-64x64.png) <br> [Skype pour <br> Business](https://www.skype.com/business/) | ![Icône StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Icône de Notes pense-bête](media/o365-stickynotes-64x64.png) <br> [Pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icône de flux de données](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icône de balancement](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Icône d’équipes](media/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône des tâches](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône de Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)