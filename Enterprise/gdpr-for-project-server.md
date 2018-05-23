---
title: RGPD pour Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment satisfaire aux exigences du RGPD dans l’environnement Project Server local.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="a05b0-103">RGPD pour Project Server</span><span class="sxs-lookup"><span data-stu-id="a05b0-103">Operations for Project Server</span></span>

<span data-ttu-id="a05b0-p101">Project Server utilise des scripts personnalisés pour exporter et supprimer des données utilisateur dans Project Web App. Le processus de base est le suivant :</span><span class="sxs-lookup"><span data-stu-id="a05b0-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="a05b0-106">Recherchez les sites Project Web App dans votre batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="a05b0-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="a05b0-107">Recherchez les projets dans chaque site contenant l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a05b0-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="a05b0-108">Exportez et passez en revue les types de données que vous voulez examiner.</span><span class="sxs-lookup"><span data-stu-id="a05b0-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="a05b0-109">Supprimez des données si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a05b0-109">Redact data as needed.</span></span>

<span data-ttu-id="a05b0-110">Ces étapes sont expliquées en détail dans les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="a05b0-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="a05b0-111">Exportation de données utilisateur depuis Project Server</span><span class="sxs-lookup"><span data-stu-id="a05b0-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="a05b0-112">Suppression de données utilisateur de Project Server</span><span class="sxs-lookup"><span data-stu-id="a05b0-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="a05b0-113">Notez que Project Server est basé sur SharePoint Server et consigne les événements dans les journaux ULS de SharePoint et dans la base de données d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a05b0-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
