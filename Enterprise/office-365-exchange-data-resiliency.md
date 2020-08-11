---
title: Résilience des données Exchange Online dans Microsoft 365
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
description: Dans cet article, vous trouverez une explication des différents aspects de la résilience des données dans Exchange Online et Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 18d8179f37cb97316b71a43cccfc631a5cc550da
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606610"
---
# <a name="exchange-online-data-resiliency-in-microsoft-365"></a>Résilience des données Exchange Online dans Microsoft 365

Il existe deux types d’endommagement pouvant avoir une incidence sur une base de données Exchange : la corruption physique, généralement causée par du matériel (en particulier, des problèmes de matériel de stockage) et une altération logique, qui se produit en raison d’autres facteurs. En règle générale, il existe deux types de corruption logique pouvant se produire dans une base de données Exchange : 
- **Corruption logique de la base** de données : le checksum de la page de base de données correspond, mais les données de la page sont incorrectes logiquement. Cela peut se produire lorsque le moteur de base de données (moteur de stockage extensible) tente d’écrire une page de base de données et même si le système d’exploitation renvoie un message de réussite, si les données ne sont pas écrites sur le disque ou si elles sont écrites au mauvais endroit. Il s’agit d’un *vidage perdu*. Le moteur ESE inclut de nombreuses fonctionnalités et protections qui sont conçues pour empêcher la corruption physique d’une base de données et d’autres scénarios de perte de données. Pour éviter la perte de données par des vidages perdus, le moteur ESE inclut un mécanisme de détection de vidage perdu dans la base de données, ainsi qu’une fonctionnalité de restauration d’une seule page. 
- **Corruption logique de magasin** : des données sont ajoutées, supprimées ou manipulées de telle sorte que l’utilisateur ne s’attend pas. Ces cas sont généralement provoqués par des applications tierces. Ce n'est généralement de la corruption que dans le sens où l'utilisateur voit cela comme une altération. La banque d'informations Exchange considère la transaction qui est à l'origine de l'altération logique comme une série d'opérations MAPI valides. Les fonctionnalités de [conservation](https://docs.microsoft.com/exchange/security-and-compliance/create-or-remove-in-place-holds) inaltérable d’Exchange Online procurent une protection contre l’altération logique du magasin (car elle empêche la suppression définitive du contenu par un utilisateur ou une application). 

Exchange Online effectue plusieurs contrôles de cohérence sur les fichiers journaux répliqués lors de l’inspection et de la relecture des journaux. Ces vérifications de cohérence empêchent la réplication physique du système. Par exemple, lors de l’inspection du journal, il existe une vérification de l’intégrité physique qui vérifie le fichier journal et vérifie que le checksum enregistré dans le fichier journal correspond à la somme de contrôle générée en mémoire. En outre, l’en-tête du fichier journal est examiné pour s’assurer que la signature du fichier journal enregistré dans l’en-tête du journal correspond à celle du fichier journal. Lors de la relecture du journal, le fichier journal est en cours d’examen. Par exemple, l’en-tête de base de données contient également la signature de journal qui est comparée à la signature du fichier journal pour s’assurer qu’elles correspondent. 

La protection contre la corruption des données de boîte aux lettres dans Exchange Online est obtenue à l’aide de la protection des données natives d’Exchange, une stratégie de résilience qui tire parti de la réplication au niveau de l’application sur plusieurs serveurs et plusieurs centres de données, ainsi que d’autres fonctionnalités permettant de protéger les données contre la perte de données en raison d’une corruption ou autres. Ces fonctionnalités incluent les fonctionnalités natives qui sont gérées par Microsoft ou l’application Exchange Online proprement dite, telles que :

- [Groupes de disponibilité des données](https://docs.microsoft.com/exchange/back-up-email)
- Correction de bit unique 
- Analyse de base de données en ligne 
- Détection de vidage perdu 
- Restauration d’une seule page 
- Service de réplication de boîte aux lettres 
- Vérifications des fichiers journaux 
- Déploiement sur un système de fichiers résilient 

Pour plus d’informations sur les fonctionnalités natives mentionnées ci-dessus, cliquez sur les liens hypertextes ci-dessus, et pour plus d’informations sur les éléments sans liens hypertexte, voir ci-dessous. En plus de ces fonctionnalités natives, Exchange Online inclut également des fonctionnalités de résilience de données que les clients peuvent gérer, telles que : 
- [Récupération d’élément unique (activée par défaut)](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages) 
- [Conservation inaltérable et conservation pour litige](https://docs.microsoft.com/exchange/security-and-compliance/in-place-and-litigation-holds) 
- [Rétention des éléments supprimés et boîtes aux lettres supprimées de manière récupérable (toutes les deux activées par défaut)](https://docs.microsoft.com/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes) 

## <a name="database-availability-groups"></a>Groupes de disponibilité de base de données 
Chaque base de données de boîtes aux lettres dans Microsoft 365 est hébergée dans un [groupe de disponibilité de base de données (DAG)](https://docs.microsoft.com/exchange/back-up-email) et répliquée dans des centres de données géographiquement distincts au sein de la même région. La configuration la plus courante est de quatre copies de bases de données dans quatre centres de données ; Toutefois, certaines régions ont moins de centres de données (les bases de données sont répliquées sur trois centres de données en Inde et deux centres de données en Australie et au Japon). Dans tous les cas, toutes les bases de données de boîtes aux lettres disposent de quatre copies qui sont distribuées entre plusieurs centres de données, garantissant ainsi la protection des données de boîte aux lettres contre les défaillances logicielles, matérielles et même dans les centres de données. 

Dans ces quatre exemplaires, trois d’entre eux sont configurés comme hautement disponibles. La quatrième copie est configurée en tant que [copie de base de données retardée](https://docs.microsoft.com/Exchange/high-availability/manage-ha/activate-lagged-db-copies). La copie de base de données retardée n’est pas conçue pour la récupération de boîte aux lettres individuelle ou la récupération des éléments de boîte aux lettres. Son objectif est de fournir un mécanisme de récupération pour les rares événements d’altération logique à l’échelle du système. 

Les copies de base de données retardée dans Exchange Online sont configurées avec un retard de relecture du fichier journal de sept jours. De plus, le gestionnaire de décalage de relecture Exchange est activé pour permettre la lecture du fichier journal dynamique pour les copies retardée afin de permettre aux copies de base de données retardée de se réparer automatiquement et de gérer la croissance des fichiers journaux. Bien que les copies de base de données retardée soient utilisées dans Exchange Online, il est important de comprendre qu’il ne s’agit pas d’une sauvegarde à un point dans le temps garantie. Les copies de base de données retardée dans Exchange Online ont un seuil de disponibilité, généralement d’environ 90%, en raison des périodes au cours desquelles le disque contenant une copie retardée est perdu suite à une défaillance du disque, la copie retardée devenant une copie hautement disponible (en raison d’une lecture automatique), ainsi que les périodes où la copie de base de données retardée recrée la file 

## <a name="transport-resilience"></a>Résilience de transport 
Exchange Online inclut deux fonctionnalités principales de résilience de transport : redondance des clichés instantanés et sécurité du réseau. La redondance des clichés instantanés conserve une copie redondante d’un message en transit. Safety net conserve une copie redondante d’un message une fois que le message a bien été remis. 

Avec la redondance des clichés instantanés, chaque serveur de transport Exchange Online effectue une copie de chaque message qu’il reçoit avant de reconnaître le message au serveur d’envoi. Cela rend tous les messages dans le pipeline de transport redondants pendant le transit. Si Exchange Online détermine que le message d’origine a été perdu en transit, une copie redondante du message est redistribuée. 

Safety net est une file d’attente de transport qui est associée au service de transport sur un serveur de boîtes aux lettres. Cette file d'attente stocke des copies des messages qui ont été correctement traités par le serveur. Lorsqu’une défaillance de serveur ou de base de données de boîte aux lettres nécessite l’activation d’une copie obsolète de la base de données de boîtes aux lettres, les messages de la file d’attente de sécurité sont automatiquement renvoyés à la nouvelle copie active de la base de données de boîtes aux lettres. Safety net est également redondant, ce qui élimine le transport en tant que point de défaillance unique. Il utilise le concept de dispositif de sécurité principal et de dispositif de sécurité de secours où, si le filet de sécurité principal n’est pas disponible pendant plus de 12 heures, les demandes de nouveau renvoi deviennent des demandes de retransmission de clichés instantanés et les messages sont remis à partir du dispositif de sécurité de secours.

Les retransmissions de messages à partir de Safety Net sont automatiquement initiées par le composant Gestionnaire Active Manager du service de réplication Microsoft Exchange qui gère les copies des bases de données de Dag et de boîtes aux lettres. Aucune action manuelle n’est requise pour resoumettre des messages à partir de Safety Net. 

## <a name="single-bit-correction"></a>Correction de bit unique 
Le moteur ESE inclut un mécanisme permettant de détecter et de résoudre les erreurs CRC codées sur un bit (c’est-à-dire les inversions monobits) résultant d’erreurs matérielles (et en tant que telles qu’elles représentent une altération physique). Lorsque ces erreurs se produisent, le moteur ESE les corrige automatiquement et enregistre un événement dans le journal des événements. 

## <a name="online-database-scanning"></a>Analyse de base de données en ligne 
L’analyse de base de données en ligne (également appelée « *parité de base de données*») est le processus dans lequel le moteur ESE utilise un vérificateur de cohérence de base de données pour lire chaque page et vérifier l’endommagement de la page. L’objectif principal est de détecter une altération physique et des vidages perdus qui ne peuvent pas être détectés par des opérations transactionnelles. L’analyse de base de données effectue également des opérations de blocage post-Store. L’espace peut être divulgué en raison de pannes, et l’analyse de base de données en ligne trouve et restaure l’espace perdu. Le système est conçu de manière à ce que toutes les bases de données soient entièrement analysées tous les sept jours. 

## <a name="lost-flush-detection"></a>Détection de vidage perdu 
Un vidage perdu se produit lorsqu’une opération de base de données que le sous-système de disque/système d’exploitation a renvoyé comme terminé n’a pas été écrite sur le disque ou a été écrite à un emplacement incorrect. Les incidents de vidage perdu peuvent entraîner une altération logique de la base de données, afin d’éviter que des vidages perdus ne se traduisent par des pertes de données, ESE inclut un mécanisme de détection de vidage perdu. Lorsque les pages de base de données sont écrites dans des copies passives, une vérification est effectuée pour les vidages perdus sur la copie active. Si un vidage perdu est détecté, le moteur ESE peut réparer le processus à l’aide d’un processus de mise à jour corrective de page. 

## <a name="single-page-restore"></a>Restauration d’une seule page 
La restauration d’une seule page, appelée mise à *jour corrective de page*, est un processus automatique dans lequel les pages de base de données endommagées sont remplacées par des copies saines d’un réplica sain. Le processus de réparation d’une page endommagée varie selon que la copie de la base de données est active ou passive. Lorsqu’une copie de base de données active rencontre une page endommagée, elle peut copier une page à partir de l’un de ses réplicas, à condition que la page copiée soit entièrement à jour. Pour ce faire, il suffit d’introduire une demande pour la page dans le flux de journal, qui est la base de la réplication de la base de données de boîtes aux lettres. Dès qu’un réplica rencontre la demande de page, il répond en envoyant une copie de la page à la copie de la base de données à l’origine de la demande. La restauration d’une seule page fournit également un mécanisme de communication asynchrone pour la demande d’une page à partir de réplicas, même si les réplicas sont actuellement en mode hors connexion. 

En cas de corruption d’une copie passive de la base de données, y compris une copie de base de données retardée, étant donné que ces copies sont toujours derrière leur copie active, il est toujours sûr de copier n’importe quelle page de la copie active vers une copie passive. Une copie de base de données passive est hautement disponible, de sorte que lors du processus de mise à jour corrective de page, la relecture des journaux est suspendue, mais la copie du journal continue. La copie de base de données passive récupère une copie de la page endommagée à partir de la copie active, attend que le fichier journal correspondant à l’exigence de génération de journal maximale requise soit copié et inspecté, puis il corrige la page endommagée. Une fois que la page a été corrigée, relancer la relecture du journal. Le processus est le même pour la copie de base de données retardée, sauf que la base de données retardée commence par relire tous les fichiers journaux nécessaires pour obtenir un État correctif. 

## <a name="mailbox-replication-service"></a>Service de réplication de boîte aux lettres 
Le transfert de boîtes aux lettres est un élément clé de la gestion d’un service de messagerie à grande échelle. Il existe toujours des technologies et des mises à niveau matérielles et de versions mises à jour pour traiter, ainsi qu’un système limité qui permet à nos ingénieurs de réaliser ce travail tout en garantissant que le déplacement des boîtes aux lettres est transparent pour les utilisateurs (en veillant à rester en ligne tout au long du processus) est essentiel et en s’assurant que le processus évolue en douceur. 

Le service de réplication de boîtes aux lettres Exchange est chargé de transférer les boîtes aux lettres entre les bases de données. Pendant le déplacement, Mme effectue une vérification de cohérence sur tous les éléments de la boîte aux lettres. Si un problème de cohérence est détecté, Mme corrige le problème ou ignore les éléments endommagés, supprimant ainsi la corruption de la boîte aux lettres. 

Étant donné que la Mme est un composant d’Exchange Online, nous pouvons modifier son code pour résoudre les nouveaux formulaires de dommages détectés à l’avenir. Par exemple, si nous détectons un problème de cohérence que Mme ne peut pas corriger, nous pouvons analyser la corruption, modifier le code de Mme et corriger l’incohérence (si nous comprenons comment procéder). 

## <a name="log-file-checks"></a>Vérifications des fichiers journaux 
Tous les fichiers journaux des transactions générés par une base de données Exchange sont soumis à plusieurs formes de vérifications de cohérence. Lors de la création d’un fichier journal, la première chose effectuée est un modèle binaire écrit, puis une série d’écritures de journal est effectuée. Cela permet à Exchange Online d’exécuter une série de vérifications (vider le vidage, le CRC et d’autres vérifications) pour valider chaque fichier journal tel qu’il est écrit, et à nouveau lors de la réplication. 

## <a name="deployment-on-resilient-file-system"></a>Déploiement sur un système de fichiers résilient 
Afin d’éviter toute altération au niveau du système de fichiers, Exchange Online est déployé sur les partitions ReFS (Resilience File System) pour fournir des fonctionnalités de récupération améliorées. ReFS est un système de fichiers dans Windows Server 2012 et versions ultérieures, conçu pour être plus résilient contre l’altération des données, ce qui optimise la disponibilité et l’intégrité des données. En particulier, ReFS apporte des améliorations quant à la façon dont les métadonnées sont mises à jour, ce qui offre une meilleure protection des données et réduit les cas de corruption des données. Il utilise également des checksum pour vérifier l’intégrité des données de fichier et des métadonnées pour s’assurer que la corruption des données est facile à trouver et à réparer. 

Exchange Online tire parti de plusieurs avantages ReFS : 
- Une résilience accrue de l’intégrité des données signifie moins d’incidents d’endommagement des données. Réduire le nombre d’incidents de corruption signifie moins de réamorces de bases de données inutiles. 
- Checksum s’exécutant sur les métadonnées pour activer les détections d’incidents d’endommagement plus rapidement et de façon plus déterministe, ce qui nous permet de résoudre les problèmes de corruption des données client avant les défaillances des volumes de données.
- Conçu pour fonctionner correctement avec des ensembles de données extrêmement volumineux, de pétaoctets et plus, sans impact sur les performances
- Prise en charge d’autres fonctionnalités utilisées par Exchange Online, telles que le chiffrement BitLocker. 

Exchange Online tire également parti des autres fonctionnalités ReFS : 
- **Intégrité (flux d’intégrité)** : ReFS stocke les données d’une manière qui les protège contre de nombreuses erreurs courantes pouvant entraîner une perte de données. Microsoft 365 Search utilise des flux d’intégrité pour détecter la corruption des disques et effectuer des checksums du contenu de fichier. La fonctionnalité réduit également les incidents de corruption causés par des « écritures déchirées » (lorsqu’une opération d’écriture ne se termine pas suite à des pannes de courant, etc.). 
- **Availability (valeur_rés)** -ReFS hiérarchise la disponibilité des données. Traditionnellement, les systèmes de fichiers étaient souvent exposés à des données endommagées qui nécessiteraient que le système soit mis hors connexion pour réparation. Bien que rare, en cas d’endommagement, ReFS implémente Salvage, une fonctionnalité qui supprime les données endommagées de l’espace de noms sur un volume actif et garantit que les données correctes ne sont pas affectées par des données endommagées non réparables. Le fait d’appliquer la fonctionnalité de récupération et d’isoler les données endommagées pour les volumes de base de données Exchange Online signifie que nous pouvons conserver les bases de données non affectées sur un volume endommagé sain entre le moment de l’endommagement et de la réparation. Cela augmente la disponibilité des bases de données qui seraient normalement affectées par de tels problèmes d’endommagement du disque. 