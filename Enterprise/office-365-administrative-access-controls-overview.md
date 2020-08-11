---
title: Contrôles d’accès administratif dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Cet article fournit une vue d’ensemble des contrôles d’accès administratifs et de la catégorisation des données dans Microsoft 365.
ms.openlocfilehash: 58cbc7ebea3edb66f5d48d282a3e6995b247a044
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606710"
---
# <a name="administrative-access-controls-in-microsoft-365"></a>Contrôles d’accès administratif dans Microsoft 365 

Microsoft a investi beaucoup de systèmes et de contrôles qui automatisent la plupart des opérations Microsoft 365, tout en limitant intentionnellement l’accès au contenu client par Microsoft. Les êtres humains gouvernent le service et le logiciel fonctionne avec le service. Cela permet à Microsoft de gérer Microsoft 365 à l’horizontale et de gérer les risques de menaces internes pour le contenu du client.

Par défaut, les ingénieurs Microsoft disposent de zéro privilège administratif permanent et d’un accès permanent au contenu client dans Microsoft 365. Un ingénieur Microsoft peut disposer d’un accès limité, audité et sécurisé au contenu d’un client pendant une durée limitée. L’accès est uniquement nécessaire pour les opérations de service et uniquement lorsqu’il est approuvé par un membre de la direction générale Microsoft. Pour les clients titulaires d’une licence Lockbox client, le client fournit une approbation d’accès à son contenu hébergé sur Microsoft 365.

Microsoft fournit des services en ligne à l’aide de plusieurs formes de remise en nuage :

- **Nuages publics :** Inclut des versions mutualisées de Microsoft 365, Azure et d’autres services hébergés en Amérique du Nord, en Amérique du Sud, en Europe, en Asie, en Australie, etc.
- **Clouds nationaux :** Comprend tous les nuages souverains et tiers gérés en dehors des États-Unis (sauf ceux notés précédemment), tels que Microsoft 365 en Chine (géré par 21Vianet) et Microsoft 365 en Allemagne (géré par Microsoft, mais sous un modèle dans lequel un tiers de confiance des données, Deutsche Telekom, contrôle et surveille l’accès de Microsoft aux données et systèmes clients qui contiennent des données client).
- **Clouds gouvernementaux :** Inclut Microsoft 365 et Azure services disponibles pour les clients gouvernementaux des États-Unis.

Pour les besoins de cet article, les services Microsoft 365 sont les suivants :

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive Entreprise](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype Entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="microsoft-365-access-controls"></a>Contrôles d’accès Microsoft 365

À des fins de contrôle d’accès, Microsoft catégorise les données Microsoft 365 en tant que données client ou d’autres types de données.

### <a name="customer-data"></a>Données client

Les données client sont toutes les données fournies par ou pour le compte d’un client lors de l’utilisation des services Microsoft 365. Il s’agit de contenu client directement créé ou téléchargé par les utilisateurs de Microsoft 365, notamment :

- Messages électroniques
- Contenu SharePoint Online
- Messages instantanés
- Éléments de calendrier
- Documents
- Contacts
- Informations identifiables par l’utilisateur final (EUII) (données propres à un utilisateur ou pouvant être liées à un utilisateur individuel, mais n’incluant pas de contenu client)

### <a name="other-types-of-data"></a>Autres types de données

Les autres types de données sont les suivants :

- **Données de compte :** Inclut des données d’administration (informations fournies par les administrateurs lorsqu’ils se connectent ou achètent des services) et des données de paiement (informations sur les instruments de paiement, telles que les informations de carte de crédit).
- **Informations identifiables de l’Organisation :** Inclut des données utilisées pour identifier un client, des données d’utilisation et ne pas être lié à un utilisateur individuel ou incluse dans le contenu du client.
- **Métadonnées système :** Inclut des journaux de service qui contiennent des paramètres de configuration, l’état du système, des adresses IP Microsoft et des informations techniques sur les abonnements et les clients.

Microsoft a établi des mécanismes de contrôle d’accès pour s’assurer que personne ne dispose d’un accès non approuvé aux données du client ou aux données de contrôle d’accès. Les données de contrôle d’accès gèrent l’accès à d’autres types de données ou fonctions au sein de l’environnement, y compris l’accès au contenu du client ou EUII, les mots de passe Microsoft, les certificats de sécurité et d’autres données liées à l’authentification. Les mécanismes de contrôle d’accès protègent également contre les accès physiques, logiques ou distants non approuvés à l’environnement de production Microsoft 365.

Il existe trois catégories de contrôles d’accès utilisés par Microsoft pour l’exploitation de Microsoft 365 :

- Contrôles d’isolation
- Contrôles du personnel
- Contrôles de technologie

Lorsqu’ils sont combinés, ces contrôles aident à prévenir et à détecter les actions malveillantes dans Microsoft 365. Outre les contrôles d’isolation, de personnel et de technologie utilisés par Microsoft, il existe une quatrième catégorie de contrôles : ceux mis en œuvre par les clients.

Microsoft 365 vous permet de gérer les données de la même manière que les données sont gérées dans les environnements locaux. La personne qui souscrit une organisation pour Microsoft 365 devient automatiquement un administrateur général. L’administrateur global a accès à toutes les fonctionnalités des portails de gestion et peut :

- Créer ou modifier des utilisateurs
- Attribuer des rôles d’administrateur à d’autres personnes
- Réinitialiser les mots de passe utilisateur
- Gérer les licences utilisateur
- Gérer les domaines
- Approuver les demandes de référentiel sécurisé du client

Il est recommandé que chaque organisation configure au moins deux comptes d’administrateur. Pour les grandes organisations d’entreprise, nous recommandons des comptes d’administrateur spécialisés qui remplissent différentes fonctions.

Pour plus d’informations sur l’attribution des rôles et des autorisations d’administrateur, voir [Assign admin Roles](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles) et [about admin Roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

## <a name="related-links"></a>Liens connexes

- [Contrôles d’isolation](office-365-isolation-controls.md)
- [Contrôles du personnel](office-365-personnel-controls.md)
- [Contrôles technologiques](office-365-technology-controls.md)
- [Surveillance et audit des contrôles d’accès](office-365-monitoring-and-auditing-access-controls.md)
- [Contrôles d’accès de Yammer Entreprise](office-365-yammer-enterprise-access-controls.md)