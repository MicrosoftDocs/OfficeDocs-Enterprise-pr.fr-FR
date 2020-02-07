---
title: Défense contre les attaques par déni de service dans Office 365
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
f1.keywords:
- NOCSH
description: Vue d’ensemble des attaques par déni de service (DoS).
ms.openlocfilehash: 16378800fc7bb61b8f78e2c4c51eb7940cb45d17
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843587"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a>Défense contre les attaques par déni de service dans Office 365

## <a name="introduction"></a>Introduction

Microsoft offre une infrastructure de confiance pour plus de 200 services Cloud hébergés dans une infrastructure de Cloud internationale de plus de 100 centres de donnees. Cela inclut ce qui suit :

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft Office 365
- Microsoft OneDrive
- Skype
- Xbox LIVE

En tant qu’organisation mondiale avec une présence Internet importante et de nombreuses propriétés Internet importantes qui fournissent des services en nuage, Microsoft est une cible commune et commune aux pirates et autres personnes malveillantes. La couche de communication réseau entre les clients et le Cloud Microsoft est l’une des principales cibles d’attaques malveillantes. En fait, Microsoft s’exécute de façon continue et permanente sous une forme de cyber basée sur le réseau. En fonction de ces principes, Microsoft utilise des principes de sécurité de défense en profondeur pour protéger ses services et réseaux Cloud. Sans systèmes d’atténuation fiables et persistants qui se défendent contre ces attaques, les services Cloud de Microsoft seraient hors ligne et indisponibles pour les clients.

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>Définition et symptômes des attaques par déni de service

Pour attaquer les services réseau, il est possible de créer de nombreuses requêtes auprès d’hôtes de service afin de submerger le réseau et les serveurs afin de refuser les services aux utilisateurs légitimes. Il s’agit d’une attaque par déni de service (DoS). Lorsque l’attaque est effectuée par plusieurs acteurs, points de terminaison et/ou vecteurs, elle est considérée comme une attaque de déni de service distribuée. Bien que les moyens, les motivations et les cibles varient, les attaques DoS et DDoS consistent généralement à empêcher un site ou un service Internet de fonctionner correctement ou du tout, de façon temporaire ou indéfinie.

L’équipe américaine de préparation de l' [urgence informatique](https://www.us-cert.gov/) (US-CERT) définit les symptômes des attaques par déni :

- Ralentissement des performances réseau (lors de l’ouverture de fichiers ou accès aux sites Internet)
- Indisponibilité d’un site Web
- Impossibilité d’accéder à un site Web
- Augmentation spectaculaire du courrier indésirable reçu
- Déconnexion d’une connexion Internet câblée ou sans fil
- Perte d’accès à long terme pour le Web ou tout service Internet

## <a name="related-topics"></a>Rubriques connexes

- [Principes fondamentaux de défense contre les attaques par déni de service](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Stratégie de défense contre les attaques par déni de service de Microsoft](office-365-microsoft-dos-defense-strategy.md)
- [Protection des services de Cloud Computing Microsoft contre les attaques par déni de service](office-365-defending-cloud-services-against-dos-attacks.md)
