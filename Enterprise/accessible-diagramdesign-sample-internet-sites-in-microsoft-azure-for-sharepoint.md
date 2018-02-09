---
title: Exemple de conception accessible diagramme - sites Internet de Microsoft Azure pour SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Cet article est une version texte accessible du diagramme nommé Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013"
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramme accessible : Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013

**Résumé :** Cet article est une version texte accessible du diagramme exemple de conception : sites Internet de Microsoft Azure pour SharePoint 2013.
  
Utilisez cet exemple de conception comme point de départ pour un site Internet orienté dans Azure à l’aide de SharePoint 2013.
  
Cet affichage montre un exemple de la façon de concevoir les aspects suivants de SharePoint 2013 :
  
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
  
- Les clients anonymes, les clients anonymes ont accès à un site par exemple http://www.contoso.com. La zone qu’ils utilisent est la « zone Internet / anonyme », qui utilise l’authentification anonyme.
    
- Authentification des clients : les clients authentifiés ont accès à un site par exemple https://secure.contoso.com. La zone qu’ils utilisent est la « zone Extranet / SAML », qui utilise Azure Active Directory avec l’authentification SAML.
    
- Les auteurs et les développeurs de site, les auteurs de Site et les développeurs ont accès à des sites tels que http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. La zone qu’ils utilisent est la « zone par défaut / Windows intégrée », qui utilise les Services de domaine Active Directory (AD DS).
    
- Recherche un compte d’analyse — Le compte d’analyse recherche a accès via les sites tels que http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. La zone qu’il utilise est la « zone par défaut / Windows intégrée », qui utilise les services AD DS avec une authentification Windows NTLM.
    
## <a name="server-farm"></a>Batterie de serveurs

Les utilisateurs accèdent à la batterie de serveurs via Azure. La batterie de serveurs contient un ou plusieurs serveurs web.
  
## <a name="administration-site"></a>Site d’administration

Le site d’administration contient plusieurs serveurs d’applications, qui communiquent avec un pool d’applications (Pool d’applications 1 dans l’exemple) qui utilise l’application web Central Administration Site. L’application Central Administration Site permet d’accéder aux collections de sites au sein de l’organisation.
  
Le site d’administration contient également des serveurs de base de données SQL, qui sont des serveurs de base de données sur lesquels SQL Server est installé et configuré pour prendre en charge le clustering, la mise en miroir ou la disponibilité AlwaysOn de SQL (AlwaysOn s’applique à SQL Server 2012 uniquement).
  
## <a name="services"></a>Services

L’exemple de conception présente un site web de Services Internet (IIS), Services web SharePoint. Le site Services web SharePoint contient un pool d’applications (pools d’applications 2) avec trois services : profil utilisateur, recherche et métadonnées gérées.
  
Remarques sur les Services pour les sites Internet :
  
> Métadonnées gérées — Veillez à sélectionner **cette application de service est l’emplacement de stockage par défaut pour les ensembles de termes spécifiques des colonnes**.
    
> Gestion des applications — Nous ne recommandons pas d’utiliser des applications dans un site Internet destiné au public dans Azure.
    
## <a name="application-pools-and-web-applications"></a>Pools d’applications et applications web

Le groupe par défaut dans Azure montre le pool d’applications 3, qui contient une application web nommée Contoso Sites. Cette collection de sites basés sur des chemins d’accès est disponible à l’adresse http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Collections de site et sites

Les collections de sites contenues dans le pool d’applications sont les suivantes :
  
- Collection de sites nommée par l’hôte 1 pour l’analyse (emplacement de l’exemple http://authoring.contoso.com:8000)
    
- Collection de sites nommée par l’hôte 2 pour les requêtes (emplacement des exemples http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)
    
- Collection de sites nommée par l’hôte 3 pour les requêtes (emplacement des exemples http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bases de données de contenu

L’exemple montre deux bases de données de contenu. L’une correspond à la collection de sites 1 utilisée pour l’analyse (http://authoring.contoso.com:8000). L’autre correspond aux deux collections de sites 2 et 3 utilisées pour les requêtes (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 ou http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Zones et URL

L’exemple montre les trois zones avec les URL à charge équilibrée associées qui sont utilisées par différents comptes utilisateurs.  
  
La première liste de zones et d’URL est liée à la collection de sites 1 et elle contient les informations suivantes :
  
- Utilisateurs - les auteurs de Site
    
- Zone - par défaut
    
- URL avec équilibrage de charge - http://authoring.contoso.com:8000
    
La seconde liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 2 et elle contient les informations suivantes :
  
Première zone :
  
- Utilisateurs - les auteurs de Site
    
- Zone - par défaut
    
- URL avec équilibrage de charge - http://www.contoso.com:8000
    
Deuxième zone :
  
- Utilisateurs - clients anonymes
    
- Zone - Internet
    
- URL - à charge équilibrée http://www.contoso.com
    
Troisième zone :
  
- Utilisateurs - clients authentifiés
    
- Zone - Extranet
    
- Équilibrage de charge URL - https://secure.contoso.com
    
La troisième liste de zones et d’URL comporte trois types différents d’utilisateurs dans trois zones différentes. Elle est liée à la collection de sites 3 et elle contient les informations suivantes :
  
Première zone :
  
- Utilisateurs - les auteurs de Site
    
- Zone - Internet
    
- URL avec équilibrage de charge - http://assets.contoso.com:8000
    
Deuxième zone :
  
- Utilisateurs - clients anonymes
    
- Zone - Internet
    
- Équilibrage de charge URL - http://assets.contoso.com
    
Troisième zone :
  
- Utilisateurs - clients authentifiés
    
- Zone - Extranet
    
- Équilibrage de charge URL - http://secureassets.contoso.com
    

