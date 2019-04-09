---
title: Prise en charge de l'application cliente Office 365-gestion des applications mobiles
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Comprendre la prise en charge de l'application cliente Office 365 pour la gestion des applications mobiles
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517548"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="d2bc0-103">Prise en charge de l'application cliente Office 365-gestion des applications mobiles</span><span class="sxs-lookup"><span data-stu-id="d2bc0-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="d2bc0-104">En tirant parti de la suite de fonctionnalités de gestion Intune, la gestion des applications mobiles (MAM) vous permet de publier, de diffuser, de configurer, de sécuriser, de surveiller et de mettre à jour les applications mobiles pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d2bc0-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="d2bc0-105">MAM peut protéger les données d'une organisation dans une application pour tous les appareils, qu'ils soient inclus dans Intune ou non.</span><span class="sxs-lookup"><span data-stu-id="d2bc0-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="d2bc0-106">En savoir plus sur la [gestion des applications mobiles](https://docs.microsoft.com/intune/mam-faq) et les [Mam à identités multiples](https://docs.microsoft.com/intune/app-protection-policy).</span><span class="sxs-lookup"><span data-stu-id="d2bc0-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="d2bc0-107">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="d2bc0-107">Supported platforms</span></span>

 - <span data-ttu-id="d2bc0-108">Android</span><span class="sxs-lookup"><span data-stu-id="d2bc0-108">Android</span></span>
 - <span data-ttu-id="d2bc0-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d2bc0-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="d2bc0-110">Pour plus d'informations sur la prise en charge de la plateforme dans Office 365, voir [Configuration requise pour office 365](https://products.office.com/office-system-requirements).</span><span class="sxs-lookup"><span data-stu-id="d2bc0-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="d2bc0-111">Clients pris en charge</span><span class="sxs-lookup"><span data-stu-id="d2bc0-111">Supported clients</span></span>

<span data-ttu-id="d2bc0-112">Les versions les plus récentes des clients suivants prennent en charge la gestion des applications mobiles:</span><span class="sxs-lookup"><span data-stu-id="d2bc0-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icône Dynamics 365](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="d2bc0-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="d2bc0-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![Icône de serveur Edge](media/o365-edge-64x64.png) <br> [<span data-ttu-id="d2bc0-116">Bord</span><span class="sxs-lookup"><span data-stu-id="d2bc0-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![Icône Excel](media/o365-excel-64x64.png) <br> [<span data-ttu-id="d2bc0-118">Excel</span><span class="sxs-lookup"><span data-stu-id="d2bc0-118">Excel</span></span>](https://products.office.com/excel) | ![Icône de flux](media/o365-flow-64x64.png) <br> [<span data-ttu-id="d2bc0-120">Flux</span><span class="sxs-lookup"><span data-stu-id="d2bc0-120">Flow</span></span>](https://flow.microsoft.com) | ![Icône Kaizala](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="d2bc0-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="d2bc0-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icône OneDrive entreprise](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="d2bc0-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="d2bc0-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icône OneNote](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="d2bc0-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="d2bc0-126">OneNote</span></span>](https://products.office.com/onenote) | ![Icône Outlook](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="d2bc0-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="d2bc0-128">Outlook</span></span>](https://products.office.com/outlook) | ![Icône du planificateur](media/o365-planner-64x64.png) <br> [<span data-ttu-id="d2bc0-130">Planificateur</span><span class="sxs-lookup"><span data-stu-id="d2bc0-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![Icône PowerApp](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="d2bc0-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="d2bc0-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![Icône PowerBI](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="d2bc0-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="d2bc0-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![Icône PowerPoint](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="d2bc0-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="d2bc0-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![Icône SharePoint](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="d2bc0-138">SharePoint</span><span class="sxs-lookup"><span data-stu-id="d2bc0-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![Icône Skype entreprise](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="d2bc0-140">Skype <br> entreprise</span><span class="sxs-lookup"><span data-stu-id="d2bc0-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![Icône StaffHub](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="d2bc0-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="d2bc0-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![Icône de flux](media/o365-stream-64x64.png) <br> [<span data-ttu-id="d2bc0-144">Stream</span><span class="sxs-lookup"><span data-stu-id="d2bc0-144">Stream</span></span>](https://stream.microsoft.com) | ![Icône Sway](media/o365-sway-64x64.png) <br> [<span data-ttu-id="d2bc0-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d2bc0-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![Icône teams](media/o365-teams-64x64.png) <br> [<span data-ttu-id="d2bc0-148">Équipes</span><span class="sxs-lookup"><span data-stu-id="d2bc0-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![Icône action](media/o365-todo-64x64.png) <br> [<span data-ttu-id="d2bc0-150">To-Do</span><span class="sxs-lookup"><span data-stu-id="d2bc0-150">To-Do</span></span>](https://todo.microsoft.com) | ![Icône Visio](media/o365-visio-64x64.png) <br> [<span data-ttu-id="d2bc0-152">Visio</span><span class="sxs-lookup"><span data-stu-id="d2bc0-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![Icône Word](media/o365-word-64x64.png) <br> [<span data-ttu-id="d2bc0-154">Word</span><span class="sxs-lookup"><span data-stu-id="d2bc0-154">Word</span></span>](https://products.office.com/word) | ![Icône Yammer](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="d2bc0-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="d2bc0-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="d2bc0-157"><sup>1</sup> prise en charge de Sway sur iOS bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="d2bc0-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>