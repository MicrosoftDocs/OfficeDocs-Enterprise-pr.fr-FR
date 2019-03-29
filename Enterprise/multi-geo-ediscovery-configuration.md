---
title: Configurer l’eDiscovery d’Office 365 multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Découvrez comment configurer l’eDiscovery dans Office 365 multigéographique.
ms.openlocfilehash: 11d226605ba1f194393405edd5bb535da6ad7343
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933986"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="ef3b7-103">Configuration de l’eDiscovery d’Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="ef3b7-103">Office 365 Multi-Geo eDiscovery configuration</span></span>


<span data-ttu-id="ef3b7-p101">Par défaut, un gestionnaire ou un administrateur eDiscovery d’un client multigéographique peut mettre en place un processus eDiscovery uniquement dans l’emplacement central de ce client. Pour pouvoir mettre en place un processus eDiscovery dans les emplacements satellites, il existe un nouveau paramètre Filtre de sécurité de conformité appelé « Région » dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3b7-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="ef3b7-106">L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre « Région » dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite.</span><span class="sxs-lookup"><span data-stu-id="ef3b7-106">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="ef3b7-p102">Quand un gestionnaire ou un administrateur eDiscovery est défini pour un emplacement satellite particulier, ce gestionnaire ou cet administrateur eDiscovery peut uniquement effectuer des actions de recherche eDiscovery dans les sites SharePoint et OneDrive situés dans cet emplacement satellite. Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de l’emplacement satellite spécifié, aucun résultat n’est renvoyé. Par ailleurs, lorsque le gestionnaire ou l’administrateur eDiscovery d’un emplacement satellite déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Ainsi, les entreprises respectent les règles de conformité en interdisant l’exportation de contenu au-delà de frontières contrôlées.</span><span class="sxs-lookup"><span data-stu-id="ef3b7-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="ef3b7-111">Si un gestionnaire eDiscovery doit effectuer des recherches dans plusieurs emplacements satellites SharePoint, un autre compte d’utilisateur doit être créé pour ce gestionnaire, lequel doit indiquer un autre emplacement satellite où sont situés les sites OneDrive ou SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ef3b7-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="ef3b7-112">Pour définir le filtre de sécurité de conformité pour une région :</span><span class="sxs-lookup"><span data-stu-id="ef3b7-112">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="ef3b7-113">Ouvrez Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef3b7-113">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="ef3b7-114">Entrez </span><span class="sxs-lookup"><span data-stu-id="ef3b7-114">Enter</span></span>  
    <span data-ttu-id="ef3b7-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="ef3b7-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="ef3b7-116">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="ef3b7-116">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="ef3b7-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="ef3b7-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="ef3b7-118">Par exemple : **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="ef3b7-118">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="ef3b7-119">Consultez l’article [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) pour en savoir plus sur la syntaxe et les paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ef3b7-119">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>
