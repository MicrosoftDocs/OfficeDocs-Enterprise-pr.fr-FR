---
title: 'Diagramme accessible : Flux de découverte électronique local'
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
description: 'Cet article est une version texte accessible du diagramme nommé Flux eDiscovery local :'
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487700"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagramme accessible : Flux de découverte électronique local

**Résumé:** Cet article est une version texte accessible du diagramme, appelé flux de découverte électronique local.
  
Cette affiche fournit des détails sur l’architecture et le flux de données dans tous les produits de serveur. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>Sur SharePoint, Exchange, Lync et partages de fichiers

Le diagramme montre un utilisateur envoyant une requête qui accède à deux batteries de serveurs, une batterie d'applications SharePoint 2013 Enterprise et une batterie de services SharePoint 2013. La batterie de services SharePoint 2013 communique avec une batterie de serveurs de contenu SharePoint 2013, Exchange Server 2013 (qui communique avec Lync 2013) et les partages de fichiers Windows. 
  
La liste flux eDiscovery décrit le flux de données et l’ordre dans lequel se produisent les actions de requête eDiscovery au sein de SharePoint, Exchange, Lync et des partages de fichiers.  
  
La liste flux eDiscovery est tout d’abord décrite en détail, suivie d’une description détaillée des fonctionnalités illustrées dans le diagramme.  
  
### <a name="ediscovery-flow-list"></a>Liste flux eDiscovery

Les chiffres pour chacune des étapes décrites dans cette liste se rapportent à une étape illustrée dans le diagramme. Le diagramme est décrit en détail plus loin dans ce document.  
  
1. Les cas eDiscovery sont créés, gérés et utilisés dans le centre eDiscovery (EDC). L'EDC est une collection de sites SharePoint 2013. C’est à cet endroit que les cas sont définis, les sources devant être suivies identifiées, les requêtes émises, les résultats des requêtes examinés et les conservations de contenu placées ou supprimées. 
    
2. La requête ou l’action eDiscovery (Hold, ReleaseHold, ou GetStatus) est relayée de l’EDC au proxy de l’application Service de recherche (SSA) dans la batterie d’applications Entreprise. Le proxy SSA transmet ensuite le trafic à l’application de service de recherche (SSA) dans la batterie des applications de services. Dans cet exemple, la demande doit placer tout élément dans la batterie de serveurs de contenu SharePoint avec «CONTOSO» dans le nom de fichier en conservation. 
    
3. Si la demande consiste à rechercher un cas, la SSA consulte l’index de recherche. Ensuite, le résultat de requête eDiscovery défini est renvoyé à l’utilisateur par le biais de l’EDC.  
    
4. Si la demande est une action (insérer une action Hold ou ReleaseHold, par exemple), cette action est écrite dans Actions_Table dans la base de données administrative SSA. Dans cet exemple, une demande de conservation pour tout élément de la batterie de contenu SharePoint avec «CONTOSO» est écrite dans le Actions_Table. 
    
5. À intervalles réguliers, le travail du minuteur de conservation inaltérable eDiscovery de la batterie de contenu est activé et génère une demande pour les actions en attente, puis envoie des mises à jour d’état via le proxy SSA à l’application de service de recherche. 
    
6. La requête pour les actions en attente est transmise à la SSA centrale, qui consulte Action_Table pour connaître les actions en attente pour la batterie de contenu. Le travail du minuteur de conservation inaltérable de la batterie de contenu envoie également des mises à jour d’état pour les objets et les actions qu’il a reçus, qui sont écrits dans ActionsTable. 
    
7. La demande de blocage de tout contenu avec «CONTOSO» dans le nom de la batterie de contenu SharePoint 2013 est envoyée par la SSA au travail du minuteur de conservation inaltérable eDiscovery dans la batterie de contenu. 
    
8. Le travail du minuteur de conservation inaltérable eDiscovery place le «site CONTOSO» et le «contenu CONTOSO» en conservation. 
    
9. Le travail du minuteur de conservation inaltérable eDiscovery s’exécute périodiquement dans la batterie d’applications Enterprise pour vérifier l’état des actions de détection et mettre l’état à jour.  
    
10. La requête d’état est relayée par le biais du proxy SSA de la batterie d’applications Enterprise à la SSA de la batterie des services SharePoint.  
    
11. La SSA récupère l’état de la table Actions et le renvoie au travail du minuteur dans la batterie des applications Enterprise, qui propose les mises à jour d’état à l’EDC. 
    
12. Lorsque l’utilisateur eDiscovery recherche (ou effectue une action sur) des sources Exchange (boîte aux lettres ou contenu Lync archivé, par exemple), la SSA centrale utilise le proxy des services web Exchange (EWS) pour interroger des services web Exchange. Exchange possède sa propre infrastructure eDiscovery et de recherche et gère tous les appels eDiscovery en interne. 
    
13. Des services web Exchange répondent à la SSA avec des résultats de recherche eDiscovery ou une réponse à une demande d’état pour une conservation basée sur une requête, qui à son tour est relayée à l’EDC.  
    
#### <a name="prerequisites"></a>Conditions requises

- La recherche de contenu d’entreprise SharePoint doit être configurée, des analyses de recherche sur les sources de contenu (SharePoint et partages de fichiers Windows) sont en cours d’exécution et l’ensemble des sources de contenu sont dans l’index.  
    
- L’approbation et l’authentification de serveur à serveur doivent être configurées entre la batterie de services SharePoint et Exchange et également entre Exchange et Lync.  
    
### <a name="description-of-components-in-the-diagram"></a>Description des composants du diagramme

Le diagramme montre un utilisateur envoyant une requête, qui accède à deux batteries de serveurs, une batterie d'applications SharePoint 2013 Enterprise et une batterie de services SharePoint 2013. La batterie de serveurs SharePoint Services est dotée d'une batterie de serveurs de contenu SharePoint 2013, d'Exchange Server 2013 (qui est une interface avec Lync 2013) et de partages de fichiers Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Batterie de serveurs SharePoint 2013 Enterprise App

La batterie de serveurs SharePoint 2013 Enterprise App contient les composants suivants: 
  
- EDC
    
- Proxy SSA  
    
- Travail du minuteur 
    
Une requête ou une action envoyée par l’utilisateur est envoyée à l’EDC dans la batterie d’applications Enterprise. Les actions suivantes se produisent :  
  
- La requête ou l’action accède au proxy SSA.  
    
- Le proxy SSA envoie une requête d’état ou une réponse au travail du minuteur dans la batterie d’applications Enterprise et il envoie également une requête d’état ou une réponse au service SSA dans la batterie de services SharePoint. Les actions qui en découlent sont décrites dans la section sur la batterie de services SharePoint.  
    
- Lorsqu’il reçoit une réponse, le travail du minuteur envoie la réponse au proxy SSA et à l’EDC.  
    
- Tous les résultats de la requête ou de l’action sont envoyés à l’utilisateur de l’EDC.  
    
#### <a name="sharepoint-2013-services-farm"></a>Batterie de services SharePoint 2013

La batterie de services SharePoint 2013 contient les composants suivants: 
  
- Service SSA  
    
- Base de données de l’index de recherche 
    
- Base de données SSA admin_db. Le tableau d’actions dans cette base de données contient : Hold Release Hold GetStatus 
    
- Proxy EWS  
    
Lorsque le proxy SSA de la batterie d’applications Enterprise SharePoint envoie une requête d’état au SSA de la batterie de services SharePoint, les actions suivantes se produisent :  
  
- Si la demande est une requête, le SSA consulte l’index de recherche. La réponse de découverte est renvoyée au SSA, puis à l’utilisateur par le biais de l’EDC.  
    
- Si la demande est une action d’écriture, le service SSA envoie l’action d’écriture au SSAadmin_db.  
    
- Une demande d'analyse et de résultats de réponse est envoyée de la SSA à la batterie de contenu SharePoint 2013 et une réponse est renvoyée au SSA. 
    
- Une demande d’analyse et de résultats est envoyée à partir du SSA aux partages de fichiers Windows et une réponse est renvoyée au SSA.  
    
- Une requête pour une ou plusieurs actions, réponses ou mises à jour d’état en attente est envoyée à partir du SSA vers le proxy SSA de la batterie de contenu SharePoint, et une réponse est renvoyée au SSA.  
    
- Une demande d’état/d’action Exchange est envoyée à partir du SSA vers le proxy EWS, qui envoie une demande d’état/d’action Exchange au Service web Exchange sur le serveur Exchange 2013.   
    
- Une requête/réponse d’état est envoyée à partir du SSA au SSA admin_db et est renvoyé au SSA.  
    
- Une requête/réponse d’action en attente est envoyée à partir du SSA au SSA admin_db et est renvoyée au SSA.  
    
#### <a name="sharepoint-2013-content-farm"></a>Batterie de contenu SharePoint 2013

La batterie de contenu SharePoint 2013 contient les composants suivants: 
  
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
  
- L'approbation de serveur à serveur/OAuth est gérée entre la batterie de contenu SharePoint 2013 et Exchange 2013. 
    
- L’approbation de serveur à serveur/OAuth est gérée entre Exchange 2013 et Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

Le composant de Lync 2013 archive le contenu Lync dans Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Partages de fichiers Windows

Le composant de partages de fichiers Windows fournit les résultats d’analyse pour le SSA de la batterie de services SharePoint.  
  
### <a name="legend"></a>Légende

La légende pour ce diagramme représente graphiquement les différents types de trafic décrits parmi les composants à l’aide de lignes de couleur comme suit :  
  
- Ligne bleu clair: requête/action-requête eDiscovery ou données d'action 
    
- Ligne orange: réponse eDisovery-données de réponse à la requête eDiscovery 
    
- Ligne verte: état requête/réponse-État eDiscovery requête/réponse données 
    
- Ligne violette: demande d'état/d'action Exchange-demande eDiscovery pour l'état de l'action pour le trafic Exchange. 
    
- Ligne rouge: réponse d'état/de données Exchange-requête eDiscovery ou réponse d'État à partir d'Exchange. 
    
- Ligne noire en pointillés : Approbation de serveur à serveur/Oauth  
    
- Ligne noire continue : Analyse/résultats  
    

