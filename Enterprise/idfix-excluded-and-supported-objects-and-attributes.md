---
title: Attributs et objets d’IdFix pris en charge et exclus
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
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
description: Répertorie les attributs qui sont exclus et pris en charge par l'outil IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085083"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="6e535-103">Attributs et objets d’IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="6e535-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="6e535-p101">Il existe deux jeux de règles gérés par IdFix ; Multiclients et Dédié/ITAR. À ce stade, les deux jeux de règles excluent les mêmes objets, attributs et valeurs d'attributs de la recherche. Cela pourrait changer dans les prochaines versions.</span><span class="sxs-lookup"><span data-stu-id="6e535-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="6e535-107">Exclusions d'erreurs Multiclients et Dédié utilisées par IdFix</span><span class="sxs-lookup"><span data-stu-id="6e535-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="6e535-p102">Cette section répertorie les objets, attributs et valeurs que IdFix exclut de sa recherche dans l'annuaire. L'astérisque (\*) est un caractère générique qui peut être remplacé par d'autres caractères.</span><span class="sxs-lookup"><span data-stu-id="6e535-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="6e535-110">Objets, attributs et valeurs exclus lors d'une recherche IdFix</span><span class="sxs-lookup"><span data-stu-id="6e535-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="6e535-111">**Exclusion**</span><span class="sxs-lookup"><span data-stu-id="6e535-111">**Exclusion**</span></span>|<span data-ttu-id="6e535-112">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="6e535-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6e535-113">Choix\*</span><span class="sxs-lookup"><span data-stu-id="6e535-113">Admini\*</span></span> |<span data-ttu-id="6e535-114">Administrateur</span><span class="sxs-lookup"><span data-stu-id="6e535-114">Administrator</span></span> |
|<span data-ttu-id="6e535-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="6e535-115">CAS_{\*</span></span>  |<span data-ttu-id="6e535-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="6e535-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="6e535-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6e535-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="6e535-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="6e535-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="6e535-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="6e535-119">FederatedEmail\*</span></span> |<span data-ttu-id="6e535-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="6e535-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="6e535-122">Invité\*</span><span class="sxs-lookup"><span data-stu-id="6e535-122">Guest\*</span></span> ||
|<span data-ttu-id="6e535-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="6e535-123">HTTPConnector\*</span></span>  |<span data-ttu-id="6e535-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="6e535-124">HTTPConnector</span></span> |
|<span data-ttu-id="6e535-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="6e535-125">krbtgt\*</span></span> |<span data-ttu-id="6e535-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="6e535-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="6e535-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="6e535-127">iusr_\*</span></span> |<span data-ttu-id="6e535-128">IUSR _ *nomordinateur*</span><span class="sxs-lookup"><span data-stu-id="6e535-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="6e535-129">connaît\*</span><span class="sxs-lookup"><span data-stu-id="6e535-129">iwam\*</span></span>  |<span data-ttu-id="6e535-130">IWAM _ *nomordinateur*</span><span class="sxs-lookup"><span data-stu-id="6e535-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="6e535-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="6e535-131">msol\*</span></span> |<span data-ttu-id="6e535-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="6e535-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="6e535-133">prend\*</span><span class="sxs-lookup"><span data-stu-id="6e535-133">support_\*</span></span> ||
|<span data-ttu-id="6e535-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6e535-134">SystemMailbox\*</span></span> |<span data-ttu-id="6e535-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="6e535-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="6e535-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="6e535-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="6e535-137">distinguishedName contient «\0ACNF:»</span><span class="sxs-lookup"><span data-stu-id="6e535-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="6e535-138">«\0ACNF: *GUID* »</span><span class="sxs-lookup"><span data-stu-id="6e535-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="6e535-139">L'objet contient l'attribut IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="6e535-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="6e535-140">Voir [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="6e535-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="6e535-141">Attributs et objets Multiclients et Dédié vérifiés par IdFix</span><span class="sxs-lookup"><span data-stu-id="6e535-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="6e535-142">Les attributs vérifiés pour les erreurs par IdFix sont décrits dans la section «Préparation des attributs et des objets d'annuaire» de [Prepare Directory attributes for Synchronization with Office 365 à l'aide de l'outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="6e535-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

