---
title: Vue d’ensemble de connectivité de réseau Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Explique pourquoi l’optimisation du réseau est importante pour les services SaaS, l’objectif de mise en réseau Office 365, et comment SaaS requiert différents réseau à partir d’autres charges de travail.
ms.openlocfilehash: ebd7410ec5fe421561543f1223e455377e99e625
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "25002353"
---
# <a name="office-365-network-connectivity-overview"></a>Vue d’ensemble de connectivité de réseau Office 365

Office 365 est un nuage Software-as-a-Service (SaaS) distribué qui fournit des scénarios de collaboration et de productivité via un ensemble divers de micro-services et applications. Les composants clients d’Office 365, tels que Outlook, Word et PowerPoint exécutent sur les ordinateurs des utilisateurs et se connecter à d’autres composants d’Office 365 qui s’exécutent dans des centres de données Microsoft. Le facteur déterminant qui détermine la qualité de l’expérience utilisateur Office 365 est la fiabilité du réseau et une latence faible entre les clients Office 365 et capots avant de service Office 365.

Dans cet article, vous allez apprendre aux objectifs d’Office 365 mise en réseau, et pourquoi Office 365 exige une approche différente à l’optimisation de trafic Internet générique.

## <a name="office-365-networking-goals"></a>Objectifs de mise en réseau Office 365

Le but ultime de mise en réseau Office 365 consiste à optimiser l’expérience utilisateur en activant l’accès moins restrictives entre les clients et les points de terminaison Office 365 le plus proche. La qualité de l’expérience utilisateur final est directement liée à la performance et la réactivité de l’application à l’aide de l’utilisateur. Par exemple, Microsoft Teams repose sur la latence faible afin que les appels téléphoniques utilisateur, les conférences et les collaborations écran partagé sont sans problème et Outlook s’appuie sur une connectivité réseau pour les fonctionnalités de recherche instantanée qui tirent parti de l’indexation du côté serveur et AI fonctionnalités.

Le principal objectif de la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (durée aller-retour) à partir des ordinateurs clients au réseau Global Microsoft, public dorsale principale de Microsoft qui relie tous les centres de données de Microsoft avec une faible latence , les points d’entrée application cloud haute disponibilité répartis dans le monde entier. Pour plus d’informations sur le réseau Global Microsoft [comment Microsoft crée son réseau global rapides et fiables](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optimisation des performances du réseau Office 365 ne doit pas être complexe. Vous pouvez obtenir les meilleures performances possibles en suivant les quelques principes clés suivants :

- Identifier le trafic réseau de Office 365
- Autoriser sortie agence de trafic d’Office 365 à internet à partir de chaque emplacement où les utilisateurs se connectent à Office 365
- Autoriser le trafic d’Office 365 contourner les proxys et les périphériques inspection de paquets

Pour plus d’informations sur les principes de connectivité réseau Office 365, voir [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Architectures de réseau traditionnel et SaaS

Principes d’architecture réseau classique pour les charges de travail client/serveur sont conçus autour du principe que le trafic entre les clients et les points de terminaison ne dépasse pas le périmètre du réseau d’entreprise. En outre, dans de nombreux réseaux d’entreprise, toutes les connexions Internet sortantes traversent le réseau d’entreprise et sortie à partir d’un emplacement central.

Architectures de réseau traditionnels, latence plus élevée pour le trafic Internet générique est un compromis nécessaire afin de préserver la sécurité de périmètre de réseau et l’optimisation des performances pour le trafic Internet implique généralement la mise à niveau ou montée en puissance parallèle le équipement à des points de sortie de réseau. Toutefois, cette approche ne traite pas de la configuration requise pour des performances réseau optimales des services SaaS, tels qu’Office 365.

## <a name="identifying-office-365-network-traffic"></a>Identifier le trafic réseau de Office 365

Nous rendre plus facile d’identifier le trafic réseau de Office 365 et et simplifie la gestion de l’identification du réseau.

- Nouvelles catégories de points de terminaison de réseau pour différencier le trafic réseau hautement critique le trafic réseau qui n’est pas affecté par la latence d’Internet. Il existe quelques exemples d’URL et la prise en charge des adresses IP dans la catégorie « Optimiser » plus critiques.
- Identification de réseau de services Web pour l’utilisation du script ou périphérique direct configuration et gestion du changement d’Office 365. Les modifications sont disponibles à partir du service web, ou au format RSS ou sur le courrier électronique à l’aide d’un modèle Microsoft Flow.
- [Programme de partenariat office 365 réseau](http://aka.ms/Office365NPP) avec les partenaires Microsoft qui proposent des périphériques ou des services qui suivent les principes de connectivité réseau Office 365 et ont une configuration simple.

## <a name="securing-office-365-connections"></a>Sécurisation des connexions d’Office 365

L’objectif de la sécurité réseau traditionnelle consiste à renforcer la sécurité du périmètre du réseau d’entreprise contre les intrusions et les attaques malveillantes. La plupart des réseaux d’entreprise appliquer la sécurité réseau pour le trafic Internet à l’aide de technologies telles que les serveurs proxy, pare-feu, arrêt SSL et vérifiez, approfondie des paquets et les systèmes de prévention de perte de données. Ces technologies fournissent de réduire les risques importants pour les demandes Internet génériques mais peuvent réduire considérablement les performances, l’évolutivité et la qualité de l’expérience utilisateur final lorsqu’elle est appliquée aux points de terminaison Office 365.

Office 365 vous aide à répondre aux besoins de votre organisation pour la sécurité et les données d’utilisation conformité du contenu avec des fonctionnalités de sécurité et de la gouvernance intégrées conçue spécifiquement pour les charges de travail et des fonctionnalités d’Office 365. Pour plus d’informations sur la sécurité Office 365 et de conformité, voir le [Guide de sécurité Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Pour plus d’informations sur les recommandations et la position de la prise en charge de Microsoft sur les solutions de réseau avancées qui effectuent le traitement de niveau avancé sur le trafic d’Office 365, voir [l’aide de périphériques réseau tiers ou solutions sur le trafic d’Office 365](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>Pourquoi Office 365 est un réseau différent ?

Office 365 est conçu pour des performances optimales à l’aide de la sécurité du point de terminaison et connexions réseau cryptées, réduisant le besoin de l’application de sécurité de périmètre. Centres de données Office 365 sont trouvent dans le monde entier et le service est conçu pour l’utilisation des différentes méthodes de connexion des clients à meilleures points de terminaison de service disponibles. Étant donné que les données utilisateur et traitement est répartie entre plusieurs centres de données Microsoft, il n’existe aucun point de terminaison de réseau client qui machines peuvent se connecter. En fait, les données et les services dans votre organisation cliente Office 365 dynamiquement optimisées par le réseau Global Microsoft pour s’adapter aux emplacements géographiques à partir de laquelle ils sont accessibles par les utilisateurs finaux.

Certains problèmes de performances sont créés lorsque le trafic Office 365 est soumis à l’inspection des paquets entrant et sortant centralisée :

- Latence élevée peut entraîner des performances très médiocres des flux audio et vidéos et la lenteur de récupération des données, les recherches, collaboration en temps réel, informations de disponibilité du calendrier, contenu dans les produits et d’autres services
- Egressing des connexions à partir d’un emplacement central d’annule les capacités de routage dynamiques du réseau global d’Office 365, en ajoutant la latence et le temps d’aller-retour
- Déchiffrement SSL sécurisée le trafic réseau de Office 365 et rechiffre il peut entraîner des erreurs de protocole de risques de sécurité

Connectivité raccourcir le chemin d’accès réseau Office 365 les points d’entrée en autorisant le trafic client à la sortie aussi proche que possible à leur emplacement géographique peut améliorer les performances et l’utilisateur final une expérience dans Office 365. Il permet également de réduire l’impact des modifications ultérieures à l’architecture du réseau sur les performances d’Office 365 et la fiabilité. Le modèle de connectivité optimale est toujours fournir la sortie de réseau à l’emplacement de l’utilisateur, que ce soit sur le réseau d’entreprise ou les sites distants tels qu’accueil, hôtels, cafés et les aéroports. Le trafic Internet et réseau étendu en fonction du trafic réseau d’entreprise serait routé séparément et n’utilisez pas le modèle local sortant directement. Ce modèle local sortant directement est représenté dans le diagramme ci-dessous.

![Architecture de réseau local sortant](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

L’architecture de sortie local présente les avantages suivants pour le trafic réseau Office 365 sur le modèle traditionnel :
  
- Fournit des performances optimales Office 365 en optimisant la longueur de l’itinéraire. Connexions de l’utilisateur final sont dynamiquement acheminées vers le point d’entrée le plus proche Office 365 par infrastructure de _porte sur Service distribué_ du réseau Global Microsoft, et le trafic est ensuite acheminé en interne à des points de terminaison de service et les données de Microsoft Fibre foncé de haute disponibilité très faible latence.
- Réduit la charge sur l’infrastructure du réseau d’entreprise en autorisant sortant local pour le trafic Office 365, en ignorant les proxys et les périphériques de contrôle du trafic.
- Sécurise les connexions aux deux extrémités en tirant parti du client du point de terminaison dans le nuage sécurité fonctionnalités de sécurité et, application de technologies de sécurité réseau redondantes.

> [!NOTE]
> L’infrastructure _distribuée porte de Service_ est côté du réseau hautement disponible et évolutif du réseau Global Microsoft avec réparties géographiquement. Elle met fin à des connexions de l’utilisateur final et les achemine efficacement au sein du réseau Global Microsoft. Pour plus d’informations sur le réseau Global Microsoft [comment Microsoft crée son réseau global rapides et fiables](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Pour plus d’informations sur la présentation et l’application des principes de connectivité réseau Office 365, voir [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles#office-365-connectivity-principles).

## <a name="conclusion"></a>Conclusion

Optimisation des performances du réseau Office 365 en d’autres termes à la suppression des obstacles inutiles. En traitant des connexions Office 365 comme le trafic approuvé, vous pouvez empêcher la latence par les paquets et de la concurrence pour la bande passante du proxy. Autoriser les connexions locales entre les ordinateurs clients et les points de terminaison Office 365 permet le trafic vers dynamiquement acheminés via le réseau Global Microsoft.

## <a name="related-topics"></a>Voir aussi

[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

[Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md)

[Connectivité réseau à Office 365](network-connectivity.md)

[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[Comment Microsoft crée son réseau global rapides et fiables](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
