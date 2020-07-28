---
title: Expérience utilisateur dans un environnement multigéographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Normal
description: Découvrez l’expérience utilisateur de SharePoint, de OneDrive et d’Exchange dans un environnement multigéographique.
ms.openlocfilehash: 55c3f431474715ce03cc313a5d8d208d76b60b78
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433795"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Expérience utilisateur dans un environnement multigéographique

Voici ce que vos utilisateurs verront dans une configuration multigéographique de OneDrive :

## <a name="exchange-mailbox"></a>Boîte aux lettres Exchange

La boîte aux lettres Exchange d’un utilisateur est approvisionnée dans l’emplacement par défaut des données de celui-ci, et déplacée automatiquement si cet emplacement change. Les utilisateurs peuvent se servir d’Outlook et d’Outlook sur le web normalement, sans que cela change l’expérience utilisateur dans un environnement multigéographique.

## <a name="hub-sites"></a>Sites hub

Les sites hub SharePoint améliorent la détection et renforcent l’implication à l’aide de contenu destiné aux employés lors de la création d’une représentation complète et cohérente de projets, départements ou régions. Dans un environnement multigéographique, des sites d’emplacements satellites peuvent facilement être associés à un site hub, indépendamment de l’emplacement géographique de celui-ci. Les utilisateurs peuvent rechercher et obtenir des résultats sur le hub via une simple expérience de recherche, indépendamment de l’emplacement géographique des sites.

## <a name="microsoft-365-app-launcher"></a>Lanceur d’applications Microsoft 365

Le lanceur d’applications prend en compte la configuration multigéographique et dirige chaque vignette vers l’emplacement géographique approprié de la charge de travail. Les vignettes SharePoint et OneDrive pointent vers l’utilisateur à l’emplacement correspondant à l’emplacement géographique approvisionné de l’utilisateur. Cela signifie que, si l’utilisateur a un OneDrive dans l’emplacement central, sa vignette SharePoint pointe vers sa page d’accueil SharePoint dans l’emplacement central, mais que son site de groupe sera approvisionné à l’emplacement correspondant à son emplacement par défaut des données. 

## <a name="office-applications"></a>Applications Office

Les applications Office telles que Word, Excel et PowerPoint détectent automatiquement l’emplacement géographique OneDrive Entreprise correct pour chaque utilisateur à la connexion. Les utilisateurs ne doivent pas entrer l’URL géographique spécifique de leurs sites OneDrive ou SharePoint.

## <a name="onedrive-for-business-sync-client"></a>Client de synchronisation OneDrive Entreprise

Le Client de synchronisation OneDrive Entreprise (version 17.3.6943.0625 et les versions ultérieures) détecte automatiquement l’emplacement géographique OneDrive Entreprise correct pour l’utilisateur. La prise en charge du client de synchronisation inclut la possibilité de synchroniser des sites basés sur des groupes indépendamment de leur emplacement géographique. Notez que le client de synchronisation Groove n’est pas pris en charge dans une configuration multigéographique. 

## <a name="onedrive-for-business-location"></a>Emplacement OneDrive Entreprise

OneDrive Entreprise sera configuré pour les utilisateurs dans leur emplacement de données préféré. Si un utilisateur accède à une URL OneDrive qui contient un emplacement géographique incorrect (par exemple, un signet provenant d’un emplacement géographique précédent), il est automatiquement redirigé vers OneDrive dans l’emplacement géographique approprié.

## <a name="onedrive-ios-and-android"></a>OneDrive iOS et Android 

Les applications mobiles OneDrive iOS et Android indiquent vos fichiers OneDrive et les fichiers partagés avec vous, indépendamment de leur emplacement géographique. Les recherches dans les applications mobiles OneDrive affichent des résultats pertinents de tous les emplacements géographiques. Téléchargez la dernière version de ces applications.

Consultez [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [Utiliser OneDrive sur Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) pour plus d’informations.

## <a name="onedrive-mobile-client"></a>Client mobile OneDrive 

Le client mobile OneDrive prend en compte la configuration multigéographique et affiche du contenu et des résultats pertinents de tous les emplacements géographiques.

## <a name="search"></a>Search

Chaque emplacement géographique a ses propres index de recherche et son centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est envoyée à tous les emplacements géographiques et les résultats renvoyés sont fusionnés puis classés afin que l’utilisateur dispose de résultats unifiés. Les utilisateurs obtiennent des résultats de tous les emplacements géographiques, indépendamment de leur emplacement géographique. Reportez-vous à la rubrique relative à la [configuration de la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour des informations spécifiques.

Les clients de recherche suivants sont pris en charge :

-   OneDrive Entreprise

-   Delve

-   Page d’accueil SharePoint

-   Centre de recherche

-   Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint

## <a name="sharepoint-home"></a>Page d’accueil SharePoint 

Dans SharePoint multigéographique, votre page d’accueil SharePoint est hébergée dans l’emplacement où l’utilisateur se trouve, tel que déterminé par son emplacement OneDrive Entreprise. Par exemple, si le OneDrive de l’utilisateur est hébergé dans un emplacement satellite européen, la page d’accueil SharePoint sera restituée à partir de l’Europe. La page d’accueil SharePoint inclut tout contenu pertinent pour l’utilisateur indépendamment de son emplacement géographique. 

**Sites suivis, Actualités de sites, Sites récents, Sites fréquents et Sites suggérés**

Toutes ces composants s’affichent pour l’utilisateur indépendamment de l’emplacement géographique où le contenu est hébergé, aussi longtemps que l’utilisateur est autorisé à accéder au contenu en question. 

**Liens proposés**

Les administrateurs peuvent configurer dans la page d’accueil SharePoint des liens proposés pertinents pour chaque emplacement géographique. Ainsi, dans la page d’accueil SharePoint, l’administrateur peut suggérer, pour chaque région, des liens appropriés pour les utilisateurs dans cette région. 

## <a name="sharepoint-mobile-client"></a>Client mobile SharePoint 

Le client mobile SharePoint prend en compte la configuration multigéographique et affiche du contenu et des résultats pertinents de tous les emplacements géographiques.

## <a name="sharing"></a>Partage

L’interface du Sélecteur de personnes affiche tous les utilisateurs indépendamment de leur emplacement géographique. Cela permet à un utilisateur de partager avec un autre utilisateur dans le même emplacement géographique, ou dans tout autre emplacement géographique de votre locataire. Le contenu des différents emplacements géographiques s’affiche dans la vue **Partagé avec moi** sur le OneDrive Entreprise de l’utilisateur, et est accessible via une interface d’authentification unique indépendamment de l’emplacement géographique où il est hébergé.

## <a name="teams-experience"></a>Expérience Teams

Teams prend en compte la configuration multigéographique. Les fichiers OneDrive et les fichiers récemment consultés s’affichent indépendamment de l’emplacement géographique de l’utilisateur. Les mentions @ fonctionnent avec des utilisateurs de tous les emplacements géographiques.

## <a name="user-profiles"></a>Profils utilisateur

Les informations de profil utilisateur sont gérées dans l’emplacement géographique de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous êtes redirigé vers l’emplacement géographique approprié pour l’utilisateur, qui indique ses informations de profil complètes.

Si Delve est désactivé, vous voyez l’expérience profil classique dans SharePoint, qui n’est pas adaptée à Multi-Géo.


