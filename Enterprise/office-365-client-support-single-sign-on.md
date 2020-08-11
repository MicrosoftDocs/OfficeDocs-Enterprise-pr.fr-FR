---
title: Prise en charge des applications clientes Microsoft 365 — authentification unique
ms.author: josephd
author: JoeDavies-MSFT
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
description: Dans cet article, Découvrez les plateformes, les clients et les modules PowerShell qui prennent en charge l’authentification unique pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0f757c28695c46e6a960828914fff34c7fab5e9
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605646"
---
# <a name="microsoft-365-client-app-support--single-sign-on"></a>Prise en charge des applications clientes Microsoft 365 — authentification unique

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification unique (SSO) ajoute de la sécurité et de la commodité lorsque vos utilisateurs se connectent à des applications dans Azure Active Directory (Azure AD). Avec l’authentification unique, les utilisateurs se connectent une seule fois avec un compte pour accéder aux appareils joints au domaine, aux ressources de l’entreprise, aux applications SaaS (Software as a service) et aux applications Web.

En savoir plus sur l' [authentification unique](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau<sup>2</sup> Windows 10
 - Applications modernes Windows 10
 - Navigateurs Web
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS<sup>4</sup>

Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les versions les plus récentes des clients suivants prennent en charge l’authentification unique :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icône portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Portail d’entreprise <br> <sup>3, 4</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icône Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [Edge<sup>1</sup>](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Icône Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icône de l’objectif](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) 
| ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook<sup>4</sup>](https://products.office.com/outlook) | ![Icône planificateur](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icône de mise en marche automatique](media/o365-flow-64x64.png) <br> [Automate d’alimentation <br>](https://flow.microsoft.com) | ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icône Project](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icône de pense-bête](media/o365-stickynotes-64x64.png) <br> [Notes du pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw)  | ![Icône Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Icône Teams](media/o365-teams-64x64.png) <br> [Teams<sup>2, 4</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône action](media/o365-todo-64x64.png) <br> [Action](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône de tableau blanc](media/o365-whiteboard-64x64.png) <br> [Tableau blanc<sup>3</sup>](https://whiteboard.microsoft.com/) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> la prise en charge de Edge et de Kaizala sur iOS est bientôt disponible. <br>
> <sup>2</sup> la prise en charge de OneNote, de PowerBI, de teams et de Yammer sur le bureau Windows 10 bientôt disponible. <br>
> <sup>3</sup> la prise en charge du tableau blanc sur Android est bientôt disponible. <br>
> <sup>4</sup> la prise en charge d’Outlook, de teams et du portail d’entreprise sur MacOS est bientôt disponible. <br>

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
