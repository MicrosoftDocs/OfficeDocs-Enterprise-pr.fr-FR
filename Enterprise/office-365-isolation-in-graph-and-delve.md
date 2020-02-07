---
title: Isolation du client Office 365 dans Office Graph et Delve
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
description: 'Résumé : explication de l’isolation du client dans Office Graph et dans Delve.'
ms.openlocfilehash: c9e054494e6d71d84a19350bc38e0d3981fede45
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844435"
---
# <a name="tenant-isolation-in-the-office-graph-and-delve"></a>Isolation du client dans Office Graph et Delve

## <a name="tenant-isolation-in-the-office-graph"></a>Isolation du client dans Office Graph

L’activité des modèles [Office Graph](https://developer.microsoft.com) dans Office 365 services, y compris Exchange Online, SharePoint Online, Yammer, Skype entreprise, Azure Active Directory, etc., et dans les services externes, tels que les autres services Microsoft ou services tiers. Les composants Office Graph sont utilisés dans Office 365. Office Graph représente une collection de contenu et d’activité, ainsi que les relations entre ceux-ci dans l’ensemble de la suite Office. Il utilise des techniques d’apprentissage automatique sophistiquées pour connecter des personnes au contenu, aux conversations et aux personnes qui les entourent. Par exemple, l’index client dans SharePoint Online a un index Office Graph utilisé pour traiter les requêtes de Delve, le moteur de traitement de l’analyse dans SharePoint Online est utilisé pour stocker les signaux et calculer les informations, et Exchange Online calcule les cache de destinataires en tant qu’entrée dans l’analyse de client.

Office Graph contient des informations sur les objets d'entreprise, tels que les contacts et les documents, ainsi que sur les relations et les interactions entre ces objets. Les relations et les interactions sont représentées par des *connexions*. Office Graph est segmenté par client, de sorte que les bords ne peuvent exister qu’entre les *nœuds* du même client. Un *nœud* est une entité avec un URI (Uniform Resource Identifier), un type de nœud, une liste de contrôle d’accès et un ensemble de facettes contenant des *métadonnées* et des bords. Chaque nœud est associé à des métadonnées et des bords, organisés en *facettes* comme dans le modèle de connaissances commun. Les *métadonnées* sont nommées les propriétés stockées sur un nœud qui peuvent être utilisées pour la recherche, le filtrage ou l’analyse dans Office Graph. Une *facette* est une collection logique de métadonnées et de bords sur un nœud. Chaque facette décrit un aspect d’un nœud. 

Office Graph ne fait pas toutes les données dans un seul référentiel ; au lieu de cela, il stocke les métadonnées et les relations relatives aux données qui se trouvent ailleurs. Office Graph se compose de plusieurs magasins de données et composants de traitement :

- Le magasin Graph de client offre un stockage en bloc optimisé pour une analyse efficace.
- Le cache de contenu actif offre un accès aléatoire rapide aux nœuds actifs et aux périphéries pour conduire les expériences utilisateur.
- Le routeur d’entrée avertit les composants internes et externes des modifications apportées au graphique client.

L’analyse de chaque charge de travail déduit des informations pertinentes pour les calculs à l’échelle du client et les achemine vers le graphique client. Des raisons d’analyse de client pour toutes les activités d’un client pour produire des idées dans des modèles de comportement. Par exemple, Exchange Online calcule le cache de destinataires de chaque utilisateur avec une analyse de la boîte aux lettres de chaque utilisateur. Ces analyses par utilisateur produisent un ensemble de *périphéries RecipientCache* sur chaque personne, qui sont ensuite envoyées au graphique client. Cela permet de conserver la plus grande partie du traitement de l’analyse aussi près que possible des données sources.

## <a name="tenant-isolation-in-delve"></a>Isolation du client dans Delve

Comme mentionné précédemment, Office Graph fournit des expériences qui aident les utilisateurs à découvrir et à collaborer sur les activités actuelles dans leur entreprise, et fournit une plateforme centrée sur l’entité pour les analyses pour des raisons de contenu et d’activité sur les charges de travail et au-delà d’Office 365. Delve est la première expérience d’Office Graph.
Delve est une expérience Web Office 365 qui couvre le contenu d’Office 365 et Yammer Enterprise vers les utilisateurs d’Office 365 via Office Graph. L’expérience Web affiche les données sous la forme de différentes cartes, chacune comportant une rubrique particulière, telle que la *tendance à moi* ou *modifiée par moi*. Chaque carte se compose de plusieurs cartes de document qui affichent un texte de synthèse et une image du document. La carte permet aux utilisateurs d’effectuer des actions comme ouvrir le document ou une page Yammer pour le document. Il existe une page pour chaque personne d’un client Office 365 qui affiche les documents les plus pertinents pour cette personne, ainsi que les icônes qui peuvent appeler Exchange Online ou Skype entreprise pour interagir avec cette personne. Étant donné que Delve est basé sur l’API Office Graph, il est lié par l’isolation basée sur le client de cette API.