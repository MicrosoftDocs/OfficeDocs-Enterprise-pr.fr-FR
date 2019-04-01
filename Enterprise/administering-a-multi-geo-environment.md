---
title: Administration d’un environnement multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment administrer des services SharePoint et OneDrive dans un environnement multigéographique.
ms.openlocfilehash: 7a9865424a18a681dcdbf89b607ab2ae73f44098
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931673"
---
# <a name="administering-a-multi-geo-environment"></a>Administration d’un environnement multigéographique

Découvrez le fonctionnement des services Office 365 dans un environnement multigéographique.

## <a name="audit-log-search"></a>Recherche de journal d’audit

Un [journal d’audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unifié pour vos emplacements satellites est disponible dans la page de recherche dans le journal d’audit d’Office 365. Vous pouvez consulter toutes les entrées de journal d’audit des emplacements géographiques. Par exemple, les activités des utilisateurs dans les régions NAM et EUR apparaissent dans un seul affichage, et vous pouvez appliquer les filtres existants pour voir les activités de certains utilisateurs.

## <a name="bcs-secure-store-apps"></a>BCS, service Banque d’informations sécurisé, applications

BCS, le service Banque d’informations sécurisé et les applications ont des instances distinctes dans chaque emplacement satellite. Ainsi, l’administrateur SharePoint Online doit gérer et configurer ces services séparément à partir de chaque emplacement satellite.

## <a name="ediscovery"></a>eDiscovery 

Par défaut, un responsable ou administrateur d’eDiscovery d’un locataire multigéographique ne peut effectuer une découverte électronique que dans l’emplacement central de ce client. L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre « Région » dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite. Pour configurer le filtre de sécurité de la conformité pour une région, voir [Configurer l’eDiscovery d’Office 365 multigéographique](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Boîtes aux lettres Exchange

Les boîtes aux lettres Exchange des utilisateurs sont déplacées automatiquement en cas de modification de leur emplacement par défaut des données. Lors de sa création, une boîte aux lettres est approvisionnée à l’emplacement par défaut des données de l’utilisateur, ou à l’emplacement central si aucune valeur n’a été définie pour l’emplacement par défaut des données.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Stratégies de protection contre la perte de données d’Information Protection

Vous pouvez définir des stratégies de protection contre la perte de données d’Information Protection pour OneDrive Entreprise, SharePoint et Exchange dans le centre Sécurité et conformité, en étendant les stratégies selon vos besoins au locataire entier ou à des utilisateurs éligibles. Par exemple, si vous souhaitez sélectionner une stratégie pour un utilisateur dans un emplacement satellite, vous pouvez l’appliquer à un compte OneDrive spécifique et entrer l’URL du OneDrive de cet utilisateur. Pour accéder à des instructions générales concernant la création de stratégies de protection contre la perte de données, voir [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

Les stratégies DLP sont synchronisées automatiquement en fonction de leurs conditions d’application à chaque emplacement géographique.

L’interface utilisateur ne permettant pas d’appliquer des stratégies de protection contre la perte de données et de protection des informations à tous les utilisateurs d’un emplacement géographique, vous devez sélectionner les comptes concernés par la stratégie ou appliquer celle-ci globalement à tous les comptes.

## <a name="microsoft-flow"></a>Microsoft Flow

Les flux créés pour l’emplacement satellite utilisent le point de terminaison situé dans l’emplacement géographique par défaut pour le client.  Microsoft Flow n’est pas un service multigéographique. 

## <a name="microsoft-powerapps"></a>Microsoft PowerApps

Les applications créées pour l’emplacement satellite utilisent le point de terminaison situé dans l’emplacement central pour le client. Microsoft PowerApps n’est pas un service multigéographique. 

## <a name="onedrive-administrator-experience"></a>Expérience de l’administrateur OneDrive

Dans le [Centre d’administration OneDrive](https://admin.onedrive.com), l’onglet **Emplacements géographiques** dans le volet de navigation gauche présente une carte où vous pouvez afficher et gérer vos emplacements géographiques. Utilisez cette page pour ajouter ou supprimer des emplacements géographiques pour votre client.

## <a name="security-and-compliance-admin-center"></a>Centre de sécurité et conformité

Il existe un centre de conformité central pour le client multigéographique : [Centre de sécurité et conformité Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

## <a name="sharepoint-storage-quota"></a>Quota de stockage SharePoint

Par défaut, tous les emplacements géographiques d’un environnement multigéographique partagent le quota de stockage disponible du locataire.  Vous pouvez également gérer le quota de stockage en allouant un quota spécifique à un emplacement géographique particulier. Pour plus d’informations, voir [Quotas de stockage SharePoint dans des environnements multigéographiques](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Partage

Les administrateurs peuvent définir et gérer des stratégies de partage pour chacun de leurs emplacements. Les sites OneDrive et SharePoint de chaque emplacement géographique respectent uniquement les paramètres de partage associés à un emplacement géographique précis (par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre emplacement central, mais pas pour votre emplacement satellite, et inversement). Notez que les paramètres de partage ne vous permettent pas de configurer des limites de partage entre emplacements géographiques.

## <a name="taxonomy"></a>Taxonomie

Nous prenons en charge une [taxonomie](https://docs.microsoft.com/sharepoint/managed-metadata) unifiée pour gérer les métadonnées dans l’entreprise à différents emplacements géographiques, les données de référence étant hébergées dans l’emplacement central de votre entreprise. Nous vous recommandons de gérer votre taxonomie globale à partir de l’emplacement central et d’ajouter uniquement des termes spécifiques à la taxonomie de l’emplacement satellite. Les termes de la taxonomie globale sont synchronisés avec les emplacements satellites.

Pour plus de détails et pour obtenir des instructions de développement, voir [Gérer les métadonnées dans un client multigéographique](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata).

## <a name="user-profile-application"></a>Application de profil utilisateur

Il existe une [application de profil utilisateur](https://docs.microsoft.com/sharepoint/manage-user-profiles) dans chaque emplacement géographique. Les informations de profil de chaque utilisateur sont hébergées dans l’emplacement géographique de celui-ci et accessibles à l’administrateur de cet emplacement.

Si vous avez des propriétés de profil personnalisées, nous vous recommandons d’utiliser le même schéma de profil dans toutes les zones géographiques et de remplir vos propriétés de profil personnalisées dans tous les emplacements géographiques ou dans les emplacements requis. Pour savoir comment remplir les données de profil utilisateur par programme, consultez l’[API de mise à jour en bloc de profil utilisateur](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Pour plus de détails et pour obtenir des instructions de développement, voir [Utiliser les profils utilisateur dans un client multigéographique](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience).

## <a name="video-portal"></a>Portail vidéo

Dans un client multigéographique, le portail vidéo Office 365 est servi uniquement à partir de la zone géographique, et tous les utilisateurs sont redirigés vers l’URL de ce portail central. Par conséquent, le service multimédia à distance pour cette région est utilisé comme suit en fonction de votre emplacement central.

Stream est actuellement disponible dans les régions suivantes :

- Amérique du Nord, hébergé aux États-Unis 
- Europe
- Asie-Pacifique

En revanche, Stream n’est pas encore disponible dans les régions suivantes actuellement prises en charge pour Office 365 Video. Par conséquent, pour ces instances locales, nous utilisons le service multimédia à distance le plus proche de la région prise en charge.

- Australie
- Canada
- Inde
- Royaume-Uni
