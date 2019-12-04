---
title: Identités Cloud Office 365 uniquement
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
ms.openlocfilehash: 6815c89821216416379a27eb525e66b90b828ea8
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813412"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="a8ef6-103">Identités Cloud Office 365 uniquement</span><span class="sxs-lookup"><span data-stu-id="a8ef6-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="a8ef6-104">*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="a8ef6-105">Avec l’identité Cloud uniquement, tous vos utilisateurs, groupes et contacts sont stockés dans le client Azure Active Directory (Azure AD) de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="a8ef6-106">Voici les composants de base de l’identité en nuage uniquement.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-106">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="a8ef6-107">Les utilisateurs et leurs comptes d’utilisateur dans les organisations peuvent être catégorisés de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-107">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="a8ef6-108">Par exemple, certains sont employés et ont un statut permanent.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-108">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="a8ef6-109">Certains sont des fournisseurs, des sous-traitants ou des partenaires dont le statut est temporaire.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-109">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="a8ef6-110">Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent toujours avoir accès à des ressources et des services spécifiques pour prendre en charge l’interaction et la collaboration.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-110">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="a8ef6-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a8ef6-111">For example:</span></span>

- <span data-ttu-id="a8ef6-112">Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud</span><span class="sxs-lookup"><span data-stu-id="a8ef6-112">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="a8ef6-113">Les comptes B2B (Business to Business) représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration et qui prennent la place des utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-113">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="a8ef6-114">Quels sont les regroupements ?</span><span class="sxs-lookup"><span data-stu-id="a8ef6-114">What are the groupings?</span></span> <span data-ttu-id="a8ef6-115">Par exemple, vous pouvez regrouper des utilisateurs selon des fonctions ou des objectifs de haut niveau pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-115">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="a8ef6-p104">Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="a8ef6-118">Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins afin de simplifier la gestion de votre environnement Cloud.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-118">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="a8ef6-119">Par exemple, avec les groupes Azure AD, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="a8ef6-119">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="a8ef6-120">Utilisez les licences basées sur les groupes pour attribuer automatiquement des licences pour Office 365 à vos comptes d’utilisateur dès qu’elles sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-120">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="a8ef6-121">ajouter des comptes d’utilisateur à des groupes spécifiques dynamiquement basés sur des attributs de compte d’utilisateur, comme l’attribut service ;</span><span class="sxs-lookup"><span data-stu-id="a8ef6-121">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="a8ef6-122">configurer automatiquement des utilisateurs pour des applications SaaS et protéger l’accès à ces applications avec l’authentification multifacteur et d’autres règles d’accès conditionnel ;</span><span class="sxs-lookup"><span data-stu-id="a8ef6-122">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="a8ef6-123">Mettre en service des autorisations et des niveaux d’accès pour les sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a8ef6-123">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="a8ef6-124">Vous pouvez créer des ***utilisateurs avec les*** éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a8ef6-124">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="a8ef6-125">Le Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a8ef6-125">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="a8ef6-126">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8ef6-126">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="a8ef6-127">Vous pouvez créer des ***groupes*** avec :</span><span class="sxs-lookup"><span data-stu-id="a8ef6-127">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="a8ef6-128">Le Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a8ef6-128">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="a8ef6-129">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8ef6-129">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="a8ef6-130">Étape suivante pour les identités en nuage uniquement</span><span class="sxs-lookup"><span data-stu-id="a8ef6-130">Next step for cloud-only identities</span></span>

[<span data-ttu-id="a8ef6-131">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a8ef6-131">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
