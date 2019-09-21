---
title: Office 365 isolation et contrôle d’accès dans Office 365
ms.author: robmazz
author: robmazz
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
description: 'Résumé : explication de l’isolation et du contrôle d’accès dans les différentes applications d’Office 365.'
ms.openlocfilehash: 541aef20e885f6d7fbd505ffe2fe32a8525999d4
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067360"
---
# <a name="isolation-and-access-control-in-office-365"></a>Isolation et contrôle d’accès dans Office 365

Azure Active Directory et Office 365 utilisez un modèle de données hautement complexe qui inclut des dizaines de services, des centaines d’entités, des milliers de relations et des dizaines de milliers d’attributs. À un niveau élevé, Azure Active Directory et les annuaires de services sont les conteneurs de clients et de destinataires maintenus synchronisés à l’aide de protocoles de réplication basée sur l’État. En plus des informations d’annuaire stockées dans Azure Active Directory, chacune des charges de travail de service a leur propre infrastructure de services d’annuaire.
 
![Synchronisation des données client Office 365](media/office-365-isolation-tenant-data-sync.png)

Dans ce modèle, il n’existe pas de source unique de données d’annuaire. Systèmes spécifiques qui possèdent des données individuelles, mais aucun système ne contient toutes les données. Les services Office 365 collaborent avec Azure Active Directory dans ce modèle de données. Azure Active Directory est le « système de vérité » pour les données partagées, qui sont généralement des petites et des données statiques utilisées par chaque service. Le modèle fédéré utilisé dans Office 365 et Azure Active Directory fournit la vue partagée des données.

Office 365 utilise à la fois le stockage physique et le stockage cloud Azure. Exchange Online (y compris Exchange Online Protection) et Skype entreprise utilisent leur propre espace de stockage pour les données client. SharePoint Online utilise à la fois le stockage SQL Server et Azure Storage, ce qui nécessite une isolation supplémentaire des données client au niveau du stockage.

## <a name="exchange-online"></a>Exchange Online

Exchange Online stocke les données client dans les boîtes aux lettres. Les boîtes aux lettres sont hébergées dans des bases de données ESE (Extensible Storage Engine) appelées bases de données de boîtes aux lettres. Cela inclut les boîtes aux lettres utilisateur, les boîtes aux lettres liées, les boîtes aux lettres partagées et les boîtes aux lettres de dossiers publics. Les boîtes aux lettres utilisateur incluent le contenu Skype entreprise enregistré, tel que l’historique des conversations.

Le contenu des boîtes aux lettres utilisateur inclut :

- Messages électroniques et pièces jointes
- Calendrier et informations de disponibilité
- Contacts
- Tâches
- Notes
- Groupes
- Données d’inférence

Chaque base de données de boîtes aux lettres dans Exchange Online contient des boîtes aux lettres de plusieurs clients. Un code d’autorisation sécurise chaque boîte aux lettres, y compris au sein d’un client. Par défaut, seul l’utilisateur affecté a accès à une boîte aux lettres. La liste de contrôle d’accès (ACL) qui sécurise une boîte aux lettres contient une identité authentifiée par Azure Active Directory au niveau du client. Les boîtes aux lettres de chaque client sont limitées aux identités authentifiées par rapport au fournisseur d’authentification du client, qui inclut uniquement les utilisateurs de ce client. Le contenu du client A ne peut être obtenu par les utilisateurs dans le client B, sauf s’il est explicitement approuvé par le client A.

## <a name="skype-for-business"></a>Skype Entreprise

Skype entreprise stocke les données à différents endroits :

- Les informations d’utilisateur et de compte, qui incluent les points de terminaison de connexion, les ID de client, les plans de numérotation, les paramètres d’itinérance, l’état de présence, les listes de contacts, etc., sont stockées dans les serveurs Active Directory Skype entreprise et dans différents serveurs de base de données Skype entreprise. Les listes de contacts sont stockées dans la boîte aux lettres Exchange Online de l’utilisateur si l’utilisateur est activé pour les deux produits ou sur les serveurs Skype entreprise si l’utilisateur ne l’est pas. Les serveurs de base de données Skype entreprise ne sont pas partitionnés par client, mais l’isolation mutualisée des données est appliquée via le contrôle d’accès basé sur un rôle (RBAC).
- Le contenu de réunion et les données téléchargées sont stockés sur des partages de système de fichiers distribués (DFS). Ce contenu peut également être archivé dans Exchange Online s’il est activé. Les partages DFS ne sont pas partitionnés par client. le contenu est sécurisé avec des ACL et l’architecture mutualisée est appliquée via RBAC.
- Les enregistrements des détails des appels, qui sont l’historique des activités, par exemple l’historique des appels, les sessions de messagerie instantanée, le partage d’application, l’historique de la messagerie instantanée, peuvent également être stockés dans Exchange Online, mais la plupart des enregistrements des détails des appels sont stockés temporairement sur les serveurs d’enregistrement des détails des appels. Le contenu n’est pas partitionné par client, mais l’architecture mutualisée est appliquée via RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online dispose de plusieurs mécanismes indépendants qui permettent d’isoler les données. Il stocke les objets en tant que code abstrait dans les bases de données d’application. Par exemple, lorsqu’un utilisateur télécharge un fichier vers SharePoint Online, le fichier est décomposé, traduit en code d’application et stocké dans plusieurs tables sur plusieurs bases de données.

Si un utilisateur peut accéder directement au stockage qui contient les données, le contenu ne peut pas être interprété par une personne ou un système autre que SharePoint Online. Ces mécanismes incluent le contrôle d’accès de sécurité et les propriétés. Toutes les ressources SharePoint Online sont sécurisées par le code d’autorisation et la stratégie RBAC, y compris au sein d’un client. La liste de contrôle d’accès (ACL) qui sécurise une ressource contient une identité authentifiée au niveau du client. Les données SharePoint Online d’un client sont limitées aux identités authentifiées par le fournisseur d’authentification pour le client.

En plus des ACL, une propriété de niveau client qui spécifie le fournisseur d’authentification (qui est l’Azure Active Directory propre au client), est écrite une seule fois et ne peut pas être modifiée. Une fois que la propriété client du fournisseur d’authentification a été définie pour un client, elle ne peut plus être modifiée à l’aide de n’importe quelle API exposée à un client.

Un *SubscriptionId* unique est utilisé pour chaque client. Tous les sites client appartiennent à un client et un *SubscriptionId* unique lui est attribué. La propriété *SubscriptionId* sur un site est écrite une fois et est permanente. Une fois affecté à un client, un site ne peut pas être déplacé vers un autre client. Le *SubscriptionId* est la clé utilisée pour créer l’étendue de sécurité pour le fournisseur d’authentification et est liée au client.

SharePoint Online utilise SQL Server et le stockage Azure pour le stockage de métadonnées de contenu. La clé de partition pour le magasin de contenu est *siteid* dans SQL. Lors de l’exécution d’une requête SQL, SharePoint Online utilise un *siteid* vérifié dans le cadre d’une vérification *SubscriptionId* au niveau du client.

SharePoint Online stocke le contenu de fichier chiffré dans les objets BLOB Microsoft Azure. Chaque batterie de serveurs SharePoint Online dispose de son propre compte Microsoft Azure et tous les objets BLOB enregistrés dans Azure sont chiffrés individuellement avec une clé stockée dans le magasin de contenu SQL. La clé de chiffrement est protégée dans le code par la couche d’autorisation et n’est pas exposée directement à l’utilisateur final. SharePoint Online dispose d’une surveillance en temps réel pour détecter quand une requête HTTP lit ou écrit des données pour plusieurs clients. L’identité de la demande *SubscriptionId* est suivie par rapport à la *SubscriptionId* de la ressource accédée. Les demandes d’accès aux ressources de plus d’un client ne doivent jamais se produire par les utilisateurs finaux. Les demandes de service dans un environnement mutualisée sont la seule exception. Par exemple, le robot de recherche extrait les modifications de contenu d’une base de données complète en une seule fois. Cela implique généralement l’interrogation de sites de plusieurs clients dans une seule demande de service, ce qui est nécessaire pour des raisons d’efficacité.
