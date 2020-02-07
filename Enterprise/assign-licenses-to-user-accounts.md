---
title: Affecter des licences Office 365 à des comptes d’utilisateur
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
description: Indique comment attribuer des licences Office 365 à des comptes d’utilisateur, individuellement ou en fonction de l’appartenance à un groupe.
ms.openlocfilehash: 3ffd51b6b3ab4add900746f14f013a307ca352ad
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843785"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Affecter des licences Office 365 à des comptes d’utilisateur

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Pour le modèle d’identité Cloud uniquement, vous pouvez attribuer des licences Office 365 à des comptes d’utilisateur au fur et à mesure de leur création, en fonction de leur création.

Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur des services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, une licence Office 365 n’est pas automatiquement attribuée à ces comptes.

Dans les deux cas, vous devez attribuer une licence aux comptes d’utilisateurs pour permettre à vos utilisateurs d’accéder aux services Office 365, tels que le courrier électronique et Microsoft Teams.

Vous pouvez attribuer des licences à des comptes d’utilisateur de manière individuelle ou automatique via l’appartenance à un groupe.

Pour attribuer des licences Office 365 à des comptes d’utilisateur individuels, vous pouvez utiliser les éléments suivants :

- [Le Centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Pour l’attribution automatique de licence, consultez la rubrique [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Étapes suivantes

À l’aide de l’ensemble complet des comptes d’utilisateur auxquels des licences ont été attribuées, vous êtes maintenant prêt à :

- [Implémenter la sécurité](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Déployer le logiciel client, tel qu’Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Configurer la gestion des appareils mobiles dans Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configurer les services et les applications](configure-services-and-applications.md)
