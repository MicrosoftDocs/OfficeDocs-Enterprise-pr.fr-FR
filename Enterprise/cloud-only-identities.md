---
title: Identités Cloud Office 365 uniquement
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Indique comment créer des utilisateurs et des groupes lorsque votre abonnement Office 365 utilise des identités de Cloud uniquement.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164609"
---
# <a name="office-365-cloud-only-identities"></a>Identités Cloud Office 365 uniquement

Avec l’identité Cloud uniquement, tous vos utilisateurs, groupes et contacts sont stockés dans le client Azure Active Directory (Azure AD) de votre abonnement Office 365. Voici les composants de base de l’identité en nuage uniquement.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

Les utilisateurs et leurs comptes d’utilisateur dans les organisations peuvent être catégorisés de plusieurs façons. Par exemple, certains sont employés et ont un statut permanent. Certains sont des fournisseurs, des sous-traitants ou des partenaires dont le statut est temporaire. Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent toujours avoir accès à des ressources et des services spécifiques pour prendre en charge l’interaction et la collaboration. Par exemple :

- Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud

- Les comptes B2B (Business to Business) représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration et qui prennent la place des utilisateurs de votre organisation. Quels sont les regroupements? Par exemple, vous pouvez regrouper des utilisateurs selon des fonctions ou des objectifs de haut niveau pour votre organisation.

Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.

Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins afin de simplifier la gestion de votre environnement Cloud. Par exemple, avec les groupes Azure AD, vous pouvez:

- Utilisez les licences basées sur les groupes pour attribuer automatiquement des licences pour Office 365 à vos comptes d’utilisateur dès qu’elles sont ajoutées.
- ajouter des comptes d’utilisateur à des groupes spécifiques dynamiquement basés sur des attributs de compte d’utilisateur, comme l’attribut service ;
- configurer automatiquement des utilisateurs pour des applications SaaS et protéger l’accès à ces applications avec l’authentification multifacteur et d’autres règles d’accès conditionnel ;
- Mettre en service des autorisations et des niveaux d’accès pour les sites d’équipe SharePoint Online.

Vous pouvez créer des ***utilisateurs avec les*** éléments suivants:

- [Centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

Vous pouvez créer des ***groupes*** avec:

- [Centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>Étape suivante pour les identités en nuage uniquement

[Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
