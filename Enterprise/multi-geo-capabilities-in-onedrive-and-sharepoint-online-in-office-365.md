---
title: Fonctionnalités Multi-Geo dans OneDrive et SharePoint Online dans Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Développez votre présence sur Office 365 dans plusieurs régions géographiques avec des capacités multi-geo dans SharePoint Online et de OneDrive.
ms.openlocfilehash: 2c5de533aaaace68e51b747cd62a53b9572bcaec
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="3b392-103">Fonctionnalités Multi-Geo dans OneDrive et SharePoint Online dans Office 365</span><span class="sxs-lookup"><span data-stu-id="3b392-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="3b392-p101">Avec les fonctionnalités multigéographiques dans OneDrive et SharePoint Online, votre organisation peut étendre sa présence Office 365 à plusieurs régions géographiques ou pays au sein de votre client existant. Cette fonctionnalité est actuellement en phase d’évaluation. Prenez contact avec votre équipe de compte Microsoft pour inscrire votre entreprise internationale à la version d’évaluation multigéographique de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="3b392-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="3b392-107">Avec OneDrive Multi-Geo, vous pouvez provisionner et stocker des données au repos dans l’emplacement géographique que vous avez choisi pour répondre aux exigences en matière de délégation de compétences de données et en même temps déverrouiller votre déploiement global des expériences de productivité moderne à vos effectifs.</span><span class="sxs-lookup"><span data-stu-id="3b392-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="3b392-108">Voici comment les fonctionnalités multi-geo peuvent bénéficier à votre organisation :</span><span class="sxs-lookup"><span data-stu-id="3b392-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="3b392-109">Opérez en tant que multinationale connectée avec un client Office 365 unique qui s’étend sur plusieurs emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="3b392-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="3b392-110">Répondez aux besoins spécifiques en matière d’emplacement des données en créant et en hébergeant des données au repos dans un emplacement géographique spécifié.</span><span class="sxs-lookup"><span data-stu-id="3b392-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="3b392-111">Responsabilisez vos utilisateurs satellites en mettant à leur disposition les mêmes expériences de productivité moderne appréciées par les utilisateurs de votre emplacement centralisé.</span><span class="sxs-lookup"><span data-stu-id="3b392-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="3b392-112">Autorisez vos utilisateurs à se déplacer sur plusieurs emplacements géographiques à mesure que leurs rôles changent, tandis que l’accès à leur contenu reste intact.</span><span class="sxs-lookup"><span data-stu-id="3b392-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="3b392-113">Personnalisez vos stratégies de partage par emplacement géographique et vos stratégies de protection contre la perte de données par site.</span><span class="sxs-lookup"><span data-stu-id="3b392-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="3b392-114">Désignez les responsables eDiscovery par emplacement géographique et autorisez la gestion des cas adaptés à votre emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="3b392-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="3b392-115">Choisissez des espaces de noms URL uniques (par exemple, ContosoEUR.sharepoint.com) pour vos emplacements géographiques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3b392-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="3b392-116">Consolidez vos données régionales locales dans votre client multi-géographique Office 365.</span><span class="sxs-lookup"><span data-stu-id="3b392-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="3b392-p102">Dans une configuration multi-geo, vos clients Office 365 comprend un emplacement central (également connu sous le nom, l’emplacement par défaut) et un ou plusieurs emplacements de geo satellite. Le concept clé de multi-geo est qu’une location simple couvrira sur un plusieurs emplacements géographiquement. Dans un client multi-geo, les informations sur les emplacements de la zone géographique, les groupes et les informations utilisateur, sont gravées dans Azure Active Directory (DAS). Parce que vos informations de locataire sont maîtrisées de façon centralisée et synchronisées dans chaque emplacement géographique, partage et expériences impliquant toute personne de votre société contiennent des championnats.</span><span class="sxs-lookup"><span data-stu-id="3b392-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="3b392-121">Exemple de configuration de client multi-geo</span><span class="sxs-lookup"><span data-stu-id="3b392-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="3b392-122">En utilisant un client multigéographique, Contoso, dont l’emplacement central est situé en Amérique du Nord, peut s’étendre jusqu’aux emplacements géographiques satellites en Europe et en Australie dans le cadre de la même organisation Contoso.com. Les utilisateurs dont l’emplacement de données favori est défini sur Europe ont leur OneDrive en Europe, tandis que les utilisateurs dont l’emplacement de données favori est en Amérique du Nord ont leur OneDrive aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="3b392-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Carte du monde affichant les emplacements géographique de Contoso et autres emplacements disponibles geo](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="3b392-124">Obtention des fonctionnalités multigéographiques en trois étapes simples</span><span class="sxs-lookup"><span data-stu-id="3b392-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="3b392-125">La configuration Multi-Geo est facile :</span><span class="sxs-lookup"><span data-stu-id="3b392-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="3b392-p103">Travailler avec votre équipe de compte à ajouter le plan de service _Multi-Geo des fonctionnalités dans Office 365_ . Ils vous guide pour ajouter le nombre de licences nécessaires.</span><span class="sxs-lookup"><span data-stu-id="3b392-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="3b392-128">Ajoutez vos emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="3b392-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="3b392-129">Configurez vos comptes d’utilisateur pour l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="3b392-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="3b392-130">Disponibilité et état de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="3b392-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="3b392-131">Les fonctionnalités multigéographiques de OneDrive sont actuellement disponibles dans les régions et pays suivants :</span><span class="sxs-lookup"><span data-stu-id="3b392-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="3b392-132">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="3b392-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="3b392-133">Australie</span><span class="sxs-lookup"><span data-stu-id="3b392-133">Australia</span></span>
    
- <span data-ttu-id="3b392-134">Canada</span><span class="sxs-lookup"><span data-stu-id="3b392-134">Canada</span></span>
    
- <span data-ttu-id="3b392-135">Union européenne (EMEA)</span><span class="sxs-lookup"><span data-stu-id="3b392-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="3b392-136">Japon</span><span class="sxs-lookup"><span data-stu-id="3b392-136">Japan</span></span>
    
- <span data-ttu-id="3b392-137">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="3b392-137">United Kingdom</span></span>
    
- <span data-ttu-id="3b392-138">États-Unis (Amérique du Nord)</span><span class="sxs-lookup"><span data-stu-id="3b392-138">United States (North America)</span></span>
    
- <span data-ttu-id="3b392-139">Corée</span><span class="sxs-lookup"><span data-stu-id="3b392-139">Korea</span></span>
      
<span data-ttu-id="3b392-140">Emplacements géographiques à venir :</span><span class="sxs-lookup"><span data-stu-id="3b392-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="3b392-141">France</span><span class="sxs-lookup"><span data-stu-id="3b392-141">France</span></span>
- <span data-ttu-id="3b392-142">Inde</span><span class="sxs-lookup"><span data-stu-id="3b392-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="3b392-143">Prise en main</span><span class="sxs-lookup"><span data-stu-id="3b392-143">Getting started</span></span>

<span data-ttu-id="3b392-p104">Pour vous familiariser avec OneDrive pour entreprise Multi-Geo, la première étape consiste à [planifier votre OneDrive pour un environnement d’entreprise Multi-Geo](plan-for-multi-geo.md). Suivant, [en savoir plus sur l’administration d’un environnement multi-geo](administering-a-multi-geo-environment.md) et [comment vos utilisateurs connaîtront un environnement multi-geo](multi-geo-user-experience.md). Lorsque vous êtes prêt à configurer les OneDrive d’entreprise Multi-Geo, [configurer vos clients pour multi-geo](multi-geo-tenant-configuration.md), puis [déplacer des sites OneDrive à leurs nouveaux emplacements de geo](move-onedrive-between-geo-locations.md) et [recherche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="3b392-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
