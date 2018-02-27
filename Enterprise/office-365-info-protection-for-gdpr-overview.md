---
title: "Protection des informations Office 365 pour le RGPD - Vue d’ensemble"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "Obtenez une vue d’ensemble de la protection des informations Office 365 pour le RGPD. Apprenez à découvrir, classer, protéger et surveiller les données personnelles."
ms.openlocfilehash: b3af91608d545b221694b9e4a18db07b85d7541a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a>Protection des informations Office 365 pour le RGPD - Vue d’ensemble

Cette solution décrit comment protéger les données sensibles stockées dans les services Office 365. Elle inclut des recommandations normatives pour la découverte, la classification, la protection et la surveillance des données personnelles. Cette solution utilise le Règlement général sur la protection des données (RGPD) comme exemple, mais vous pouvez appliquer le même processus pour être conforme aux nombreux autres règlements.

Le RGPD réglemente la collecte, le stockage, le traitement et le partage des données personnelles. Les données personnelles sont définies à très grande échelle dans le cadre du RGPD comme les données associées à une personne naturelle identifiée ou identifiable qui est résidente de l’Union européenne (UE).

Article 4 - Définitions

> Les « données personnelles » correspondent aux informations relatives à une personne naturelle identifiée ou identifiable (« la personne concernée ») ; une personne naturelle identifiable est une personne qui peut être identifiée, directement ou indirectement, notamment par référence à un identificateur par exemple, un nom, un numéro d’identification, des données de localisation, un identificateur en ligne, ou un ou plusieurs facteurs spécifiques de l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne naturelle ;

Cette solution a été conçue pour permettre aux organisations de découvrir et protéger les données personnelles dans Office 365 qui peuvent être soumises au RGPD. Elle n’est pas proposée comme attestation de conformité au RGPD. Les organisations doivent garantir elles-mêmes leur conformité au RGPD et sont invitées à consulter leurs équipes juridiques et de conformité ou à s’adresser à des tiers spécialisés dans le domaine de la conformité.

L’outil d’[évaluation RGPD](https://www.gdprbenchmark.com) est un outil rapide d’auto-évaluation en ligne, disponible gratuitement pour aider votre organisation à revoir son niveau de préparation global pour se conformer au RGPD (<http://aka.ms/gdprassessment>).

## <a name="assess-and-manage-your-compliance-risk"></a>Évaluation et gestion des risques de conformité

La première étape vers la conformité au RGPD consiste à évaluer si le RGPD s’applique à votre organisation et, si c’est le cas, dans quelle mesure. Cette analyse permet de comprendre les données traitées par votre organisation et l’endroit où elles résident.

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a>Étape 1 - Utilisez le Gestionnaire de conformité pour afficher les exigences en matière de règlement et suivre votre progression

Le Gestionnaire de conformité fournit des outils pour suivre, implémenter et gérer les contrôles d’audit qui permettent à votre organisation d’être conforme à différentes normes, notamment au RGPD.

![Utilisation du Gestionnaire de conformité pour afficher les exigences et suivre la progression](Media/Overview-image1.png)

Pour plus d’informations, reportez-vous à la rubrique [Utiliser le Gestionnaire de conformité dans le portail de gestion de la confidentialité du Service](https://support.office.com/fr-FR/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942). 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a>Étape 2 - Utilisez la recherche de contenu et les types d’informations sensibles pour rechercher des données personnelles 

Découvrez les données personnelles dans votre environnement qui sont soumises au RGPD. Utilisez la recherche de contenu avec des types d’informations sensibles pour :

-   Rechercher et créer des rapports sur l’emplacement des données personnelles.

-   Optimiser les types de données sensibles et d’autres requêtes pour rechercher toutes les données personnelles dans votre environnement.

![Utilisation de la recherche de contenu et des types d’informations sensibles pour rechercher des données personnelles](Media/Overview-image2.png)

Les types d’informations sensibles définissent la façon dont le processus automatisé reconnaît des types d’informations spécifiques tels que les numéros de sécurité sociale et les numéros de carte de crédit. Cet article inclut un ensemble de données que vous pouvez utiliser comme point de départ. De nombreux autres types d’informations sensibles seront prochainement disponibles pour les données personnelles dans les pays de l’Union européenne.

Pour plus d’informations, reportez-vous à la rubrique relative à la [recherche et à la localisation des données personnelles](search-for-and-find-personal-data.md). 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a>Classification, protection et surveillance des données personnelles dans Office 365 et d’autres applications SaaS

Certaines fonctionnalités utilisées pour la protection des informations dans Office 365 peuvent également servir à protéger les données sensibles dans d’autres applications SaaS.

![Classification, protection et surveillance des données personnelles](Media/Overview-image3.png)

Cette illustration est décrite dans le reste cette section (étapes 3 à 5).

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a>Étape 3 - Déterminez si vous voulez utiliser des étiquettes en plus des types d’informations sensibles

Les types d’informations sensibles constituent une forme de classification. Reportez-vous à la rubrique relative à la [création d’un schéma de classification pour les données personnelles](architect-a-classification-schema-for-personal-data.md) pour décider si vous souhaitez implémenter des étiquettes également. Pour appliquer des étiquettes, reportez-vous à la rubrique relative à l’[application d’étiquettes à des données personnelles dans Office 365](apply-labels-to-personal-data-in-office-365.md).

Dans l’illustration, des étiquettes et types d’informations sensibles sont utilisés dans Office 365. Bientôt, vous pourrez les utiliser avec Cloud App Security pour rechercher des données sensibles dans d’autres applications SaaS, telles que Box et Salesforce.

### <a name="step-4--protect-personal-data-in-office-365"></a>Étape 4 - Protégez des données personnelles dans Office 365 

La protection des données personnelles commence par la prévention contre la perte de données Office 365. Il existe plusieurs autres fonctionnalités recommandées pour protéger l’accès aux données personnelles, notamment le chiffrement de messages Office 365 pour le courrier électronique.

Ces protections peuvent cibler des ensembles de données spécifiques :

-   Autorisations au niveau de la bibliothèque et du site

-   Stratégies de partage externe au niveau du site

-   Stratégies d’accès d’appareil au niveau du site

La protection pour l’accès à Office 365 et les autres services cloud comprend :

-   Protection des identités et protection d’accès d’appareil dans Enterprise Mobility + Security (EMS)

-   Gestion des accès privilégiés

-   Fonctionnalités de sécurité Windows 10

Pour plus d’informations sur l’application de la protection, reportez-vous à la rubrique relative à l’[application de la protection aux données personnelles dans Office 365](apply-protection-to-personal-data-in-office-365.md).

### <a name="step-5--monitor-for-leaks-of-personal-data"></a>Étape 5 - Surveillez les fuites de données personnelles

Les rapports sur la protection contre la perte de données Office 365 fournissent les informations les plus détaillées concernant la surveillance des données sensibles. Vous pouvez configurer des alertes automatisées et examiner les violations de données à l’aide du journal d’audit Office 365. Cloud App Security étend la possibilité de rechercher et de surveiller les données sensibles à d’autres fournisseurs SaaS. Pour plus d’informations sur ces outils, reportez-vous à la rubrique relative à la [surveillance des atteintes à la sécurité des données personnelles](monitor-for-leaks-of-personal-data.md).
