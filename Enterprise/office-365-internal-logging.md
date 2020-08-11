---
title: Journalisation interne de Microsoft 365 pour Microsoft 365 Engineering
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dans cet article, vous trouverez une explication du fonctionnement de la journalisation interne pour Microsoft 365 Engineering Teams.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e7c5c32d1ea0704f8f56a4af6e6dd85f73f9c2df
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606550"
---
# <a name="internal-logging-for-microsoft-365-engineering"></a>Journalisation interne pour l’ingénierie Microsoft 365

Outre les événements et les données de journalisation disponibles pour les clients, il existe également un système de collecte de données de journal interne disponible pour les ingénieurs Microsoft 365 de Microsoft. De nombreux types de données de journal sont téléchargés à partir des serveurs Microsoft 365 vers un service informatique interne et de grande taille appelé Cosmos. Chaque équipe de service télécharge les journaux d’audit de leurs serveurs respectifs dans la base de données Cosmos pour l’agrégation et l’analyse. Ce transfert de données se produit sur une connexion TLS validée par FIPS 140-2 sur des ports et protocoles approuvés spécifiquement à l’aide d’un outil Automation propriétaire appelé le chargeur de données Office (ODL). Les outils utilisés dans Microsoft 365 pour collecter et traiter des enregistrements d’audit n’autorisent pas les modifications permanentes ou irréversibles du contenu des enregistrements d’audit d’origine ou de l’ordre des heures.

Les équipes de service utilisent Cosmos en tant que référentiel centralisé pour effectuer une analyse de l’utilisation des applications, mesurer les performances du système et des opérations, et Rechercher des anomalies et des motifs susceptibles d’indiquer des problèmes ou des problèmes de sécurité. Chaque équipe de service télécharge une ligne de base des journaux dans Cosmos, en fonction de ce qu’elles cherchent à analyser, qui sont souvent les suivantes :

- Journaux des événements
- Journaux AppLocker
- Données de performances
- Données System Center
- Enregistrements des détails des appels
- Données de qualité de l’expérience
- Journaux de serveur Web IIS
- Journaux SQL Server
- Données syslog
- Journaux d’audit de sécurité

Avant de télécharger des données dans Cosmos, l’application ODL utilise un service de nettoyage pour brouiller les champs contenant des données client, tels que les informations client et les informations identifiables de l’utilisateur final, et remplacer ces champs par une valeur de hachage. Les journaux hachés et iranonymes sont réécrits, puis téléchargés dans Cosmos. Les équipes de service exécutent des requêtes délimitées par rapport à leurs données dans Cosmos à des fins de corrélation, d’alerte et de création de rapports. La période de rétention des données du journal d’audit dans Cosmos est déterminée par les équipes de service ; la plupart des données du journal d’audit sont conservées pendant 90 jours ou plus afin de prendre en charge les analyses des incidents de sécurité et de respecter les exigences de rétention réglementaire.

L’accès aux données Microsoft 365 stockées dans Cosmos est limité au personnel autorisé. Microsoft limite la gestion de la fonctionnalité d’audit au sous-ensemble limité des membres de l’équipe de service qui sont responsables de la fonctionnalité d’audit. Ces membres de l’équipe n’ont pas la possibilité de modifier ou de supprimer des données de Cosmos, et toutes les modifications apportées aux mécanismes de journalisation pour Cosmos sont enregistrées et auditées.

Chaque équipe de service accède à ses données de journal pour analyse en autorisant certaines applications à effectuer des analyses spécifiques. Par exemple, l’équipe de sécurité Microsoft 365 utilise les données de Cosmos via un analyseur des journaux d’événements propriétaire pour corréler, alerter et générer des rapports actionnables sur les éventuelles activités suspectes dans l’environnement de production Microsoft 365. Les rapports de ces données sont utilisés pour corriger les vulnérabilités et améliorer les performances globales du service. Si une alerte ou un rapport spécifique nécessite une nouvelle enquête, le personnel de service peut demander que les données soient réimportées dans le service Microsoft 365. Étant donné que le journal spécifique importé depuis Cosmos est chiffré et que le personnel de service n’a pas accès aux clés de déchiffrement, le journal cible est transmis par programmation via un service de déchiffrement qui renvoie des résultats délimités au personnel de service autorisé. Les vulnérabilités figurant dans cet exercice sont signalées et transmises à l’aide des canaux de gestion des incidents de sécurité standard de Microsoft.
