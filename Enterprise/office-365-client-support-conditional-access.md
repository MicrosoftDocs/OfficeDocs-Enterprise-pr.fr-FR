---
title: Prise en charge des applications clientes Office 365 — accès conditionnel
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
description: Comprendre la prise en charge des applications clientes Office 365 pour l’accès conditionnel
ms.openlocfilehash: c5c94a1ed7d87a625599c37e5652911109afec33
ms.sourcegitcommit: b1a32e8df403143fb34eaddf116aed3595228c8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2019
ms.locfileid: "36817285"
---
# <a name="office-365-client-app-support--conditional-access"></a>Prise en charge des applications clientes Office 365 — accès conditionnel

Dans l’espace de travail moderne, les utilisateurs peuvent accéder aux ressources de votre organisation à l’aide de divers appareils et applications depuis n’importe quel endroit. Par conséquent, il ne suffit plus de se concentrer sur qui peut accéder à une ressource. Votre organisation doit également prendre en charge la façon et l’emplacement d’accès à une ressource dans votre infrastructure de contrôle d’accès.

Avec l’accès conditionnel à un appareil Azure AD, un emplacement et un accès conditionnel multi-facteur, vous pouvez répondre à cette nouvelle exigence. L’accès conditionnel est une fonctionnalité d’Azure Active Directory qui vous permet d’appliquer des contrôles sur l’accès aux applications de votre environnement, toutes basées sur des conditions spécifiques et gérées à partir d’un emplacement central.

En savoir plus sur [l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateurs Web
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

Pour plus d’informations sur la prise en charge de la plateforme dans Office 365, voir [Configuration requise pour office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les versions les plus récentes des clients suivants prennent en charge l’accès conditionnel :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Portail Azure <br> ad](https://azure.microsoft.com/features/azure-portal/) | ![Icône accès](media/o365-access-64x64.png) <br> [Accès](https://products.office.com/access) | ![Icône portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Portail <br> d’entreprise](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Icône Delve](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [Cadre](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône de flux](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icône formulaires](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icône Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icône de l’objectif](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icône d’administrateur Office 365](media/o365-o365admin-64x64.png) <br> [Administrateur Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône du planificateur](media/o365-planner-64x64.png) <br> [Planificateur](https://products.office.com/business/task-management-software) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icône de projet](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icône Skype entreprise](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> entreprise](https://www.skype.com/business/) | ![Icône de pense-bête](media/o365-stickynotes-64x64.png) <br> [Notes du pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Icône de flux](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icône Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône teams](media/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône action](media/o365-todo-64x64.png) <br> [Action](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) 
| ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> la prise en charge de Delve sur Android est bientôt disponible. <br>
> <sup>2</sup> la prise en charge de OneDrive sur MacOS est bientôt disponible.
