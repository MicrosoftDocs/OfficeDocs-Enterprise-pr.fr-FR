---
title: Isolation et contrôle d’accès dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
- SPO_Content
f1.keywords:
- NOCSH
description: 'Résumé : explication de l’isolation et du contrôle d’accès dans les différentes applications de Microsoft 365.'
ms.openlocfilehash: fc0aa37025936a1a60cfbb8914b079eba5ba2e7f
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052587"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Isolation et contrôle d’accès dans Microsoft 365

Azure Active Directory (Azure AD) et Microsoft 365 utilisent un modèle de données hautement complexe qui inclut des dizaines de services, des centaines d’entités, des milliers de relations et des dizaines de milliers d’attributs. À un niveau élevé, Azure AD et les annuaires de services sont les conteneurs de clients et de destinataires maintenus synchronisés à l’aide de protocoles de réplication basée sur l’État. En plus des informations d’annuaire stockées dans Azure AD, chacune des charges de travail de service ont leur propre infrastructure de services d’annuaire.
 
![Synchronisation des données client Microsoft 365](media/office-365-isolation-tenant-data-sync.png)

Dans ce modèle, il n’existe pas de source unique de données d’annuaire. Systèmes spécifiques qui possèdent des données individuelles, mais aucun système ne contient toutes les données. Les services Microsoft 365 collaborent avec Azure AD dans ce modèle de données. Azure AD est le « système de vérité » pour les données partagées, qui sont généralement des petites et des données statiques utilisées par chaque service. Le modèle fédéré utilisé dans Microsoft 365 et Azure AD fournit la vue partagée des données.

Microsoft 365 utilise à la fois le stockage physique et le stockage cloud Azure. Exchange Online (y compris Exchange Online Protection) et Skype entreprise utilisent leur propre espace de stockage pour les données client. SharePoint Online utilise à la fois le stockage SQL Server et Azure Storage, ce qui nécessite une isolation supplémentaire des données client au niveau du stockage.

## <a name="exchange-online"></a>Exchange Online

Exchange Online stocke les données client dans les boîtes aux lettres. Les boîtes aux lettres sont hébergées dans des bases de données ESE (Extensible Storage Engine) appelées bases de données de boîtes aux lettres. Cela inclut les boîtes aux lettres utilisateur, les boîtes aux lettres liées, les boîtes aux lettres partagées et les boîtes aux lettres de dossiers publics. Les boîtes aux lettres utilisateur incluent le contenu Skype entreprise enregistré, tel que l’historique des conversations.

Le contenu des boîtes aux lettres utilisateur inclut :

- Messages électroniques et pièces jointes
- Calendrier et informations de disponibilité
- Contacts
- Tâches
- Notes
- Groupes
- Données d’inférence

Chaque base de données de boîtes aux lettres dans Exchange Online contient des boîtes aux lettres de plusieurs clients. Un code d’autorisation sécurise chaque boîte aux lettres, y compris au sein d’un client. Par défaut, seul l’utilisateur affecté a accès à une boîte aux lettres. La liste de contrôle d’accès (ACL) qui sécurise une boîte aux lettres contient une identité authentifiée par Azure AD au niveau du client. Les boîtes aux lettres de chaque client sont limitées aux identités authentifiées par rapport au fournisseur d’authentification du client, qui inclut uniquement les utilisateurs de ce client. Le contenu du client A ne peut être obtenu par les utilisateurs dans le client B, sauf s’il est explicitement approuvé par le client A.

## <a name="skype-for-business"></a>Skype Entreprise

Skype entreprise stocke les données à différents endroits :

- Les informations d’utilisateur et de compte, qui incluent les points de terminaison de connexion, les ID de client, les plans de numérotation, les paramètres d’itinérance, l’état de présence, les listes de contacts, etc., sont stockées dans les serveurs Active Directory Skype entreprise et dans différents serveurs de base de données Skype entreprise. Les listes de contacts sont stockées dans la boîte aux lettres Exchange Online de l’utilisateur si l’utilisateur est activé pour les deux produits ou sur les serveurs Skype entreprise si l’utilisateur ne l’est pas. Les serveurs de base de données Skype entreprise ne sont pas partitionnés par client, mais l’isolation mutualisée des données est appliquée via le contrôle d’accès basé sur un rôle (RBAC).
- Le contenu de réunion et les données téléchargées sont stockés sur des partages de système de fichiers distribués (DFS). Ce contenu peut également être archivé dans Exchange Online s’il est activé. Les partages DFS ne sont pas partitionnés par client. le contenu est sécurisé avec des ACL et l’architecture mutualisée est appliquée via RBAC.
- Les enregistrements des détails des appels, qui sont l’historique des activités, par exemple l’historique des appels, les sessions de messagerie instantanée, le partage d’application, l’historique de la messagerie instantanée, peuvent également être stockés dans Exchange Online, mais la plupart des enregistrements des détails des appels sont stockés temporairement sur les serveurs d’enregistrement des détails des appels. Le contenu n’est pas partitionné par client, mais l’architecture mutualisée est appliquée via RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online dispose de plusieurs mécanismes indépendants qui permettent d’isoler les données. Il stocke les objets en tant que code abstrait dans les bases de données d’application. Par exemple, lorsqu’un utilisateur télécharge un fichier vers SharePoint Online, le fichier est décomposé, traduit en code d’application et stocké dans plusieurs tables sur plusieurs bases de données.

Si un utilisateur peut accéder directement au stockage qui contient les données, le contenu ne peut pas être interprété par une personne ou un système autre que SharePoint Online. Ces mécanismes incluent le contrôle d’accès de sécurité et les propriétés. Toutes les ressources SharePoint Online sont sécurisées par le code d’autorisation et la stratégie RBAC, y compris au sein d’un client. La liste de contrôle d’accès (ACL) qui sécurise une ressource contient une identité authentifiée au niveau du client. Les données SharePoint Online d’un client sont limitées aux identités authentifiées par le fournisseur d’authentification pour le client.

En plus des ACL, une propriété de niveau client qui spécifie le fournisseur d’authentification (qui est l’Azure AD spécifique au client), est écrite une seule fois et ne peut pas être modifiée. Une fois que la propriété client du fournisseur d’authentification a été définie pour un client, elle ne peut plus être modifiée à l’aide de n’importe quelle API exposée à un client.

Un *SubscriptionId* unique est utilisé pour chaque client. Tous les sites client appartiennent à un client et un *SubscriptionId* unique lui est attribué. La propriété *SubscriptionId* sur un site est écrite une fois et est permanente. Une fois affecté à un client, un site ne peut pas être déplacé vers un autre client. Le *SubscriptionId* est la clé utilisée pour créer l’étendue de sécurité pour le fournisseur d’authentification et est liée au client.

SharePoint Online utilise SQL Server et le stockage Azure pour le stockage de métadonnées de contenu. La clé de partition pour le magasin de contenu est *siteid* dans SQL. Lors de l’exécution d’une requête SQL, SharePoint Online utilise un *siteid* vérifié dans le cadre d’une vérification *SubscriptionId* au niveau du client.

SharePoint Online stocke le contenu de fichier chiffré dans les objets BLOB Microsoft Azure. Chaque batterie de serveurs SharePoint Online dispose de son propre compte Microsoft Azure et tous les objets BLOB enregistrés dans Azure sont chiffrés individuellement avec une clé stockée dans le magasin de contenu SQL. La clé de chiffrement est protégée dans le code par la couche d’autorisation et n’est pas exposée directement à l’utilisateur final. SharePoint Online dispose d’une surveillance en temps réel pour détecter quand une requête HTTP lit ou écrit des données pour plusieurs clients. L’identité de la demande *SubscriptionId* est suivie par rapport à la *SubscriptionId* de la ressource accédée. Les demandes d’accès aux ressources de plus d’un client ne doivent jamais se produire par les utilisateurs finaux. Les demandes de service dans un environnement mutualisée sont la seule exception. Par exemple, le robot de recherche extrait les modifications de contenu d’une base de données complète en une seule fois. Cela implique généralement l’interrogation de sites de plusieurs clients dans une seule demande de service, ce qui est nécessaire pour des raisons d’efficacité.

## <a name="teams"></a>Équipes

Les données de vos équipes sont stockées différemment, selon le type de contenu. 

Consultez la [session d’enflamme sur l’architecture de Microsoft teams](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) pour une discussion approfondie.

### <a name="core-teams-customer-data"></a>Données client principales teams

Si votre client est approvisionné en Australie, au Canada, dans l’Union européenne, en France, en Allemagne, en Inde, au Japon, en Afrique du Sud, en Corée du Sud, en Suisse (incluant le Liechtenstein), aux Émirats Arabes Unis, au Royaume-Uni ou aux États-Unis, Microsoft stocke les données client suivantes au reste à l’emplacement suivant :

- Les conversations de teams, les conversations d’équipe et de canal, les images, les messages vocaux et les contacts.
- contenu du site SharePoint Online et fichiers stockés dans ce site ;
- Fichiers téléchargés vers OneDrive entreprise ou scolaire.

#### <a name="chat-channel-messages-team-structure"></a>Conversation, messages de canal, structure d’équipe

Chaque équipe dans teams est sauvegardée par un groupe Microsoft 365 et son site SharePoint et sa boîte aux lettres Exchange. Les conversations privées (y compris les conversations de groupe), les messages envoyés dans le cadre d’une conversation dans un canal et la structure des équipes et des canaux sont stockées dans un service de conversation en cours d’exécution dans Azure. Les données sont également stockées dans un dossier masqué dans les boîtes aux lettres des utilisateurs et des groupes pour activer les fonctionnalités de protection des informations.

#### <a name="voicemail-and-contacts"></a>Messagerie vocale et contacts

Les messages vocaux sont stockés dans Exchange. Les contacts sont stockés dans le magasin de données Cloud basé sur Exchange. Exchange et le magasin Cloud Exchange fournissent déjà des données de résidence dans chacun des centres de données régions centres. Pour toutes les équipes, la messagerie vocale et les contacts sont stockés dans le pays pour l’Australie, le Canada, la France, l’Inde, le Japon, les Émirats Arabes Unis, le Royaume-Uni, l’Afrique du Sud, la Corée du Sud, la Suisse (qui inclut le Liechtenstein) et les États-Unis. Pour tous les autres pays, les fichiers sont stockés aux États-Unis, en Europe ou en Asie Pacifique en fonction de l’affinité du client.

#### <a name="images-and-media"></a>Images et médias

Les médias utilisés dans les conversations (à l’exception des fichiers GIF Giphy qui ne sont pas stockés mais sont un lien de référence vers l’URL du service Giphy d’origine, Giphy est un service non-Microsoft) sont stockés dans un service multimédia basé sur Azure qui est déployé aux mêmes emplacements que le service de conversation.

#### <a name="files"></a>Fichiers

Les fichiers (y compris OneNote et wiki) que les partages d’une personne dans un canal sont stockés dans le site SharePoint de l’équipe. Les fichiers partagés dans une conversation privée ou une conversation pendant une réunion ou un appel sont téléchargés et stockés dans le compte OneDrive entreprise ou scolaire de l’utilisateur qui partage le fichier. Exchange, SharePoint et OneDrive fournissent déjà des données de résidence dans chacun des centres de données régions centres. Ainsi, pour les clients existants, tous les fichiers, les blocs-notes OneNote, le contenu wiki teams et les boîtes aux lettres qui font partie de l’expérience de teams sont déjà stockés à l’emplacement basé sur l’affinité de votre client. Les fichiers sont stockés dans le pays pour l’Australie, le Canada, la France, l’Allemagne, l’Inde, le Japon, les Émirats Arabes Unis, le Royaume-Uni, l’Afrique du Sud, la Corée du Sud et la Suisse (qui inclut le Liechtenstein). Pour tous les autres pays, les fichiers sont stockés aux États-Unis, en Europe ou en Asie Pacifique en fonction de l’affinité du client.
