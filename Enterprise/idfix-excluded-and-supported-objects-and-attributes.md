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
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Répertorie les attributs qui sont exclus et pris en charge par l’outil IdFix.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711574"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="88639-103">Attributs et objets d'IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="88639-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="88639-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="88639-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="88639-105">Il existe deux ensembles de règles gérées par IdFix ; Mutualisée et dédiée/ITAR.</span><span class="sxs-lookup"><span data-stu-id="88639-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="88639-106">Pour l’instant, les deux ensembles de règles excluent les mêmes objets, attributs et valeurs d’attribut de la recherche.</span><span class="sxs-lookup"><span data-stu-id="88639-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="88639-107">Cela peut changer dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="88639-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="88639-108">Exclusions d’erreurs dédiées et mutualisées utilisées par IdFix</span><span class="sxs-lookup"><span data-stu-id="88639-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="88639-109">Cette section répertorie les objets, attributs et valeurs que IdFix exclut de sa recherche dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="88639-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="88639-110">L’astérisque ( \* ) est un caractère générique qui peut être remplacé par d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="88639-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="88639-111">Objets, attributs et valeurs exclus pendant une recherche IdFix</span><span class="sxs-lookup"><span data-stu-id="88639-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="88639-112">**Exclusion**</span><span class="sxs-lookup"><span data-stu-id="88639-112">**Exclusion**</span></span>|<span data-ttu-id="88639-113">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="88639-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88639-114">Choix\*</span><span class="sxs-lookup"><span data-stu-id="88639-114">Admini\*</span></span> |<span data-ttu-id="88639-115">Administrateur</span><span class="sxs-lookup"><span data-stu-id="88639-115">Administrator</span></span> |
|<span data-ttu-id="88639-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="88639-116">CAS_{\*</span></span>  |<span data-ttu-id="88639-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="88639-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="88639-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="88639-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="88639-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="88639-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="88639-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="88639-120">FederatedEmail\*</span></span> |<span data-ttu-id="88639-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="88639-121">FederatedEmail.</span></span> <span data-ttu-id="88639-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="88639-122">*GUID*</span></span> |
|<span data-ttu-id="88639-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="88639-123">Guest\*</span></span> ||
|<span data-ttu-id="88639-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="88639-124">HTTPConnector\*</span></span>  |<span data-ttu-id="88639-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="88639-125">HTTPConnector</span></span> |
|<span data-ttu-id="88639-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="88639-126">krbtgt\*</span></span> |<span data-ttu-id="88639-127">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="88639-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="88639-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="88639-128">iusr_\*</span></span> |<span data-ttu-id="88639-129">iusr_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="88639-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="88639-130">connaît\*</span><span class="sxs-lookup"><span data-stu-id="88639-130">iwam\*</span></span>  |<span data-ttu-id="88639-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="88639-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="88639-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="88639-132">msol\*</span></span> |<span data-ttu-id="88639-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="88639-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="88639-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="88639-134">support_\*</span></span> ||
|<span data-ttu-id="88639-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="88639-135">SystemMailbox\*</span></span> |<span data-ttu-id="88639-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="88639-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="88639-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="88639-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="88639-138">distinguishedName contient « \0ACNF : »</span><span class="sxs-lookup"><span data-stu-id="88639-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="88639-139">« \0ACNF : *GUID* »</span><span class="sxs-lookup"><span data-stu-id="88639-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="88639-140">L’objet contient l’attribut IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="88639-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="88639-141">Voir [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="88639-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="88639-142">Objets et attributs dédiés à plusieurs clients et contrôlés par IdFix</span><span class="sxs-lookup"><span data-stu-id="88639-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="88639-143">Les attributs vérifiés pour les erreurs par IdFix sont décrits dans la section « Préparation des attributs et des objets d’annuaire » de [Prepare Directory attributes for Synchronization with Microsoft 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="88639-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Microsoft 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

