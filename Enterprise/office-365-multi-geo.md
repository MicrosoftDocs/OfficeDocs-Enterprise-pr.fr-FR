---
title: Office 365 multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Étendez votre présence Office 365 à plusieurs régions géographiques avec Office 365 multigéographique.
ms.openlocfilehash: 86234cb025d5e0398cbfa626b4867642412e7e0b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031929"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="3c675-103">Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="3c675-103">Office 365 Multi-Geo</span></span>

<span data-ttu-id="3c675-104">Avec Office 365 multigéographique, votre organisation peut étendre sa présence Office 365 à plusieurs régions ou pays au sein de votre client existant.</span><span class="sxs-lookup"><span data-stu-id="3c675-104">With Office 365 Multi-Geo, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="3c675-105">Pour inscrire votre entreprise internationale à Office 365 multigéographique, contactez votre Équipe des comptes Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3c675-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="3c675-106">Office 365 multigéographique vous permet d’approvisionner et de stocker des données au repos dans les emplacements géographiques de votre choix afin de répondre à des besoins spécifiques en matière de résidence des données, tout en déverrouillant le déploiement global d’expériences de productivité moderne à vos employés.</span><span class="sxs-lookup"><span data-stu-id="3c675-106">With Office 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="3c675-107">Vidéo : Présentation d’Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="3c675-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="3c675-108">Dans un environnement multigéographique, votre client Office 365 se compose d’un emplacement central (où votre abonnement Office 365 d’origine a été approvisionné) et d’un ou plusieurs emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="3c675-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="3c675-109">Dans un client multigéographique, les informations concernant les emplacements géographiques, les groupes et les informations utilisateur sont gérées dans Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="3c675-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="3c675-110">Étant donné que les informations de votre client sont gérées de façon centralisée et synchronisées à chaque emplacement géographique, le partage et les expériences concernant tout membre de votre société impliquent une sensibilisation à l’échelle mondiale.</span><span class="sxs-lookup"><span data-stu-id="3c675-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Capture d’écran d’un mappage multigéographique du Centre d’administration SharePoint](media/multi-geo-world-map.png)

<span data-ttu-id="3c675-112">Notez qu’Office 365 multigéographique n’est pas conçu pour optimiser les performances, mais pour répondre aux exigences de résidence des données.</span><span class="sxs-lookup"><span data-stu-id="3c675-112">Note that Office 365 Multi-Geo is not primarily designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="3c675-113">Pour plus d’informations sur l’optimisation des performances pour Office 365, voir [Planification réseau et optimisation des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou contacter votre groupe de support.</span><span class="sxs-lookup"><span data-stu-id="3c675-113">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="3c675-114">Terminologie</span><span class="sxs-lookup"><span data-stu-id="3c675-114">Terminology</span></span>

<span data-ttu-id="3c675-115">Voici les termes clés utilisés dans la description d’Office 365 multigéographique :</span><span class="sxs-lookup"><span data-stu-id="3c675-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="3c675-116">**Emplacement central** : emplacement géographique où votre client a été approvisionné à l’origine.</span><span class="sxs-lookup"><span data-stu-id="3c675-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="3c675-117">**Administrateur de zone géographique** : un administrateur pouvant administrer un ou plusieurs emplacements satellites spécifiés.</span><span class="sxs-lookup"><span data-stu-id="3c675-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="3c675-118">**Géocode** : code de trois lettres correspondant à un emplacement géographique donné.</span><span class="sxs-lookup"><span data-stu-id="3c675-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="3c675-119">**Emplacement géographique** : emplacement géographique utilisable dans un client multigéographique pour héberger des données, notamment dans des boîtes aux lettres Exchange et des sites OneDrive ou SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3c675-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="3c675-120">**Emplacement par défaut des données** : propriété d’utilisateur définie par l’administrateur, indiquant l’emplacement géographique où la boîte aux lettres Exchange et le OneDrive des utilisateurs doivent être déployés.</span><span class="sxs-lookup"><span data-stu-id="3c675-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="3c675-121">L’emplacement par défaut des données détermine où sont déployés les sites SharePoint créés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3c675-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="3c675-122">**Emplacement satellite** : emplacement géographique où les charges de travail Office 365 sensibles à la zone géographique (SharePoint, OneDrive et Exchange) sont activées dans un client multigéographique.</span><span class="sxs-lookup"><span data-stu-id="3c675-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="3c675-123">**Locataire** : représentation d’une organisation dans Office 365 à laquelle sont généralement associés un ou plusieurs domaines (par exemple, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="3c675-123">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="3c675-124">Disponibilité d’Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="3c675-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="3c675-125">Office 365 multigéographique est actuellement disponible dans les régions et pays suivants :</span><span class="sxs-lookup"><span data-stu-id="3c675-125">Office 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="3c675-126">Prise en main</span><span class="sxs-lookup"><span data-stu-id="3c675-126">Getting started</span></span>

<span data-ttu-id="3c675-127">Pour commencer à utiliser la fonctionnalité multigéographique, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3c675-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="3c675-128">Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Office 365_.</span><span class="sxs-lookup"><span data-stu-id="3c675-128">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span> <span data-ttu-id="3c675-129">Ils vous guident pour ajouter le nombre de licences nécessaires.</span><span class="sxs-lookup"><span data-stu-id="3c675-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="3c675-130">La fonctionnalité Zones géographiques multiples est actuellement disponible pour les clients avec au moins 500 abonnements Office 365.</span><span class="sxs-lookup"><span data-stu-id="3c675-130">Multi-Geo feature is available to customers with a minimum of 500 Office 365 subscriptions.</span></span>

   <span data-ttu-id="3c675-131">Avant que vous puissiez commencer à utiliser Office 365 multigéographique, Microsoft doit configurer votre client Exchange Online afin qu’il bénéficie d’une prise en charge multigéographique.</span><span class="sxs-lookup"><span data-stu-id="3c675-131">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="3c675-132">Ce processus de configuration est déclenché lorsque vous commandez le plan de services des *fonctionnalités multigéographiques d’Office 365* et que les licences apparaissent dans votre client.</span><span class="sxs-lookup"><span data-stu-id="3c675-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="3c675-133">Une fois vos licences multigéographiques appliquées, vous recevez des notifications dans le [Centre de messages Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) et pouvez commencer à configurer et à utiliser les fonctionnalités d’Office 365 multigéographique.</span><span class="sxs-lookup"><span data-stu-id="3c675-133">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="3c675-134">Lisez [Planifier votre environnement multigéographique](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="3c675-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="3c675-135">Découvrez [comment administrer un environnement multigéographique](administering-a-multi-geo-environment.md) et [comment vos utilisateurs feront l’expérience de cet environnement](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="3c675-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="3c675-136">Lorsque vous êtes prêt à configurer Office 365 multigéographique, [configurez votre client pour une utilisation multigéographique](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3c675-136">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="3c675-137">[Configurez la recherche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="3c675-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c675-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c675-138">See also</span></span>

[<span data-ttu-id="3c675-139">Géo multiple dans Exchange Online et OneDrive</span><span class="sxs-lookup"><span data-stu-id="3c675-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="3c675-140">Fonctionnalités multigéographiques dans OneDrive et SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3c675-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="3c675-141">Fonctionnalités multi-localisés dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3c675-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
