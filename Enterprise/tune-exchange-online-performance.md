---
title: Optimiser les performances d'Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Cet article contient des conseils généraux et des liens vers d'autres ressources qui vous indiquent comment améliorer les performances d'Exchange Online.
ms.openlocfilehash: f75869ba6d83a92b1e19743c8b38c4bcbb6762cf
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372851"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="fe2bf-103">Optimiser les performances d'Exchange Online</span><span class="sxs-lookup"><span data-stu-id="fe2bf-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="fe2bf-104">Cet article contient des conseils généraux et des liens vers d'autres ressources qui vous indiquent comment améliorer les performances d'Exchange Online, en particulier avant une migration.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="fe2bf-105">Cet article fait partie du projet [planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="fe2bf-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="fe2bf-106">Éléments à prendre en compte pour améliorer les performances d'Exchange Online</span><span class="sxs-lookup"><span data-stu-id="fe2bf-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="fe2bf-107">Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, prenez en compte les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="fe2bf-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="fe2bf-108">**Réduisez la taille des boîtes aux lettres.**</span><span class="sxs-lookup"><span data-stu-id="fe2bf-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="fe2bf-109">La taille de boîte aux lettres réduite améliore la vitesse de migration.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="fe2bf-110">**Utiliser les fonctionnalités de déplacement de boîtes aux lettres avec un déploiement hybride Exchange.**</span><span class="sxs-lookup"><span data-stu-id="fe2bf-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="fe2bf-111">Avec un déploiement hybride Exchange, le courrier hors connexion (sous la forme de. Fichiers OST) ne nécessite pas de téléchargement à nouveau lors de la migration vers Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="fe2bf-112">Cela réduit considérablement vos besoins en matière de bande passante de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="fe2bf-113">**Planifiez les déplacements de boîtes aux lettres au cours des périodes de trafic Internet faible et de l'utilisation d'Exchange en local.**</span><span class="sxs-lookup"><span data-stu-id="fe2bf-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="fe2bf-114">Lors de la planification des déplacements, les demandes de migration sont envoyées au proxy de réplication de boîte aux lettres et ne peuvent pas être placées immédiatement.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="fe2bf-115">**Utilisez la la messagerie instantanée épuré pour Outlook sur le Web.**</span><span class="sxs-lookup"><span data-stu-id="fe2bf-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="fe2bf-116">Les la messagerie instantanée épurées fournissent des versions plus petites et moins gourmandes en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer en affichant certains composants sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="fe2bf-117">Pour plus d'informations, reportez-vous à la rubrique [use Lean la messagerie instantanée pour réduire la mémoire utilisée lors de la lecture des messages électroniques](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="fe2bf-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="fe2bf-118">Conseils généraux</span><span class="sxs-lookup"><span data-stu-id="fe2bf-118">General advice</span></span>

- <span data-ttu-id="fe2bf-119">Assurez-vous que la recherche DNS pour outlook.office.com entre dans le centre de donnée Microsoft à un emplacement d'entrée logique de votre emplacement.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="fe2bf-120">Rechercher la mise en cache des boîtes aux lettres et choisir les options appropriées (re.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="fe2bf-121">période de mise en cache, mise en cache des boîtes aux lettres partagées et cetera).</span><span class="sxs-lookup"><span data-stu-id="fe2bf-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="fe2bf-122">Conservez vos données Outlook en transitant par des connexions VPN (vers un bureau central) avant qu'elles ne circulent sur Internet.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="fe2bf-123">Assurez-vous que les données de votre boîte aux lettres respectent les limites du dossier et de l'élément, amounts.</span><span class="sxs-lookup"><span data-stu-id="fe2bf-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="fe2bf-124">Pour plus d'informations sur les performances de migration Exchange, consultez la rubrique relative aux [performances et aux meilleures pratiques pour la migration Office 365](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="fe2bf-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

