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
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Expérience utilisateur dans un environnement multigéographique

Voici ce que vos utilisateurs verront dans une configuration multigéographique OneDrive :

#### <a name="users-onedrive-for-business-location"></a>Emplacement OneDrive Entreprise de l’utilisateur

OneDrive Entreprise sera configuré pour les utilisateurs dans leur emplacement de données préféré. Si un utilisateur accède à une URL OneDrive qui contient un emplacement géographique incorrect (par exemple, un signet provenant d’un emplacement géographique précédent), ils sont automatiquement redirigés vers OneDrive dans l’emplacement géographique approprié.

#### <a name="sharing"></a>Partage

L’expérience Sélecteur de personnes affiche tous les utilisateurs quel que soit leur emplacement géographique. Cela permet à un utilisateur de partager avec un autre utilisateur dans leur même emplacement géographique ou dans l’un des autres emplacements géographiques de votre client. Le contenu de différents emplacements géographiques s’affichera dans la vue **Partagés avec moi** dans OneDrive Entreprise de l’utilisateur et est accessible avec l’expérience d’authentification unique, indépendamment de l’emplacement géographique dans lequel il est hébergé.

#### <a name="office-applications"></a>Applications Office

Les applications Office telles que Word, Excel et PowerPoint détectent automatiquement l’emplacement géographique OneDrive Entreprise correct pour chaque utilisateur à la connexion. Les utilisateurs ne doivent pas entrer l’URL géographique spécifique de leur OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>Client de synchronisation OneDrive Entreprise

Le Client de synchronisation OneDrive Entreprise (version 17.3.6943.0625 et les versions ultérieures) détecte automatiquement l’emplacement géographique OneDrive Entreprise correct pour l’utilisateur.

#### <a name="office-365-app-launcher"></a>Lanceur d’applications Office 365

Le Lanceur d’application est adapté à Multi-Géo et redirige chaque vignette à l’emplacement géographique approprié de la charge de travail. La vignette OneDrive pointe vers l’emplacement géographique correct qui héberge la bibliothèque OneDrive de l’utilisateur, tandis que la vignette SharePoint pointe tous les utilisateurs vers l’emplacement central, car les sites d’équipe y sont toujours hébergés.

#### <a name="delve-user-profiles"></a>Profils utilisateur Delve

Les informations de profil utilisateur sont gérées dans l’emplacement géographique de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous êtes redirigé vers l’emplacement géographique approprié pour l’utilisateur, qui indique ses informations de profil complètes.

Si Delve est désactivé, vous voyez l’expérience profil classique dans SharePoint, qui n’est pas adaptée à Multi-Géo.

#### <a name="delve"></a>Delve

Pour les utilisateurs d’Office 365 qui ne figurent pas dans les instances satellite, Delve Multi-Géo est pris en charge, mais avec une limite : Delve n’effectue pas le lien vers les billets de blog écrits par des utilisateurs dans d’autres régions, mais uniquement vers leurs sites de blog SharePoint.

#### <a name="search"></a>Rechercher

Chaque emplacement géographique a ses propres index de recherche et son centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est envoyée à tous les emplacements géographiques et les résultats renvoyés sont fusionnés puis classés afin que l’utilisateur dispose de résultats unifiés. Les utilisateurs obtiennent des résultats de tous les emplacements géographiques, indépendamment de leur emplacement géographique. Reportez-vous à la rubrique relative à la [configuration de la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour des informations spécifiques.

Les clients de recherche suivants sont pris en charge :

-   OneDrive Entreprise

-   Delve

-   Page d’accueil SharePoint

-   Centre de recherche

-   Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS et Android 

Les applications mobiles OneDrive iOS et Android indiquent vos fichiers OneDrive et les fichiers partagés avec vous, indépendamment de leur emplacement géographique. Les recherches dans les applications mobiles OneDrive affichent des résultats pertinents de tous les emplacements géographiques. Téléchargez la dernière version de ces applications.

Consultez [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [Utiliser OneDrive sur Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) pour plus d’informations.

#### <a name="teams-experience"></a>Expérience Teams

Teams est adapté à Multi-Géo. Les fichiers OneDrive et les fichiers récemment consultés sont affichés indépendamment de l’emplacement géographique de l’utilisateur. Les mentions @ fonctionnement avec les utilisateurs de tous les emplacements géographiques.
