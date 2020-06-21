---
title: Audit et création de rapports dans les services Cloud de Microsoft
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
- M365-analytics
- SPO_Content
f1.keywords:
- NOCSH
description: Vue d’ensemble des fonctionnalités d’audit et de création de rapports dans Microsoft 365 et service assurance.
ms.openlocfilehash: 10bbf660ee0e0868abdb6b41c1cc318f6d64bb61
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774959"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Audit et création de rapports dans les services Cloud de Microsoft

Les services de Cloud Computing Microsoft incluent plusieurs fonctionnalités d’audit et de création de rapports que vous pouvez utiliser pour suivre l’activité des utilisateurs et de l’administration au sein de leur client, des exemples de modifications apportées aux paramètres de configuration du client Exchange Online et SharePoint Online, ainsi que les modifications apportées par les utilisateurs aux documents et autres éléments. Vous pouvez utiliser des informations d’audit et des rapports disponibles dans les services de Cloud Computing Microsoft pour gérer plus efficacement l’expérience utilisateur, atténuer les risques et respecter les obligations de conformité.

## <a name="security--compliance-centers"></a>Centres de sécurité & conformité

Le centre de sécurité [& sécurité microsoft 365](https://protection.office.com), le [Centre de sécurité Microsoft 365](https://security.microsoft.com)et le [Centre de conformité Microsoft 365](https://compliance.microsoft.com) sont des portails d’un seul point pour protéger les données de votre organisation, et ils incluent de nombreuses fonctionnalités d’audit et de création de rapports. Ces centres vous aident à répondre à vos besoins en matière de protection des données ou de conformité et d’auditer l’activité des utilisateurs et des administrateurs. Vous pouvez accéder à ces centres à l’aide de votre compte d’administrateur d’abonnement.

Ces centres incluent des volets de navigation permettant d’accéder à plusieurs fonctionnalités :

- **Alertes :** Vous permet de gérer les alertes, d’afficher les alertes liées à la sécurité et de gérer les alertes avancées à l’aide de la [sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).
- **Autorisations :** Vous permet d' [affecter des autorisations](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center) telles que l’administrateur de la conformité, le gestionnaire eDiscovery et d’autres personnes au sein de votre organisation afin qu’ils puissent effectuer des tâches dans ces centres. Vous attribuez des autorisations pour la plupart des fonctionnalités de chaque centre, mais les autres autorisations doivent être configurées à l’aide du centre d’administration Exchange et du centre d’administration SharePoint.
- **Gestion des menaces :** Vous permet de créer et d’appliquer des stratégies de gestion des appareils à l’aide de la [gestion des appareils mobiles Microsoft 365](https://support.microsoft.com/office/overview-of-mobile-device-management-mdm-for-microsoft-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a)afin de configurer des stratégies de protection contre la [perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies) (DLP) pour votre organisation, de configurer le filtrage du courrier électronique, anti-programme malveillant, DomainKeys Identified identifiés (DKIM), des pièces jointes fiables, des liens fiables et des applications OAuth.
- **Gouvernance des données :** Vous permet d' [importer des données de messagerie ou SharePoint à partir d’autres systèmes vers Microsoft 365](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), de [configurer des boîtes aux lettres d’archivage](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)et de définir des [stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) pour le courrier électronique et d’autres contenus au sein de votre organisation.
- **Recherche & :** Fournit des outils de [recherche de contenu](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), de [Journal d’audit](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), de mise en quarantaine et de gestion des dossiers [eDiscovery](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) pour explorer rapidement les activités dans les boîtes aux lettres, les groupes et les dossiers publics Exchange Online, SharePoint Online et OneDrive entreprise.
- **Rapports :** Vous permet d’accéder rapidement aux [rapports](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) pour SharePoint Online, OneDrive entreprise, Exchange Online et Azure ad.
- **Assurance de service :** Fournit des informations sur la façon dont Microsoft gère la sécurité, la confidentialité et la conformité avec les normes globales pour Microsoft 365, Azure, Microsoft Dynamics CRM Online, Microsoft Intune et d’autres services Cloud. Inclut également l’accès à des rapports d’audit, tels que ISO, SOC et d’autres rapports, ainsi que des contrôles audités, qui fournissent des détails sur les différents contrôles qui ont été testés et vérifiés par des auditeurs tiers de Microsoft 365.

## <a name="service-assurance"></a>Service assurance

De nombreuses organisations dans les industries réglementées sont soumises à des exigences de conformité étendues. Pour effectuer leurs évaluations des risques propres, les clients ont souvent besoin d’informations détaillées sur la façon dont Microsoft 365 maintient la sécurité et la confidentialité de leurs données. Microsoft s’engage à respecter la sécurité et la confidentialité des données des clients dans ses services Cloud et à bénéficier d’une relation de confiance client en fournissant une vue transparente de ses opérations et un accès facile aux rapports et aux évaluations de conformité indépendantes.

Service assurance fournit la transparence des opérations et des informations sur la façon dont Microsoft conserve la sécurité, la confidentialité et la conformité des données client dans Microsoft 365. Elle inclut des rapports d’audit tiers, ainsi qu’une bibliothèque de livres blancs, de FAQ et d’autres informations sur les sujets Microsoft 365, telles que le chiffrement des données, la résilience des données, la gestion des incidents de sécurité, etc. Les clients peuvent utiliser ces informations pour effectuer leurs propres évaluations de risques réglementaires. Les responsables de la conformité peuvent affecter le rôle « utilisateur d’assurance de service » pour permettre aux utilisateurs d’accéder à l’assurance de service. L’administrateur client peut également fournir aux utilisateurs externes, tels que des auditeurs indépendants, un accès aux informations du tableau de bord service assurance via le [portail d’approbation de service Cloud Microsoft](https://aka.ms/STP) (STP).

## <a name="onedrive-for-business-admin-center"></a>Centre d’administration de OneDrive entreprise

Le centre d’administration Microsoft OneDrive vous permet de gérer rapidement et facilement les paramètres OneDrive entreprise de votre organisation à partir d’un seul et même emplacement. Pour utiliser le centre d’administration OneDrive, l’accès à onedrive.com est requis. Vous devez également être administrateur général de votre organisation ou administrateur personnalisé avec le rôle d’administrateur SharePoint. Accédez au centre d’administration OneDrive entreprise à l’adresse [https://admin.onedrive.com](https://admin.onedrive.com/) .

Les fonctionnalités clés incluent une zone de conformité qui fournit aux administrateurs des liens vers le centre de gestion approprié pour les scénarios clés tels que la recherche dans le journal d’audit, l’utilisation de DLP, la rétention, la découverte électronique et l’alerte.

## <a name="related-links"></a>Liens connexes

- [eDiscovery et fonctionnalités de recherche](office-365-ediscovery-and-search-features.md)
- [Fonctionnalités de création de rapports Microsoft 365](office-365-reporting-features.md)
- [API d’activité de gestion Microsoft 365](office-365-management-activity-api.md)
- [Migrations de boîtes aux lettres Microsoft 365](office-365-mailbox-migrations.md)
- [Journalisation interne pour l’ingénierie Microsoft 365](office-365-internal-logging.md)