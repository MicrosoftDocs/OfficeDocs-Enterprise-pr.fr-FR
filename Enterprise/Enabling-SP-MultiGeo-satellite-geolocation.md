---
title: Activation de SharePoint Multi-Geo dans votre emplacement géographique satellite
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Activation de SharePoint Multi-Geo dans votre emplacement satellite géographique.
ms.openlocfilehash: f5f7137f64f26ce324894ee80b5dfb2f46888889
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41848757"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="82fa6-103">Activation de SharePoint Multi-Geo dans votre emplacement géographique satellite</span><span class="sxs-lookup"><span data-stu-id="82fa6-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="82fa6-104">Cet article est destiné aux administrateurs généraux ou SharePoint qui ont créé un emplacement satellite géo multiple **avant** les fonctionnalités SharePoint Multi-géo sont devenues généralement disponibles le 27 mars 2019 et n’ont pas activé SharePoint multi-Geo dans leurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="82fa6-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="82fa6-105">Si vous avez ajouté un nouvel emplacement géo **après le 27 mars**, vous n’avez pas besoin effectuer ces instructions car votre nouvel emplacement géo sera déjà activé pour OneDrive et SharePoint Multi-géo.</span><span class="sxs-lookup"><span data-stu-id="82fa6-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="82fa6-106">Ces instructions permettent d’activer SharePoint dans votre emplacement satellite, vos utilisateurs satellite géo multiple peuvent tirer parti des fonctionnalités OneDrive et SharePoint Multi-géo dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="82fa6-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="82fa6-107">Veuillez noter qu’il s’agit d’une activation possible.</span><span class="sxs-lookup"><span data-stu-id="82fa6-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="82fa6-108">Une fois que vous définissez le mode SharePoint Online, vous ne pouvez pas revenir vers votre client OneDrive uniquement en mode multiple géo sans une escalade avec une prise en charge.</span><span class="sxs-lookup"><span data-stu-id="82fa6-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="82fa6-109">Pour définir l’emplacement géo en mode SPO</span><span class="sxs-lookup"><span data-stu-id="82fa6-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="82fa6-110">Pour définir un emplacement géo en mode SPO, connectez-vous à l’emplacement géo que vous souhaitez définir en Mode SPO :</span><span class="sxs-lookup"><span data-stu-id="82fa6-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="82fa6-111">Ouvrez votre outil SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="82fa6-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="82fa6-112">Se connecter-SPOService-URL « https://$tenantGeo-admin.sharepoint.com »- informations d’identification $credential</span><span class="sxs-lookup"><span data-stu-id="82fa6-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="82fa6-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="82fa6-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="82fa6-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="82fa6-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="82fa6-115">Cette opération généralement prend environ une heure pendant que nous réalisons divers publications dans le service et de nouveau apposer un cachet à votre client.</span><span class="sxs-lookup"><span data-stu-id="82fa6-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="82fa6-116">Après au moins 1 heure, veuillez effectuer une SPOMultiGeoExperience Get.</span><span class="sxs-lookup"><span data-stu-id="82fa6-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="82fa6-117">Vous verrez alors que cet emplacement géo est en mode SPO.</span><span class="sxs-lookup"><span data-stu-id="82fa6-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="82fa6-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="82fa6-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="82fa6-119">Certains caches dans le service se mettent à jour toutes les 24 heures, il est donc possible que pendant une période de 24 heures, votre géo satellite peut, par intermittence, se comporter comme s’il s’agit en mode ODB.</span><span class="sxs-lookup"><span data-stu-id="82fa6-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="82fa6-120">Cela n’entraîne pas de problème d’ordre technique.</span><span class="sxs-lookup"><span data-stu-id="82fa6-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="82fa6-121">Pour plus d’informations concernant SharePoint Multi-géo, veuillez consulter [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span><span class="sxs-lookup"><span data-stu-id="82fa6-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


