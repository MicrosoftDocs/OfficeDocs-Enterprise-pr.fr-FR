---
title: Expérience de l’utilisateur dans un environnement multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenir des informations sur l’expérience utilisateur SharePoint et OneDrive dans un environnement multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Expérience de l’utilisateur dans un environnement multi-geo

Voici ce que verront les utilisateurs dans une configuration Multi-Geo de OneDrive :

#### <a name="users-onedrive-for-business-location"></a>OneDrive de l’utilisateur pour le lieu de travail

Les utilisateurs auront leur OneDrive pour entreprise mis en service dans leur emplacement de données par défaut. Si un utilisateur navigue vers une URL OneDrive qui contient un géo-emplacement incorrect (tel qu’un signet à partir d’un emplacement géographique précédent), ils sont automatiquement redirigés à l’OneDrive de l’emplacement géographique appropriée.

#### <a name="sharing"></a>Partage

L’expérience de sélecteur de personnes affiche tous les utilisateurs, quel que soit leur emplacement géographique. Cela permet à un utilisateur de partager avec un autre utilisateur dans leur zone géographique même ou dans d’autres emplacements de géographique de vos clients. Contenu de geo différent emplacements s’affichera dans la vue **partagées avec moi** dans le OneDrive de l’utilisateur pour les entreprises et est accessible avec une expérience unique Single-Sign-On que la géolocalisation, il est hébergé dans.

#### <a name="office-applications"></a>Applications Office

Applications Office telles que Word, Excel et PowerPoint détecte automatiquement le OneDrive correct de géolocalisation professionnels pour chaque utilisateur lors de la connexion. Les utilisateurs n’avez pas besoin d’entrer l’URL de la zone géographique spécifiques pour leur OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive pour le Client de synchronisation Business

Le OneDrive pour le Client de synchronisation Business (version 17.3.6943.0625 ou version ultérieure) détecte automatiquement le OneDrive correct pour l’emplacement géographique de professionnels pour l’utilisateur.

#### <a name="office-365-app-launcher"></a>Lanceur d’applications Office 365

Le Lanceur d’applications est prenant en charge le Multi-Geo et dirigera chaque mosaïque pour l’emplacement géographique appropriée de la charge de travail. Les points de mosaïque OneDrive à l’emplacement correct geo où bibliothèque de OneDrive de l’utilisateur est hébergée, tandis que la mosaïque SharePoint pointera l’emplacement central, de tous les utilisateurs comme sites d’équipe toujours hébergés il.

#### <a name="delve-user-profiles"></a>Plonger les profils utilisateur

Les informations de profil utilisateur sont gravées dans l’emplacement géographique de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous allez être redirigé vers l’emplacement géographique appropriée pour l’utilisateur, où vous pouvez voir les détails de leur profil complet.

Si Delve est désactivée, vous verrez le profil classique rencontrer dans SharePoint, qui n’est pas multi-geo prenant en charge.

#### <a name="delve"></a>Delve

Pour les utilisateurs Office 365 dans les instances de satellite, plonger Multi-Geo est pris en charge, avec la restriction que Delve ne lie pas aux billets de blog SharePoint écrites par des utilisateurs dans d’autres régions, uniquement pour les sites de blogs SharePoint.

#### <a name="search"></a>Rechercher

Chaque emplacement géographique a son propre index de recherche et le centre de recherche. Lorsqu’un utilisateur recherche, la requête est envoyée à tous les emplacements de la zone géographique, et les résultats renvoyés sont fusionnées et ensuite classées afin que l’utilisateur obtient les résultats unifiées. Les utilisateurs obtiennent des résultats de tous les emplacements de géo, quel que soit leur emplacement géographique. Pour les détails, reportez-vous à la section [Configurer la recherche de OneDrive de professionnels Multi-Geo](configure-search-for-multi-geo.md) .

Les clients de recherche suivants sont pris en charge :

-   OneDrive Entreprise

-   Delve

-   Accueil SharePoint

-   Le centre de recherche

-   Applications de recherche personnalisées qui utilisent l’API de recherche de SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS et Android 

Le OneDrive iOS et Android applications mobiles affichera les fichiers OneDrive et fichiers partagés avec vous, indépendamment de leur emplacement géographique. Recherche dans les applications mobiles OneDrive affichera les résultats pertinents de tous les emplacements de la zone géographique. Veuillez télécharger la dernière version de ces applications.

Pour plus d’informations, reportez-vous à la section Utilisation [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [OneDrive d’utilisation pour Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .

#### <a name="teams-experience"></a>Expérience des équipes

Équipes est multi-geo prenant en charge. Les fichiers OneDrive et les fichiers récemment affichés sont affichés, quel que soit l’emplacement géographique de l’utilisateur. @ mentionne le travail avec les utilisateurs de tous les géo-nombre de sites.
