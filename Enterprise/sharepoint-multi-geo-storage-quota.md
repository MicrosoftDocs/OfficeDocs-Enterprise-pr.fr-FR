---
title: Quotas de stockage SharePoint dans des environnements multigéographiques
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez les quotas de stockage SharePoint dans des environnements multigéographiques.
ms.openlocfilehash: a9ccc32940293dcd11e2f3b89607950f7b6ae3f0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070750"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="a3fd3-103">Quotas de stockage SharePoint dans des environnements multigéographiques</span><span class="sxs-lookup"><span data-stu-id="a3fd3-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="a3fd3-104">Par défaut, tous les emplacements géographiques d’un environnement multigéographique partagent le quota de stockage disponible du locataire.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="a3fd3-105">Avec le paramètre de quota de stockage de zone géographique SharePoint, vous pouvez gérer le quota de stockage de chaque emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="a3fd3-106">Lorsque vous allouez un quota de stockage à un emplacement géographique, ce quota devient le volume maximal de stockage disponible pour cet emplacement géographique, et est déduit du quota de stockage disponible du locataire.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="a3fd3-107">Le quota de stockage disponible restant du client est ensuite partagé entre les emplacements géographiques configurés auxquels aucun quota de stockage spécifique n’a pas été alloué.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="a3fd3-108">L’administrateur SharePoint Online peut allouer le quota de stockage SharePoint de tout emplacement géographique en se connectant à l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="a3fd3-109">Les administrateurs géographiques des emplacements satellites peuvent consulter le quota de stockage mais ne peuvent pas l’allouer.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="a3fd3-110">Configurer un quota de stockage pour un emplacement géographique</span><span class="sxs-lookup"><span data-stu-id="a3fd3-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="a3fd3-111">Utilisez le [Module Microsoft Office SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) pour vous connecter à l’emplacement central afin d’allouer le quota de stockage d’un emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="a3fd3-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="a3fd3-112">Pour allouer un quota de stockage à un emplacement, exécutez la cmdlet suivante :</span><span class="sxs-lookup"><span data-stu-id="a3fd3-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="a3fd3-113">Pour afficher le quota de stockage de l’emplacement géographique actuel, exécutez la cmdlet suivante :</span><span class="sxs-lookup"><span data-stu-id="a3fd3-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Capture d’écran d’une fenêtre de PowerShell affichant la cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="a3fd3-115">Pour afficher le quota de stockage de tous les emplacements géographiques, exécutez la cmdlet suivante :</span><span class="sxs-lookup"><span data-stu-id="a3fd3-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="a3fd3-116">Pour supprimer le quota de stockage alloué à un emplacement géographique, définissez `StorageQuota value = 0` :</span><span class="sxs-lookup"><span data-stu-id="a3fd3-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
