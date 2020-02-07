---
title: Surveillance et autoréparation d’Office 365
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
description: Informations sur les fonctionnalités de surveillance et d’autoréparation d’Office 365.
ms.openlocfilehash: 825edd1bc994f696c14e53d8830fc10defb04630
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844365"
---
# <a name="office-365-monitoring-and-self-healing"></a>Surveillance et autoréparation d’Office 365

Étant donné l’ampleur d’Office 365, il serait impossible de maintenir les données client résistantes et sûres des programmes malveillants sans surveillance intégrée complète, alerte intelligente et auto-réparation rapide et fiable. La surveillance d’un ensemble de services à l’étendue d’Office 365 est très complexe. De nouvelles mentalités et méthodologies devaient être introduites, ainsi que de nouveaux ensembles de technologies qui devaient être créés pour fonctionner et gérer le service dans un environnement global connecté. Nous avons quitté l’approche de surveillance traditionnelle de la collecte de données et du filtrage pour créer des alertes à une approche basée sur l’analyse des données ; prendre des signaux et renforcer la confiance de ces données, puis utiliser l’automatisation pour récupérer ou résoudre le problème. Cette approche permet de tirer le meilleur parti de l’équation de récupération, qui, à son tour, rend les opérations moins onéreuses, plus rapides et moins sujettes aux erreurs. 

La surveillance fondamentale de Office 365 est une collection de technologies qui comprend notre moteur Data Insights, qui est basé sur Azure, SQL Azure et la [technologie de base de données de flux Open source](https://cassandra.apache.org/). Elle est conçue pour collecter et agréger des données et atteindre des conclusions. Actuellement, il traite plus de 500 millions événements par heure à partir de plus de 100 000 serveurs (~ 15 to par jour) disséminés sur des dizaines de centres de contenu dans de nombreuses régions, et ces chiffres augmentent. 

Office 365 utilise la *surveillance extérieure*, qui implique la création de transactions synthétiques pour tester tout ce qui est important. Par exemple, dans Exchange Online, chaque scénario teste toutes les bases de données dans le monde entier toutes les cinq minutes de manière disséminée, ce qui permet une couverture quasi continue de tout ce qui se trouve dans le système. À partir de plusieurs emplacements, 250 millions transactions de test par jour sont effectuées pour créer une base ou une pulsation robuste pour le service. 

Office 365 utilise également le concept d' *alerte rouge*, qui réduit tous les signaux de surveillance de tous les ordinateurs de nos centres de donnes à un point gérable par un humain. Le concept est assez simple : si un événement se produit sur plusieurs signaux, il doit y avoir un problème. Comme il ne s’agit pas de la création d’une confiance dans un signal, il est possible d’avoir une fidélité raisonnable pour chaque signal afin d’obtenir une plus grande précision. Ce système de surveillance est si puissant que nous n’avons pas de personnel 24x7 qui surveille nos moniteurs. tout ce dont nous disposons est la machine qui s’en sort si elle détecte un problème, auquel cas le personnel d’appel approprié, ou, le cas échéant, sera plus souvent mis en page et résoudrea le problème. Une fois que nous avons commencé à collecter des signaux et créé des alertes rouges, nous pouvons démarrer la triangulation sur toutes les partitions de service. 

En fonction de la combinaison de l’alerte d’échec et des alertes rouges, cette alerte indique exactement quels composants pourraient présenter un problème et que le système va tenter de corriger le problème en redémarrant un serveur de boîtes aux lettres. 

En plus des fonctionnalités de réparation automatique, telles que la restauration d’une seule page, Exchange Online comprend plusieurs fonctionnalités qui prennent une approche de surveillance et d’auto-réparation qui se concentre sur la préservation de l’expérience de l’utilisateur final. Ces fonctionnalités incluent la *disponibilité gérée*, qui fournit des actions de surveillance et de récupération intégrées, et autoseed, qui restaure automatiquement la redondance des bases de données après une défaillance du disque. 

## <a name="managed-availability"></a>Disponibilité gérée 

La disponibilité gérée offre une solution native de vérification et de récupération de l’intégrité qui surveille et protège l’expérience de l’utilisateur final via des actions orientées sur la récupération. La disponibilité gérée est l’intégration des actions de surveillance et de récupération intégrées à la plateforme de haute disponibilité Exchange. Elle est conçue pour détecter des problèmes et procéder à une récupération dès qu'ils apparaissent ou sont découverts par le système. À la différence des techniques et solutions externes de surveillance précédentes pour Exchange, la disponibilité gérée ne tente pas d'identifier ni de communiquer la cause première d'un incident. Au lieu de cela, il est axé sur des aspects de récupération qui concernent trois domaines clés de l’expérience de l’utilisateur final :

- **Disponibilité** : les utilisateurs peuvent-ils accéder au service ? 
- **Latence** -comment est l’expérience pour les utilisateurs ? 
- **Erreurs** -les utilisateurs peuvent-ils faire ce qu’ils veulent ? 

La disponibilité gérée est une fonctionnalité interne qui s’exécute sur chaque serveur Office 365 exécutant Exchange Online. Elle interroge et analyse des centaines de paramètres d'intégrité par seconde. Si un problème se trouve incorrect, la plupart du temps, il est résolu automatiquement. Toutefois, il y aura toujours des problèmes selon lesquels la disponibilité gérée ne sera pas en mesure de réparer de lui-même. Dans ce cas, la disponibilité gérée transmet le problème à une équipe de support Office 365 par le biais de la journalisation des événements.

## <a name="autoreseed"></a>AutoReseed

Les serveurs Exchange Online sont déployés dans une configuration qui stocke plusieurs bases de données et leurs flux de journal sur le même disque non RAID. Cette configuration est souvent appelée *simplement un paquet de disques* (JBOD) car aucun mécanisme de redondance de stockage, tel qu’un RAID, n’est utilisé pour dupliquer les données sur le disque. Lorsqu’un disque tombe en panne dans un environnement JBOD, les données sur ce disque sont perdues. 

Étant donné la taille d’Exchange Online et le fait que le déploiement dans ce sont des millions de disques, les défaillances de lecteur de disque sont une occurrence normale dans Exchange Online. En fait, plus de 100 échouent tous les jours. Lorsqu’un disque tombe en panne dans un déploiement d’entreprise local, un administrateur doit manuellement remplacer le disque défaillant et restaurer les données affectées. Dans un déploiement Cloud, la taille d’Office 365, avec des opérateurs (administrateurs Cloud) qui remplacent manuellement les disques n’est ni pratique ni économiquement réalisable. 

Le réamorçage automatique, ou *autoseed*, est une fonctionnalité qui remplace l’action normalement pilotée par un opérateur en réponse à une défaillance du disque, à un événement d’endommagement de la base de données ou à un autre problème nécessitant la réamorçage d’une copie de base de données. La fonctionnalité AutoReseed permet de restaurer automatiquement la redondance de base de données après une défaillance de disque par le biais de disques de rechange qui ont été configurés sur le système. En cas de défaillance du disque, les copies de base de données stockées sur ce disque sont automatiquement réamorcées sur un disque de rechange préconfiguré sur le serveur, ce qui permet de restaurer la redondance. 