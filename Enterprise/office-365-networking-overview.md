---
title: Vue d’ensemble de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Explique pourquoi l’optimisation du réseau est importante pour les services SaaS, l’objectif de la mise en réseau Microsoft 365 et la façon dont SaaS requiert une mise en réseau différente des autres charges de travail.
ms.openlocfilehash: 6dc1ea91607dc43d4e24546f938f4f7ee3af8b3a
ms.sourcegitcommit: 92bbb6d005d005952a9e2055661fcdccfdd0567b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "46533499"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Vue d’ensemble de la connectivité réseau Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est un Cloud SaaS (Software-as-a-service) distribué qui fournit des scénarios de productivité et de collaboration via un ensemble diversifié de micro-services et d’applications. Les composants clients de Microsoft 365 tels qu’Outlook, Word et PowerPoint s’exécutent sur les ordinateurs des utilisateurs et se connectent à d’autres composants de Microsoft 365 qui s’exécutent dans des centres de contenu Microsoft. Le facteur le plus significatif qui détermine la qualité de l’expérience de l’utilisateur final de Microsoft 365 est la fiabilité du réseau et la faible latence entre les clients Microsoft 365 et les portes frontales du service Microsoft 365.

Dans cet article, vous découvrirez les objectifs de la mise en réseau Microsoft 365 et les raisons pour lesquelles la mise en réseau Microsoft 365 nécessite une approche différente de celle du trafic Internet générique.

## <a name="microsoft-365-networking-goals"></a>Objectifs de mise en réseau Microsoft 365

Le but ultime de la mise en réseau Microsoft 365 est d’optimiser l’expérience de l’utilisateur final en autorisant l’accès le moins restrictif entre les clients et les points de terminaison Microsoft 365 les plus proches. La qualité de l’expérience de l’utilisateur final est directement liée aux performances et à la réactivité de l’application utilisée par l’utilisateur. Par exemple, Microsoft teams repose sur une faible latence, de sorte que les appels téléphoniques, les conférences et les collaborations à l’écran partagés soient exempts de problèmes, et qu’Outlook s’appuie sur une connectivité réseau de grande qualité pour les fonctionnalités de recherche instantanée qui exploitent les fonctionnalités d’indexation et de préversions côté serveur.

L’objectif principal de la conception du réseau est de réduire la latence en réduisant le temps d’aller-retour (RTT) entre les ordinateurs clients et le réseau global Microsoft, le réseau principal du réseau public de Microsoft qui interconnecte tous les centres de contenu de Microsoft avec une faible latence, les points d’entrée des applications Cloud haute disponibilité répartis dans le monde entier. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

L’optimisation des performances réseau Microsoft 365 n’a pas besoin d’être compliquée. Vous pouvez obtenir les meilleures performances possibles en suivant quelques principes clés :

- Identifier le trafic réseau Microsoft 365
- Autoriser la sortie de succursale locale du trafic réseau Microsoft 365 vers Internet à partir de tous les emplacements où les utilisateurs se connectent à Microsoft 365
- Autoriser le trafic Microsoft 365 à contourner les proxys et les appareils d’inspection de paquets

Pour plus d’informations sur les principes de connectivité réseau de Microsoft 365, consultez les [principes de connectivité réseau de microsoft 365](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Architectures réseau traditionnelles et SaaS

Les principes d’architecture réseau traditionnels pour les charges de travail client/serveur sont conçus en partant du principe que le trafic entre les clients et les points de terminaison ne s’étend pas en dehors du périmètre réseau d’entreprise. En outre, dans de nombreux réseaux d’entreprise, toutes les connexions Internet sortantes traversent le réseau d’entreprise, ainsi que la sortie à partir d’un emplacement central.

Dans les architectures réseau traditionnelles, une latence élevée pour le trafic Internet générique est un compromis nécessaire pour maintenir la sécurité du périmètre réseau, et l’optimisation des performances pour le trafic Internet implique généralement une mise à niveau ou une montée en charge de l’équipement sur les points de sortie réseau. Toutefois, cette approche ne répond pas aux exigences de performances réseau optimales des services SaaS tels que Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identification du trafic réseau Microsoft 365

Nous facilitent l’identification du trafic réseau Microsoft 365 et simplifient la gestion de l’identification réseau.

- Nouvelles catégories de points de terminaison réseau permettant de différencier le trafic réseau hautement critique du trafic réseau qui n’est pas influencé par les latences Internet. Il existe simplement quelques URL et prise en charge des adresses IP dans la catégorie « optimiser » la plus critique.
- Services Web pour l’utilisation de scripts ou la configuration de l’appareil direct et la gestion des modifications de l’identification réseau Microsoft 365. Les modifications sont disponibles à partir du service Web ou au format RSS, ou sur le courrier électronique à l’aide d’un modèle de flux Microsoft.
- [Programme de partenariat réseau Office 365](https://aka.ms/Office365NPP) avec des partenaires Microsoft qui fournissent des appareils ou des services qui respectent les principes de connectivité réseau de Microsoft 365 et ont une configuration simple.

## <a name="securing-microsoft-365-connections"></a>Sécurisation des connexions Microsoft 365

L’objectif de la sécurité réseau traditionnelle est de renforcer le périmètre du réseau de l’entreprise contre les intrusions et les logiciels malveillants. La plupart des réseaux d’entreprise appliquent la sécurité réseau pour le trafic Internet à l’aide de technologies telles que les serveurs proxy, les pare-feu, les interruptions de l’activité SSL et les systèmes de protection contre la perte de données. Ces technologies fournissent une atténuation importante des risques pour les demandes Internet génériques, mais peuvent réduire considérablement les performances, l’évolutivité et la qualité de l’expérience de l’utilisateur final lorsqu’elles sont appliquées aux points de terminaison Microsoft 365.

Microsoft 365 permet de répondre aux besoins de votre organisation en matière de conformité de la sécurité et de l’utilisation des données grâce à des fonctionnalités de sécurité et de gouvernance intégrées conçues spécifiquement pour les charges de travail et les fonctionnalités Microsoft 365. Pour plus d’informations sur la sécurité et la conformité de Microsoft 365, voir la feuille de [route de sécurité d’Office 365](https://docs.microsoft.com/office365/securitycompliance/security-roadmap). Pour plus d’informations sur les recommandations de Microsoft et la position de support sur les solutions réseau avancées qui effectuent un traitement avancé sur le trafic Microsoft 365, consultez la rubrique [utilisation de périphériques ou de solutions réseau tiers sur le trafic Office 365](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Pourquoi la mise en réseau Microsoft 365 est-elle différente ?

Microsoft 365 est conçu pour optimiser les performances à l’aide de la sécurité du point de terminaison et des connexions réseau chiffrées, ce qui réduit le besoin de mise en œuvre de la sécurité du périmètre. Les centres de contenu Microsoft 365 sont disponibles dans le monde entier et le service est conçu pour utiliser différentes méthodes de connexion des clients aux meilleurs points de terminaison de service disponibles. Étant donné que les données utilisateur et le traitement sont répartis entre de nombreux centres de données Microsoft, il n’existe pas de point de terminaison réseau auquel les ordinateurs clients peuvent se connecter. En fait, les données et les services de votre client Microsoft 365 sont optimisés dynamiquement par le réseau mondial Microsoft pour s’adapter aux emplacements géographiques à partir desquels les utilisateurs finaux peuvent y accéder.

Certains problèmes de performances courants sont créés lorsque le trafic Microsoft 365 est soumis à une inspection de paquets et à une sortie centralisée :

- Une latence élevée peut entraîner de très faibles performances des flux vidéo et audio, ainsi qu’une réponse lente de l’extraction des données, des recherches, de la collaboration en temps réel, des informations de disponibilité du calendrier, du contenu de produit et d’autres services.
- Les connexions Egressing à partir d’un emplacement central dépassent les capacités de routage dynamique du réseau global Microsoft 365, en ajoutant de la latence et du temps d’aller-retour
- Le déchiffrement du trafic réseau SSL sécurisé de Microsoft 365 et son rechiffrement peuvent entraîner des erreurs de protocole et des risques de sécurité

Le fait de raccourcir le chemin d’accès réseau aux points d’entrée Microsoft 365 en autorisant le trafic client à sortir aussi près que possible de son emplacement géographique peut améliorer les performances de connectivité et l’expérience de l’utilisateur final dans Microsoft 365. Elle peut également contribuer à réduire l’impact des modifications futures apportées à l’architecture réseau sur les performances et la fiabilité de Microsoft 365. Le modèle de connectivité optimale consiste à toujours fournir une sortie réseau à l’emplacement de l’utilisateur, qu’il s’agisse d’un réseau d’entreprise ou de sites distants, tels que la maison, les hôtels, les cafés-restaurants et les aéroports. Le trafic Internet générique et le trafic réseau d’entreprise basé sur le WAN seraient acheminés séparément et ne doivent pas utiliser le modèle de sortie directe locale. Ce modèle local de sortie directe est représenté dans le diagramme ci-dessous.

![Architecture du réseau de sortie local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

L’architecture de sortie locale présente les avantages suivants pour le trafic réseau Microsoft 365 sur le modèle traditionnel :
  
- Fournit des performances Microsoft 365 optimales en optimisant la longueur de l’itinéraire. Les connexions des utilisateurs finaux sont routées de manière dynamique vers le point d’entrée Microsoft 365 le plus proche par l’infrastructure de l' _avant de service distribué_ de Microsoft Global Network, et le trafic est ensuite routé en interne vers les données et les points de terminaison de service via la fibre haute disponibilité de latence ultra faible de Microsoft.
- Réduit la charge sur l’infrastructure réseau d’entreprise en autorisant la sortie locale pour le trafic Microsoft 365, en contournant les proxys et les appareils d’inspection du trafic.
- Sécurise les connexions aux deux extrémités en tirant parti des fonctionnalités de sécurité du point de terminaison client et de sécurité du Cloud, ce qui évite l’application de technologies de sécurité réseau redondantes.

> [!NOTE]
> L’infrastructure de _façade de service distribué_ est le périmètre réseau hautement disponible et évolutif du réseau Microsoft Global, avec des emplacements géographiquement dispersés. Il met fin aux connexions des utilisateurs finaux et les achemine efficacement dans le réseau global de Microsoft. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Pour plus d’informations sur la compréhension et l’application de principes de connectivité réseau Microsoft 365, consultez les [principes de connectivité réseau de microsoft 365](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Conclusion

L’optimisation des performances du réseau Microsoft 365 s’avère très utile pour supprimer les obstacles inutiles. En traitant les connexions Microsoft 365 comme du trafic approuvé, vous pouvez empêcher la latence d’être introduite par l’inspection des paquets et la concurrence pour la bande passante par proxy. Autoriser les connexions locales entre les ordinateurs clients et les points de terminaison Office 365 permet d’acheminer le trafic de manière dynamique via le réseau global de Microsoft.

## <a name="related-topics"></a>Rubriques connexes

[Principes de connectivité réseau Microsoft 365](office-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](office-365-ip-web-service.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Test de connectivité Microsoft 365](https://aka.ms/netonboard)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
