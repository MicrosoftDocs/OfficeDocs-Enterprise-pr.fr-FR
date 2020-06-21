---
title: Contrôles d’accès Yammer Enterprise de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Résumé : Résumé succinct sur les contrôles d’accès aux entreprises Yammer dans l’environnement de production.'
ms.openlocfilehash: 0da479eb36359ec6b795a8e4323441edc4678f1a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775113"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="b7dce-103">Contrôles d’accès à l’entreprise Yammer</span><span class="sxs-lookup"><span data-stu-id="b7dce-103">Yammer enterprise access controls</span></span> 

<span data-ttu-id="b7dce-104">L’accès physique et logique à l’environnement de production Yammer est limité à un petit ensemble de personnes (infrastructure et opérations).</span><span class="sxs-lookup"><span data-stu-id="b7dce-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="b7dce-105">Comme avec d’autres ingénieurs Microsoft 365, les ingénieurs Yammer disposent d’un accès permanent aux données client.</span><span class="sxs-lookup"><span data-stu-id="b7dce-105">As with other Microsoft 365 engineers, Yammer engineers have zero standing access to customer data.</span></span> <span data-ttu-id="b7dce-106">L’accès doit être demandé à l’aide d’un système de contrôle d’accès juste-à-temps basé sur l’approbation, comme le Lockbox avec un nombre limité d’approbateurs.</span><span class="sxs-lookup"><span data-stu-id="b7dce-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="b7dce-107">Les approbateurs vérifient la demande (par exemple, ils vérifient si la demande est légitime en fonction de la demande, du cas client, du temps, etc.), puis approuvez ou refusez la demande.</span><span class="sxs-lookup"><span data-stu-id="b7dce-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="b7dce-108">Si la demande est approuvée, l’accès JIT est accordé pour un temps défini et limité.</span><span class="sxs-lookup"><span data-stu-id="b7dce-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="b7dce-109">Une fois le temps d’accès dépassé, l’accès expire automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b7dce-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="b7dce-110">Tout comme les autres services Microsoft 365, tout accès à l’environnement de production Yammer utilise l’authentification multifacteur.</span><span class="sxs-lookup"><span data-stu-id="b7dce-110">As with other Microsoft 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="b7dce-111">Tous les accès et historique des commandes sont attribués à un utilisateur et sont consignés et révisés régulièrement par l’équipe de sécurité Yammer.</span><span class="sxs-lookup"><span data-stu-id="b7dce-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="b7dce-112">Pour plus d’informations sur l’administration et la gestion de Yammer, consultez [l’aide de l’administrateur de Yammer](https://docs.microsoft.com/yammer/yammer-landing-page).</span><span class="sxs-lookup"><span data-stu-id="b7dce-112">For more information about Yammer administration and management, see [Yammer admin help](https://docs.microsoft.com/yammer/yammer-landing-page).</span></span>