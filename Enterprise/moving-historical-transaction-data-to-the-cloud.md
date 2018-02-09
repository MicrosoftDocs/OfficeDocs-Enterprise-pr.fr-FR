---
title: "Déplacement des données de transaction historiques dans le cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "Résumé : Comment Contoso a implémenté SQL Server Stretch Database pour réduire ses besoins en matière de stockage de données locales et ses dépenses quotidiennes de fonctionnement."
ms.openlocfilehash: 9d8d51aa1bc7a304d1148111aedd54916d9e8052
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>Déplacement des données de transaction historiques dans le cloud

 **Résumé :** Comment Contoso a implémenté SQL Server Stretch Database pour réduire ses besoins en matière de stockage de données locales et ses dépenses quotidiennes de fonctionnement.
  
Le système de stockage d'entreprise de Contoso stocke une grande quantité de données de transaction historiques pour garantir le respect des exigences réglementaires et réaliser des études marketing et analyses décisionnelles sur les tendances des dépenses. Contoso doit également restaurer les données archivées sur des bandes magnétiques, ce qui prend beaucoup de temps. La date de fin de vie utile du matériel utilisé dans le système de stockage d'entreprise de Contoso approchait, et son remplacement aurait eu un coût important. 
  
Dans la mesure où l'entreprise avait besoin de réduire la taille de ses centres de données locales, Contoso a choisi de procéder à la mise à niveau vers SQL Server 2016 en raison de la fonction hybride de Stretch Database et de son intégration transparente avec Azure. Stretch Database permet à Contoso de déplacer les données froides de ses tables depuis son emplacement de stockage local vers le cloud, pour libérer de l'espace disque local et réduire la maintenance. Les données froides et chaudes se trouvent dans les mêmes tables, peuvent toujours être utilisées par les applications et leurs utilisateurs, et restent disponibles pour les opérations de maintenance, telles que les sauvegardes et les restaurations. La figure 1 présente Stretch Database.
  
**Figure 1 : SQL Server Stretch Database**

![Stretch Database avec SQL Server comme solution de données hybride](images/Contoso_Poster/StretchDB01.png)
  
La figure 1 montre comment un client SQL envoie des requêtes T-SQL sur un serveur qui exécute SQL Server 2016, lequel les transfère vers Azure SQL Stretch Database dans Azure PaaS.
  
Pour plus d'informations, voir [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).
  
Contoso a suivi les étapes suivantes pour déplacer ses données historiques vers le cloud :
  
1. Analyse des bases de données
    
    A analysé les tables situées dans les bases de données qu'il prévoyait de transférer vers le cloud et a résolu tous les problèmes. Le nouveau gestionnaire de Stretch Database leur a présenté les fonctionnalités de SQL Server 2016, y compris les tables qui contiennent des données froides extensibles.
    
2. Mise à niveau
    
    A mis à niveau les serveurs SQL existants du centre de données de son siège social parisien vers SQL Server 2016.
    
3. Migration des données froides vers le cloud
    
    A identifié les bases de données à étendre et les tables à migrer vers des instances de Stretch Database dans Azure, à l'aide de SQL Management Studio. En arrière-plan, SQL Server 2016 a progressivement déplacé les données historiques vers Stretch Database dans Azure.
    
Voici la configuration finale d’un serveur exécutant SQL Server 2016 au siège social parisien.
  
**Figure 2 : Utilisation de Stretch Database pour un serveur situé dans le centre de données de Contoso**

![Configuration de Contoso pour Stretch Database avec SQL Server pour un ordinateur unique exécutant SQL Server](images/Contoso_Poster/StretchDB02.png)

  
La figure 2 montre comment les requêtes d’utilisateurs envoyées sur un serveur d’applications du centre de données de Contoso deviennent des requêtes SQL transmises à Azure SQL Stretch Database dans Azure PaaS.
  
Les utilisateurs ont accès aux données via les requêtes et les applications existantes. Les stratégies d'accès ne sont pas modifiées. Contoso n'aura plus besoin d'effectuer des sauvegardes sur bande par la suite. Les opérations de maintenance consisteront uniquement en la sauvegarde et la restauration des données chaudes.
  
Après l’implémentation de Stretch Database, Contoso a :
  
- réduit de 85 % ses besoins en matière de stockage de données locales ;
    
- mis à jour le système de stockage d’entreprise et a supprimé l’archivage des données sur bande magnétique ;
    
- réalisé d’importantes économies sur ses dépenses quotidiennes de fonctionnement.
    
## <a name="see-also"></a>Voir aussi

[Scénarios d'entreprise pour la société Contoso](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Feuille de route de Microsoft Enterprise Cloud : Ressources pour les décideurs informatiques](https://sway.com/FJ2xsyWtkJc2taRD)




