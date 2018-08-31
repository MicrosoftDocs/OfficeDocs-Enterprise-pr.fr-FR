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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Répertorie les attributs qui sont pris en charge par l’outil IdFix et exclus.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540474"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="94024-103">Attributs et objets d’IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="94024-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="94024-p101">Il existe deux jeux de règles gérés par IdFix ; Multiclients et Dédié/ITAR. À ce stade, les deux jeux de règles excluent les mêmes objets, attributs et valeurs d'attributs de la recherche. Cela pourrait changer dans les prochaines versions.</span><span class="sxs-lookup"><span data-stu-id="94024-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="94024-107">Exclusions d'erreurs Multiclients et Dédié utilisées par IdFix</span><span class="sxs-lookup"><span data-stu-id="94024-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="94024-p102">Cette section répertorie les objets, attributs et valeurs IdFix exclut de la recherche dans le répertoire. L’astérisque (\*) est un caractère générique qui peut être remplacé par d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="94024-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="94024-110">Objets, attributs et valeurs exclus lors d'une recherche IdFix</span><span class="sxs-lookup"><span data-stu-id="94024-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="94024-111">**Exclusion**</span><span class="sxs-lookup"><span data-stu-id="94024-111">**Exclusion**</span></span>|<span data-ttu-id="94024-112">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="94024-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="94024-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="94024-113">Admini\*</span></span> |<span data-ttu-id="94024-114">Administrateur</span><span class="sxs-lookup"><span data-stu-id="94024-114">Administrator</span></span> |
|<span data-ttu-id="94024-115">{CAS_\*</span><span class="sxs-lookup"><span data-stu-id="94024-115">CAS_{\*</span></span>  |<span data-ttu-id="94024-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="94024-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="94024-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="94024-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="94024-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="94024-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="94024-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="94024-119">FederatedEmail\*</span></span> |<span data-ttu-id="94024-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="94024-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="94024-122">Invité\*</span><span class="sxs-lookup"><span data-stu-id="94024-122">Guest\*</span></span> ||
|<span data-ttu-id="94024-123">Connecteur HTTP\*</span><span class="sxs-lookup"><span data-stu-id="94024-123">HTTPConnector\*</span></span>  |<span data-ttu-id="94024-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="94024-124">HTTPConnector</span></span> |
|<span data-ttu-id="94024-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="94024-125">krbtgt\*</span></span> |<span data-ttu-id="94024-126">MS-DS-KrbTgt-lien</span><span class="sxs-lookup"><span data-stu-id="94024-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="94024-127">IUSR_\*</span><span class="sxs-lookup"><span data-stu-id="94024-127">iusr_\*</span></span> |<span data-ttu-id="94024-128">IUSR_ *NomOrdinateur*</span><span class="sxs-lookup"><span data-stu-id="94024-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="94024-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="94024-129">iwam\*</span></span>  |<span data-ttu-id="94024-130">IWAM_ *NomOrdinateur*</span><span class="sxs-lookup"><span data-stu-id="94024-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="94024-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="94024-131">msol\*</span></span> |<span data-ttu-id="94024-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="94024-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="94024-133">compte Support_\*</span><span class="sxs-lookup"><span data-stu-id="94024-133">support_\*</span></span> ||
|<span data-ttu-id="94024-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="94024-134">SystemMailbox\*</span></span> |<span data-ttu-id="94024-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="94024-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="94024-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="94024-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="94024-137">distinguishedName contient « \0ACNF : »</span><span class="sxs-lookup"><span data-stu-id="94024-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="94024-138">« \0ACNF : *GUID* »</span><span class="sxs-lookup"><span data-stu-id="94024-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="94024-139">L'objet contient l'attribut IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="94024-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="94024-140">Consultez la rubrique [attribut isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="94024-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="94024-141">Attributs et objets Multiclients et Dédié vérifiés par IdFix</span><span class="sxs-lookup"><span data-stu-id="94024-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="94024-142">Les attributs qui sont en cours pour les erreurs par IdFix sont décrits dans la section « Objet et attribut préparation Directory » dans les [attributs d’annuaire préparer pour la synchronisation avec Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="94024-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

