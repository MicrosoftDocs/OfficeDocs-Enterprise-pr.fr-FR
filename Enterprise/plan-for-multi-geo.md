---
title: Planification de OneDrive Entreprise Multi-Géo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez OneDrive Entreprise Multi-Géo, son fonctionnement et les emplacements géographiques disponibles pour le stockage des données.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="00b4d-103">Planification de OneDrive Entreprise Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="00b4d-103">Plan for OneDrive for Business</span></span>

<span data-ttu-id="00b4d-104">Ce guide est conçu pour les administrateurs des entreprises multinationales qui préparent le déploiement de leur client SharePoint Online dans des emplacements géographiques supplémentaires en fonction de la présence de l’entreprise pour répondre aux exigences de résidence.</span><span class="sxs-lookup"><span data-stu-id="00b4d-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="00b4d-p101">Dans une configuration OneDrive Multi-Géo, votre client Office 365 est constitué d’un emplacement central (également appelé emplacement par défaut) et d’un ou plusieurs emplacements géographiques satellites. Il s’agit d’un client unique déployé sur plusieurs emplacements géographiques. Dans OneDrive Multi-Géo, vos informations de client, y compris les emplacements géographiques, sont gérées dans Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="00b4d-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="00b4d-108">Voici des termes géographiques clés pour vous aider à comprendre les concepts de base de la configuration :</span><span class="sxs-lookup"><span data-stu-id="00b4d-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="00b4d-109">**Client** : représentation d’une organisation dans le cloud Office 365 qui a généralement un ou plusieurs domaines qui lui sont associés (par exemple, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="00b4d-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="00b4d-p102">**Emplacements géographiques** : emplacements géographiques où sont hébergées les données de votre client. Les clients multigéographiques sont déployés sur plusieurs emplacements géographiques (par exemple, en Amérique du Nord et en Europe).</span><span class="sxs-lookup"><span data-stu-id="00b4d-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="00b4d-112">**Emplacements de données autorisés** : les emplacements géographiques pour lesquels votre client a été configuré pour héberger des données OneDrive et SharePoint.</span><span class="sxs-lookup"><span data-stu-id="00b4d-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="00b4d-p103">**Emplacement de données par défaut** : l’emplacement géographique où les données OneDrive d’un utilisateur individuel sont stockées. Il peut être défini par l’administrateur sur l’un des emplacements de données autorisés configurés pour le client. Notez que si vous changez l’emplacement de données par défaut d’un utilisateur qui possède déjà un site OneDrive, ses données OneDrive ne sont pas déplacées vers le nouvel emplacement géographique automatiquement. Reportez-vous à l’article relatif au [déplacement d’une bibliothèque OneDrive vers un autre emplacement géographique](move-onedrive-between-geo-locations.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="00b4d-117">L’activation Multi-Géo requiert quatre étapes principales :</span><span class="sxs-lookup"><span data-stu-id="00b4d-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="00b4d-118">Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Office 365_.</span><span class="sxs-lookup"><span data-stu-id="00b4d-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="00b4d-119">Choisir des emplacements géographiques satellites et les ajouter à votre client.</span><span class="sxs-lookup"><span data-stu-id="00b4d-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="00b4d-p104">Définir l’emplacement de données par défaut de vos utilisateurs sur l’emplacement géographique satellite souhaité. Lorsqu’un nouveau site OneDrive est configuré pour un utilisateur, il est configuré pour ses emplacements de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="00b4d-122">Déplacer les sites OneDrive existants de vos utilisateurs de l’emplacement initial vers leur emplacement de données par défaut, selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="00b4d-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="00b4d-123">Reportez-vous à la [configuration de OneDrive Entreprise Multi-Géo](multi-geo-tenant-configuration.md) pour plus d’informations sur chacune de ces étapes.</span><span class="sxs-lookup"><span data-stu-id="00b4d-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00b4d-p105">Notez que les fonctionnalités multigéographiques d’Office 365 ne sont pas conçues pour des cas d’optimisation des performances. Elles sont conçues pour répondre aux exigences de résidence des données. Pour plus d’informations sur l’optimisation des performances pour Office 365, reportez-vous à l’article relatif à la [planification réseau et à l’optimisation des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou contactez votre groupe de support.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="00b4d-p106">Vous pouvez configurer les emplacements géographiques satellites suivants où vous pouvez héberger les fichiers OneDrive. Lorsque vous planifiez Multi-Géo, créez une liste des emplacements à ajouter à votre client Office 365. Nous vous recommandons de commencer avec un ou deux emplacements satellites puis de déployer progressivement sur d’autres emplacements géographiques, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="00b4d-129"><strong>Emplacement</strong></span><span class="sxs-lookup"><span data-stu-id="00b4d-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="00b4d-130"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="00b4d-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="00b4d-131">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="00b4d-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="00b4d-132">APC</span><span class="sxs-lookup"><span data-stu-id="00b4d-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="00b4d-133">Europe / Moyen-Orient / Afrique</span><span class="sxs-lookup"><span data-stu-id="00b4d-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="00b4d-134">EUR</span><span class="sxs-lookup"><span data-stu-id="00b4d-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="00b4d-135">Amérique du Nord</span><span class="sxs-lookup"><span data-stu-id="00b4d-135">North America</span></span></td>
<td align="left"><span data-ttu-id="00b4d-136">NAM</span><span class="sxs-lookup"><span data-stu-id="00b4d-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="00b4d-137">Australie</span><span class="sxs-lookup"><span data-stu-id="00b4d-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="00b4d-138">AUS</span><span class="sxs-lookup"><span data-stu-id="00b4d-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="00b4d-139">Canada</span><span class="sxs-lookup"><span data-stu-id="00b4d-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="00b4d-140">CAN</span><span class="sxs-lookup"><span data-stu-id="00b4d-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="00b4d-141">Japon</span><span class="sxs-lookup"><span data-stu-id="00b4d-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="00b4d-142">JPN</span><span class="sxs-lookup"><span data-stu-id="00b4d-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="00b4d-143">Corée</span><span class="sxs-lookup"><span data-stu-id="00b4d-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="00b4d-144">KOR</span><span class="sxs-lookup"><span data-stu-id="00b4d-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="00b4d-145">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="00b4d-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="00b4d-146">GBR</span><span class="sxs-lookup"><span data-stu-id="00b4d-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="00b4d-147">Emplacements géographiques à venir :</span><span class="sxs-lookup"><span data-stu-id="00b4d-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="00b4d-148">France</span><span class="sxs-lookup"><span data-stu-id="00b4d-148">France</span></span>
- <span data-ttu-id="00b4d-149">Inde</span><span class="sxs-lookup"><span data-stu-id="00b4d-149">India</span></span>

<span data-ttu-id="00b4d-p107">Lorsque vous configurez Multi-Géo, envisagez de consolider votre infrastructure locale lors de la migration vers Office 365. Par exemple, si vous avez des batteries de serveurs locales à Singapour et en Malaisie, vous pouvez les consolider avec l’emplacement satellite APC, à condition que les exigences de résidence des données vous permettent de le faire.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="00b4d-152">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="00b4d-152">Best practices</span></span>

<span data-ttu-id="00b4d-p108">Nous vous recommandons de créer un utilisateur test dans Office 365 pour effectuer des tests initiaux. Nous allons passer en revue quelques étapes de test et de vérification avec cet utilisateur avant d’intégrer des utilisateurs de production dans la fonction OneDrive Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="00b4d-p109">Une fois que vous avez terminé les tests avec l’utilisateur test, sélectionnez un groupe pilote (éventuellement de votre service informatique) qui sera le premier à utiliser OneDrive dans un nouvel emplacement géographique. Pour ce premier groupe, sélectionnez les utilisateurs qui ne possèdent pas encore un OneDrive. Nous vous recommandons de ne pas sélectionner plus de cinq personnes dans ce groupe initial et de le développer progressivement à l’aide d’une approche de déploiement par lot.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="00b4d-p110">Chaque utilisateur doit disposer d’un *emplacement de données par défaut* (PDL) défini afin qu’Office 365 puisse déterminer dans quel emplacement géographique configurer son OneDrive. L’emplacement de données par défaut de l’utilisateur doit correspondre à l’un de vos emplacements satellites choisis ou à votre emplacement central. Le champ PDL n’est pas obligatoire, mais nous vous recommandons de définir un PDL pour tous les utilisateurs. Les charges de travail d’un utilisateur sans PDL seront configurées dans l’emplacement central en fonction de la logique Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="00b4d-p111">Créez une liste de vos utilisateurs et incluez leur nom d’utilisateur principal (UPN) et le code de l’emplacement des données par défaut approprié. Incluez votre utilisateur test et votre groupe pilote initial pour commencer. Vous aurez besoin de cette liste pour les procédures de configuration.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="00b4d-p112">Si vos utilisateurs sont synchronisés à partir d’un système Active Directory (AD) local avec Azure Active Directory (AAD), vous devez définir l’emplacement de données par défaut pour les utilisateurs synchronisés à l’aide d’Azure Active Directory Connect. Vous ne pouvez pas configurer directement l’emplacement des données par défaut pour les utilisateurs synchronisés à l’aide d’Azure AD PowerShell. Les étapes à suivre pour configurer le PDL dans AD et le synchroniser sont décrites dans l’article [Synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources Office 365](https://docs.microsoft.com/fr-FR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="00b4d-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/fr-FR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="00b4d-p113">L’administration d’un client multigéographique peut être différente de celle d’un client non multigéographique, car de nombreux services et paramètres SharePoint et OneDrive sont adaptés à un environnement multigéographique. Nous vous recommandons de consulter l’article relatif à l’[administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md) avant de poursuivre votre configuration.</span><span class="sxs-lookup"><span data-stu-id="00b4d-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="00b4d-170">Lisez l’article [Expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md) pour plus d’informations sur l’expérience de vos utilisateurs finaux dans un environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="00b4d-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="00b4d-171">Pour démarrer la configuration de OneDrive Entreprise Multi-Géo, reportez-vous à la [configuration de OneDrive Entreprise Multi-Géo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="00b4d-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="00b4d-172">Une fois que vous avez terminé la configuration, n’oubliez pas de [migrer les bibliothèques OneDrive de vos utilisateurs](move-onedrive-between-geo-locations.md) pour permettre à vos utilisateurs de travailler depuis leur emplacement de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="00b4d-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
