---
title: Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)
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
description: Vue d’ensemble des recommandations en matière de performances réseau dans le centre d’administration 365 de Microsoft (version préliminaire)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106305"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)

La page des performances réseau dans le centre d’administration 365 de Microsoft affiche des informations sur le réseau et un score réseau pour les clients d’entreprise. Les informations sur le réseau sont des modifications de conception d’architecture réseau recommandées pour améliorer l’expérience utilisateur liée à la connectivité réseau à Office 365 et le score réseau, qui a un impact sur l’expérience utilisateur permettant de comparer différentes connexions réseau d’emplacement utilisateur. Les entreprises qui utilisent Office 365 avec plusieurs emplacements de bureau et des architectures de périmètre réseau non triviales peuvent bénéficier de cette possibilité lors de leur intégration initiale à Office 365 ou pour corriger les problèmes de performances réseau découverts avec l’utilisation explosion. Cette fonction n’est généralement pas nécessaire pour les petites entreprises qui utilisent Office 365, ni dans les entreprises qui disposent déjà d’une connectivité réseau simple et directe. Les entreprises disposant de plus de 500 utilisateurs et de plusieurs emplacements de bureau sont censées tirer le meilleur parti.

>[!IMPORTANT]
>Les recommandations en matière de performances réseau, les informations et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="enterprise-network-connectivity-challenges"></a>Défis de connectivité du réseau d’entreprise

![Réseau client vers Cloud](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

De nombreuses entreprises ont des configurations de périmètre réseau qui se sont produites au fil du temps et qui sont principalement conçues pour prendre en charge l’accès aux sites Web des employés où la plupart des sites Web ne sont pas connus à l’avance et ne sont pas approuvés. L’objectif de ce site est d’éviter les attaques de programmes malveillants et de pêche à partir de ces sites Web inconnus. Cette stratégie de configuration réseau, tout en étant utile pour des raisons de sécurité, peut entraîner une dégradation des performances utilisateur d’Office 365 et de l’expérience utilisateur. Les entreprises peuvent améliorer l’expérience utilisateur, tout en continuant à sécuriser leur environnement en suivant les [principes de connectivité d’Office 365](https://aka.ms/pnc) et bientôt en utilisant la nouvelle fonctionnalité de performances réseau du centre d’administration Microsoft 365. Cette fonctionnalité facilite la conception de l’architecture réseau qui s’aligne sur les principes de connectivité d’Office 365 et doit conduire à une optimisation des performances réseau pour la connectivité à Office 365.

## <a name="how-we-can-solve-these-challenges"></a>Comment nous pouvons résoudre ces problèmes

Microsoft est parfois invité à enquêter sur les problèmes de performances réseau avec Office 365 pour les grandes entreprises et celles-ci ont fréquemment une cause principale liée à l’infrastructure de sortie du réseau des clients. Lors de la détection d’une cause racine commune d’un problème de périmètre réseau client, nous cherchons à identifier les mesures de test simples qui l’identifient. Un test avec un seuil de mesure qui identifie un problème spécifique est utile, car nous pouvons tester la même mesure dans n’importe quel emplacement, indiquer si cette cause première existe et la partager en tant que Network Insight avec l’administrateur. Certains aspects du réseau indiquent simplement un problème qui nécessite une nouvelle enquête. Un Network Insight où nous avons suffisamment de tests pour afficher une action corrective spécifique pour corriger la cause principale est mentionné comme une action recommandée. Ces informations sur le réseau, basées sur des mesures effectuées au-delà d’un seuil prédéterminé, sont beaucoup plus précieuses que les conseils de meilleures pratiques générales étant donné que vous n’avez pas à vous demander si certaines meilleures pratiques s’appliquent et entraînent une amélioration importante de l’expérience utilisateur ou non. .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Vue d’ensemble des performances réseau dans le centre d’administration Microsoft 365

Microsoft a des mesures de réseau existantes d’inclure plusieurs clients de bureau et Web Office qui prennent en charge le fonctionnement d’Office 365. Ces mesures sont désormais utilisées pour fournir des informations sur la conception de l’architecture réseau et un score de performances réseau affiché dans la page des performances réseau du centre d’administration Microsoft 365.

Les informations d’emplacement approximatives associées aux mesures du réseau permettent d’identifier la ville où se trouvent les appareils clients. Il est utilisé pour afficher les emplacements de bureau des clients et les mesures de réseau sont regroupées afin de fournir des informations sur le réseau pour cet emplacement Office. Le score réseau à chaque emplacement est affiché avec la couleur et le nombre d’utilisateurs par rapport à chaque emplacement est représenté par la taille du cercle. La page de vue d’ensemble indique également le score réseau pour le client sous la forme d’une moyenne pondérée sur tous les emplacements de bureau.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Informations spécifiques sur les performances et les informations du réseau d’emplacement de bureau

La sélection d’un emplacement de bureau ouvre une page de résumé spécifique à l’emplacement. Nous expliquons les détails de la sortie réseau qui a été identifiée à partir de mesures pour cet emplacement de bureau.

La page de résumé des emplacements Office indique également l’emplacement du score réseau, l’historique des scores réseau, une comparaison entre cet emplacement et les autres clients de la même ville, ainsi qu’une liste d’informations et de recommandations spécifiques que le client peut entreprendre pour améliorer la connectivité réseau. Les comparaisons entre les clients de la même ville sont basées sur l’attente que tous les clients ont un accès égal aux fournisseurs de services réseau, à l’infrastructure de télécommunications et aux points de présence réseau Microsoft voisins.

L’onglet Détails de la page emplacement du Bureau affiche les résultats de mesure spécifiques qui ont été utilisés pour trouver des informations, des recommandations et la note réseau. Cela permet aux ingénieurs réseau de valider les recommandations et facteurs dans les contraintes ou les spécificités de leur environnement.
Pour les clients qui souhaitent améliorer la précision des emplacements et des recommandations de bureau fournis, nous autorisons la saisie d’informations plus spécifiques. Pour ce faire, vous devez modifier les informations d’emplacement découvertes et réduire les approximations inhérentes aux informations d’emplacement disponibles pour les mesures réseau.

## <a name="faq"></a>Forum aux questions

### <a name="what-is-office-365-service-front-door"></a>Qu’est-ce que le service frontal Office 365 ?

Le volet Office 365 service est un point d’entrée sur le réseau mondial de Microsoft où les clients et les services Office mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Office 365, il est recommandé que votre connexion réseau soit interrompue dans le volet frontal Office 365 le plus proche de votre ville ou de votre métro.
Remarque : le volet frontal du service Office 365 n’a pas de relation directe avec le produit « Azure Front Door service » disponible sur le marché Azure.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>Qu’est-ce qu’une trappe frontale d’Office 365 service optimale ?

Une porte de service frontale Office 365 optimale est celle qui est la plus proche de la sortie de votre réseau, généralement dans votre ville ou votre région de métro. Utilisez l’outil de performances réseau Office 365 pour déterminer l’emplacement de votre service 365 d’utilisation et de votre porte de service frontale. Si l’outil détermine que votre porte avant de l’utilisation est optimale, vous vous connectez de manière optimale au réseau global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Elle est également identifiée comme l’emplacement où vous avez un périphérique de traduction d’adresses réseau (NAT) et généralement l’endroit où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement Internet sortant, cela peut indiquer une sorte de trajet WAN important.

## <a name="related-topics"></a>Voir aussi

[Informations sur les performances du réseau Office 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Office 365 (préversion)](office-365-network-mac-perf-score.md)

[Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)](office-365-network-mac-perf-onboarding-tool.md)
