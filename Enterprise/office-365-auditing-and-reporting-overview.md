---
title: Audit et création de rapports dans les services Cloud de Microsoft
ms.author: robmazz
author: robmazz
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
description: Vue d’ensemble des fonctionnalités d’audit et de création de rapports dans Office 365, Microsoft 365 et service assurance.
ms.openlocfilehash: 991eb807ee297ea9dc912be53d99c80247220c1b
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076228"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Audit et création de rapports dans les services Cloud de Microsoft

## <a name="introduction"></a>Introduction

Les services de Cloud Computing Microsoft incluent plusieurs fonctionnalités d’audit et de création de rapports que vous pouvez utiliser pour effectuer le suivi de l’activité des utilisateurs et de l’administration au sein de leur client, par exemple : modifications apportées aux paramètres de configuration du client Exchange Online et SharePoint Online, et modifications apportées par les utilisateurs à des documents et à d’autres éléments. Vous pouvez utiliser des informations d’audit et des rapports disponibles dans les services de Cloud Computing Microsoft pour gérer plus efficacement l’expérience utilisateur, atténuer les risques et respecter les obligations de conformité.

## <a name="security--compliance-centers"></a>Centres de sécurité & conformité

Le centre de sécurité [& Office 365 Security](https://protection.office.com)Center, le [Centre de sécurité Microsoft 365](https://security.microsoft.com)et le [Centre de conformité Microsoft 365](https://compliance.microsoft.com) sont des portails d’un seul point pour protéger les données de votre organisation, et ils incluent de nombreuses fonctionnalités d’audit et de création de rapports. Ces centres vous aident à répondre à vos besoins en matière de protection des données ou de conformité et d’auditer l’activité des utilisateurs et des administrateurs. Vous pouvez accéder à ces centres à l’aide de votre compte d’administrateur d’abonnement.

Ces centres incluent des volets de navigation permettant d’accéder à plusieurs fonctionnalités :

- **Alertes :** Vous permet de gérer les alertes, d’afficher les alertes liées à la sécurité et de gérer les alertes avancées à l’aide de la [sécurité des applications Cloud d’Office 365](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).
- **Autorisations :** Vous permet d' [affecter des autorisations](https://support.office.com/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76) telles que l’administrateur de la conformité, le gestionnaire eDiscovery et d’autres personnes au sein de votre organisation afin qu’ils puissent effectuer des tâches dans ces centres. Vous attribuez des autorisations pour la plupart des fonctionnalités de chaque centre, mais les autres autorisations doivent être configurées à l’aide du centre d’administration Exchange et du centre d’administration SharePoint.
- **Gestion des menaces :** Vous permet de créer et d’appliquer des stratégies de gestion des appareils à l’aide de la [gestion des appareils mobiles Office 365](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a), pour configurer des stratégies de protection contre la [perte de données](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e) (DLP) pour votre organisation, pour configurer le filtrage du courrier électronique, les logiciels anti-programme malveillant, le DomainKeys Identified identifié (DKIM), les pièces jointes fiables, les liens fiables et les applications OAuth.
- **Gouvernance des données :** Vous permet d' [importer des données de messagerie ou SharePoint à partir d’autres systèmes dans Office 365](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), de [configurer des boîtes aux lettres d’archivage](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)et de définir des [stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) pour le courrier électronique et d’autres contenus au sein de votre organisation.
- **Recherche & :** Fournit des outils de [recherche de contenu](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), de [Journal d’audit](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), de mise en quarantaine et de gestion des dossiers [eDiscovery](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) pour explorer rapidement les activités dans les boîtes aux lettres, les groupes et les dossiers publics Exchange Online, SharePoint Online et OneDrive entreprise.
- **Rapports :** Vous permet d’accéder rapidement aux [rapports](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) pour SharePoint Online, OneDrive entreprise, Exchange Online et Azure ad.
- **Assurance de service :** Fournit des informations sur la façon dont Microsoft gère la sécurité, la confidentialité et la conformité avec les normes globales pour Office 365, Azure, Microsoft Dynamics CRM Online, Microsoft Intune et d’autres services Cloud. Inclut également l’accès à des rapports d’audit, tels que ISO, SOC et d’autres rapports, ainsi que des contrôles audités, qui fournissent des détails sur les différents contrôles qui ont été testés et vérifiés par des auditeurs tiers d’Office 365.

## <a name="service-assurance"></a>Service assurance

De nombreuses organisations dans les industries réglementées sont soumises à des exigences de conformité étendues. Pour effectuer leurs évaluations des risques propres, les clients ont souvent besoin d’informations détaillées sur la façon dont Office 365 maintient la sécurité et la confidentialité de leurs données. Microsoft s’engage à respecter la sécurité et la confidentialité des données des clients dans ses services Cloud et à bénéficier d’une relation de confiance client en fournissant une vue transparente de ses opérations et un accès facile aux rapports et aux évaluations de conformité indépendantes.

Service assurance fournit la transparence des opérations et des informations sur la façon dont Microsoft conserve la sécurité, la confidentialité et la conformité des données client dans Office 365. Elle inclut des rapports d’audit tiers, ainsi qu’une bibliothèque de livres blancs, de FAQ et d’autres documents sur les sujets Office 365, tels que le chiffrement des données, la résilience des données, la gestion des incidents de sécurité, etc. Les clients peuvent utiliser ces informations pour effectuer leurs propres évaluations de risques réglementaires. Les responsables de la conformité peuvent affecter le rôle « utilisateur d’assurance de service » pour permettre aux utilisateurs d’accéder à l’assurance de service. L’administrateur client peut également fournir aux utilisateurs externes, tels que des auditeurs indépendants, un accès aux informations du tableau de bord service assurance via le [portail d’approbation de service Cloud Microsoft](https://aka.ms/STP) (STP). Pour plus d’informations sur la façon d’accéder au protocole STP, consultez [la prise en main du portail de confiance des services pour Office 365 pour les abonnements pour les entreprises, Azure et Dynamics CRM Online](https://aka.ms/STPHelp).

## <a name="onedrive-for-business-admin-center"></a>Centre d’administration de OneDrive entreprise

Le centre d’administration Microsoft OneDrive vous permet de gérer rapidement et facilement les paramètres OneDrive entreprise de votre organisation à partir d’un seul et même emplacement. Pour utiliser le centre d’administration OneDrive, l’accès à onedrive.com est requis. Vous devez également être administrateur général de votre organisation ou administrateur personnalisé avec le rôle d’administrateur SharePoint. Accédez au centre d’administration OneDrive entreprise à [https://admin.onedrive.com](https://admin.onedrive.com/)l’adresse.

Les fonctionnalités clés incluent une zone de conformité qui fournit aux administrateurs des liens vers le centre de gestion approprié pour les scénarios clés tels que la recherche dans le journal d’audit, l’utilisation de DLP, la rétention, la découverte électronique et l’alerte.

## <a name="related-links"></a>Liens connexes

- [eDiscovery et fonctionnalités de recherche](office-365-ediscovery-and-search-features.md)
- [Fonctionnalités de création de rapports Office 365](office-365-reporting-features.md)
- [API Activité de gestion Office 365](office-365-management-activity-api.md)
- [Migrations de boîtes aux lettres Office 365](office-365-mailbox-migrations.md)
- [Journalisation interne pour Office 365 Engineering](office-365-internal-logging.md)