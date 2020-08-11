---
title: Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: Dans cet article, Découvrez comment gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell.
ms.openlocfilehash: b5a2d43ad4dee3a70f934f9fc52b93e7c99f3644
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605880"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="99cca-103">Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="99cca-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="99cca-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="99cca-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="99cca-105">L’une des principales tâches des administrateurs de Microsoft 365 est la gestion des comptes d’utilisateur, des licences et des groupes.</span><span class="sxs-lookup"><span data-stu-id="99cca-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="99cca-106">Bien que vous puissiez accomplir la plupart des aspects de ces tâches dans le centre d’administration 365 de Microsoft, les autres tâches sont beaucoup plus rapides et plus faciles avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99cca-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="99cca-107">Pour plus d’informations, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="99cca-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="99cca-108">Comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="99cca-108">User accounts</span></span>

- [<span data-ttu-id="99cca-109">Création de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-110">Affichage de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-111">Configuration des propriétés de compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="99cca-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-112">Attribution de rôles aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-113">Suppression et restauration de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-114">Blocage de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="99cca-115">Licences et services</span><span class="sxs-lookup"><span data-stu-id="99cca-115">Licenses and services</span></span>
- [<span data-ttu-id="99cca-116">Affichage des licences et des services</span><span class="sxs-lookup"><span data-stu-id="99cca-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-117">Affichage des utilisateurs sous licence et sans licence</span><span class="sxs-lookup"><span data-stu-id="99cca-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-118">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-119">Affichage des détails de service et de licence de compte</span><span class="sxs-lookup"><span data-stu-id="99cca-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-120">Désactivation de l’accès aux services</span><span class="sxs-lookup"><span data-stu-id="99cca-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="99cca-121">Désactivation de l’accès à Sway</span><span class="sxs-lookup"><span data-stu-id="99cca-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="99cca-122">Désactivation de l’accès aux services lors de l’attribution des licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="99cca-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="99cca-123">Suppression de licences à des comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="99cca-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="99cca-124">Groupes</span><span class="sxs-lookup"><span data-stu-id="99cca-124">Groups</span></span>
- [<span data-ttu-id="99cca-125">Maintenir l’appartenance à un groupe</span><span class="sxs-lookup"><span data-stu-id="99cca-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="99cca-126">Gestion des groupes Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="99cca-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

