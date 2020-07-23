---
title: Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell
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
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 'Résumé : Découvrez comment gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell.'
ms.openlocfilehash: 26da0d13ecc9c14be4abe059943bd91d88126f1e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230410"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="bb3c5-103">Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb3c5-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="bb3c5-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="bb3c5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="bb3c5-105">L’une des principales tâches des administrateurs de Microsoft 365 est la gestion des comptes d’utilisateur, des licences et des groupes.</span><span class="sxs-lookup"><span data-stu-id="bb3c5-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="bb3c5-106">Bien que vous puissiez accomplir la plupart des aspects de ces tâches dans le centre d’administration 365 de Microsoft, les autres tâches sont beaucoup plus rapides et plus faciles avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb3c5-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="bb3c5-107">Pour plus d’informations, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="bb3c5-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="bb3c5-108">Comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-108">User accounts</span></span>

- [<span data-ttu-id="bb3c5-109">Création de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-110">Affichage de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-111">Configuration des propriétés de compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="bb3c5-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-112">Attribution de rôles aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-113">Suppression et restauration de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-114">Blocage de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="bb3c5-115">Licences et services</span><span class="sxs-lookup"><span data-stu-id="bb3c5-115">Licenses and services</span></span>
- [<span data-ttu-id="bb3c5-116">Affichage des licences et des services</span><span class="sxs-lookup"><span data-stu-id="bb3c5-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-117">Affichage des utilisateurs sous licence et sans licence</span><span class="sxs-lookup"><span data-stu-id="bb3c5-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-118">Attribution de licences aux comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-119">Affichage des détails de service et de licence de compte</span><span class="sxs-lookup"><span data-stu-id="bb3c5-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-120">Désactivation de l’accès aux services</span><span class="sxs-lookup"><span data-stu-id="bb3c5-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="bb3c5-121">Désactivation de l’accès à Sway</span><span class="sxs-lookup"><span data-stu-id="bb3c5-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="bb3c5-122">Désactivation de l’accès aux services lors de l’attribution des licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="bb3c5-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="bb3c5-123">Suppression de licences à des comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bb3c5-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="bb3c5-124">Groupes</span><span class="sxs-lookup"><span data-stu-id="bb3c5-124">Groups</span></span>
- [<span data-ttu-id="bb3c5-125">Maintenir l’appartenance à un groupe</span><span class="sxs-lookup"><span data-stu-id="bb3c5-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="bb3c5-126">Gérer les groupes Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bb3c5-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

