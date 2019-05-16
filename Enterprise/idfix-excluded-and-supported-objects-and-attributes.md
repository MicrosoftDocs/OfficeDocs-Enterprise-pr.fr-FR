---
title: Attributs et objets d'IdFix pris en charge et exclus
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Répertorie les attributs qui sont exclus et pris en charge par l’outil IdFix.
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067270"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="64c6b-103">Attributs et objets d'IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="64c6b-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="64c6b-104">Il existe deux ensembles de règles gérées par IdFix; Mutualisée et dédiée/ITAR.</span><span class="sxs-lookup"><span data-stu-id="64c6b-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="64c6b-105">Pour l’instant, les deux ensembles de règles excluent les mêmes objets, attributs et valeurs d’attribut de la recherche.</span><span class="sxs-lookup"><span data-stu-id="64c6b-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="64c6b-106">Cela peut changer dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="64c6b-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="64c6b-107">Exclusions d’erreurs dédiées et mutualisées utilisées par IdFix</span><span class="sxs-lookup"><span data-stu-id="64c6b-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="64c6b-108">Cette section répertorie les objets, attributs et valeurs que IdFix exclut de sa recherche dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="64c6b-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="64c6b-109">L’astérisque (\*) est un caractère générique qui peut être remplacé par d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="64c6b-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="64c6b-110">Objets, attributs et valeurs exclus pendant une recherche IdFix</span><span class="sxs-lookup"><span data-stu-id="64c6b-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="64c6b-111">**Exclusion**</span><span class="sxs-lookup"><span data-stu-id="64c6b-111">**Exclusion**</span></span>|<span data-ttu-id="64c6b-112">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="64c6b-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="64c6b-113">Choix\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-113">Admini\*</span></span> |<span data-ttu-id="64c6b-114">Administrateur</span><span class="sxs-lookup"><span data-stu-id="64c6b-114">Administrator</span></span> |
|<span data-ttu-id="64c6b-115">CAS_{\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-115">CAS_{\*</span></span>  |<span data-ttu-id="64c6b-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="64c6b-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="64c6b-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="64c6b-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="64c6b-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="64c6b-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-119">FederatedEmail\*</span></span> |<span data-ttu-id="64c6b-120">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="64c6b-120">FederatedEmail.</span></span> <span data-ttu-id="64c6b-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="64c6b-121">*GUID*</span></span> |
|<span data-ttu-id="64c6b-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-122">Guest\*</span></span> ||
|<span data-ttu-id="64c6b-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-123">HTTPConnector\*</span></span>  |<span data-ttu-id="64c6b-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="64c6b-124">HTTPConnector</span></span> |
|<span data-ttu-id="64c6b-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-125">krbtgt\*</span></span> |<span data-ttu-id="64c6b-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="64c6b-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="64c6b-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-127">iusr_\*</span></span> |<span data-ttu-id="64c6b-128">IUSR _ *nomordinateur*</span><span class="sxs-lookup"><span data-stu-id="64c6b-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="64c6b-129">connaît\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-129">iwam\*</span></span>  |<span data-ttu-id="64c6b-130">IWAM _ *nomordinateur*</span><span class="sxs-lookup"><span data-stu-id="64c6b-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="64c6b-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-131">msol\*</span></span> |<span data-ttu-id="64c6b-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="64c6b-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="64c6b-133">prend\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-133">support_\*</span></span> ||
|<span data-ttu-id="64c6b-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-134">SystemMailbox\*</span></span> |<span data-ttu-id="64c6b-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="64c6b-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="64c6b-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="64c6b-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="64c6b-137">distinguishedName contient «\0ACNF:»</span><span class="sxs-lookup"><span data-stu-id="64c6b-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="64c6b-138">«\0ACNF: *GUID* »</span><span class="sxs-lookup"><span data-stu-id="64c6b-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="64c6b-139">L’objet contient l’attribut IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="64c6b-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="64c6b-140">Voir [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="64c6b-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="64c6b-141">Objets et attributs dédiés à plusieurs clients et contrôlés par IdFix</span><span class="sxs-lookup"><span data-stu-id="64c6b-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="64c6b-142">Les attributs vérifiés pour les erreurs par IdFix sont décrits dans la section «Préparation des attributs et des objets d’annuaire» de [Prepare Directory attributes for Synchronization with Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="64c6b-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

