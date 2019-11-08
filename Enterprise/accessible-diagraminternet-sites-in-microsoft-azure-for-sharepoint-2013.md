---
title: 'Diagramme accessible : sites Internet dans Microsoft Azure pour SharePoint 2013'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: Cet article est une version texte accessible du diagramme Sites Internet dans Microsoft Azure pour SharePoint 2013.
ms.openlocfilehash: cf978dfb95b1f201c342889fc3dda428bb618241
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028058"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramme accessible : sites Internet dans Microsoft Azure pour SharePoint 2013

**Résumé :** Cet article est une version texte accessible du diagramme intitulé sites Internet dans Microsoft Azure pour SharePoint 2013.
  
Cette affiche décrit et illustre la façon dont les sites Internet publics bénéficient de la flexibilité du cloud et d’Azure AD pour les comptes clients. Il existe six différents scénarios qui décrivent comment les sites Internet bénéficient d’Azure :  
  
- Conception et redimensionnement de la topologie de la batterie de serveurs.  
    
- Ajustement pour Azure.  
    
- Choix du modèle Active Directory.  
    
- Conception de la gestion des identités, des zones et de l’authentification.  
    
- Conception des sites et des URL pour la publication intersites.  
    
- Conception de l’environnement Azure.  
    
## <a name="design-and-size-the-farm-topology"></a>Conception et redimensionnement de la topologie de la batterie de serveurs

Utilisez les conseils de topologie, de capacité et de performances pour SharePoint 2013 sur TechNet pour concevoir la topologie de la batterie de serveurs. 
  
Assurez-vous que la batterie que vous concevez répond aux objectifs de capacité et de performance.  
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Exemple : Batterie de serveurs de sites Internet de taille moyenne (environ 85 pages consultées par seconde)

Cette batterie de serveurs fournit une topologie de batterie de serveurs de recherche SharePoint 2013 tolérante aux pannes qui est optimisée pour un corpus contenant 3,4 millions éléments. 
  
L’exemple de batterie de serveurs traite 100-200 documents par seconde, en fonction de la langue, et il prend en charge les vues de page 85 par seconde et les requêtes 100 par seconde. 
  
Le diagramme associé présente une batterie de serveurs de sites Internet de taille moyenne avec trois types de serveurs :  
  
- Serveurs web 
    
- Serveurs d’applications 
    
- Serveurs de base de données 
    
#### <a name="web-servers"></a>Serveurs Web

La section des serveurs web contient trois serveurs web : Hôte A, Hôte B et Hôte C. Chaque serveur web possède un cache distribué, des profils utilisateur, des métadonnées gérées et des capacités de traitement de requêtes. Ils possèdent également une copie de partition d’index résidant sur chaque serveur.   
  
Pour monter en charge, ajoutez un serveur web supplémentaire avec les mêmes fonctionnalités pour permettre 28 affichages de pages supplémentaires par seconde.  
  
#### <a name="application-servers"></a>Serveurs d’applications

La section des serveurs d’applications contient trois serveurs d’applications : Hôte D, Hôte E et Hôte F. L’hôte D possède les composants de traitement Analyse, Admin, Analytics et Contenu. L’hôte E possède les composants de traitement Analyse, Admin et Contenu. L’hôte F possède les composants de traitement Analyse et Contenu.  
  
Pour monter en charge, procédez comme suit : ajoutez un serveur d’applications avec un composant d’analyse et un composant de traitement du contenu pour traiter 40 documents supplémentaires par seconde.  
  
#### <a name="database-servers"></a>Serveurs de base de données

La section des serveurs de base de données contient deux serveurs : Hôte G et Hôte H. Les serveurs de base de données sont des hôtes jumelés pour la tolérance de panne.  
  
L’hôte G contient toutes les bases de données SharePoint, notamment la base de données d’administration de la recherche, la base de données de liens, deux bases de données d’analyse, la base de données analytique et toutes les autres bases de données SharePoint. L’hôte H contient toutes les bases de données SharePoint, notamment les copies redondantes de toutes les bases de données utilisant le clustering SQL, la mise en miroir ou SQL Server 2012 AlwaysOn.  
  
## <a name="fine-tune-for-azure"></a>Ajustement pour Azure

La batterie de serveurs SharePoint a peut-être besoin d’être ajustée pour des groupes à haute disponibilité dans la plateforme Azure. Pour assurer la haute disponibilité de tous les composants, assurez-vous que les rôles serveur sont configurés de manière identique.    
  
Dans la topologie exemple du diagramme :  
  
- Les serveurs web et les serveurs de base de données sont configurés de manière identique.  
    
- Les trois serveurs d’applications ne sont pas configurés de manière identique. Ces rôles serveur exigent un ajustement pour les groupes à haute disponibilité dans Azure.    
    
### <a name="before"></a>Avant

La partie supérieure du diagramme représente la batterie de serveurs SharePoint avant qu’elle ait été ajustée pour des groupes à haute disponibilité dans Azure. Dans le diagramme, les trois serveurs d’applications hôtes ne sont pas configurés de manière identique. Le nombre de composants est déterminé par les objectifs de capacité et de performance établis pour la batterie de serveurs. Les trois serveurs sont configurés comme suit :  
  
- Le serveur d’applications Hôte D est configuré avec les rôles Analyse, Admin, Analytics et Traitement du contenu.  
    
- Le serveur d’applications Hôte E est configuré avec les rôles Analyse, Admin et Traitement du contenu.  
    
- Le serveur d’applications Hôte F est configuré avec les rôles Analyse et Traitement du contenu.  
    
### <a name="after"></a>Après

Cette partie du diagramme représente la batterie de serveurs SharePoint après qu’elle a été ajustée pour les groupes à haute disponibilité dans Azure. Pour adapter cette architecture à Azure, nous allons répliquer quatre composants sur les trois serveurs. Ceci augmente le nombre de composants au-delà de ce qui est nécessaire pour atteindre les objectifs de performances et de capacité. En échange, cette conception garantit la haute disponibilité des quatre composants dans la plateforme Azure lorsque ces trois machines virtuelles sont affectées à un groupe à haute disponibilité. 
  
Les trois serveurs sont configurés pour posséder tous les rôles Analyse, Admin, Analytics et Traitement du contenu.  
  
## <a name="choose-the-active-directory-model"></a>Choix du modèle Active Directory

Toutes les solutions SharePoint nécessitent les services de domaine Active Directory. À ce stade, il existe deux options pour les solutions SharePoint dans Azure.   
  
- Option 1 : domaine dédié : vous pouvez déployer un domaine dédié et isolé vers Azure pour prendre en charge une batterie de serveurs SharePoint. Il s'agit d'un bon choix pour les sites Internet destinés au public. 
    
- Option 2 : étendre le domaine local via une connexion VPN de site à site. Lorsque vous étendez le domaine local via une connexion VPN de site à site, les utilisateurs accèdent à la batterie de serveurs SharePoint comme si elle était hébergée localement. Vous pouvez tirer parti de votre implémentation Active Directory et DNS existante. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Conception de la gestion des identités, des zones et de l’authentification

### <a name="design-for-accounts-and-authentication"></a>Conception des comptes et de l’authentification

Déterminez de quelle façon les comptes seront gérés et le type d’authentification qui sera utilisé.  
  
#### <a name="accounts-for-site-developers-and-authors"></a>Comptes pour développeurs et auteurs de sites

- Ajoutez des comptes au domaine dans Azure.  
    
- Utilisez les services ADFS (Active Directory Federation Services)  localement pour fédérer les comptes internes dans le domaine sur Azure.  
    
- Si la conception comprend une connexion VPN de site à site, utilisez les comptes internes.  
    
#### <a name="accounts-for-customers"></a>Comptes pour les clients

- Utilisez Azure Active Directory.  
    
- Utilisez un autre fournisseur SAML.  
    
### <a name="design-for-zones"></a>Conception de zones

Dans SharePoint 2013, la gestion des identités est prise en compte dans la configuration des zones et de l’authentification.  
  
Cette conception fournit une séparation claire entre les comptes clients et tous les autres comptes.  
  
- Utilisez cette conception si vous souhaitez que les comptes clients soient traités de manière entièrement différente des comptes internes pour les auteurs et les développeurs de sites.  
    
- Grâce à cette conception, vous pouvez utiliser des stratégies de zones pour limiter les actions des utilisateurs dans une application web.  
    
- Cette conception se traduit par une URL différente pour les comptes client et interne.  
    
Dans cet exemple : 
  
- Configurez la zone par défaut pour vos comptes internes.  
    
- Configurez la zone extranet pour l’accès client authentifié. Utilisez Azure Active Directory (AD) pour les comptes clients ou utilisez un autre fournisseur SAML.  
    
- Configurez la zone Internet pour un accès anonyme.   
    
N’utilisez pas de conception à deux zones dans laquelle tous les utilisateurs authentifiés sont configurés pour utiliser la zone par défaut. 
  
Le diagramme associé représente une conception en trois zones dans laquelle les comptes internes et clients sont séparés.   
  
Les visiteurs et les clients accèdent au client Azure AD dans la batterie de serveurs SharePoint 2013 par le biais d’applications Web dans l’une des deux zones. Les deux zones sont les suivantes : 
  
- Zone : Internet pour les utilisateurs anonymes  
    
- Zone : Extranet pour les utilisateurs authentifiés  
    
Les utilisateurs disposant de comptes internes accèdent au locataire Azure Active Directory à partir de AD DS et AD FS dans l’environnement local via le tunnel VPN vers Azure AD. La zone par défaut fournit l’authentification Windows (NTLM).  
  
### <a name="design-for-connecting-to-azure-ad"></a>Conception de connexion à Azure AD

 Azure AD offre des fonctionnalités de gestion des identités et de contrôle d’accès pour les services dans le nuage. Les fonctionnalités comprennent un magasin cloud pour les données d’annuaire et un ensemble principal de services d’identité, incluant des processus d’ouverture de session, des services d’authentification et des services AD FS. Les services d’identité qui sont inclus avec Azure AD s’intègrent facilement à vos déploiements AD DS locaux et prennent entièrement en charge les fournisseurs d’identité tiers. 
  
Le diagramme associé présente le scénario suivant :  
  
Lors de l’intégration de SharePoint 2013 à Azure Active Directory, un service de contrôle d’accès Azure (ACS) a deux objectifs : 
  
-   Azure AD utilise SAML 2.0 et SharePoint fonctionne uniquement avec SAML 1.1. ACS comprend les deux formats et fait office d’intermédiaire pour transformer les formats de jeton entre SharePoint et Azure AD.   
    
- ACS remplace la nécessité d’un service de jeton de sécurité du fournisseur d’identité (IP-STS) pour ce scénario SAML.  
    
Pour plus d’informations, voir la rubrique Configuration de Azure Active Directory avec SharePoint 2013 disponible dans la bibliothèque TechNet.  
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Conception des sites et des URL pour la publication intersites

Une conception à une application web est recommandée pour les scénarios de publication.  
  
- Les sites de création et de publication se trouvent dans la même application web.  
    
- La publication intersites permet de publier des ressources.  
    
Utilisez des collections de sites basées sur le chemin d’accès et nommées par l’hôte. 
  
- L’utilisation d’une collection de site racine est une condition requise. Créez ce site en tant que site basé sur le chemin d’accès.  
    
- Créez toutes les autres collections de site en tant que collections de sites nommées par l’hôte.  
    
URL d’application web et de site racine  
  
- Utilisez un nom interne pour l’URL d’application web. SharePoint utilise le nom de la machine locale comme nom par défaut, sauf si un nom différent est spécifié. Vous pouvez utiliser un nom de domaine qui est réservé pour l’environnement réseau interne.   
    
- SharePoint affecte un numéro de port non standard lors de la création de l’application web. Utilisez ce numéro de port au lieu du port 80 ou du port 443. Vous pouvez utiliser un autre port à condition qu’il ne soit pas standard.  
    
- Utilisez les mêmes nom et numéro de port pour la collection de sites racine, qui est une collection de sites basée sur des chemins d’accès.  
    
Le diagramme associé représente des services de pool d’applications telles que la recherche interagissant avec les collections de sites à l’aide des applications web. Les collections de sites affichées sont les suivantes :  
  
- Collection de sites basée sur des chemins https://internal:8000 d’accès située sur (site racine). 
    
- Analyse : collections de sites nommées par l’hôte situées à une https://authoring.contoso.com:8000adresse telle que. 
    
- Requêtes : 2 collections de sites distinctes nommées par l’hôte et situées à des adresses telles que les suivantes :  
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Conception de l’environnement Azure

Cet exemple d’architecture inclut les éléments suivants :  
  
- Une connexion VPN de site à site est facultative et étend l’environnement local DNS et AD DS de Windows au réseau virtuel dans Azure.  
    
- Le cas échéant, utilisez un domaine dédié dans Azure pour prendre en charge la batterie de serveurs SharePoint.  
    
- Les serveurs sont répartis entre les services cloud d’Azure selon leur rôle.  
    
- Les groupes à haute disponibilité assurent la haute disponibilité de rôles serveur configurés de manière identique.   
    
Pour plus d’informations, voir l’article suivant sur TechNet : Architectures Microsoft Azure pour solutions SharePoint  
  
Le diagramme associé représente un exemple d’environnement local qui se connecte à un réseau virtuel Azure.    
  
L’environnement local, qui est un élément facultatif de l’environnement Azure, comporte les éléments suivants :  
  
- Windows Server 2012 RRAS 
    
- AD DS ; 
    
- Passerelle VPN entre Windows Server et AD DS, d’un côté, et le sous-réseau de passerelle VPN actif, de l’autre  
    
L’environnement de réseau virtuel Azure comporte les éléments suivants :  
  
- Sous-réseau de passerelle VPN actif (à cheval sur l’environnement local, le cas échéant)  
    
- Service cloud incluant le groupe à haute disponibilité AD DS et DNS (deux serveurs)  
    
- Service cloud incluant le groupe à haute disponibilité du serveur frontal (trois serveurs SharePoint) et le groupe à haute disponibilité du serveur d’applications (trois serveurs SharePoint)  
    
- Service cloud contenant deux groupes à haute disponibilité de base de données  
    

