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
ms.openlocfilehash: f28b9a6367cec2f67b664db2d43ba55b9cf19638
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735932"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a><span data-ttu-id="c6b4d-103">Attribuer des licences Microsoft 365 à des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c6b4d-103">Assign Microsoft 365 licenses to user accounts</span></span>

<span data-ttu-id="c6b4d-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="c6b4d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c6b4d-105">Pour le modèle d’identité Cloud uniquement, vous pouvez attribuer des licences Microsoft 365 à des comptes d’utilisateur au fur et à mesure de leur création, en fonction de leur création.</span><span class="sxs-lookup"><span data-stu-id="c6b4d-105">For the cloud-only identity model, you can assign Microsoft 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="c6b4d-106">Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur des services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, une licence Microsoft 365 n’est pas automatiquement attribuée à ces comptes.</span><span class="sxs-lookup"><span data-stu-id="c6b4d-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license.</span></span> <span data-ttu-id="c6b4d-107">Vous devez d’abord configurer chaque compte d’utilisateur avec un emplacement utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c6b4d-107">You must first configure each user account with a user location.</span></span>

<span data-ttu-id="c6b4d-108">Dans les deux cas, vous devez attribuer une licence à des comptes d’utilisateurs pour permettre à vos utilisateurs d’accéder aux services Microsoft 365, tels que le courrier électronique et Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c6b4d-108">In either case, you must assign a license to user accounts so your users can access Microsoft 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="c6b4d-109">Vous pouvez attribuer des licences à des comptes d’utilisateur de manière individuelle ou automatique via l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="c6b4d-109">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="c6b4d-110">Pour attribuer des licences Microsoft 365 à des comptes d’utilisateur individuels, vous pouvez utiliser les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c6b4d-110">To assign Microsoft 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="c6b4d-111">Le Centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6b4d-111">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [<span data-ttu-id="c6b4d-112">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6b4d-112">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="c6b4d-113">Pour l’attribution automatique de licence, consultez la rubrique [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="c6b4d-113">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6b4d-114">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c6b4d-114">Next steps</span></span>

<span data-ttu-id="c6b4d-115">À l’aide de l’ensemble complet des comptes d’utilisateur auxquels des licences ont été attribuées, vous êtes maintenant prêt à :</span><span class="sxs-lookup"><span data-stu-id="c6b4d-115">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="c6b4d-116">Implémenter la sécurité</span><span class="sxs-lookup"><span data-stu-id="c6b4d-116">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="c6b4d-117">Déployer le logiciel client, tel que les applications Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6b4d-117">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="c6b4d-118">Configurer la gestion des appareils mobiles dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6b4d-118">Set up Mobile Device Management in Microsoft 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="c6b4d-119">Configurer les services et les applications</span><span class="sxs-lookup"><span data-stu-id="c6b4d-119">Configure services and applications</span></span>](configure-services-and-applications.md)
