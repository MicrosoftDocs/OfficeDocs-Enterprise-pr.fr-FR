---
title: Prise en charge des applications clientes Microsoft 365 — accès conditionnel
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: Comprendre la prise en charge des applications clientes Microsoft 365 pour l’accès conditionnel
ms.openlocfilehash: 6081af2ad3bca69978a10baabeae0a13d783f0ae
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998502"
---
# <a name="microsoft-365-client-app-support--conditional-access"></a>Prise en charge des applications clientes Microsoft 365 — accès conditionnel

Dans l’espace de travail moderne, les utilisateurs peuvent accéder aux ressources de votre organisation à l’aide de divers appareils et applications depuis n’importe quel endroit. Par conséquent, il ne suffit plus de se concentrer sur qui peut accéder à une ressource. Votre organisation doit également prendre en charge la façon et l’emplacement d’accès à une ressource dans votre infrastructure de contrôle d’accès.

Avec un appareil Azure Active Directory (Azure AD), un emplacement et un accès conditionnel multi-facteur basé sur l’authentification, vous pouvez répondre à cette nouvelle exigence. L’accès conditionnel est une fonctionnalité d’Azure AD. Elle vous permet d’appliquer des contrôles sur l’accès aux applications dans votre environnement, le tout en fonction de conditions définies et reposant sur une gestion à partir d’un emplacement central.

En savoir plus sur l’[accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Plateformes prises en charge

 - Bureau Windows 10
 - Applications modernes Windows 10
 - Navigateurs Web
 - Android
 - iOS
 - macOS<sup>1</sup>

Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clients pris en charge

Les versions les plus récentes des clients suivants prennent en charge l’accès conditionnel :

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Portail Azure AD <br>](https://azure.microsoft.com/features/azure-portal/) | ![Icône Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icône portail d’entreprise](media/o365-microsoft-64x64.png) <br> [Portail d’entreprise <br>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Icône Cortana](media/o365-cortana-64x64.png) <br> [Auxquelles](https://www.microsoft.com/cortana) | ![Icône Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) 
| ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Icône Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icône Forms](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icône Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icône de l’objectif](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icône d’administrateur Office 365](media/o365-o365admin-64x64.png) <br> [Administrateur 365 Microsoft <br>](https://products.office.com/business/manage-office-365-admin-app) | ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icône planificateur](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icône PowerApp](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icône de mise en marche automatique](media/o365-flow-64x64.png) <br> [Automate d’alimentation <br>](https://flow.microsoft.com)
| ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icône Project](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icône Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) 
| ![Icône Skype Entreprise](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> entreprise](https://www.skype.com/business/) | ![Icône de pense-bête](media/o365-stickynotes-64x64.png) <br> [Notes du pense-bête](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icône Stream](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icône Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icône Teams](media/o365-teams-64x64.png) <br> [Équipes](https://products.office.com/microsoft-teams/group-chat-software) 
| ![Icône action](media/o365-todo-64x64.png) <br> [Action](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icône Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icône Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icône Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icône de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> la prise en charge de OneDrive sur MacOS est bientôt disponible.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
