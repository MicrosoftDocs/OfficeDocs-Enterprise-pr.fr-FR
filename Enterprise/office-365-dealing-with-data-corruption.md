---
title: Office 365 traitant de l’endommagement des données
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
description: Une explication de la corruption des données dans Office 365, ainsi que les efforts de prévention et de récupération de Microsoft.
ms.openlocfilehash: 1477ab4dca0f9126eb04b76b9f8f65ff0b5eefc8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844485"
---
# <a name="dealing-with-data-corruption-in-office-365"></a>Gestion de l’altération des données dans Office 365

L’un des aspects les plus délicats de l’exécution d’un service Cloud de grande envergure est la façon de gérer l’altération des données, compte tenu du volume important de données et des systèmes indépendants. La corruption des données peut être causée par :

- Bogues d’application ou d’infrastructure, en corrompant tout ou partie de l’état de l’application
- Problèmes matériels entraînant la perte de données ou l’impossibilité de lire des données
- Erreurs opérationnelles humaines
- Pirates malveillants et employés mécontents
- Incidents dans les services externes entraînant une perte de données

Étant donné que la résilience accrue de l’intégrité des données signifie moins d’incidents d’endommagement des données, Microsoft a intégré les mécanismes de protection d’Office 365 pour empêcher la corruption, ainsi que les systèmes et les processus qui nous permettent de récupérer les données le cas échéant. Il existe des vérifications et des processus dans les différentes étapes du processus de publication d’ingénierie afin de renforcer la résistance contre l’altération des données, notamment :

- Conception du système
- Structure et organisation du code
- Révision du code
- Tests d’unité, tests d’intégration et tests système
- Tests/portails de fils de voyage

Dans les environnements de production Office 365, la réplication d’homologue entre centres de données garantit qu’il y a toujours plusieurs copies dynamiques de toutes les données. Les images et les scripts standard permettent de récupérer les serveurs perdus, et les données répliquées sont utilisées pour restaurer les données client. En raison des contrôles et des processus de résilience des données intégrés, Microsoft conserve uniquement les sauvegardes de la documentation du système d’informations Office 365 (y compris la documentation liée à la sécurité), à l’aide de la réplication intégrée dans SharePoint Online et de notre code interne outil référentiel, dépôt source. La documentation système est stockée dans SharePoint Online, et Source Depot contient des images système et d’application. SharePoint Online et le SAV source utilisent tous deux le contrôle de version et sont répliqués en quasi-temps réel.
