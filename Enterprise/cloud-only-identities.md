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
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="8111d-103">Identités Cloud Office 365 uniquement</span><span class="sxs-lookup"><span data-stu-id="8111d-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="8111d-104">Avec l’identité Cloud uniquement, tous vos utilisateurs, groupes et contacts sont stockés dans le client Azure Active Directory (Azure AD) de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="8111d-104">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="8111d-105">Voici les composants de base de l’identité en nuage uniquement.</span><span class="sxs-lookup"><span data-stu-id="8111d-105">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="8111d-106">Les utilisateurs et leurs comptes d’utilisateur dans les organisations peuvent être catégorisés de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="8111d-106">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="8111d-107">Par exemple, certains sont employés et ont un statut permanent.</span><span class="sxs-lookup"><span data-stu-id="8111d-107">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="8111d-108">Certains sont des fournisseurs, des sous-traitants ou des partenaires dont le statut est temporaire.</span><span class="sxs-lookup"><span data-stu-id="8111d-108">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="8111d-109">Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent toujours avoir accès à des ressources et des services spécifiques pour prendre en charge l’interaction et la collaboration.</span><span class="sxs-lookup"><span data-stu-id="8111d-109">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="8111d-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8111d-110">For example:</span></span>

- <span data-ttu-id="8111d-111">Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud</span><span class="sxs-lookup"><span data-stu-id="8111d-111">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="8111d-112">Les comptes B2B (Business to Business) représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration et qui prennent la place des utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="8111d-112">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="8111d-113">Quels sont les regroupements?</span><span class="sxs-lookup"><span data-stu-id="8111d-113">What are the groupings?</span></span> <span data-ttu-id="8111d-114">Par exemple, vous pouvez regrouper des utilisateurs selon des fonctions ou des objectifs de haut niveau pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="8111d-114">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="8111d-p104">Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.</span><span class="sxs-lookup"><span data-stu-id="8111d-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="8111d-117">Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins afin de simplifier la gestion de votre environnement Cloud.</span><span class="sxs-lookup"><span data-stu-id="8111d-117">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="8111d-118">Par exemple, avec les groupes Azure AD, vous pouvez:</span><span class="sxs-lookup"><span data-stu-id="8111d-118">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="8111d-119">Utilisez les licences basées sur les groupes pour attribuer automatiquement des licences pour Office 365 à vos comptes d’utilisateur dès qu’elles sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="8111d-119">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="8111d-120">ajouter des comptes d’utilisateur à des groupes spécifiques dynamiquement basés sur des attributs de compte d’utilisateur, comme l’attribut service ;</span><span class="sxs-lookup"><span data-stu-id="8111d-120">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="8111d-121">configurer automatiquement des utilisateurs pour des applications SaaS et protéger l’accès à ces applications avec l’authentification multifacteur et d’autres règles d’accès conditionnel ;</span><span class="sxs-lookup"><span data-stu-id="8111d-121">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="8111d-122">Mettre en service des autorisations et des niveaux d’accès pour les sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8111d-122">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="8111d-123">Vous pouvez créer des ***utilisateurs avec les*** éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="8111d-123">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="8111d-124">Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8111d-124">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="8111d-125">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8111d-125">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="8111d-126">Vous pouvez créer des ***groupes*** avec:</span><span class="sxs-lookup"><span data-stu-id="8111d-126">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="8111d-127">Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8111d-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="8111d-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8111d-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="8111d-129">Étape suivante pour les identités en nuage uniquement</span><span class="sxs-lookup"><span data-stu-id="8111d-129">Next step for cloud-only identities</span></span>

[<span data-ttu-id="8111d-130">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="8111d-130">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
