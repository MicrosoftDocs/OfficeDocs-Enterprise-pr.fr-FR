---
title: "Créer de A à Z"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Résumé : Obtenir les détails sur l’ensemble du nuage des blocs de construction de stockage que vous pouvez utiliser pour créer votre propre service de stockage ou de la solution."
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a>Créer de A à Z

 **Résumé :** Obtenir les détails sur l’ensemble du nuage des blocs de construction de stockage que vous pouvez utiliser pour créer votre propre service de stockage ou de la solution.
  
Les solutions de stockage à « créer de toutes pièces » :
  
- Permettent de créer votre propre solution de stockage à partir de zéro. 
    
- Nécessite la programmation à l’aide de l’API de reste.
    
- Offrir le nec plus ultra de la flexibilité et de personnalisation.
    
Les sections suivantes décrivent les détails de chaque option de stockage à « créer de toutes pièces ».
  
## <a name="azure-storage-files"></a>Stockage Azure (fichiers)

### <a name="features"></a>Fonctionnalités

- Facilite le déplacement d’applications héritées vers le cloud
    
- Stockage d’objets blob préféré pour de nouvelles applications
    
- Montage possible à partir de toute machine virtuelle Azure
    
- Montage possible en local avec SMB 3.0
    
- Fonctionne avec Linux et Windows
    
- Ne prend pas en charge l’authentification AD Azure ou ACL (clés de stockage Azure compte fournissent une authentification et un accès autorisé au partage de fichiers)
    
### <a name="common-uses"></a>Utilisations courantes

- Migration vers le cloud d’applications héritées qui dépendent de partages de fichiers
    
- Partager des outils de développement et de test
    
- Des applications distribuées peuvent stocker des journaux, des données de diagnostic et des vidages sur incident
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Sauvegarder des fichiers
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Stockage Azure (blobs)

### <a name="features"></a>Fonctionnalités

- Chaque compte de stockage peut contenir jusqu'à 500 To (un abonnement peut avoir plusieurs comptes de stockage)
    
- Les comptes de stockage sont organisés en conteneurs auxquels une sécurité peut être appliquée et qui peuvent contenir des objets blob
    
- Les objets blob de blocs sont optimisés pour la diffusion en continu et le stockage d’objets jusqu’à 200 Go
    
- Les objets blob de pages sont optimisés pour représenter des disques PaaS et prendre en charge les écritures aléatoires jusqu’à une taille de 1 To
    
- Les objets blob d’ajout sont optimisés pour ajouter des opérations jusqu’à 195 Go
    
- Un stockage Premium offre un débit d’E/S plus rapide grâce au stockage SSD
    
### <a name="common-uses"></a>Utilisations courantes

- Sauvegardes de fichiers, des ordinateurs, des bases de données et des périphériques des Images et du texte pour les applications web
    
- Données de configuration pour les applications cloud
    
- Big Data, par exemple, journaux et autres jeux de données volumineux
    
- Azure utilise Stockage Blob pour ses propres services, tels HDInsight et les disques de machine virtuelle.
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Stockage Azure (files d’attente)

### <a name="features"></a>Fonctionnalités

- Un compte de stockage peut contenir un nombre quelconque de files d’attente
    
- Une file d’attente peut contenir un nombre quelconque de messages (jusqu’à ce que le compte de stockage soit rempli)
    
- Les messages en file d’attente sont automatiquement supprimés après sept jours si aucune application ne les récupère et ne les supprime
    
- La taille des messages peut atteindre 64 Ko
    
- Sécurisé au niveau du compte de stockage
    
- Les files d’attente sont conçues pour transmettre des messages de contrôle, pas des données brutes
    
### <a name="common-uses"></a>Utilisations courantes

- Créer un backlog à traiter de façon asynchrone
    
- Traitement des messages du journal
    
- Dissocier les applications
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Distribuer des événements
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Stockage Azure (tables)

### <a name="features"></a>Fonctionnalités

- Idéal pour les jeux de données semi-structurés
    
- Généralement plus économique qu’un SQL traditionnel
    
- Très rapide si l’interrogation de la clé, ralentir si une recherche de valeur
    
- Très extensible : n’importe quelle quantité de tables dans les limites du compte de stockage
    
- Accessible via API REST, protocole oData limité, .NET
    
- Les valeurs doivent être sérialisées
    
### <a name="common-uses"></a>Utilisations courantes

- Données utilisateur pour applications web
    
- Carnets d’adresses
    
- Informations sur l’appareil
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Pour plus d'informations sur les coûts, cliquez [ici](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Recommandations concernant le Stockage Microsoft Azure

Lorsque vous concevez votre solution de stockage personnalisé avec le Stockage Microsoft Azure, gardez les points suivants à l’esprit :
  
- Tirez parti de plusieurs comptes de stockage pour une flexibilité accrue, soit via une augmentation de taille (> 100 To), soit via un débit plus important (> 5 000 opérations par seconde).
    
- Concevez la capacité d’ajout de comptes d’espace de stockage comme un changement de configuration, non un changement de code.
    
- Sélectionnez avec soin les fonctions de partitionnement pour le stockage Table, pour permettre la mise à l’échelle souhaitée en termes de performances d’insertion et de requête.
    
- Choisissez des noms de colonne courts pour les propriétés de table, car les métadonnées (noms de propriété) sont stockées dans la bande (les noms de colonne sont également inclus dans la taille maximale de ligne de 1 Mo).
    
- Autant que possible, groupez les opérations par lots dans l’espace de stockage.
    
- Placez systématiquement les informations de la base de données de configuration dans un cache distribué.
    
- Si les performances ou la fiabilité d’une application dépendent de la disponibilité d’un certain segment de données dans le cache, votre application doit refuser les demandes entrantes jusqu’à ce que le cache soit prérempli.
    
- Partitionnez les données verticalement (dans une table) ou horizontalement (en segmentant la table sur plusieurs partitions) pour répartir la charge sur plusieurs bases de données.
    
## <a name="see-also"></a>Voir aussi

[Stockage cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)



