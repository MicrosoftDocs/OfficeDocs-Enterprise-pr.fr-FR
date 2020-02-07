---
title: Diagramme accessible-exemple de conception de sites Internet dans Microsoft Azure pour SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
f1.keywords:
- NOCSH
description: 'Cet article est une version texte accessible du diagramme nommé Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013'
ms.openlocfilehash: b3669304fee6b7a89bc5d1bde96c39c496122d48
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843795"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramme accessible : Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013

**Résumé :** Cet article est une version texte accessible du diagramme nommé exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013.
  
Utilisez cet exemple de conception comme point de départ pour un site accessible sur Internet dans Azure à l’aide de SharePoint 2013.
  
Cette affiche montre un exemple de la façon de concevoir les aspects suivants de SharePoint 2013 :
  
- Utilisateurs
    
- Zones et authentification
    
- Batterie de serveurs
    
- Site d’administration
    
- Services
    
- Pools d’applications et applications web
    
- Collections de sites
    
- Sites
    
- Bases de données de contenu
    
- Zones et URL
    
## <a name="users-zones-and-authentication"></a>Utilisateurs, zones et authentification

Il existe quatre types de comptes utilisateur dans cette conception. Chaque type de compte est associé à un site d’accès et à une zone qui utilise un type spécifique d’authentification.  
  
- Clients anonymes : les clients anonymes ont accès à un https://www.contoso.comsite tel que. La zone utilisée est la « zone Internet/anonyme » qui utilise l’authentification anonyme.
    
- Clients authentifiés : les clients authentifiés ont accès à un site tel https://secure.contoso.comque. La zone utilisée est la « zone extranet/SAML » qui utilise Azure Active Directory avec l’authentification SAML.
    
- Auteurs de site et développeurs : les auteurs de site et les développeurs ont accès https://authoring.contoso.com:8000 à https://www.contoso.com:8000des sites tels que ou. La zone utilisée est la « zone par défaut/intégrée à Windows », qui utilise les services de domaine Active Directory (AD DS).
    
- Compte d’analyse de recherche : le compte d’analyse de recherche a accès https://authoring.contoso.com:8000 par https://www.contoso.com:8000le biais de sites tels que ou. La zone qu’il utilise est la « zone par défaut/intégrée à Windows », qui utilise les services AD DS avec l’authentification Windows NTLM.
    
## <a name="server-farm"></a>Batterie de serveurs

Les utilisateurs accèdent à la batterie de serveurs via Azure. La batterie de serveurs contient un ou plusieurs serveurs web.
  
## <a name="administration-site"></a>Site d’administration

Le site d’administration contient plusieurs serveurs d’applications, qui communiquent avec un pool d’applications (Pool d’applications 1 dans l’exemple) qui utilise l’application web Central Administration Site. L’application Central Administration Site permet d’accéder aux collections de sites au sein de l’organisation.
  
Le site d’administration contient également des serveurs de base de données SQL, qui sont des serveurs de base de données sur lesquels SQL Server est installé et configuré pour prendre en charge le clustering, la mise en miroir ou la disponibilité AlwaysOn de SQL (AlwaysOn s’applique à SQL Server 2012 uniquement).
  
## <a name="services"></a>Services

L’exemple de conception présente un site web de Services Internet (IIS), Services web SharePoint. Le site Services web SharePoint contient un pool d’applications (pools d’applications 2) avec trois services : profil utilisateur, recherche et métadonnées gérées.
  
Remarques sur les Services pour les sites Internet :
  
> Métadonnées gérées — Veillez à sélectionner **Cette application de service est l’emplacement de stockage par défaut pour les ensembles de termes propres aux colonnes**.
    
> Gestion des applications — Nous ne recommandons pas d’utiliser des applications dans un site Internet destiné au public dans Azure.
    
## <a name="application-pools-and-web-applications"></a>Pools d’applications et applications web

Le groupe par défaut dans Azure montre le pool d’applications 3, qui contient une application web nommée Contoso Sites. Cette collection de sites basée sur le chemin d' https://internal:8000accès se trouve à l’adresse.
  
## <a name="site-collections-and-sites"></a>Collections de site et sites

Les collections de sites contenues dans le pool d’applications sont les suivantes :
  
- Collection de sites nommée par l’hôte 1 pour l’analyse (exemple d’emplacementhttps://authoring.contoso.com:8000)
    
- Collection de sites nommée par l’hôte 2 pour les requêtes https://www.contoso.com( https://secure.contoso.comemplacements d’exemple,,https://www.contoso.com:8000)
    
- Collection de sites nommée par l’hôte 3 pour les requêtes https://assets.contoso.com( https://secureassets.contoso.comemplacements d’exemple,,https://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bases de données de contenu

L’exemple montre deux bases de données de contenu. La première concerne la collection de sites 1 utilisée pour l’analysehttps://authoring.contoso.com:8000)(. L’autre est pour les deux collections de sites 2 et 3 utilisées pour leshttps://www.contoso.comrequêtes https://secure.contoso.com( https://www.contoso.com:8000,, https://assets.contoso.com, https://secureassets.contoso.comou https://assets.contoso.com:8000),,.
  
## <a name="zones-and-urls"></a>Zones et URL

L’exemple montre les trois zones avec les URL à charge équilibrée associées qui sont utilisées par différents comptes utilisateurs.  
  
La première liste de zones et d’URL est liée à la collection de sites 1 et elle contient les informations suivantes :
  
- Utilisateurs-auteurs de site
    
- Zone-valeur par défaut
    
- URL à charge équilibrée-https://authoring.contoso.com:8000
    
La seconde liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 2 et elle contient les informations suivantes :
  
Première zone :
  
- Utilisateurs-auteurs de site
    
- Zone-valeur par défaut
    
- URL à charge équilibrée-https://www.contoso.com:8000
    
Deuxième zone :
  
- Utilisateurs-clients anonymes
    
- Zone-Internet
    
- URL à charge équilibrée-https://www.contoso.com
    
Troisième zone :
  
- Utilisateurs authentifiés
    
- Zone-extranet
    
- URL à charge équilibrée-https://secure.contoso.com
    
La troisième liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 3 et elle contient les informations suivantes :
  
Première zone :
  
- Utilisateurs-auteurs de site
    
- Zone-Internet
    
- URL à charge équilibrée-https://assets.contoso.com:8000
    
Deuxième zone :
  
- Utilisateurs-clients anonymes
    
- Zone-Internet
    
- URL à charge équilibrée-https://assets.contoso.com
    
Troisième zone :
  
- Utilisateurs authentifiés
    
- Zone-extranet
    
- URL à charge équilibrée-https://secureassets.contoso.com
    

