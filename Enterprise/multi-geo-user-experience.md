---
title: Expérience de l’utilisateur dans un environnement multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur l’expérience utilisateur SharePoint et OneDrive dans un environnement multi-geo.
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="4b04e-103">Expérience de l’utilisateur dans un environnement multi-geo</span><span class="sxs-lookup"><span data-stu-id="4b04e-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="4b04e-104">Voici ce que verront les utilisateurs dans une configuration Multi-Geo de OneDrive :</span><span class="sxs-lookup"><span data-stu-id="4b04e-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="4b04e-105">OneDrive de l’utilisateur pour le lieu de travail</span><span class="sxs-lookup"><span data-stu-id="4b04e-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="4b04e-p101">Les utilisateurs auront leur OneDrive pour entreprise mis en service dans leur emplacement de données par défaut. Si un utilisateur navigue vers une URL OneDrive qui contient un géo-emplacement incorrect (tel qu’un signet à partir d’un emplacement géographique précédent), ils sont automatiquement redirigés à l’OneDrive de l’emplacement géographique appropriée.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="4b04e-108">Partage</span><span class="sxs-lookup"><span data-stu-id="4b04e-108">Sharing</span></span>

<span data-ttu-id="4b04e-p102">L’expérience de sélecteur de personnes affiche tous les utilisateurs, quel que soit leur emplacement géographique. Cela permet à un utilisateur de partager avec un autre utilisateur dans leur zone géographique même ou dans d’autres emplacements de géographique de vos clients. Contenu de geo différent emplacements s’affichera dans la vue **partagées avec moi** dans le OneDrive de l’utilisateur pour les entreprises et est accessible avec une expérience unique Single-Sign-On que la géolocalisation, il est hébergé dans.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="4b04e-112">Applications Office</span><span class="sxs-lookup"><span data-stu-id="4b04e-112">Office applications</span></span>

<span data-ttu-id="4b04e-p103">Applications Office telles que Word, Excel et PowerPoint détecte automatiquement le OneDrive correct de géolocalisation professionnels pour chaque utilisateur lors de la connexion. Les utilisateurs n’avez pas besoin d’entrer l’URL de la zone géographique spécifiques pour leur OneDrive.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="4b04e-115">OneDrive pour le Client de synchronisation Business</span><span class="sxs-lookup"><span data-stu-id="4b04e-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="4b04e-116">Le OneDrive pour le Client de synchronisation Business (version 17.3.6943.0625 ou version ultérieure) détecte automatiquement le OneDrive correct pour l’emplacement géographique de professionnels pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b04e-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="4b04e-117">Lanceur d’applications Office 365</span><span class="sxs-lookup"><span data-stu-id="4b04e-117">Office 365 app launcher</span></span>

<span data-ttu-id="4b04e-p104">Le Lanceur d’applications est prenant en charge le Multi-Geo et dirigera chaque mosaïque pour l’emplacement géographique appropriée de la charge de travail. Les points de mosaïque OneDrive à l’emplacement correct geo où bibliothèque de OneDrive de l’utilisateur est hébergée, tandis que la mosaïque SharePoint pointera l’emplacement central, de tous les utilisateurs comme sites d’équipe toujours hébergés il.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="4b04e-120">Plonger les profils utilisateur</span><span class="sxs-lookup"><span data-stu-id="4b04e-120">Delve User profiles</span></span>

<span data-ttu-id="4b04e-p105">Les informations de profil utilisateur sont gravées dans l’emplacement géographique de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous allez être redirigé vers l’emplacement géographique appropriée pour l’utilisateur, où vous pouvez voir les détails de leur profil complet.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="4b04e-123">Si Delve est désactivée, vous verrez le profil classique rencontrer dans SharePoint, qui n’est pas multi-geo prenant en charge.</span><span class="sxs-lookup"><span data-stu-id="4b04e-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="4b04e-124">Delve</span><span class="sxs-lookup"><span data-stu-id="4b04e-124">Delve</span></span>

<span data-ttu-id="4b04e-125">Pour les utilisateurs Office 365 dans les instances de satellite, plonger Multi-Geo est pris en charge, avec la restriction que Delve ne lie pas aux billets de blog SharePoint écrites par des utilisateurs dans d’autres régions, uniquement pour les sites de blogs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4b04e-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="4b04e-126">Rechercher</span><span class="sxs-lookup"><span data-stu-id="4b04e-126">Search</span></span>

<span data-ttu-id="4b04e-p106">Chaque emplacement géographique a son propre index de recherche et le centre de recherche. Lorsqu’un utilisateur recherche, la requête est envoyée à tous les emplacements de la zone géographique, et les résultats renvoyés sont fusionnées et ensuite classées afin que l’utilisateur obtient les résultats unifiées. Les utilisateurs obtiennent des résultats de tous les emplacements de géo, quel que soit leur emplacement géographique. Pour les détails, reportez-vous à la section [Configurer la recherche de OneDrive de professionnels Multi-Geo](configure-search-for-multi-geo.md) .</span><span class="sxs-lookup"><span data-stu-id="4b04e-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="4b04e-131">Les clients de recherche suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="4b04e-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="4b04e-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="4b04e-132">OneDrive for Business</span></span>

-   <span data-ttu-id="4b04e-133">Delve</span><span class="sxs-lookup"><span data-stu-id="4b04e-133">Delve</span></span>

-   <span data-ttu-id="4b04e-134">Accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="4b04e-134">SharePoint Home</span></span>

-   <span data-ttu-id="4b04e-135">Le centre de recherche</span><span class="sxs-lookup"><span data-stu-id="4b04e-135">The Search Center</span></span>

-   <span data-ttu-id="4b04e-136">Applications de recherche personnalisées qui utilisent l’API de recherche de SharePoint</span><span class="sxs-lookup"><span data-stu-id="4b04e-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="4b04e-137">OneDrive iOS et Android</span><span class="sxs-lookup"><span data-stu-id="4b04e-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="4b04e-p107">Le OneDrive iOS et Android applications mobiles affichera les fichiers OneDrive et fichiers partagés avec vous, indépendamment de leur emplacement géographique. Recherche dans les applications mobiles OneDrive affichera les résultats pertinents de tous les emplacements de la zone géographique. Veuillez télécharger la dernière version de ces applications.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="4b04e-141">Pour plus d’informations, reportez-vous à la section Utilisation [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [OneDrive d’utilisation pour Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .</span><span class="sxs-lookup"><span data-stu-id="4b04e-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="4b04e-142">Expérience des équipes</span><span class="sxs-lookup"><span data-stu-id="4b04e-142">Teams Experience</span></span>

<span data-ttu-id="4b04e-p108">Équipes est multi-geo prenant en charge. Les fichiers OneDrive et les fichiers récemment affichés sont affichés, quel que soit l’emplacement géographique de l’utilisateur. @ mentionne le travail avec les utilisateurs de tous les géo-nombre de sites.</span><span class="sxs-lookup"><span data-stu-id="4b04e-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
