---
title: Stratégie d’Office 365 DoS Defense
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Vue d’ensemble de la stratégie de défense Microsoft pour les attaques par déni de service (DoS).
ms.openlocfilehash: c30e8e5c91ead81ceda9cfaeb4ef6b17c9addc9f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844385"
---
# <a name="office-365-denial-of-service-defense-strategy"></a>Stratégie de défense contre les attaques par déni de service Office 365

La stratégie de Microsoft visant à se défendre contre les attaques par déni de service (DoS) sur le réseau est unique en raison de notre échelle et de votre empreinte internationale. Cette mise à l’ampleur permet à Microsoft d’utiliser des stratégies et des techniques peu adaptées aux organisations, aux fournisseurs ou aux entreprises clientes. La stratégie DoS repose sur notre présence globale. Microsoft engage des fournisseurs Internet, des fournisseurs de pairs (publics et privés) et des sociétés privées dans le monde entier. Cela donne à Microsoft une présence importante sur Internet et permet à Microsoft d’absorber les attaques sur une grande surface d’exposition.

Étant donné cette nature unique, Microsoft utilise des processus de détection et de minimisation qui diffèrent de ceux utilisés par les grandes entreprises. La stratégie est basée sur une séparation de la détection et de l’atténuation distribuée globale via un grand nombre de périphéries réseau. De nombreuses entreprises utilisent des solutions tierces pour détecter et atténuer les attaques sur le serveur Edge. Au fur et à mesure de la croissance de la capacité de Microsoft, il est devenu évident que toute attaque contre des contours individuels ou spécifiques était faible. En raison de cette configuration unique, Microsoft a séparé les composants de détection et de minimisation. Microsoft déploie des systèmes de détection à plusieurs niveaux pour détecter les attaques plus près de leurs points de saturation tout en conservant une atténuation globale au niveau du périmètre. Cette stratégie garantit que nous pouvons gérer plusieurs attaques simultanées.

L’une des défenses les plus efficaces et les plus économiques employées par Microsoft contre les attaques de refus de service consiste à réduire les surfaces d’attaque de service. Le trafic indésirable est abandonné au niveau du périmètre réseau au lieu d’analyser, de traiter et de purger les données incorporées.

Au niveau de l’interface avec le réseau public, Microsoft utilise des périphériques de sécurité à usage spécial pour le pare-feu, la traduction d’adresses réseau et les fonctions de filtrage IP. Microsoft utilise également le routage de chemins d’accès multiples (ECMP) à coût égal global. Le routage ECMP global est une infrastructure réseau qui permet de s’assurer qu’il existe plusieurs chemins globaux pour atteindre un service. Avec ces chemins multiples, les attaques contre les services sont limitées à la région à partir de laquelle l’attaque est issue. Les autres régions ne doivent pas être affectées par cette attaque, car les utilisateurs finaux utiliseraient d’autres chemins pour atteindre le service dans ces régions. Microsoft a également développé des systèmes de corrélation et de détection DoS internes qui utilisent des données de flux, des mesures de performances et d’autres informations. Il s’agit d’un service Cloud de hyperéchelle de Microsoft Azure, qui analyse les données collectées à partir de différents points sur les réseaux et les services Microsoft. Une équipe de réponse aux incidents DoS entre plusieurs charges de travail identifie les rôles et les responsabilités entre les équipes, les critères de remontée des problèmes, ainsi que les protocoles permettant d’engager diverses équipes et de gérer les incidents. Ces solutions fournissent une protection réseau contre les attaques DoS.

Enfin, les charges de travail basées sur le Cloud sont configurées avec des seuils optimisés en fonction de leur protocole et de l’utilisation de la bande passante pour protéger de manière unique cette charge de travail.
