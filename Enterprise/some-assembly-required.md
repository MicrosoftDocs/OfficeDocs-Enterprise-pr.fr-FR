---
title: Certains assembly requis
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "Résumé : Obtenez des détails sur l'ensemble des options de stockage cloud que vous pouvez utiliser pour créer votre solution de stockage personnalisée."
ms.openlocfilehash: bcfc5d851a3f3b0d987214c4ea22e669db3a53ee
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="some-assembly-required"></a>Certains assembly requis

 **Résumé :** Obtenez des détails sur l'ensemble des options de stockage cloud que vous pouvez utiliser pour créer votre solution de stockage personnalisée.
  
Solutions de stockage de type « Certains assembly requis » :
  
- Utilisent des services existants comme point de départ pour votre solution de stockage.
    
- Requièrent une configuration ou un encodage.
    
- Peuvent être personnalisées pour répondre à vos besoins.
    
Les sections suivantes donnent des détails sur chaque solution de stockage de type « Certains assembly requis ».
  
## <a name="azure-content-delivery-network"></a>Réseau de distribution de contenu Azure

### <a name="features"></a>Fonctionnalités

- Analyse avancée en temps réel
    
- Sécurité robuste contre le déni de service distribué (DDoS)
    
- Obtient automatiquement du contenu à partir d’un site web Azure ou d’Azure Cloud Service une fois l’intégration configurée
    
- Nouveau partenariat avec Akamai
    
- Peut gérer des charges lourdes et des pics de trafic soudains
    
### <a name="common-uses"></a>Utilisations courantes

- Distribuer des ressources audio et vidéo, des applications, des images et d’autres fichiers plus rapidement et sûrement à l’aide des serveurs les plus proches
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
- Gérer des vidéos
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((https://azure.microsoft.com/services/cdn/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((https://azure.microsoft.com/pricing/details/cdn/)).
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>Fonctionnalités

- Distribution Hadoop Apache fournie par le cloud Service Data Lake
    
- Mettre à l’échelle de pétaoctets à la demande
    
- Traiter les données non structurées et semi-structurées Développer en Java, .NET, et bien plus
    
- Éviter l’achat et la maintenance de matériel
    
- Connecter des clusters Hadoop locaux au cloud
    
- Flexibilité permettant de déployer des projets Hadoop arbitraires via des scripts personnalisés (par exemple, R, Giraph, Solr)
    
### <a name="common-uses"></a>Utilisations courantes

- Charges de travail d’analyse des données
    
- Infrastructure de traitement de données en mémoire pour le Big Data (Spark)
    
- Traitement de flux en temps réel (Storm)
    
- Traitement transactionnel (OLTP) important de données non relationnelles (HBase)
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((https://azure.microsoft.com/services/hdinsight/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((https://azure.microsoft.com/pricing/details/hdinsight/)).
  
## <a name="azure-sql-database"></a>Base de données SQL Azure

### <a name="features"></a>Fonctionnalités

- Optimisé pour réduire la gestion et les coûts
    
- Haute disponibilité, récupération d’urgence et mise à niveau automatiques
    
- Recommandé pour les organisations qui gèrent des centaines voire des milliers de bases de données jusqu’à une taille de 1 To
    
- Les techniques de partitionnement permettent de fractionner les données en plusieurs bases de données pour accroître la capacité de stockage
    
- Stretch Database avec SQL Server 2016
    
### <a name="common-uses"></a>Utilisations courantes

- Nouvelles applications conçues pour le cloud avec des données relationnelles
    
- Traitement de données sur des jeux de données schématiques et hautement structurés avec des relations
    
- Types de données spatiales ou riches
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="elastic-database"></a>Base de données élastique

Utilisez les ressources pratiquement illimitées d’Azure SQL Database dans les cas suivants :
  
- Le volume total de données est trop important pour respecter les contraintes d’une base de données unique.
    
- Le débit de transaction de la charge de travail globale dépasse les capacités d’une base de données unique.
    
- Les clients devant être isolés physiquement les uns des autres, des bases de données distinctes sont nécessaires pour chacun d’eux.
    
- Les différentes sections d’une base de données doivent résider dans des zones géographiques différentes pour des raisons de conformité, de performances ou de géopolitique.
    
Avec la mise à l’échelle verticale, vous pouvez modifier le niveau de performances de base de données Azure par édition ou à l’aide de pools de bases de données élastiques.
  
![Échelle verticale fournie par Azure SQL Database.](images/Storage_Poster/CloudStor-VertScale.png)
  
Avec la mise à l’échelle horizontale, vous pouvez ajouter de nouvelles bases de données selon vos besoins.
  
![Échelle horizontale fournie par Azure SQL Database.](images/Storage_Poster/CloudStor-HorizScale.png)
  
Pour plus d'informations, cliquez [ici]((https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)).
  
### <a name="stretch-database-with-sql-server-2016"></a>Stretch Database avec SQL Server 2016

Stretch Database est une fonctionnalité de SQL Server 2016 qui vous permet de déplacer des données froides de façon transparente et sécurisée, telles que des données d'entreprise fermées dans une table volumineuse qui contient des informations sur les commandes client, vers une base de données SQL Stretch dans Azure. Dans le cadre d'une extension, le contenu d'une instance SQL Server, d'une base de données ou d'une table unique est la combinaison de données locales stockées sur un serveur SQL Server 2016 à des données distantes dans Azure. Les données pouvant faire l'objet d'une extension sont automatiquement déplacées vers Azure par SQL Server 2016.
  
![Stretch Database avec SQL Server 2016](images/Storage_Poster/CloudStor-Stretch.png)
  
 

Les requêtes de l’utilisateur qui incluent les données historiques sont transférés en toute transparence à Azure SQL Stretch Database. Les requêtes ne doivent pas être réécrites, même si la table fait l’objet d’une extension. 


  
Stretch Database est une solution rentable qui offre un stockage à long terme et un accès transparent aux données historiques. Elle résout également les problèmes de performances et de disponibilité qui peuvent survenir lorsque les tables deviennent très volumineuses.
  
Pour plus d'informations, cliquez [ici]((https://msdn.microsoft.com/library/dn935011.aspx)).
  
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((http://azure.microsoft.com/services/sql-database/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/sql-database/)).
  
## <a name="azure-cosmos-db"></a>Azure Cosmos DB

### <a name="features"></a>Fonctionnalités

- Faible latence et 99,99 % de temps d’activité garantis par contrat de niveau de service (SLA), avec une échelle élastique illimitée de stockage et de débit
    
- Toutes les données sont globalement répliquées sur un nombre quelconque de régions, avec basculement transparent et quatre niveaux de cohérence bien définis
    
- Indexe automatiquement toutes vos données sans nécessiter de schémas ou d’indices secondaires
    
- Requêtes SQL et JavaScript riches, et transactions sur plusieurs éléments
    
### <a name="common-uses"></a>Utilisations courantes

- IoT, Mobile et Social
    
- Jeux vidéo
    
- Détail
    
- Gestion de contenu
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>Comparaison entre Cosmos DB, Tables Azure et Azure SQL Database

Attributs communs à Cosmos DB, Stockage Table Azure et Azure SQL Database :
  
- Disponibilité de 99,99 % garantie par SLA
    
- Services de base de données entièrement gérés
    
- ISO 27001, HIPAA et Clauses contractuelles types de l’Union européenne
    
Le tableau suivant montre les attributs non communs d’Azure Cosmos DB, de Stockage Table Azure et d’Azure SQL Database.
  
![Attributs rares de Cosmos DB vs. Tables Azure vs. Base de données SQL Azure](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((http://azure.microsoft.com/services/documentdb/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/documentdb/)).
  
## <a name="azure-media-services"></a>Azure Media Services

### <a name="features"></a>Fonctionnalités

- Diffusion de vidéo en direct et à la demande (VOD) avec mise à l’échelle
    
- Encodage et diffusion en continu à haut niveau de disponibilité
    
- Prend en charge Flash, iOS, Android, HTML5 et Xbox
    
- Prise en charge de gestion des droits numériques (DRM) certifiée par Studio
    
- Monétisation de contenu riche
    
- Vaste écosystème de partenaires préintégrés
    
### <a name="common-uses"></a>Utilisations courantes

- Encodage, stockage et diffusion en continu du contenu audio et vidéo à l’échelle
    
- Diffusion en continu en temps réel et VOD
    
- Gestion simplifiée de contenu vidéo
    
### <a name="key-storage-scenarios"></a>Principaux scénarios de stockage

- Gérer des vidéos
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((https://azure.microsoft.com/services/media-services/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/media-services/)).
  
## <a name="azure-redis-cache"></a>Cache Redis Azure

### <a name="features"></a>Fonctionnalités

- Serveur Redis sécurisé, dédié, haute disponibilité avec basculement et réplication de données gérés par Microsoft
    
- Recommandé pour toute application nécessitant un haut débit
    
- Disponible dans des tailles jusqu’à 530 Go et plus (avec partitionnement Premium et automatique)
    
- La persistance Redis conserve les données en mémoire cache sur stockage Azure
    
- Le clustering Redis vous permet d’atteindre un débit et une échelle maximaux
    
- Sécurité et isolement réseau améliorés avec prise en charge de réseau virtuel Azure
    
### <a name="common-uses"></a>Utilisations courantes

- Recherche inversée de données dans un service de stockage d’Azure, comme Cosmos DB et Azure SQL Database
    
- Contenu synchronisé à partir d’autres banques de données
    
### <a name="key-storage-scenarios"></a>Principaux scénarios de stockage

- Mettre en cache des données
    
- Courtier de messages pour applications à haut débit
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((http://azure.microsoft.com/services/cache/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/cache/)).
  
## <a name="sql-server-on-an-azure-vm"></a>SQL Server sur machine virtuelle Azure

### <a name="features"></a>Fonctionnalités

- SQL Server s’exécutant en tant qu’application installée sur une machine virtuelle Azure
    
- Utiliser une image de galerie avec SQL Server installé ou apporter votre propre licence SQL Server
    
### <a name="common-uses"></a>Utilisations courantes

- Gérer des données d’applications
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((http://azure.microsoft.com/services/virtual-machines/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/virtual-machines/)).
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>Fonctionnalités

- Stockage SAN hybride d’entreprise extensible avec SSD et HDD dans la baie de stockage hybride locale, avec stockage cloud en tant qu’extension intégrée de la solution
    
- Déduplication, compression, hiérarchisation automatique et chiffrement intégrés de données non structurées et semi-structurées
    
- Protection automatisée de données hors site à l’aide d’instantanés cloud
    
- Récupération d’urgence très efficace, indépendante de l’emplacement
    
- Mobilité des données d’entreprise avec dispositif virtuel StorSimple dans Azure
    
### <a name="common-uses"></a>Utilisations courantes

- Gérer la croissance des données liée aux partages de fichiers, archives et autres référentiels de données
    
- Protection et récupération d’urgence des données hors site pour partages de fichiers, machines virtuelles, SQL et SharePoint (à l’aide d’un stockage d’objets blob distants)
    
- Utiliser des instantanés cloud pour cloner des données dans Azure et améliorer la réactivité
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
- Collaborer
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((http://azure.microsoft.com/services/storsimple/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((http://azure.microsoft.com/pricing/details/storsimple/)).
  
## <a name="azure-sql-data-warehouse"></a>Azure SQL Data Warehouse

### <a name="features"></a>Fonctionnalités

- Entrepôt de données élastique qui se met à l'échelle de pétaoctets Jusqu'à 32 demandes simultanées
    
- Gérer de grands volumes de données structurées avec une analyse rapide Augmenter et réduire de façon dynamique, en quelques secondes, la capacité de calcul
    
- Prend en charge Transparent Data Encryption
    
- Sauvegarde toutes les 8 heures pendant 7 jours
    
### <a name="common-uses"></a>Utilisations courantes

- Rapports des ventes
    
- Rapports d’utilisation
    
- Nombreuses données
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((https://azure.microsoft.com/services/sql-data-warehouse/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((https://azure.microsoft.com/pricing/details/sql-data-warehouse/)).
  
## <a name="azure-data-lake-store"></a>Azure Data Lake Store

### <a name="features"></a>Fonctionnalités

- Référentiel hyperscale pour les charges de travail d’analyse du Big Data
    
- Système de fichiers HDFS pour le cloud
    
- Aucune limite fixe pour la taille des fichiers
    
- Aucune limite fixe pour la taille des comptes
    
- Données structurées et non structurées dans leur format d’origine
    
- Débit élevé pour augmenter les performances analytiques
    
- Grande durabilité, disponibilité et fiabilité (contrat de niveau de service de 99,9 % de qualité professionnelle et assistance 24 h/24, 7 j/7)
    
- Contrôle d’accès Azure Active Directory
    
### <a name="common-uses"></a>Utilisations courantes

- Référentiel à l’échelle de l’entreprise pour stocker chaque type de données collecté dans un même emplacement
    
### <a name="key-storage-scenarios"></a>Scénarios de stockage de clés

- Gérer des données
    
### <a name="resources"></a>Ressources

Pour plus d'informations, cliquez [ici]((https://azure.microsoft.com/services/data-lake-store/)).
  
Pour plus d'informations sur les coûts, cliquez [ici]((https://azure.microsoft.com/pricing/details/data-lake-store/)).
  
## <a name="next-step"></a>Étape suivante

Consultez les options de stockage cloud décrites dans l'article [Créer de A à Z](build-from-the-ground-up.md).
  
## <a name="see-also"></a>Voir aussi

[Stockage cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs]((https://sway.com/FJ2xsyWtkJc2taRD))



