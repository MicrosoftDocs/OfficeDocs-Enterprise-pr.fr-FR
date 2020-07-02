---
title: Microsoft 365 traitant de l’endommagement des données
ms.author: josephd
author: JoeDavies-MSFT
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
description: Une explication de la corruption des données dans Microsoft 365, ainsi que les efforts de prévention et de récupération de Microsoft.
ms.openlocfilehash: 674f2a3a026c5706f5c3a23db6e2d968ed815656
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998448"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a>Gestion de l’endommagement des données dans Microsoft 365

L’un des aspects les plus délicats de l’exécution d’un service Cloud de grande envergure est la façon de gérer l’altération des données, compte tenu du volume important de données et des systèmes indépendants. La corruption des données peut être causée par :

- Bogues d’application ou d’infrastructure, en corrompant tout ou partie de l’état de l’application
- Problèmes matériels entraînant la perte de données ou l’impossibilité de lire des données
- Erreurs opérationnelles humaines
- Pirates malveillants et employés mécontents
- Incidents dans les services externes entraînant une perte de données

Étant donné que la résilience accrue de l’intégrité des données signifie moins d’incidents d’endommagement des données, Microsoft a intégré les mécanismes de protection de Microsoft 365 pour empêcher la corruption, ainsi que les systèmes et les processus qui nous permettent de récupérer les données le cas échéant. Il existe des vérifications et des processus dans les différentes étapes du processus de publication d’ingénierie afin de renforcer la résistance contre l’altération des données, notamment :

- Conception du système
- Structure et organisation du code
- Révision du code
- Tests d’unité, tests d’intégration et tests système
- Tests/portails de fils de voyage

Dans les environnements de production Microsoft 365, la réplication d’homologue entre centres de données garantit qu’il y a toujours plusieurs copies dynamiques de toutes les données. Les images et les scripts standard permettent de récupérer les serveurs perdus, et les données répliquées sont utilisées pour restaurer les données client. En raison des contrôles et des processus de résilience des données intégrés, Microsoft conserve uniquement les sauvegardes de la documentation du système d’information Microsoft 365 (y compris la documentation liée à la sécurité), à l’aide de la réplication intégrée dans SharePoint Online et de notre outil référentiel de code interne, Source Depot. La documentation système est stockée dans SharePoint Online, et Source Depot contient des images système et d’application. SharePoint Online et le SAV source utilisent tous deux le contrôle de version et sont répliqués en quasi-temps réel.
