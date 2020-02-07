---
title: Configurer votre réseau pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Voir les articles suivants pour comprendre la mise en réseau pour Office 365.'
ms.openlocfilehash: c1976a6b1ae5bff0b5f6f909ee9ab8495f371653
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844025"
---
# <a name="set-up-your-network-for-office-365"></a>Configurer votre réseau pour Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Une partie importante de votre intégration Office 365 est de vous assurer que vos connexions réseau et Internet sont définies pour optimiser l’accès. Configurer votre réseau local pour accéder à un cloud logiciel en tant que service (SaaS) distribué globalement est différent d’un réseau traditionnel optimisé pour le trafic vers des centres de données locaux et une connexion internet centrale. 

Utilisez ces articles pour comprendre les différences clés et modifier vos équipements de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances de la part de vos utilisateurs locaux.

## <a name="how-office-365-networking-works"></a>Fonctionnement de mise en réseau Office 365

Consultez les articles suivants pour une vue d’ensemble de la connectivité pour Office 365 :

- [Vue d’ensemble de la connectivité réseau Office 365](office-365-networking-overview.md)
- [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)
- [Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

Pour obtenir des conseils sur l’amélioration des performances, voir [planification réseau et optimisation des performances pour Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Prise en charge de la mise en réseau Office 365 comme un fournisseur d’équipement réseau

Si vous êtes un fournisseur d’équipement réseau, rejoignez le[programme de partenariat mise en réseau d’Office 365](office-365-networking-partner-program.md). Inscrivez-vous au programme pour développer les principes de connectivité réseau Office 365 dans vos produits et solutions. 

## <a name="office-365-endpoints"></a>Points de terminaison Office 365

Les points de terminaison sont l’ensemble des adresses IP de destination, noms de domaine DNS et URL pour le trafic sur Internet Office 365. 

Pour optimiser les performances aux services Office 365 basés sur le cloud, certains points de terminaison nécessitent une gestion spéciale par les autres navigateurs client et les appareils dans votre réseau de périmètre. Ces appareils incluent pare-feux, SSL Break and Inspect et des appareils d’inspection des paquets, et systèmes de protection contre la perte de données.

Voir [Gestion des points de terminaison d’Office 365 ](managing-office-365-endpoints.md) pour plus d’informations.

Il existe actuellement cinq différents clouds Office 365. Ce tableau vous permet d’accéder à la liste des points de terminaison pour chacun d’eux.

|||
|:-------|:-----|
| [Points de terminaison internationaux](urls-and-ip-address-ranges.md) | Les points de terminaison pour les abonnements Office 365 dans le monde, dont le États-Unis Government Community Cloud (GCC). |
| [Points de terminaison DoD du gouvernement américain](office-365-u-s-government-dod-endpoints.md) | Les points de terminaison pour les abonnements aux États-Unis Department of Defense (DoD). |
| [Points de terminaison GCC High du gouvernement américain](office-365-u-s-government-gcc-high-endpoints.md) | Les points de terminaison pour les abonnements aux États-Unis pour le secteur public Communauté Cloud élevé (GCC élevé). |
| [Office 365 géré par les points de terminaison 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Les points de terminaison pour Office 365 géré par 21Vianet, qui est conçu pour répondre aux besoins d’Office 365 en Chine. |
| [Points de terminaison Office 365 Germany](office-365-germany-endpoints.md) | Les points de terminaison pour un cloud en Europe distinct, pour les clients plus régulés en Allemagne, Union européenne (UE) et l’Association européenne de libre-échange (AELE). |
|||

Pour automatiser l’obtention de la dernière liste des points de terminaison pour votre cloud Office 365, voir [Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md).

Pour plus de points de terminaison, voir les articles suivants :

- [Autres points de terminaison supplémentaires non inclus dans les services web](additional-office365-ip-addresses-and-urls.md)
- [Requêtes réseau dans Office 2016 pour Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a>Autres rubriques réseau Office 365

Voir les articles suivants pour rubriques spécialisés dans la mise en réseau Office 365 :

- [Réseaux de distribution de contenu](content-delivery-networks.md)
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
- [Prise en charge de la traduction d’adresses réseau (NAT) avec Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute pour Office 365

Consultez les articles suivants pour plus d’informations sur l’utilisation d’ExpressRoute pour le trafic Office 365 :

- [Azure ExpressRoute pour Office 365](azure-expressroute.md)
- [Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
- [Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
- [Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
