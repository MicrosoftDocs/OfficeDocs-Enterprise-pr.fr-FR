---
title: Fonctionnalités Multi-Geo dans OneDrive et SharePoint Online dans Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Étendez votre présence Office 365 à plusieurs régions géographiques grâce aux fonctionnalités multigéographiques dans OneDrive et SharePoint Online.
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012734"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="714d0-103">Fonctionnalités Multi-Géo dans OneDrive et SharePoint Online dans Office 365</span><span class="sxs-lookup"><span data-stu-id="714d0-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="714d0-p101">Grâce aux fonctionnalités Multi-Géo dans OneDrive et SharePoint Online, votre organisation peut étendre sa présence Office 365 à plusieurs régions géographiques ou pays au sein de votre client existant. Prenez contact avec votre équipe de compte Microsoft pour inscrire votre entreprise internationale à la version Multi-Géo de OneDrive Entreprise.</span><span class="sxs-lookup"><span data-stu-id="714d0-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="714d0-106">Avec les fonctionnalités multigéographiques de OneDrive, vous pouvez configurer et stocker des données au repos dans les emplacements géographiques choisis afin de satisfaire les besoins spécifiques en matière d’emplacement des données, et en même temps déverrouiller votre déploiement général d’expériences de productivité moderne à votre personnel.</span><span class="sxs-lookup"><span data-stu-id="714d0-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="714d0-107">Voici comment les fonctionnalités multigéographiques peuvent être utiles à votre organisation :</span><span class="sxs-lookup"><span data-stu-id="714d0-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="714d0-108">Opérez en tant que multinationale connectée avec un client Office 365 unique qui s’étend sur plusieurs emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="714d0-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="714d0-109">Répondez aux besoins spécifiques en matière d’emplacement des données en créant et en hébergeant des données au repos dans un emplacement géographique spécifié.</span><span class="sxs-lookup"><span data-stu-id="714d0-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="714d0-110">Responsabilisez vos utilisateurs satellites en mettant à leur disposition les mêmes expériences de productivité moderne appréciées par les utilisateurs de votre emplacement centralisé.</span><span class="sxs-lookup"><span data-stu-id="714d0-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="714d0-111">Autorisez vos utilisateurs à se déplacer sur plusieurs emplacements géographiques à mesure que leurs rôles changent, tandis que l’accès à leur contenu reste intact.</span><span class="sxs-lookup"><span data-stu-id="714d0-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="714d0-112">Personnalisez vos stratégies de partage par emplacement géographique et vos stratégies de protection contre la perte de données par site.</span><span class="sxs-lookup"><span data-stu-id="714d0-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="714d0-113">Désignez les responsables eDiscovery par emplacement géographique et autorisez la gestion des cas adaptés à votre emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="714d0-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="714d0-114">Choisissez des espaces de noms URL uniques (par exemple, ContosoEUR.sharepoint.com) pour vos emplacements géographiques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="714d0-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="714d0-115">Consolidez vos données régionales locales dans votre client multi-géographique Office 365.</span><span class="sxs-lookup"><span data-stu-id="714d0-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="714d0-p102">Dans une configuration multi-géographique, votre client Office 365 se compose d’un emplacement central (également appelé emplacement par défaut) et d’un ou de plusieurs emplacements géographiques satellites. Le concept clé de la fonction multi-géographique est qu’une seule location couvre plusieurs emplacements géographiques. Dans un client multi-géographique, les informations concernant les emplacements géographiques, les groupes et les informations utilisateur sont gérées dans Azure Active Directory (AAD). Étant donné que les informations de votre client sont gérées de façon centralisée et synchronisées à chaque emplacement géographique, le partage et les expériences concernant tout membre de votre société impliquent une sensibilisation à l’échelle mondiale.</span><span class="sxs-lookup"><span data-stu-id="714d0-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="714d0-120">Vidéo : Présentation d’Office 365 Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="714d0-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="714d0-121">Obtention des fonctionnalités multigéographiques en trois étapes simples</span><span class="sxs-lookup"><span data-stu-id="714d0-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="714d0-122">La configuration Multi-Géo est facile :</span><span class="sxs-lookup"><span data-stu-id="714d0-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="714d0-p103">Travaillez avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Office 365_. Vous pourrez ainsi ajouter le nombre de licences nécessaires.</span><span class="sxs-lookup"><span data-stu-id="714d0-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="714d0-125">Ajoutez vos emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="714d0-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="714d0-126">Configurez vos comptes d’utilisateur pour l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="714d0-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="714d0-127">Disponibilité et état de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="714d0-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="714d0-128">Les fonctionnalités multigéographiques de OneDrive sont actuellement disponibles dans les régions et pays suivants :</span><span class="sxs-lookup"><span data-stu-id="714d0-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="714d0-129">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="714d0-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="714d0-130">Australie</span><span class="sxs-lookup"><span data-stu-id="714d0-130">Australia</span></span>
    
- <span data-ttu-id="714d0-131">Canada</span><span class="sxs-lookup"><span data-stu-id="714d0-131">Canada</span></span>
    
- <span data-ttu-id="714d0-132">Union européenne (EMEA)</span><span class="sxs-lookup"><span data-stu-id="714d0-132">European Union (EMEA)</span></span>

- <span data-ttu-id="714d0-133">France</span><span class="sxs-lookup"><span data-stu-id="714d0-133">France</span></span>
    
- <span data-ttu-id="714d0-134">Japon</span><span class="sxs-lookup"><span data-stu-id="714d0-134">Japan</span></span>
    
- <span data-ttu-id="714d0-135">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="714d0-135">United Kingdom</span></span>
    
- <span data-ttu-id="714d0-136">États-Unis (Amérique du Nord)</span><span class="sxs-lookup"><span data-stu-id="714d0-136">United States (North America)</span></span>
    
- <span data-ttu-id="714d0-137">Corée</span><span class="sxs-lookup"><span data-stu-id="714d0-137">Korea</span></span>
      
<span data-ttu-id="714d0-138">Emplacements géographiques à venir :</span><span class="sxs-lookup"><span data-stu-id="714d0-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="714d0-139">Inde</span><span class="sxs-lookup"><span data-stu-id="714d0-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="714d0-140">Prise en main</span><span class="sxs-lookup"><span data-stu-id="714d0-140">Getting started</span></span>

<span data-ttu-id="714d0-p104">Pour commencer à utiliser OneDrive Entreprise Multi-Géo, la première étape consiste à [planifier votre environnement OneDrive Entreprise Multi-Géo](plan-for-multi-geo.md). Ensuite, [découvrez comment administrer un environnement multigéographique](administering-a-multi-geo-environment.md) et [comment vos utilisateurs expérimenteront un environnement multigéographique](multi-geo-user-experience.md). Lorsque vous êtes prêt à configurer OneDrive Entreprise Multi-Géo, [configurez votre client pour Multi-Géo](multi-geo-tenant-configuration.md), puis [déplacez les sites OneDrive existants vers leurs nouveaux emplacements géographiques](move-onedrive-between-geo-locations.md) et [configurez la recherche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="714d0-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
