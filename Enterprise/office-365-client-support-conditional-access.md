---
title: Prise en charge des applications Office 365 Client - accès conditionnel
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Comprendre la prise en charge des application client Office 365 pour l’accès conditionnel
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541964"
---
# <a name="office-365-client-app-support---conditional-access"></a>Prise en charge des applications Office 365 Client - accès conditionnel

Dans l’espace de travail moderne, les utilisateurs peuvent accéder à des ressources de votre organisation à l’aide d’une variété de périphériques et d’applications à partir de n’importe quel emplacement. Par conséquent, juste en mettant l’accent sur qui peut accéder à une ressource ne suffit pas plus. Votre organisation doit également en charge comment et où une ressource est effectuée dans votre infrastructure de contrôle d’accès. Avec Azure AD périphérique, l’emplacement et accès conditionnel authentification multifacteur, vous pouvez vous réunir cette nouvelle exigence. Accès conditionnel est une fonctionnalité d’Azure Active Directory qui vous permet d’appliquer des contrôles de l’accès aux applications dans votre environnement, tout en fonction de conditions spécifiques et gérés à partir d’un emplacement central. 

Pour plus d’informations sur [des périphériques](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [basée sur l’emplacement](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)et accès conditionnel [MFA](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) .

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateur Web
 - Android
 - iOS
 - Mac OS<sup>1</sup>

## <a name="supported-clients"></a>Clients pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Entrer l’icône](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône Excel](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône de flux](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône de formulaires](images/o365-forms-64x64.png) <br> [Formulaires](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icône Kaizala](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icône d’administration d’Office 365](images/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive entreprise icône](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icône OneNote](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône du planificateur](images/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) 
| ![Icône PowerBI](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icône PowerPoint](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône de projet](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône SharePoint](images/o365-sharepoint-64x64.png) <br> [SharePoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype pour entreprise icône](images/o365-skypeforbusiness-64x64.png) <br> [Skype pour <br> Business](https://www.skype.com/business/) 
| ![Icône StaffHub](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Icône de flux de données](images/o365-stream-64x64.png) <br> [Flux](https://stream.microsoft.com) | ![Icône de balancement](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône d’équipes](images/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône des tâches](images/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Icône Visio](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône de Yammer](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> application SharePoint prend en charge sur Mac OS bientôt disponible.