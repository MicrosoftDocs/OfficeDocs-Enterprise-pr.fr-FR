---
title: Expérience utilisateur dans un environnement multigéographique
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
description: Découvrez l’expérience utilisateur SharePoint et OneDrive dans un environnement multigéographique.
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849830"
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="56e8a-103">Expérience utilisateur dans un environnement multigéographique</span><span class="sxs-lookup"><span data-stu-id="56e8a-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="56e8a-104">Voici ce que vos utilisateurs verront dans une configuration multigéographique OneDrive :</span><span class="sxs-lookup"><span data-stu-id="56e8a-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="56e8a-105">Emplacement OneDrive Entreprise de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="56e8a-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="56e8a-p101">OneDrive Entreprise sera configuré pour les utilisateurs dans leur emplacement de données préféré. Si un utilisateur accède à une URL OneDrive qui contient un emplacement géographique incorrect (par exemple, un signet provenant d’un emplacement géographique précédent), il est automatiquement redirigé vers OneDrive dans l’emplacement géographique approprié.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="56e8a-108">Partage</span><span class="sxs-lookup"><span data-stu-id="56e8a-108">Sharing</span></span>

<span data-ttu-id="56e8a-p102">L’expérience Sélecteur de personnes affiche tous les utilisateurs, quel que soit leur emplacement géographique. Cela permet à l’utilisateur d’effectuer un partage avec un autre utilisateur dans le même emplacement géographique ou dans l’un des autres emplacements géographiques de votre client. Le contenu de différents emplacements géographiques s’affiche dans la vue **Partagés avec moi** dans OneDrive Entreprise de l’utilisateur et est accessible via l’expérience d’authentification unique, indépendamment de l’emplacement géographique dans lequel il est hébergé.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="56e8a-112">Applications Office</span><span class="sxs-lookup"><span data-stu-id="56e8a-112">Office applications</span></span>

<span data-ttu-id="56e8a-p103">Les applications Office telles que Word, Excel et PowerPoint détectent automatiquement l’emplacement géographique OneDrive Entreprise correct pour chaque utilisateur à la connexion. Les utilisateurs ne doivent pas entrer l’URL géographique spécifique de leur OneDrive.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="56e8a-115">Client de synchronisation OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="56e8a-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="56e8a-116">Le Client de synchronisation OneDrive Entreprise (version 17.3.6943.0625 et les versions ultérieures) détecte automatiquement l’emplacement géographique OneDrive Entreprise correct pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="56e8a-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="56e8a-117">Lanceur d’applications Office 365</span><span class="sxs-lookup"><span data-stu-id="56e8a-117">Office 365 app launcher</span></span>

<span data-ttu-id="56e8a-p104">Le lanceur d’application est adapté à Multi-Géo et redirige chaque vignette vers l’emplacement géographique approprié de la charge de travail. La vignette OneDrive pointe vers l’emplacement géographique correct qui héberge la bibliothèque OneDrive de l’utilisateur, tandis que la vignette SharePoint pointe tous les utilisateurs vers l’emplacement central, car les sites d’équipe y sont toujours hébergés.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="56e8a-120">Profils utilisateur Delve</span><span class="sxs-lookup"><span data-stu-id="56e8a-120">Delve User profiles</span></span>

<span data-ttu-id="56e8a-p105">Les informations de profil utilisateur sont gérées dans l’emplacement géographique de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous êtes redirigé vers l’emplacement géographique approprié pour l’utilisateur, qui indique ses informations de profil complètes.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="56e8a-123">Si Delve est désactivé, vous voyez l’expérience profil classique dans SharePoint, qui n’est pas adaptée à Multi-Géo.</span><span class="sxs-lookup"><span data-stu-id="56e8a-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="56e8a-124">Delve</span><span class="sxs-lookup"><span data-stu-id="56e8a-124">Delve</span></span>

<span data-ttu-id="56e8a-125">Pour les utilisateurs d’Office 365 qui ne figurent pas dans les instances satellite, Delve Multi-Géo est pris en charge, mais avec une limite : Delve n’effectue pas le lien vers les billets de blog écrits par des utilisateurs dans d’autres régions, mais uniquement vers leurs sites de blog SharePoint.</span><span class="sxs-lookup"><span data-stu-id="56e8a-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="56e8a-126">Rechercher</span><span class="sxs-lookup"><span data-stu-id="56e8a-126">Search</span></span>

<span data-ttu-id="56e8a-p106">Chaque emplacement géographique a ses propres index de recherche et son centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est envoyée à tous les emplacements géographiques et les résultats renvoyés sont fusionnés puis classés afin que l’utilisateur dispose de résultats unifiés. Les utilisateurs obtiennent des résultats de tous les emplacements géographiques, indépendamment de leur emplacement géographique. Reportez-vous à la rubrique relative à la [configuration de la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour des informations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="56e8a-131">Les clients de recherche suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="56e8a-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="56e8a-132">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="56e8a-132">OneDrive for Business</span></span>

-   <span data-ttu-id="56e8a-133">Delve</span><span class="sxs-lookup"><span data-stu-id="56e8a-133">Delve</span></span>

-   <span data-ttu-id="56e8a-134">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="56e8a-134">SharePoint Home</span></span>

-   <span data-ttu-id="56e8a-135">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="56e8a-135">The Search Center</span></span>

-   <span data-ttu-id="56e8a-136">Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint</span><span class="sxs-lookup"><span data-stu-id="56e8a-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="56e8a-137">OneDrive iOS et Android</span><span class="sxs-lookup"><span data-stu-id="56e8a-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="56e8a-p107">Les applications mobiles OneDrive iOS et Android indiquent vos fichiers OneDrive et les fichiers partagés avec vous, indépendamment de leur emplacement géographique. Les recherches dans les applications mobiles OneDrive affichent des résultats pertinents de tous les emplacements géographiques. Téléchargez la dernière version de ces applications.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="56e8a-141">Consultez [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [Utiliser OneDrive sur Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="56e8a-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="56e8a-142">Expérience Teams</span><span class="sxs-lookup"><span data-stu-id="56e8a-142">Teams Experience</span></span>

<span data-ttu-id="56e8a-p108">Teams est adapté à Multi-Géo. Les fichiers OneDrive et les fichiers récemment consultés sont affichés indépendamment de l’emplacement géographique de l’utilisateur. Les mentions @ fonctionnement avec les utilisateurs de tous les emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="56e8a-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
