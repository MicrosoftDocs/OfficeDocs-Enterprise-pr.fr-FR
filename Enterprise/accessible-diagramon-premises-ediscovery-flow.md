---
title: "Diagramme accessible : Flux de découverte électronique local"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Cet article est une version texte accessible du diagramme nommé Flux eDiscovery local :"
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagramme accessible : Flux de découverte électronique local

**Résumé :** Cet article est une version texte accessible du diagramme nommé local eDiscovery flux.
  
Cette affiche fournit des détails sur l’architecture et le flux de données dans tous les produits de serveur. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>Sur SharePoint, Exchange, Lync et partages de fichiers

Le diagramme illustre un utilisateur qui envoie une requête qui accède à une batterie de serveurs SharePoint 2013 Services, une batterie de serveurs SharePoint 2013 Enterprise application et deux batteries de serveurs. La batterie de serveurs SharePoint 2013 Services communique avec une batterie de contenu SharePoint 2013, 2013 d’Exchange Server (qui communique avec Lync 2013) et les partages de fichiers Windows. 
  
La liste flux eDiscovery décrit le flux de données et l’ordre dans lequel se produisent les actions de requête eDiscovery au sein de SharePoint, Exchange, Lync et des partages de fichiers.  
  
La liste flux eDiscovery est tout d’abord décrite en détail, suivie d’une description détaillée des fonctionnalités illustrées dans le diagramme.  
  
### <a name="ediscovery-flow-list"></a>Liste flux eDiscovery

Les chiffres pour chacune des étapes décrites dans cette liste se rapportent à une étape illustrée dans le diagramme. Le diagramme est décrit en détail plus loin dans ce document.  
  
1. cas d’e-Discovery sont créés, gérés et utilisés dans le centre de l’e-Discovery (EDC). EDC est une collection de sites SharePoint 2013. Il s’agit d’où cas sont définis, sources de suivi sont identifiés, les requêtes sont émises, résultats de la requête sont passés en revue et contient du contenu est placé ou supprimés. 
    
2. La requête de découverte électronique ou d’une action, par exemple place un blocage, ReleaseHold ou GetStatus, est relayée EDC vers le proxy d’Application de Service de recherche (SSA) dans la batterie de serveurs Enterprise application. Le proxy SSA relaie ensuite le trafic à la SSA dans la batterie de serveurs de Services application. Dans cet exemple, la demande doit rien placer dans la batterie de serveurs de contenu de SharePoint avec « CONTOSO » dans le nom de fichier en attente. 
    
3. Si la demande consiste à rechercher un cas, la SSA consulte l’index de recherche. Ensuite, le résultat de requête eDiscovery défini est renvoyé à l’utilisateur par le biais de l’EDC.  
    
4. Si la demande est une action, par exemple place un blocage ou un ReleaseHold, qui est écrite dans la Actions_Table dans la base de données administration SSA. Dans cet exemple, une demande de suspension de quoi que ce soit dans la batterie de serveurs de contenu de SharePoint avec « CONTOSO » est écrite à la Actions_Table. 
    
5. À intervalles réguliers, le travail du minuteur de conservation inaltérable eDiscovery de la batterie de contenu est activé et génère une demande pour les actions en attente, puis envoie des mises à jour d’état via le proxy SSA à l’application de service de recherche.  
    
6. La requête pour les actions en attente est relayée à la SSA centrale, qui consulte le Action_Table pour les actions pour le contenu de la batterie de serveurs en attente. Le travail du minuteur suspension de place batterie contenu envoie également des mises à jour de statut pour les objets et les actions qu’il a reçus, lesquelles sont écrites dans le ActionsTable. 
    
7. La demande de suspension de tout contenu avec « CONTOSO » dans le nom de la batterie de serveurs SharePoint 2013 contenu est envoyée par la SSA pour le travail du minuteur eDiscovery blocage de place dans la batterie de serveurs de contenu. 
    
8. L’e-Discovery place Maintenez timer des lieux de travail du « Site CONTOSO » et « Contenu CONTOSO » sur Maintenez. 
    
9. Le travail du minuteur de conservation inaltérable eDiscovery s’exécute périodiquement dans la batterie d’applications Enterprise pour vérifier l’état des actions de détection et mettre l’état à jour.  
    
10. La requête d’état est relayée par le biais du proxy SSA de la batterie d’applications Enterprise à la SSA de la batterie des services SharePoint.  
    
11. La SSA récupère l’état de la table Actions et le renvoie au travail du minuteur dans la batterie des applications Enterprise, qui propose les mises à jour d’état à l’EDC.  
    
12. Lorsque l’utilisateur d’e-Discovery est recherche (ou effectuer une action) pour les sources de Exchange, tel qu’une boîte aux lettres ou les contenus archivés de Lync, la SSA centrale utilise des proxy Exchange Web Services (EWS) sur une requête Exchange Web Services. Exchange a sa propre infrastructure de recherche et d’e-Discovery et gère tous les appels d’e-Discovery en interne. 
    
13. Des services web Exchange répondent à la SSA avec des résultats de recherche eDiscovery ou une réponse à une demande d’état pour une conservation basée sur une requête, qui à son tour est relayée à l’EDC.  
    
#### <a name="prerequisites"></a>Conditions préalables

- La recherche de contenu d’entreprise SharePoint doit être configurée, des analyses de recherche sur les sources de contenu (SharePoint et partages de fichiers Windows) sont en cours d’exécution et l’ensemble des sources de contenu sont dans l’index.  
    
- L’approbation et l’authentification de serveur à serveur doivent être configurées entre la batterie de services SharePoint et Exchange et également entre Exchange et Lync.  
    
### <a name="description-of-components-in-the-diagram"></a>Description des composants du diagramme

Le diagramme illustre un utilisateur qui envoie une requête qui accède à deux batteries de serveurs, une batterie de serveurs SharePoint 2013 Enterprise application et d’une batterie de serveurs SharePoint 2013 Services. La batterie de serveurs SharePoint Services interfaces avec une batterie de contenu SharePoint 2013, 2013 d’Exchange Server (qui sert d’interface avec Lync 2013) et les partages de fichiers Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Batterie de serveurs SharePoint 2013 Enterprise application

La batterie de serveurs SharePoint 2013 Enterprise application contient les composants suivants : 
  
- EDC
    
- Proxy SSA  
    
- Travail du minuteur 
    
Une requête ou une action envoyée par l’utilisateur est envoyée à l’EDC dans la batterie d’applications Enterprise. Les actions suivantes se produisent :  
  
- La requête ou l’action accède au proxy SSA.  
    
- Le proxy SSA envoie une requête d’état ou une réponse au travail du minuteur dans la batterie d’applications Enterprise et il envoie également une requête d’état ou une réponse au service SSA dans la batterie de services SharePoint. Les actions qui en découlent sont décrites dans la section sur la batterie de services SharePoint.  
    
- Lorsqu’il reçoit une réponse, le travail du minuteur envoie la réponse au proxy SSA et à l’EDC.  
    
- Tous les résultats de la requête ou de l’action sont envoyés à l’utilisateur de l’EDC.  
    
#### <a name="sharepoint-2013-services-farm"></a>Batterie de serveurs SharePoint 2013 Services

La batterie de serveurs SharePoint 2013 Services contient les composants suivants : 
  
- Service SSA  
    
- Base de données de l’index de recherche  
    
- Base de données d’admin_db SSA. La Table des Actions dans cette base de données contient : maintenez le version maintenez GetStatus 
    
- Proxy EWS  
    
Lorsque le proxy SSA de la batterie d’applications Enterprise SharePoint envoie une requête d’état au SSA de la batterie de services SharePoint, les actions suivantes se produisent :  
  
- Si la demande est une requête, le SSA consulte l’index de recherche. La réponse de découverte est renvoyée au SSA, puis à l’utilisateur par le biais de l’EDC.  
    
- Si la demande est une action d’écriture, le service SSA envoie l’action d’écriture au SSAadmin_db.  
    
- Une analyse et répondre les résultats de la requête est envoyée à partir de la SSA à la batterie de serveurs SharePoint 2013 contenu et une réponse est renvoyée à la SSA. 
    
- Une demande d’analyse et de résultats est envoyée à partir du SSA aux partages de fichiers Windows et une réponse est renvoyée au SSA.  
    
- Une requête pour une ou plusieurs actions, réponses ou mises à jour d’état en attente est envoyée à partir du SSA vers le proxy SSA de la batterie de contenu SharePoint, et une réponse est renvoyée au SSA.  
    
- Une demande d’état/d’action Exchange est envoyée à partir du SSA vers le proxy EWS, qui envoie une demande d’état/d’action Exchange au Service web Exchange sur le serveur Exchange 2013.   
    
- Une requête/réponse d’état est envoyée à partir du SSA au SSA admin_db et est renvoyé au SSA.  
    
- Une requête/réponse d’action en attente est envoyée à partir du SSA au SSA admin_db et est renvoyée au SSA.  
    
#### <a name="sharepoint-2013-content-farm"></a>Batterie de contenu SharePoint 2013

La batterie de serveurs SharePoint 2013 contenu contient les composants suivants : 
  
- Proxy SSA  
    
- Travail du minuteur 
    
- Site SharePoint Contoso  
    
- Contenu SharePoint Contoso  
    
Lorsque le  SSA de la batterie de services SharePoint envoie une requête d’état au proxy SSA de la batterie de contenu SharePoint, les actions suivantes se produisent :  
  
- Le proxy SSA de la batterie de contenu SharePoint envoie une requête pour la réponse d’actions/d’états en attente pour le travail du minuteur.  
    
- Le travail du minuteur envoie une demande au site SharePoint Contoso, qui examine le contenu de SharePoint Contoso.  
    
- La réponse à la requête d’actions/d’état en attente est envoyée à partir du travail du minuteur vers le proxy SSA de la batterie de contenu SharePoint et elle est ensuite envoyée au service SSA de la batterie de services SharePoint  
    
#### <a name="exchange-2013"></a>Exchange 2013

Le composant de serveur Exchange 2013 contient le service web Exchange et fournit les éléments suivants :  
  
- Serveur approbation/OAuth est gérée entre la batterie de serveurs SharePoint 2013 contenu et Exchange 2013. 
    
- L’approbation de serveur à serveur/OAuth est gérée entre Exchange 2013 et Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

Le composant de Lync 2013 archive le contenu Lync dans Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Partages de fichiers Windows

Le composant de partages de fichiers Windows fournit les résultats d’analyse pour le SSA de la batterie de services SharePoint.  
  
### <a name="legend"></a>Légende

La légende pour ce diagramme représente graphiquement les différents types de trafic décrits parmi les composants à l’aide de lignes de couleur comme suit :  
  
- Ligne bleue de lumière : requête/action - données de requête ou action e-Discovery 
    
- Ligne orange : réponse d’eDisovery - données de réponse de requête eDiscovery 
    
- Vert ligne : requête/réponse d’état : données de requête et la réponse d’état e-Discovery 
    
- Violet de ligne : demande d’échange et l’état de l’action - demande d’e-Discovery pour l’état de l’action pour le trafic de Exchange. 
    
- Ligne rouge : échange de réponse de données et l’état - réponse de statut ou de la requête e-Discovery à partir d’Exchange. 
    
- Ligne noire en pointillés : Approbation de serveur à serveur/Oauth  
    
- Ligne noire continue : Analyse/résultats  
    

