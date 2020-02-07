---
title: Résilience des données dans Office 365
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
description: Comprendre la résilience des données dans Microsoft Office 365.
ms.openlocfilehash: 43eae5db254a0b352f44d60c81767dfa4caa33f3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843675"
---
# <a name="data-resiliency-in-office-365"></a>Résilience des données dans Office 365

## <a name="introduction"></a>Introduction

Étant donné la nature complexe de l’informatique en nuage, Microsoft est conscient du fait qu’il ne s’agit pas d’un cas où des choses ne seront pas correctes, mais plutôt à la place. Nous concevons nos services Cloud pour optimiser la fiabilité et réduire les effets négatifs sur les clients en cas de problème. Nous avons dépassé la stratégie traditionnelle basée sur l’infrastructure physique complexe, et nous avons intégré la redondance directement dans nos services Cloud. Nous utilisons une combinaison d’infrastructure physique moins complexe et de logiciels plus intelligents qui génèrent la résilience des données dans nos services et offrent une haute disponibilité à nos clients. 

## <a name="resiliency-and-recoverability-are-built-in"></a>La résilience et la récupérabilité sont intégrées 

L’intégration de la résilience et de la récupération commence en partant du principe que l’infrastructure et les processus sous-jacents échouent à un moment donné : le matériel (infrastructure) échouera, les êtres humains et les logiciels comportent des bogues. Bien qu’il soit incorrect de dire que les développeurs de logiciels n’ont pas pensé à ces éléments avant le Cloud, la façon dont ces problèmes étaient gérés dans une implémentation informatique classique était très différente avant le Cloud :

- Premièrement, les protections du matériel et de l’infrastructure étaient importantes. Cela signifiait que les centres de donneurs disposant d’une fiabilité de 99,99% nécessitaient une redondance importante de la puissance et du réseau, et que les serveurs étaient implémentés avec un clustering matériel, des alimentations doubles, des interfaces réseau doubles, etc. 
- Deuxièmement, le processus était primordial. Les équipes d’exploitation ont géré les procédures rigoureuses, changent les fenêtres utilisées et il y a souvent eu une charge de gestion de projet importante. 
- Troisièmement, le déploiement a eu lieu à un rythme glacial. Le déploiement de code sans propriétaire de la source attendue pour les correctifs et les versions majeures impliquaient le remplacement du matériel et les dépenses importantes en capital. De plus, la seule façon de corriger un problème était de revenir en arrière. Par conséquent, la plupart des organisations informatiques déploieront uniquement des versions majeures pour éviter que le travail ne se maintienne à jour. 
- Enfin, l’échelle des systèmes déployés, ainsi que le niveau de leur Interconnectedness, ont été nettement plus petits que c’est le cas. 

Aujourd’hui, les clients attendent une innovation continue de Microsoft sans compromettre la qualité, et c’est l’une des raisons pour lesquelles les services et les logiciels de Microsoft sont construits avec la résistance et la récupérabilité à l’esprit. 

## <a name="office-365-data-resiliency-principles"></a>Principes de résilience des données Office 365

La résilience fait référence à la capacité d’un service informatique à résister à certains types de défaillances, tout en restant entièrement fonctionnelle du point de vue du client. La résilience des données signifie que, quelle que soit la cause des défaillances dans Office 365, les données client critiques restent intactes et non affectées. À cette fin, les services Office 365 ont été conçus pour cinq principes de résistance spécifiques :

- Il existe des données critiques et non critiques. Les données non critiques (par exemple, si un message a été lu) peuvent être supprimées dans de rares scénarios d’échec. Les données critiques (par exemple, les données client telles que les messages électroniques) doivent être protégées à un coût extrême. En tant qu’objectif de conception, les messages électroniques sont toujours critiques et des éléments tels que la lecture d’un message ne sont pas critiques. 
- Les copies des données client doivent être séparées en différentes zones d’erreur ou autant de domaines d’erreur que possible (par exemple, centres de données, accessibles par des informations d’identification uniques (processus, serveur ou opérateur)) pour fournir une isolation des échecs. 
- Les données client critiques doivent être surveillées pour ne pas faire l’élément d’atomicité, de cohérence, d’isolation, de durabilité (ACID). 
- Les données client doivent être protégées contre toute altération. Elle doit être analysée ou surveillée activement, réparable et récupérable. 
- La plupart des pertes de données générées par les actions client, permettent aux clients de se retrouver eux-mêmes à l’aide d’une interface utilisateur graphique qui leur permet de restaurer accidentellement des éléments supprimés. 
 
Dans le cadre de nos services Cloud à ces principes, associés à des tests et validations robustes, Office 365 est capable de satisfaire et de dépasser les exigences des clients tout en garantissant une plateforme pour l’innovation et l’amélioration continues. 

## <a name="related-links"></a>Liens connexes

- [Gérer l’altération des données](office-365-dealing-with-data-corruption.md)
- [Protection contre les ransomware et programmes malveillants](office-365-malware-and-ransomware-protection.md)
- [Surveillance et auto-adaptation](office-365-monitoring-and-self-healing.md)
- [Résilience des données Exchange](office-365-exchange-data-resiliency.md)