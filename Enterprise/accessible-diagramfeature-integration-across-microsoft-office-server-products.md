---
title: 'Diagramme accessible : Intégration de fonctionnalités entre les produits Microsoft Office Server'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: d78983fa-0951-49b8-b890-d76a44c70035
f1.keywords:
- NOCSH
description: Cet article est une version texte accessible du diagramme intitulé intégration de fonctionnalités dans les produits Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server et Office Online Server.
ms.openlocfilehash: 37339c2c4a8a8cf08b3b0b2772e274383c5a4bdd
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843885"
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagramme accessible : Intégration de fonctionnalités entre les produits Microsoft Office Server

**Résumé :** Cet article est une version texte accessible du diagramme intitulé intégration de fonctionnalités dans les produits Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server et Office Online Server.
  
Le diagramme se compose de plusieurs onglets, comme indiqué par les titres de section de ce document.
  
## <a name="introduction-tab"></a>Onglet Introduction

### <a name="illustrations-for-cross-server-features"></a>Illustrations pour les fonctionnalités entre serveurs

Ce fichier Visio (ou fichier PDF multipage) comporte neuf onglets, chacun d’eux comportant des informations et un diagramme sur une fonctionnalité qui fonctionne sur plusieurs produits Office Server.
  
Les fonctionnalités et les onglets sont :  
  
- Introduction
    
- Authentification de serveur à serveur 
    
- Photos haute résolution de l’utilisateur  
    
- Magasin de contacts unifié 
    
- Boîtes aux lettres de site 
    
- Synchronisation de tâches Exchange 
    
- Présence de Lync dans Outlook Web App 
    
- Messagerie vocale
    
- Enregistrements de réunions 
    
Envoyez des commentaires sur cette solution ou des demandes pour des solutions supplémentaires à MODAContent@microsoft.com.  
  
### <a name="tips-for-printing"></a>Conseils pour l’impression

La taille de page de chaque onglet est 22 x 17 pouces (environ un quart de la taille d’un diagramme d’ingénierie ANSI). Vous pouvez imprimer cette page sur deux feuilles format tabloïd (11 x 17 pouces) ou quatre feuilles format lettre (8,5 x 11 pouces). Si vous avez un traceur, vous pouvez imprimer ces affiches à leur taille réelle. Sinon, suivez les étapes ci-après pour les imprimer dans un format réduit.  
  
 **Imprimer des affiches sur un papier de petite taille**
  
1. Ouvrez l’affiche dans Visio. 
    
2. Dans le menu **Fichier**, cliquez sur **Mise en page**. 
    
3. Dans l’onglet **Mise en page**, dans la section **Papier de l’imprimante**, sélectionnez la taille du papier sur lequel vous voulez imprimer.
    
4. Dans l’onglet **Configuration de l’impression**, dans la section **Zoom d’impression**, cliquez sur **Ajuster** et entrez **1 page en largeur et 1 page en hauteur**. 
    
5. Dans l’onglet **Taille de la page**, cliquez sur **Ajuster au contenu du dessin**, puis sur **OK**. 
    
6. Dans le menu **Fichier**, cliquez sur **Imprimer**. 
    
### <a name="microsoft-tags-and-qr-codes"></a>Balises Microsoft et codes QR

Utilisez votre Windows phone ou téléchargez un lecteur de code QR pour obtenir plus d’informations sur la mise en œuvre de ces fonctionnalités.  
  
### <a name="cross-server-features"></a>Fonctionnalités entre serveurs

Un tableau indique les fonctionnalités et les produits Office Server qui les utilisent. Les fonctionnalités sont :  
  
Authentification de serveur à serveur Cette fonctionnalité s’applique à :  
  
- SharePoint 
    
- Exchange
    
- Lync
    
- Office Online Server (anciennement appelé Office Web Apps) 
    
Photos haute résolution de l’utilisateur Cette fonctionnalité s’applique à :  
  
- SharePoint
    
- Exchange
    
- Lync
    
Magasin de contacts unifié Cette fonctionnalité s’applique à :  
  
- Exchange
    
- Lync
    
Boîtes aux lettres de site. Cette fonctionnalité s’applique à :  
  
- SharePoint
    
- Exchange
    
Synchronisation de tâches Exchange Cette fonctionnalité s’applique à :  
  
- SharePoint
    
- Exchange
    
Présence de Lync dans Outlook Web App Cette fonctionnalité s’applique à :  
  
- Lync
    
Messagerie vocale. Cette fonctionnalité s’applique à :  
  
- Lync
    
Enregistrements de réunions. Cette fonctionnalité s’applique à :  
  
- SharePoint
    
- Lync
    
### <a name="office-web-apps-server"></a>Office Web Apps Server

Office Web Apps Server est un produit Office Server qui offre des services d’affichage et de modification de fichier basés sur navigateur pour les fichiers Office. Office Web Apps Server est compatible avec les produits et services qui prennent en charge le protocole WOPI (Web Application Open Platform Interface). Ces produits, appelés hôtes, incluent SharePoint 2013, Lync Server 2013 et Exchange Server 2013.   
  
Pour en savoir plus sur Office Web Apps Server, téléchargez l’affiche simplifiée pour le déploiement https://aka.ms/OfficeWebAppsPosterd’Office Web Apps à l’adresse. 
  
## <a name="server-to-server-authentication-tab"></a>Onglet Authentification de serveur à serveur

### <a name="servicing-resource-requests-between-servers"></a>Traitement des demandes de ressources entre les serveurs

L’authentification de serveur à serveur est une nouvelle fonctionnalité d’Exchange Server 2013, Lync Server 2013 et SharePoint Server 2013 qui permet à un serveur de demander des ressources d’un autre serveur pour le compte d’un utilisateur. Cette fonctionnalité utilise le protocole industriel standard Open Authorization (OAuth) 2.0. L’authentification de serveur à serveur permet de nombreux nouveaux scénarios comme eDiscovery, les photos utilisateur à haute résolution et les boîtes aux lettres de site.  
  
 **Produits Server** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relations d’approbation de serveur à serveur

Pour qu’un serveur puisse traiter une demande de ressource entrante, il doit approuver le serveur qui effectue la demande. Pour établir cette approbation, vous devez configurer des relations d’approbation de serveur à serveur.   
  
Une relation d’approbation de serveur à serveur est unidirectionnelle. Lorsque vous configurez un serveur qui exécute SharePoint 2013 pour approuver un serveur Exchange 2013, le serveur qui exécute SharePoint Server approuve les demandes de ressources du serveur Exchange, mais le serveur Exchange n’approuve pas les demandes de ressources issues du serveur qui exécute SharePoint Server. Pour une intégration transparente, vous devez établir des approbations bidirectionnelles.  
  
Le diagramme associé présente les relations d’approbation de serveur à serveur qui sont créées sous forme d’approbations bidirectionnelles. Les relations d’approbation bidirectionnelles présentées existent entre un serveur Exchange Server, un serveur SharePoint Server et un serveur Lync Server. Chaque type de serveur dispose d’une approbation bidirectionnelle avec chacun des deux autres serveurs.  
  
### <a name="configuration"></a>Configuration

Pour configurer une approbation d’authentification de serveur à serveur, vous devez ajouter un nouvel émetteur de jeton de sécurité approuvé qui correspond à chaque serveur qui envoie des demandes de ressources pour le compte des utilisateurs. Chaque type de serveur a un point de terminaison de métadonnées JSON (JavaScript Object Notation) contenant des informations de configuration et une partie publique du certificat de signature du jeton d’accès. Une partie de la configuration d’une approbation d’authentification de serveur à serveur spécifie le point de terminaison de métadonnées JSON de l’autre serveur.  
  
Le tableau suivant répertorie le point de terminaison de métadonnées JSON pour chaque serveur. Le tableau montre :  
  
- Un serveur Exchange avec un point de terminaison de métadonnées JSON de https://<server name>/Autodiscover/Metadata/JSON/1 
    
- Un serveur Lync avec un point de terminaison de métadonnées JSON de https://<server name>/Metadata/JSON/1 
    
- Un serveur SharePoint avec un point de terminaison de métadonnées JSON de https://<web app name>/_layouts/15/Metadata/JSON/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Exemple : Fonctionnement de l’authentification de serveur à serveur pour eDiscovery entre SharePoint et Exchange

Dans cet exemple, le serveur Exchange 2013 a été configuré pour approuver le serveur qui exécute SharePoint Server avec une approbation de serveur à serveur. Un centre eDiscovery sur le serveur qui exécute SharePoint Server a été configuré pour inclure des données dans des boîtes aux lettres sur le serveur Exchange.  
  
Les demandes de ressources sur un autre serveur prennent la forme de jetons d’accès qui sont envoyés au service de serveur web sur le serveur de destination.  
  
Le diagramme associé représente la manière dont les requêtes et les jetons d’accès se déplacent entre les deux serveurs.  
  
1. Un administrateur eDiscovery envoie une requête au serveur exécutant SharePoint Server qui inclut des ressources sur un serveur Exchange.  
    
2. Le serveur qui exécute SharePoint Server génère un jeton d’accès, identifiant l’utilisateur et la ressource demandée.  
    
3. Le serveur qui exécute SharePoint Server envoie le jeton d’accès au serveur Exchange.  
    
4. Le serveur Exchange valide le jeton d’accès et envoie les résultats de la requête.  
    
5. Le serveur qui exécute SharePoint Server envoie les résultats de la requête eDiscovery à l’ordinateur de l’administrateur eDiscovery. 
    
## <a name="high-resolution-user-photos-tab"></a>Onglet Photos haute résolution de l’utilisateur

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Photo de profil plus grande utilisée pour toutes les applications Office

À l’aide de l’onglet **photos haute résolution de l’utilisateur**, vous pouvez stocker des photos jusqu’à 648 x 648 pixels dans Exchange 2013. Elles sont ensuite accessibles par le biais d’applications clientes, notamment Outlook, Outlook Web App, SharePoint 2013, Lync 2013 et des clients de messagerie mobiles. Une photo basse résolution est également stockée dans Active Directory.
  
 **Produits Server** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="configuration"></a>Configuration

Configurer l’authentification de serveur à serveur. 
  
- Entre Exchange 2013 et SharePoint 2013.  
    
- Entre Exchange 2013 et Lync 2013.  
    
 **Sur Exchange Server 2013**
  
- Démarrez et configurez le service de découverte automatique d’Exchange 2013.  
    
- Définissez les URL externes pour SharePoint. Il s’agit des URL que SharePoint utilise lorsqu’il accède à des photos dans Exchange.  
    
 **Sur SharePoint Server 2013**
  
- Installez Exchange Web Services Managed API. Utilisez GacUtil pour charger la DDL Microsoft.Exchange.WebServices.dll dans le Global Assembly Cache (GAC).   
    
- Utiliser Windows PowerShell pour configurer la synchronisation des photos avec Exchange.  
    
 **Fonctionnement**
  
- Les utilisateurs téléchargent une photo à l’aide de la page Mon compte dans Outlook Web App (OWA) ou les paramètres de compte dans Outlook 2013.  
    
- Exchange redimensionne automatiquement l’image à utiliser avec les services AD DS (48 x 48 pixels) ou avec d’autres applications Office, y compris OWA et le client Outlook 2013 (96 x 96 pixels).   
    
Les utilisateurs peuvent télécharger des images dans des plages de pixels allant de 48 × 48 à 648 × 648. Les photos sont redimensionnées :  
  
- Le format 64 x 64 est utilisé pour la miniature AD.  
    
- Le format 96 x 96 est utilisé pour Outlook Web Access, Outlook, Lync Web Access et Lync 2013.  
    
- Le format 648 × 648 est utilisé pour Lync Web Access et Lync 2013.  
    
Pour obtenir des exemples de scripts de configuration, voir les Articles de blog de Jens des Rasmussen Rasmussen : 
  
- Utilisation de photos haute résolution Exchange 2013 à partir de SharePoint Server 2013 (https://aka.ms/Bhr4d2) 
    
- Intégration d’Exchange 2013 et de Lync Server 2013 (https://aka.ms/Pn08dw) 
    
L’affiche contient également des codes QR pour ces deux articles de blog.  
  
Le diagramme associé montre comment un utilisateur peut mettre à jour une photo à utiliser dans toutes les applications Office.  
  
1. L’utilisateur met à jour la photo dans Outlook, SharePoint et Lync. Une fois mise à jour, la photo est utilisée dans toutes les applications Office.   
    
2. L’utilisateur peut recourir à plusieurs méthodes pour mettre à jour une photo :  
    
3. 
  - Client Outlook ou Outlook Web App (OWA) sur le port HTTP 443 vers un serveur d’accès au client Exchange.  
    
  - Mon Site via HTTP ou HTTPS vers un serveur SharePoint. SharePoint place l’utilisateur dans un cache dans la base de données Mon site (Https:443). Le serveur SharePoint communique avec le serveur d’accès au client Exchange à l’aide d’URL externes définies dans Exchange.  
    
  - Client Lync 2013, qui gère une fonction GetConnection avec le serveur Exchange pour obtenir des mises à jour de photos (HTTPs Get Request-443). 
    
4. Le serveur d’accès au client Exchange se connecte au serveur de boîtes aux lettres Exchange à l’aide de la communication interne Exchange.   
    
5. Le serveur de boîtes aux lettres Exchange utilise Exchange 2013 pour pousser la photo haute résolution de l’utilisateur vers AD DS (LDAP:389).  
    
6. La photo est synchronisée à partir des services de domaine Active Directory (AD DS) vers le service de carnet d’adresse (ABS) sur le serveur Lync afin que les clients hérités puissent accéder à la même photo (LDAP:389).  
    
7. Le client Lync hérité a désormais accès à la photo.  
    
## <a name="unified-contact-store-tab"></a>Onglet Magasin de contacts unifié

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>Exchange 2013 est le magasin de contacts pour toutes les applications Office

Le magasin de contacts unifié offre une gestion cohérente des contacts entre plusieurs produits Microsoft Office. Les utilisateurs stockent toutes les informations de contacts dans leur boîte aux lettres Exchange 2013. Les mêmes informations de contact sont disponibles globalement sur Lync, Exchange, Outlook et Outlook Web App.   
  
 **Produits Server** 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configuration**
  
- Configurer une authentification de serveur à serveur entre Exchange Server 2013 et Lync Server 2013.  
    
- Dans Lync 2013, activer la stratégie de magasin contacts unifié (activée par défaut).  
    
Pour obtenir des exemples de scripts de configuration, voir l’article du blog de Jens des Rasmussen Rasmussen : 
  
- Intégration d’Exchange 2013 et de Lync Server 2013 (https://aka.ms/Oyg7fh) 
    
 **Fonctionnement** 
  
- Les contacts de Lync pour un utilisateur sont automatiquement transférés vers Exchange 2013 lorsque l’utilisateur se connecte avec Lync 2013.  
    
- Les utilisateurs peuvent consulter et gérer leurs contacts Lync à partir de Lync 2013, Outlook 2013 ou Outlook Web Access.   
    
Les contacts d’un utilisateur sont transférés automatiquement vers le serveur Exchange 2013 quand : 
  
1. Une stratégie de services utilisateur dont le paramètre UcsAllowed a la valeur **True** a été attribuée à l’utilisateur. 
    
2. Une boîte aux lettres Exchange 2013 a été mise en service pour cet utilisateur et qu’il s’y est connecté au moins une fois. 
    
3. L’utilisateur se connecte à Lync à l’aide d’un client riche Lync 2013. 
    
L’utilisateur se connecte à Lync à l’aide d’un client riche Lync 2013.  
  
1. L’utilisateur se connecte à sa boîte aux lettres Exchange 2013 sur le serveur d’accès au client Exchange, à l’aide d’un client Outlook ou Outlook Web App (OWA) via le protocole HTTPS/443. Le serveur de boîtes aux lettres Exchange utilise une communication Exchange interne pour communiquer avec le serveur d’accès au client Exchange.  
    
2. L’utilisateur se connecte à Lync 2013. Le client Lync contacte le serveur Lync sur SIP/5061 HTTPS/443.  
    
3. Le client Lync indique au serveur Lync que l’utilisateur est activé pour le magasin de contacts unifié sur SIP/5061.  
    
4. Le serveur Lync utilise le service de stockage Lync pour migrer les contacts de l’utilisateur vers Exchange 2013 sur le serveur d’accès au client Exchange. 
    
5. L’utilisateur doit se déconnecter et se connecter à Lync 2013 pour que les modifications apparaissent (pas représentées dans le diagramme).  
    
6. Après la migration, le client Lync utilise Exchange Web Services (EWS) pour lire et à gérer les contacts Lync.  
    
## <a name="site-mailboxes-tab"></a>Onglet Boîtes aux lettres de site

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Classeur central pour les messages électroniques et les documents

Les boîtes aux lettres de site améliorent la collaboration et la productivité des utilisateurs en autorisant l’accès aux documents stockés dans SharePoint et aux messages électroniques enregistrés dans Exchange, avec la même interface client. 
  
 **Produits Server** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configuration**
  
Configuration SharePoint :  
  
- Configurer la synchronisation des profils utilisateur dans la batterie de serveurs SharePoint.  
    
- Configurer l’application de service de gestion des applications dans la batterie de serveurs SharePoint.  
    
- Configurer SSL pour la zone par défaut pour prendre en charge l’authentification de serveur à serveur.  
    
- Installez l’API EWS sur les serveurs exécutant SharePoint 2013.  
    
- Établir une approbation OAuth et des autorisations de service sur les serveurs exécutant SharePoint 2013.  
    
Configuration d’Exchange :  
  
- Établir une approbation OAuth et une autorisation de service sur les serveurs Exchange.  
    
- Créer une stratégie de mise en service de boîte aux lettres de site.  
    
- Configurer le préfixe du nom d’une boîte aux lettres de site (facultatif).  
    
 **Fonctionnement**
  
Une boîte aux lettre de site se compose de l’appartenance à un site SharePoint 2013 (propriétaires et membres), un stockage partagé par le biais d’une boîte aux lettres Exchange 2013 pour des messages électroniques et un site SharePoint 2013 pour des documents, ainsi qu’une interface de gestion qui répond aux besoins de mise en service et de cycle de vie.  
  
Le diagramme associé représente l’utilisation de boîtes aux lettres de site pour accéder aux messages électroniques dans Outlook et aux documents stockés dans SharePoint.  
  
1. Les utilisateurs peuvent accéde aux documents de site d’équipe SharePoint via les boîtes aux lettres de site dans Outlook 2013 Pro Plus.  
    
2. Les utilisateurs peuvent également lire des messages électroniques dans la boîte de réception de la boîte aux lettres de site à partir du site d’équipe SharePoint.  
    
3. Les messages électroniques sont stockés dans les boîtes aux lettres de site sur les serveurs Exchange.  
    
4. Les documents sont stockés dans les boîtes aux lettres de site sur les serveurs SharePoint.  
    
5. Les métadonnées du contenu sur le site SharePoint sont synchronisées avec Exchange à l’aide de l’API REST sur HTTPS.  
    
### <a name="provisioning-and-management"></a>Mise en service et gestion

Les boîtes aux lettres de site sont configurées et gérées via SharePoint 2013. Il existe des fonctionnalités SharePoint et Exchange pour la mise en service et la gestion.  
  
#### <a name="sharepoint"></a>SharePoint

Un diagramme représente les composants sur SharePoint qui sont nécessaires pour la mise en service de la boîte aux lettres de site, notamment :  
  
- L’application de boîte aux lettres de site  
    
- Les propriétaires et membres du site d’équipe  
    
- La stratégie du cycle de vie du site d’équipe  
    
Pour mettre en service une nouvelle boîte aux lettres de site, installez l’application de boîte aux lettres de site sur votre site d’équipe et accédez au moins une fois à l’application.  
  
L’appartenance au site SharePoint détermine qui a accès à la boîte aux lettres de site.   
  
La rétention des boîtes aux lettres de site suit la stratégie de cycle de vie configurée pour le site SharePoint auquel elle est associée.  
  
#### <a name="exchange"></a>Exchange

Le diagramme représente la stratégie de mise en service des boîtes aux lettres de site. Il s’agit du composant Exchange requis pour mettre en service la boîte aux lettres de site.
  
Sur le serveur Exchange, vous pouvez définir des stratégies de mise en service de boîtes aux lettres de site. Ces stratégies régissent les caractéristiques des messages électroniques reçus et envoyés en direction de la boîte aux lettres de site, ainsi que la taille de la boîte aux lettres de site sur le serveur Exchange. Elle vous permettent aussi de définir un préfixe pour les adresses de messagerie des boîtes aux lettres de Site.   
  
Pour les déploiements d’Exchange en local, vous devez également rechercher et supprimer régulièrement les boîtes aux lettres de site qui ont été marquées comme étant à supprimer via la stratégie de cycle de vie de SharePoint.  
  
## <a name="exchange-task-synchronization-tab"></a>Onglet Synchronisation de tâches Exchange

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Synchronisation de tâches entre SharePoint Server 2013, Project Server 2013 et Exchange Server 2013

À l’aide de la synchronisation de tâches Exchange, vous pouvez synchroniser les tâches dans SharePoint Server 2013 et Project Server 2013 avec Exchange Server 2013. Les utilisateurs peuvent afficher et gérer leurs tâches dans Outlook 2013 ou sur leur site Mon Site.  
  
 **Produits Server** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (facultatif)  
    
 **Conditions préalables**
  
Sur Exchange 2013 :  
  
- Établir une approbation OAuth et une autorisation de service.  
    
Sur SharePoint Server 2013 :  
  
- Application de service de profil utilisateur.  
    
- Application de service Gestion du travail.  
    
- Recherche (ce paramètre est obligatoire pour les tâches dans SharePoint Server 2013). Configurer avec des analyses continues et des analyses incrémentielles.  
    
- Secure Sockets Layer (SSL) est requis.  
    
- Les utilisateurs disposent de sites Mon site existants.  
    
- Application de service Project (pour regrouper les tâches de Project Server).  
    
- API Services web Exchange sur chaque serveur frontal web (il s’agit d’un fichier .exe téléchargeable distinct qui doit être installé).  
    
Sur Project Server 2013 :  
  
- Créer des sites Project Web App. 
    
 **Fonctionnement**
  
Lorsque l’affichage Mes tâches des sites Mon site est ouvert ou actualisé :  
  
- L’application de service Gestion du travail se synchronise entre SharePoint Server et Project Server.   
    
- Le travail du minuteur de synchronisation Exchange appelle l’application de service Gestion du travail pour synchroniser les tâches avec Exchange Server 2013.  
    
- La page Mes tâches sur les sites Mon site est actualisée.  
    
Lorsque le travail du minuteur de synchronisation Exchange fonctionne :  
  
- L’application de service Gestion du travail se synchronise entre SharePoint Server, Project Server et Exchange Server.  
    
Le diagramme associé illustre l’interaction entre SharePoint Server 2013, Exchange Server 2013, Outlook 2013 et Project Server 2013.  
  
SharePoint Server 2013 exécute les tâches et applications suivantes :  
  
- Application de service de profil utilisateur.  
    
- Application de service de recherche.  
    
- Application de service Gestion du travail, qui est décrite ci-dessous.  
    
- Travail du minuteur de synchronisation Exchange, qui est décrit ci-dessous.  
    
- SharePoint Server 2013 contient le mon site et d’autres sites de l’utilisateur et exécute de nombreuses tâches utilisateur. 
    
- SharePoint Server 2013 contient un Index de recherche.  
    
Exchange Server 2013 contient les éléments suivants :  
  
- Base de données Exchange avec les informations de messagerie de l’utilisateur  
    
- Tâches de synchronisation  
    
Outlook 2013 affiche les éléments suivants :  
  
- Les utilisateurs peuvent utiliser cette fonctionnalité, décrite ci-dessous, pour synchroniser leurs tâches.  
    
- Les utilisateurs peuvent afficher et modifier des tâches dans Outlook.  
    
Project Server 2013 affiche les éléments suivants :  
  
- Base de données Project  
    
- Sites Project Web Access avec des tâches  
    
L’application de service Gestion du travail :  
  
- Regroupe les tâches à partir des listes SharePoint et des listes de tâches Project (ne synchronise pas les tâches avec Exchange Server).  
    
- Se synchronise quand les utilisateurs affichent leur site Mon Site.  
    
- Met à jour la liste des utilisateurs qui le souhaitent.   
    
- Synchronise le lot d’utilisateurs suivant.  
    
Le travail du minuteur de synchronisation Exchange  
  
- Détermine le lot d’utilisateurs suivant.  
    
- Garantit que tous les utilisateurs sont synchronisés en permanence.  
    
- Lance l’appel à l’application de service Gestion du travail pour synchroniser les tâches avec Exchange Server uniquement pour les utilisateurs qui s’y sont abonnés.  
    
Abonnement  
  
- Les utilisateurs doivent s’abonner à cette fonctionnalité pour synchroniser leurs tâches Exchange avec leur site Mon Site, ou leurs tâches SharePoint Server 2013 et Project Server 2013 avec Exchange Server 2013.  
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Présence Lync dans l’onglet Office 2013, Outlook Web App et SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server en tant que source d’autorité des informations de présence

En utilisant les informations de présence de Lync, vous pouvez obtenir un affichage cohérent des informations de présence entre Lync, Outlook et SharePoint. Outlook envoie des demandes d’informations de présence directement à partir de Lync, qui est installé localement sur le même ordinateur que Outlook. Quand les utilisateurs affichent les informations de présence dans SharePoint Server, les informations de présence sont interrogées par Lync sur l’ordinateur local.
  
Produits clients :  
  
- Outlook 2013 
    
- Lync 2013 
    
Produits serveurs :  
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Fonctionnement** 
  
Dans la mesure où Lync 2013 est installé sur l’ordinateur local de l’utilisateur, Outlook et SharePoint Server affichent automatiquement les informations de présence des utilisateurs.  
  
Pour les utilisateurs d’Outlook Web App, Exchange CAS envoie la demande de présence au nom de l’utilisateur.  
  
 **Il existe deux diagrammes associés**
  
Le premier montre comment un utilisateur se connecte à Outlook Web App, puis comment Exchange envoie une requête pour obtenir des informations de présence à Lync Server.  
  
1. L’utilisateur se connecte à Outlook Web App. L’ordinateur client accède à Exchange Client Access Server (CAS) sur HTTPS/443 et appelle également le serveur de boîtes aux lettres Exchange avec une communication Exchange interne.  
    
2. L’utilisateur se connecte à sa boîte aux lettres Exchange 2013 et Exchange CAS envoie une requête au serveur Lync pour obtenir des informations de présence sur SIP/MTLS:5061.  
    
Pour plus d’informations, reportez-vous à l' [intégration de Microsoft Lync Server 2013 et de Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
Le deuxième diagramme montre comment Outlook et SharePoint Server utilisent Lync 2013 pour afficher les informations de présence des utilisateurs.  
  
1. L’utilisateur se connecte à Lync 2013 sur SIP/TLS:5061, qui appelle le serveur Lync.   
    
2. A. L’utilisateur se connecte à sa boîte aux lettres Exchange 2013 via Outlook dans Office 2013. L’ordinateur client accède à Exchange Client Access Server (CAS) sur HTTPS/443 et appelle également le serveur de boîtes aux lettres Exchange avec une communication Exchange interne.  
    
3. A. Outlook appelle l’instance Lync installée sur le même ordinateur que Outlook pour récupérer les informations de présence.  
    
4. B. L’utilisateur se connecte au site Mon site SharePoint via HTTP ou HTTPS, qui appelle le serveur SharePoint.  
    
5. B. Internet Explorer appelle Lync, qui est installé sur le même ordinateur que le navigateur, pour récupérer les informations de présence.  
    
## <a name="voicemail-tab"></a>Onglet Messagerie vocale

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>La messagerie unifiée Exchange est le système de messagerie vocale pour Lync Server

La messagerie vocale permet à un appelant de laisser un message vocal aux utilisateurs de Lync à l’aide de la messagerie unifiée (MU) Exchange.   
  
Produits clients : 
  
- Lync 2013 
    
- Appareil PSTN (PBX, cellulaire, POTS)  
    
Produits serveurs : 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Fonctionnement** 
  
Lorsqu’un appel n’est pas traité par l’appelé sur l’un des points de terminaison actifs de l’appelé, Lync Server achemine l’appel vers la messagerie vocale sur la messagerie unifiée Exchange (par exemple, serveur de boîtes aux lettres Exchange). 
  
Le diagramme associé illustre le routage des appels pour deux scénarios :  
  
- L’appelant établit un appel à l’aide de Lync 2013.  
    
- L’appelant établit un appel à l’aide d’appareil PSTN (PBX, cellulaire, POTS).  
    
L’appelant établit un appel à l’aide de Lync 2013 :  
  
1. L’appelant A établit un appel au destinataire à l’aide de Lync 2013. L’appel est établi et envoyé au serveur Lync.  
    
2. L’appel est acheminé vers le serveur d’accueil Lync de l’appelé. 
    
3. Lync Server sonne les points de terminaison actifs de l’appelé sur Lync 2013. 
    
4. Lorsque l’appel ne reçoit pas de réponse, l’appel est acheminé vers la messagerie vocale (messagerie unifiée Exchange) sur Exchange CAS (routeur d’appel).  
    
L’appelant établit un appel à l’aide de Lync 2013 :  
  
1. L’appelant B compose le numéro de téléphone de l’appelé à l’aide du RTC. 
    
2. L’appel PSTN est routé de la passerelle IP vers le serveur de médiation, qui est un serveur Lync.  
    
3. Le serveur de médiation achemine l’appel vers le serveur d’accueil Lync du destinataire. 
    
4. Lync Server sonne les points de terminaison actifs de l’appelé sur Lync 2013. 
    
5. Lorsque l’appel ne reçoit pas de réponse, l’appel est acheminé vers la messagerie vocale (messagerie unifiée Exchange) sur Exchange CAS (routeur d’appel).  
    
## <a name="meeting-recordings-tab"></a>Onglet Enregistrements de réunions

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Publier vos enregistrements de réunions sur votre site d’équipe SharePoint

Les enregistrements de réunions sont un composant essentiel des communications unifiées. Un bon moyen de partager vos enregistrements de réunions consiste à utiliser des bibliothèques de biens SharePoint sur vos sites d’équipe pour stocker vos enregistrements de réunions.  
  
Produits clients :  
  
- Lync 2013 
    
Produits serveurs :  
  
- Produits serveurs :  
    
- SharePoint 2013 
    
Conditions préalables : 
  
- Lync 2013 — L’enregistrement de réunion est une fonctionnalité côté client dans Lync 2013.   
    
- SharePoint 2013 — Le site d’équipe dans lequel vous souhaitez stocker les enregistrements de réunions est opérationnel.  
    
 **Qu’est-ce qui est enregistré ?**
  
Les éléments suivants sont enregistrés dans un fichier MP4 pendant la réunion (chaque puce est précédée d’une icône représentant le type d’enregistrement) :  
  
- Tous les fichiers audio  
    
- Vidéo de l’intervenant actif (le cas échéant) 
    
- Une vidéo panoramique (le cas échéant)  
    
- Tout le contenu qui est présenté  
    
- Les messages instantanés*   
    
* Seuls les messages instantanés émis dans le cadre de la réunion sont inclus. Tout échange de messages peer-to-peer entre les participants de la réunion ne fait pas partie de la réunion et par conséquent n’est pas capturé.  
  
L’affiche inclut deux diagrammes pour deux scénarios différents :  
  
- Préparation pour la publication de vos enregistrements de réunions  
    
- Enregistrement et publication d’une réunion à l’aide du client Lync  
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Préparation pour la publication de vos enregistrements de réunions

Le diagramme montre SharePoint Server 2013 avec un site d’équipe, un centre d’Administration centrale et un serveur Internet Information Services (IIS).  
  
Le site d’équipe contient :  
  
- L’application de la bibliothèque de biens.  
    
- La bibliothèque des biens des réunions, à laquelle les membres de l’équipe envoient les enregistrements de réunions.  
    
Le centre d’Administration centrale contient les paramètres généraux de l’application web.  
  
Le serveur IIS contient les paramètres IIS.  
  
Pour préparer la publication de vos enregistrements de réunions : 
  
1. Sur votre site d’équipe SharePoint, ajoutez l’application de la bibliothèque des biens. Si vous le souhaitez, si vous ne parvenez pas à télécharger les enregistrements de réunions en raison de restrictions de taille ou de délais d’attente pour la connexion, effectuez les étapes supplémentaires 2 et 3. 
    
2. Dans l’Administration centrale de SharePoint, modifiez le paramètre de taille maximale de téléchargement pour l’application web qui contient votre collection de site d’équipe.  
    
3. Dans les paramètres serveur IIS, augmentez le délai d’attente pour la connexion IIS pour le site web qui contient votre collection de site d’équipe.  
    
 **Bibliothèques de biens numériques**
  
Les bibliothèques de biens numériques sont des bibliothèques de biens contenant des vidéos qui ont des conséquences sur la capacité et les performances. Pour plus d’informations, reportez-vous à la rubrique plan Digital https://aka.ms/O1vq5wAsset Libraries in SharePoint Server 2013, à l’adresse. L’affiche inclut également un code QR pour accéder à ces informations. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Enregistrement et publication d’une réunion à l’aide du client Lync

Le diagramme montre un utilisateur utilisant  Lync pour participer à une réunion. La réunion est enregistrée à l’aide du client Lync, qui crée un fichier MP4 avec le contenu de la réunion. L’enregistrement MP4 est enregistré dans le dossier d’enregistrement Lync de votre ordinateur. Vous pouvez déplacer l’enregistrement MP4 dans votre bibliothèque de biens des réunions, à partir de laquelle vous pouvez l’insérer dans un wiki, une page SharePoint ou un blog.  
  
 **Pour enregistrer et publier une réunion à l’aide du client Lync** 
  
1. Démarrer l’enregistrement de la réunion à l’aide du client Lync.  
    
2. Le contenu de la réunion est enregistré dans un fichier MP4 pendant la réunion.  
    
3. Une fois la réunion terminée, l’enregistrement MP4 apparaît dans le dossier Recording de votre ordinateur (les\\enregistrements\\<username>\\de\\vidéos de vidéos de l’utilisateur C : utilisateurs). Si vous le souhaitez, vous pouvez personnaliser l’enregistrement de la réunion à l’aide de l’application de gestionnaire d’enregistrements Lync qui est installée avec le client Lync. 
    
4. Glissez et déplacez l’enregistrement de la réunion dans votre bibliothèque de biens SharePoint. 
    
5. Facultatif : Une fois que l’enregistrement se trouve dans votre bibliothèque de biens, vous pouvez l’insérer dans n’importe quelle page SharePoint. Pour plus d’informations sur cette étape, voir l’entrée de blog Office 365, créer et publier des vidéos de formation avec SharePoint et Lync https://aka.ms/R61q35Online, à l’adresse. 
    
 **Miniatures de vidéo**
  
Les miniatures de vidéo améliorent l’apparence de votre bibliothèque de biens. Pour en savoir plus sur la création de miniatures pour vos enregistrements de réunions, reportez-vous à https://aka.ms/Kupj85la rubrique capture ou modification d’une miniature de vidéo, à l’adresse. L’affiche inclut également un code QR pour accéder à ces informations. 
  

