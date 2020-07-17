---
title: Identité Cloud Microsoft 365 uniquement
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
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
description: Indique comment créer des utilisateurs et des groupes lorsque votre abonnement Microsoft 365 utilise l’identité de Cloud uniquement.
ms.openlocfilehash: f510d82186e9a44c20bd20f1c7b5a7a44c8b765b
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774829"
---
# <a name="microsoft-365-cloud-only-identity"></a><span data-ttu-id="76393-103">Identité Cloud Microsoft 365 uniquement</span><span class="sxs-lookup"><span data-stu-id="76393-103">Microsoft 365 cloud-only identity</span></span>

<span data-ttu-id="76393-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="76393-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="76393-105">Avec l’identité Cloud uniquement, tous vos utilisateurs, groupes et contacts sont stockés dans le client Azure Active Directory (Azure AD) de votre abonnement Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="76393-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="76393-106">Voici les composants de base de l’identité en nuage uniquement.</span><span class="sxs-lookup"><span data-stu-id="76393-106">Here are the basic components of cloud-only identity.</span></span>
 
![Composants de base de l’identité en nuage uniquement](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="76393-108">Les utilisateurs et leurs comptes d’utilisateur dans les organisations peuvent être catégorisés de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="76393-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="76393-109">Par exemple, certains sont employés et ont un statut permanent.</span><span class="sxs-lookup"><span data-stu-id="76393-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="76393-110">Certains sont des fournisseurs, des sous-traitants ou des partenaires dont le statut est temporaire.</span><span class="sxs-lookup"><span data-stu-id="76393-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="76393-111">Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent toujours avoir accès à des ressources et des services spécifiques pour prendre en charge l’interaction et la collaboration.</span><span class="sxs-lookup"><span data-stu-id="76393-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="76393-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="76393-112">For example:</span></span>

- <span data-ttu-id="76393-113">Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud</span><span class="sxs-lookup"><span data-stu-id="76393-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="76393-114">Les comptes B2B représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration</span><span class="sxs-lookup"><span data-stu-id="76393-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration</span></span>

<span data-ttu-id="76393-115">Prenez le stock des types d’utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="76393-115">Take stock of the types of users in your organization.</span></span> <span data-ttu-id="76393-116">Quels sont les regroupements ?</span><span class="sxs-lookup"><span data-stu-id="76393-116">What are the groupings?</span></span> <span data-ttu-id="76393-117">Par exemple, vous pouvez regrouper des utilisateurs selon des fonctions ou des objectifs de haut niveau pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="76393-117">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="76393-p104">Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.</span><span class="sxs-lookup"><span data-stu-id="76393-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="76393-120">Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins afin de simplifier la gestion de votre environnement Cloud.</span><span class="sxs-lookup"><span data-stu-id="76393-120">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="76393-121">Par exemple, avec les groupes Azure AD, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="76393-121">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="76393-122">Utilisez les licences basées sur les groupes pour attribuer automatiquement des licences pour Microsoft 365 à vos comptes d’utilisateur dès qu’elles sont ajoutées en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="76393-122">Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.</span></span>
- <span data-ttu-id="76393-123">Ajouter des comptes d’utilisateurs à des groupes spécifiques de manière dynamique en fonction des attributs de compte d’utilisateur, tels que le nom du service.</span><span class="sxs-lookup"><span data-stu-id="76393-123">Add user accounts to specific groups dynamically based on user account attributes, such as department name.</span></span>
- <span data-ttu-id="76393-124">Approvisionner automatiquement les utilisateurs pour les applications SaaS (Software as a service) et protéger l’accès à ces applications à l’aide de l’authentification multifacteur (MFA) et d’autres règles d’accès conditionnel.</span><span class="sxs-lookup"><span data-stu-id="76393-124">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access rules.</span></span>
- <span data-ttu-id="76393-125">Mettre en service des autorisations et des niveaux d’accès pour les sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="76393-125">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="76393-126">Vous créez des ***utilisateurs*** avec :</span><span class="sxs-lookup"><span data-stu-id="76393-126">You create new ***users*** with:</span></span>

- [<span data-ttu-id="76393-127">Le Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="76393-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="76393-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="76393-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="76393-129">Vous créez des ***groupes*** avec :</span><span class="sxs-lookup"><span data-stu-id="76393-129">You create new ***groups*** with:</span></span>

- [<span data-ttu-id="76393-130">Le Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="76393-130">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="76393-131">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="76393-131">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a><span data-ttu-id="76393-132">Étape suivante pour l’identité Cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="76393-132">Next step for cloud-only identity</span></span>

[<span data-ttu-id="76393-133">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="76393-133">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
