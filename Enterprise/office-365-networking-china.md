---
title: Optimisation des performances client globales d’Office 365 pour les utilisateurs de la Chine
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/13/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
f1.keywords:
- NOCSH
description: Cet article fournit des instructions pour optimiser les performances réseau pour les utilisateurs de la Chine des clients Office 365 généraux.
ms.openlocfilehash: 33e475dfbf4accf306a099542cf8cf2f22ff23a5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106312"
---
# <a name="office-365-global-tenant-performance-optimization-for-china-users"></a>Optimisation des performances client globales d’Office 365 pour les utilisateurs de la Chine

>[!IMPORTANT]
>Ces instructions sont spécifiques aux scénarios d’utilisation dans lesquels **les utilisateurs d’office 365 en Chine** se connectent à un **client global Office 365**. Ces instructions ne s’appliquent **pas** aux clients dans Office 365 géré par 21ViaNet.

Pour les entreprises avec des clients Office 365 généraux et une présence d’entreprise en Chine, les performances du client Office 365 pour les utilisateurs en Chine peuvent être compliquées par des facteurs spécifiques à l’architecture Internet de Chine Telco.

Les fournisseurs de services Internet chinois ont des connexions offshore réglementées à l’Internet public global qui passent par des périphériques de périmètre qui sont sujets à des niveaux élevés de congestion du réseau croisé. Cette congestion crée une perte de paquets et une latence pour tout le trafic Internet entrant et sortant de la Chine.

![Trafic Office 365-non optimisé](media/O365-networking/China-O365-unoptimized.png)

La perte de paquets et la latence sont préjudiciables aux performances des services réseau, en particulier les services qui nécessitent des échanges de données volumineux (par exemple, les transferts de fichiers volumineux) ou des performances quasiment en temps réel (applications audio et vidéo).

L’objectif de cette rubrique est de fournir les meilleures pratiques pour limiter l’impact de la congestion réseau transfrontalière sur les services Office 365. Cette rubrique n’aborde pas d’autres problèmes de performances courants, tels que des problèmes de latence de paquet élevée en raison d’un routage complexe au sein des opérateurs de Chine.

## <a name="corporate-network-best-practices"></a>Meilleures pratiques en matière de réseau d’entreprise

De nombreuses entreprises avec des clients et des utilisateurs Office 365 en Chine ont implémenté des réseaux privés qui acheminent le trafic réseau d’entreprise entre des emplacements de bureau chinois et des emplacements hors site dans le monde entier. Ces entreprises peuvent tirer parti de cette infrastructure réseau pour éviter la congestion réseau transfrontalière et optimiser leurs performances de service Office 365 en Chine.

>[!IMPORTANT]
>Comme pour toutes les implémentations de réseau étendu privé, vous devez toujours consulter les exigences réglementaires pour votre pays et/ou votre région afin de vous assurer que la configuration de votre réseau est conforme.

Dans un premier temps, il est essentiel de suivre notre guide réseau de référence lors de la [planification réseau et de l’optimisation des performances pour Office 365](https://aka.ms/tune). L’objectif principal doit être d’éviter d’avoir accès aux services Office 365 globaux à partir d’Internet en Chine, si possible.

- Tirez parti de votre réseau privé existant pour transporter le trafic réseau Office 365 entre les réseaux Office chinois et les sites offshore qui sont sortants sur Internet en dehors de la Chine. Quasiment tout emplacement en dehors de la Chine offre un avantage clair. Les administrateurs réseau peuvent optimiser l’optimisation par egressing dans les zones avec une interconnexion à faible latence avec le [réseau global Microsoft](https://docs.microsoft.com/azure/networking/microsoft-global-network). Hong Kong, Japon et Corée du Sud sont des exemples.
- Configurez les appareils utilisateur pour qu’ils accèdent au réseau d’entreprise via une connexion VPN afin de permettre au trafic Office 365 de transiter le lien de mise en mer interne du réseau d’entreprise. Assurez-vous que les clients VPN ne sont pas configurés pour utiliser le tunneling fractionné ou que les appareils utilisateur sont configurés pour ignorer le tunneling fractionné pour le trafic Office 365.
- Configurez votre réseau pour acheminer tout le trafic Office 365 sur votre lien privé en mer. Si vous devez réduire le volume du trafic sur votre lien privé, vous pouvez choisir d’acheminer uniquement les points de terminaison de la catégorie **optimize** et autoriser les demandes d' **autoriser** et de points de terminaison **par défaut** à transiter sur Internet. Cela permet d’améliorer les performances et de réduire la consommation de bande passante en limitant le trafic optimisé aux services critiques les plus sensibles à la latence élevée et à la perte de paquets.
- Dans la mesure du possible, utilisez UDP au lieu de TCP pour le trafic de diffusion multimédia en continu, par exemple pour Teams. UDP offre de meilleures performances de flux multimédia en direct que TCP.

Pour plus d’informations sur la façon de router le trafic Office 365 de manière sélective, consultez la rubrique [Managing office 365 Endpoints](managing-office-365-endpoints.md). Pour obtenir la liste de toutes les URL et adresses IP du site international Office 365, voir [URL et plages d’adresses IP office 365](urls-and-ip-address-ranges.md).

![Optimisation du trafic Office 365](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Meilleures pratiques pour les utilisateurs

Les utilisateurs de la Chine qui se connectent à des clients locaux Office 365 à partir d’emplacements distants, tels que des maisons, des cafés-restaurants, des hôtels et des succursales sans connexion aux réseaux d’entreprise, peuvent rencontrer des performances réseau médiocres, car le trafic entre leurs appareils et Office 365 doivent transiter des circuits réseau transfrontaliers en Chine encombrés.

Si les réseaux privés transfrontaliers et/ou l’accès VPN au réseau d’entreprise ne sont pas facultatifs, les problèmes de performances par utilisateur peuvent toujours être atténués en formant vos utilisateurs basés sur la Chine pour suivre ces meilleures pratiques.

- Utilisez des clients Office enrichis qui prennent en charge la mise en cache (par exemple, Outlook, teams, OneDrive, etc.) et évitez les clients basés sur le Web. Les fonctionnalités de mise en cache du client Office et d’accès hors connexion peuvent considérablement réduire l’impact de la congestion et de la latence du réseau.
- Si votre client Office 365 a été configuré avec la fonctionnalité d' _audioconférence_ , les utilisateurs de teams peuvent participer à des réunions via le réseau téléphonique commuté (RTC). Pour plus d’informations, consultez la rubrique [audioconférence dans Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365).
- Si les utilisateurs rencontrent des problèmes de performances réseau, ils doivent signaler à leur service informatique la résolution des problèmes et passer à la prise en charge de Microsoft si des problèmes liés aux services Office 365 sont suspectés. Tous les problèmes ne sont pas causés par les performances réseau transfrontalières.

Microsoft travaille en permanence pour améliorer l’expérience utilisateur Office 365 et les performances des clients sur la plus large gamme possible d’architectures réseau et de caractéristiques. Visitez la [communauté technique Office 365](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) pour commencer ou rejoindre une conversation, trouver des ressources et soumettre des demandes de fonctionnalités et des suggestions.

## <a name="related-topics"></a>Voir aussi

[Planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune)

[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Réseau global Microsoft](https://docs.microsoft.com/azure/networking/microsoft-global-network)
