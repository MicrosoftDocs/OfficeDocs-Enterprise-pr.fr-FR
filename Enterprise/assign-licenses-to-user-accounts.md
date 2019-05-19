---
title: Affecter des licences Office 365 à des comptes d’utilisateur
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
description: Indique comment attribuer des licences Office 365 à des comptes d’utilisateur, individuellement ou en fonction de l’appartenance à un groupe.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164599"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="be2a2-103">Affecter des licences Office 365 à des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="be2a2-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="be2a2-104">Pour le modèle d’identité Cloud uniquement, vous pouvez attribuer des licences Office 365 à des comptes d’utilisateur au fur et à mesure de leur création, en fonction de leur création.</span><span class="sxs-lookup"><span data-stu-id="be2a2-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="be2a2-105">Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur des services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, une licence Office 365 n’est pas automatiquement attribuée à ces comptes.</span><span class="sxs-lookup"><span data-stu-id="be2a2-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="be2a2-106">Dans les deux cas, vous devez attribuer une licence aux comptes d’utilisateurs pour permettre à vos utilisateurs d’accéder aux services Office 365, tels que le courrier électronique et Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="be2a2-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="be2a2-107">Vous pouvez attribuer des licences à des comptes d’utilisateur de manière individuelle ou automatique via l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="be2a2-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="be2a2-108">Pour attribuer des licences Office 365 à des comptes d’utilisateur individuels, vous pouvez utiliser les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="be2a2-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="be2a2-109">Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="be2a2-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="be2a2-110">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be2a2-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="be2a2-111">Pour l’attribution automatique de licence, consultez la rubrique [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="be2a2-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="be2a2-112">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="be2a2-112">Next steps</span></span>

<span data-ttu-id="be2a2-113">À l’aide de l’ensemble complet des comptes d’utilisateur auxquels des licences ont été attribuées, vous êtes maintenant prêt à:</span><span class="sxs-lookup"><span data-stu-id="be2a2-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="be2a2-114">Déployer le logiciel client, tel qu’Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="be2a2-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="be2a2-115">Configurer la gestion des appareils mobiles</span><span class="sxs-lookup"><span data-stu-id="be2a2-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="be2a2-116">Configurer les services et les applications</span><span class="sxs-lookup"><span data-stu-id="be2a2-116">Configure services and applications</span></span>](configure-services-and-applications.md)
