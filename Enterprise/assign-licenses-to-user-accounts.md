---
title: Attribuer des licences Microsoft 365 à des comptes d’utilisateur
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Indique comment attribuer des licences Microsoft 365 à des comptes d’utilisateur, individuellement ou en fonction de l’appartenance au groupe.
ms.openlocfilehash: 3a51f4966cdcfede57ad8a69546face160ae1750
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230000"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Attribuer des licences Microsoft 365 à des comptes d’utilisateur

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Pour le modèle d’identité Cloud uniquement, vous pouvez attribuer des licences Microsoft 365 à des comptes d’utilisateur au fur et à mesure de leur création, en fonction de leur création.

Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur des services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, une licence Microsoft 365 n’est pas automatiquement attribuée à ces comptes. Vous devez d’abord configurer chaque compte d’utilisateur avec un emplacement utilisateur.

Dans les deux cas, vous devez attribuer une licence à des comptes d’utilisateurs pour permettre à vos utilisateurs d’accéder aux services Microsoft 365, tels que le courrier électronique et Microsoft Teams.

Vous pouvez attribuer des licences à des comptes d’utilisateur de manière individuelle ou automatique via l’appartenance à un groupe.

Pour attribuer des licences Microsoft 365 à des comptes d’utilisateur individuels, vous pouvez utiliser les éléments suivants :

- [Le Centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [PowerShell pour Microsoft 365](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Pour l’attribution automatique de licence, consultez la rubrique [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Étapes suivantes

À l’aide de l’ensemble complet des comptes d’utilisateur auxquels des licences ont été attribuées, vous êtes maintenant prêt à :

- [Implémenter la sécurité](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Déployer le logiciel client, tel que les applications Microsoft 365](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [Configurer la gestion des appareils mobiles dans Microsoft 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configurer les services et les applications](configure-services-and-applications.md)
