---
title: Plan de OneDrive pour l’entreprise Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenir des informations sur les OneDrive pour les professionnels Multi-Geo, fonctionne multi-geo et quels emplacements de geo sont disponibles pour le stockage de données.
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="a7fe6-103">Plan de OneDrive pour l’entreprise Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a7fe6-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="a7fe6-104">Ce guide est conçu pour les administrateurs de sociétés nationales multiples (MNCs) qui préparent leurs clients SharePoint Online soit étendue à d’autres régions, conformément à la présence de l’entreprise afin de répondre aux exigences en matière de délégation de compétences de données.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="a7fe6-p101">Dans une configuration Multi OneDrive-Geo, vos clients Office 365 se compose d’un emplacement central (également connu sous le nom, l’emplacement par défaut) et un ou plusieurs emplacements de geo satellite. Il s’agit d’un client unique qui s’étend sur plusieurs emplacements de la zone géographique. Dans la OneDrive Multi-Geo, vos informations clients, notamment les sites géo, sont gravées dans Azure Active Directory (DAS).</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="a7fe6-108">Voici quelques termes clés multi-geo pour vous aider à comprendre les concepts de base de la configuration :</span><span class="sxs-lookup"><span data-stu-id="a7fe6-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="a7fe6-109">**Clients** – représentation d’une entreprise dans le nuage Office 365 ayant généralement un ou plusieurs domaines lui sont associés (par exemple, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="a7fe6-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="a7fe6-p102">**Emplacements de Geo** – les sites géographiques hébergeant les données de vos clients. Les locataires multi-geo s’étendent sur plus d’un emplacement géographique, par exemple, en Amérique du Nord et en Europe.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="a7fe6-112">**Emplacements de données autorisé (ADL)** – l’emplacement géographique pour laquelle votre client a été configuré pour héberger des données OneDrive et SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="a7fe6-p103">**Emplacement de données par défaut (LDP)** – l’emplacement géographique où sont stockées les données de OneDrive d’un utilisateur individuel. Cette option peut être définie par l’administrateur pour les emplacements de données autorisés qui ont été configurés pour le client. Notez que si vous modifiez le langage PDL pour un utilisateur qui possède déjà un site de OneDrive, leurs données OneDrive ne sont pas déplacées vers le nouvel emplacement géographique automatiquement. Pour plus d’informations, voir [déplacer une bibliothèque OneDrive géo - ailleurs](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="a7fe6-117">L’activation Multi-Geo nécessite quatre étapes principales :</span><span class="sxs-lookup"><span data-stu-id="a7fe6-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="a7fe6-118">Travailler avec votre équipe de compte à ajouter le plan de service _Multi-Geo des fonctionnalités dans Office 365_ .</span><span class="sxs-lookup"><span data-stu-id="a7fe6-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="a7fe6-119">Choisissez votre souhaité de satellite géo emplacements et de les ajouter à vos clients.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="a7fe6-p104">Définir l’emplacement de données par défaut de vos utilisateurs à l’emplacement géographique de satellite souhaité. Lorsqu’un nouveau site de OneDrive est fourni pour un utilisateur, il est mis en service à leur langage PDL.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="a7fe6-122">Migrer des sites OneDrive existants de vos utilisateurs à partir de l’emplacement d’origine vers leur emplacement par défaut des données en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="a7fe6-123">Pour plus d’informations sur chacune de ces étapes, reportez-vous à la section [Configurer OneDrive pour entreprise Multi-Geo](multi-geo-tenant-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="a7fe6-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7fe6-p105">Notez que les fonctionnalités Multi-Geo d’Office 365 ne sont pas conçues pour les cas de l’optimisation des performances, ils sont conçus pour répondre aux exigences en matière de délégation de compétences de données. Pour plus d’informations sur l’optimisation des performances pour Office 365, voir [planification de réseau et de réglage des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) , ou contactez votre service de support.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="a7fe6-p106">Vous pouvez configurer un des emplacements suivants soient satellite des emplacements géographique où vous pouvez héberger les fichiers OneDrive. Lorsque vous planifiez pour multi-geo, dressez la liste des emplacements que vous souhaitez ajouter à vos clients d’Office 365. Nous vous recommandons commençant par un ou deux emplacements de satellite, puis en développant progressivement à plusieurs emplacements de la zone géographique, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a7fe6-129"><strong>Emplacement</strong></span><span class="sxs-lookup"><span data-stu-id="a7fe6-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="a7fe6-130"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="a7fe6-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a7fe6-131">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="a7fe6-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-132">APC</span><span class="sxs-lookup"><span data-stu-id="a7fe6-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a7fe6-133">Europe / Moyen-Orient / Afrique</span><span class="sxs-lookup"><span data-stu-id="a7fe6-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-134">EUROS</span><span class="sxs-lookup"><span data-stu-id="a7fe6-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a7fe6-135">Amérique du Nord</span><span class="sxs-lookup"><span data-stu-id="a7fe6-135">North America</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-136">NAM</span><span class="sxs-lookup"><span data-stu-id="a7fe6-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a7fe6-137">Australie</span><span class="sxs-lookup"><span data-stu-id="a7fe6-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-138">AUSTRALIE</span><span class="sxs-lookup"><span data-stu-id="a7fe6-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a7fe6-139">Canada</span><span class="sxs-lookup"><span data-stu-id="a7fe6-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-140">POUVEZ</span><span class="sxs-lookup"><span data-stu-id="a7fe6-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a7fe6-141">Japon</span><span class="sxs-lookup"><span data-stu-id="a7fe6-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-142">JPN</span><span class="sxs-lookup"><span data-stu-id="a7fe6-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a7fe6-143">Corée</span><span class="sxs-lookup"><span data-stu-id="a7fe6-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-144">KOR</span><span class="sxs-lookup"><span data-stu-id="a7fe6-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a7fe6-145">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="a7fe6-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="a7fe6-146">GBR</span><span class="sxs-lookup"><span data-stu-id="a7fe6-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a7fe6-147">Emplacements géographiques à venir :</span><span class="sxs-lookup"><span data-stu-id="a7fe6-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="a7fe6-148">France</span><span class="sxs-lookup"><span data-stu-id="a7fe6-148">France</span></span>
- <span data-ttu-id="a7fe6-149">Inde</span><span class="sxs-lookup"><span data-stu-id="a7fe6-149">India</span></span>

<span data-ttu-id="a7fe6-p107">Lorsque vous configurez multi-geo, prenez permettent de consolider votre infrastructure sur site lors de la migration vers Office 365. Par exemple, si vous avez des batteries de serveurs sur site en Singapour et en Malaisie, puis vous pouvez consolider les à l’emplacement de satellite APC, sous réserve des exigences en matière de délégation de compétences de données permettent de le faire.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="a7fe6-152">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="a7fe6-152">Best practices</span></span>

<span data-ttu-id="a7fe6-p108">Nous vous conseillons de créer un utilisateur test dans Office 365 pour procéder à des tests initiaux. Nous traiterons des étapes de test et la vérification avec cet utilisateur avant de procéder à des utilisateurs de production intégrée à la fonctionnalité OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="a7fe6-p109">Une fois que vous avez terminé les tests avec l’utilisateur test, sélectionnez un groupe pilote – par exemple à partir de votre service informatique – pour être le premier à utiliser OneDrive dans une nouveau géolocalisation. Pour ce premier groupe, sélectionnez les utilisateurs qui ne disposent pas encore d’un OneDrive. Nous vous recommandons de pas plus de cinq personnes de ce groupe initial et que vous développer progressivement le suivant une approche de déploiement par lot.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="a7fe6-p110">Chaque utilisateur doit disposer d’un *emplacement de données par défaut* (PDL) que Office 365 peut déterminer dans quel emplacement géographique à provisionner leur OneDrive. Emplacement de données par défaut de l’utilisateur doit correspondre à une de vos emplacements choisis satellite ou votre site central. Alors que le champ PDL n’est pas obligatoire, nous vous recommandons de définir que PDL pour tous les utilisateurs. Charges de travail d’un utilisateur sans PDL seront déployés dans l’emplacement central basé sur la logique de Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="a7fe6-p111">Créer une liste de vos utilisateurs et inclure leur nom d’utilisateur principal (UPN) et le code magasin de l’emplacement des données par défaut approprié. Inclure votre utilisateur de test et de votre groupe pilote initial commence. Vous aurez besoin de cette liste pour les procédures de configuration.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="a7fe6-p112">Si vos utilisateurs sont synchronisées à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), vous devez définir l’emplacement de données par défaut pour les utilisateurs synchronisés à l’aide d’Azure Active Directory se connecter. Impossible de configurer directement l’emplacement de données par défaut pour des utilisateurs synchronisés à l’aide de PowerShell d’AD Azure. Les étapes pour définir le langage PDL dans Active Directory et de le synchroniser sont couvertes dans [sync d’Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="a7fe6-p113">L’administration d’un client multi-geo peut différer d’un client non-multi-geo, comme de nombreux paramètres SharePoint et OneDrive et les services sont multi-geo prenant en charge. Nous vous conseillons d’étudier [administration d’un environnement multi-geo](administering-a-multi-geo-environment.md) avant de poursuivre la configuration.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="a7fe6-170">Pour plus d’informations sur l’expérience de vos utilisateurs finaux dans un environnement multi-geo, lire [l’expérience de l’utilisateur dans un environnement multgeo](multi-geo-user-experience.md) .</span><span class="sxs-lookup"><span data-stu-id="a7fe6-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="a7fe6-171">Pour démarrer la configuration OneDrive de Business Multi-Geo, consultez [Configurer OneDrive pour entreprise Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a7fe6-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="a7fe6-172">Une fois que vous avez terminé la configuration, n’oubliez pas de [migration de bibliothèques de OneDrive vos utilisateurs](move-onedrive-between-geo-locations.md) que nécessaire pour que vos utilisateurs à partir de leurs emplacements de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7fe6-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
