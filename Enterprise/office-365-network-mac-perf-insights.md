---
title: Informations sur les performances du réseau Office 365 (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Informations sur les performances du réseau Office 365 (aperçu)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106311"
---
# <a name="office-365-network-performance-insights-preview"></a>Informations sur les performances du réseau Office 365 (aperçu)

Les pages des performances du réseau du centre d’administration Microsoft 365 montrent Office 365 Network Insights, qui peut vous aider à concevoir des périmètres réseau pour vos emplacements de bureau. Cinq analyses de réseau spécifiques peuvent être affichées pour chaque emplacement de bureau.

>[!IMPORTANT]
>Les recommandations en matière de performances réseau, les informations et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="backhauled-network-egress"></a>Sortie réseau retractée

La distance entre l’emplacement de l’utilisateur et la sortie réseau est supérieure à 500 milles (800 kilomètres) et cela devrait avoir un impact sur les performances. Une sortie locale plus proche de l’utilisateur est recommandée.

Cela indique que la distance entre l’emplacement du bureau et la sortie du réseau est supérieure à 500 kilomètres. L’emplacement du Bureau est identifié par un emplacement de l’ordinateur client masqué et l’emplacement de sortie du réseau est identifié à l’aide de l’adresse IP inverse pour les bases de données d’emplacement. L’emplacement du Bureau peut être inexact si les services d’emplacement Windows sont désactivés sur les ordinateurs. L’emplacement de sortie réseau peut être inexact si les informations de la base de données d’adresses IP inversées sont inexactes.

Les détails de cette analyse incluent l’emplacement du bureau, l’emplacement de sortie réseau et la distance entre eux.

Pour cette vue, nous recommandons de passer un accès réseau plus près de l’emplacement du bureau afin que la connectivité puisse acheminer le réseau de manière optimale vers le réseau de Microsoft sur Internet et sur les portes frontales du service Office 365. Une sortie étroite du réseau vers les bureaux des utilisateurs permet également d’améliorer les performances à l’avenir à mesure que Microsoft étend à la fois les points de présence réseau et les portes frontales du service Office 365.

Cette vue est abrégée en « sortie » dans certains affichages de résumés.

## <a name="better-performance-detected-for-customers-near-you"></a>Meilleures performances détectées pour les clients proches de vous

Dans la mesure où un nombre important de clients dans votre zone de métro offre de meilleures performances que les utilisateurs de votre organisation à cet emplacement de bureau.

Cela examine les performances totales des clients Office 365 dans la même ville que cet emplacement de bureau.

![Performances réseau relatives](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

Nous calculons le pourcentage de clients Office 365 dans la même ville dans des compartiments de performance plus performants. Si ce nombre est supérieur à 10%, nous affichons Network Insight.

Cette vue est abrégée en « pairs » dans certains affichages de résumés.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Utilisation d’un service frontal Exchange Online non optimal

L’utilisateur ne se connecte pas à une trappe frontal de service Office 365 optimale et cela devrait avoir un impact sur les performances.

Nous répertorions les portes frontales du service Exchange Online qui peuvent être utilisées à partir de la ville de l’emplacement du bureau avec de bonnes performances. Si le test actuel indique l’utilisation d’un service frontal Exchange Online qui ne figurent pas sur cette liste, nous appelons cette recommandation.

L’utilisation d’une trappe frontal non optimale d’un service Exchange Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct. Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

Cette vue est abrégée en « routage » dans certains affichages de résumés.

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>Utilisation de la porte d’appel frontale SharePoint Online non optimale

L’utilisateur ne se connecte pas au volet frontal du service SharePoint Online le plus proche. Cela peut avoir un impact sur les performances.

Nous allons identifier la porte d’écran du service SharePoint Online à laquelle le client de test se connecte. Ensuite, pour la ville de l’emplacement du bureau, nous comparons cette ville avec le service SharePoint Online attendu pour cette ville. S’il ne correspond pas, nous en faisons la recommandation.

Cette vue est abrégée sous la forme « AFD » dans certains affichages de résumés.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint

Vitesse de téléchargement du réseau sous-optimal, qui a un impact sur le temps nécessaire au chargement des documents à partir de OneDrive entreprise.

La vitesse de téléchargement qu’un utilisateur peut obtenir à partir de SharePoint Online et des portes frontales du service OneDrive entreprise est exprimée en mégaoctets par seconde (Mbits/s). Si cette valeur est inférieure à 1 MBps, nous fournissons cette vue.

Pour améliorer la vitesse de téléchargement qu’un utilisateur peut obtenir de la bande passante, il est peut-être nécessaire de l’augmenter. Par ailleurs, il peut y avoir une congestion réseau entre les ordinateurs des utilisateurs à l’emplacement du bureau et le capot frontal du service SharePoint Online. Cette opération est parfois appelée perte de congestion et limite la vitesse de téléchargement disponible aux utilisateurs, même si la bande passante disponible est suffisante.

Cette vue est abrégée en « débit » dans certains affichages de résumés.

## <a name="related-topics"></a>Voir aussi

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Évaluation du réseau Office 365 (préversion)](office-365-network-mac-perf-score.md)

[Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)](office-365-network-mac-perf-onboarding-tool.md)
