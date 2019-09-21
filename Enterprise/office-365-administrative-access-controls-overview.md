---
title: Contrôles d’accès des administrateurs dans Office 365
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
description: 'Résumé : vue d’ensemble des contrôles d’accès administratif et de la catégorisation des données d’Office 365.'
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067409"
---
# <a name="administrative-access-controls-in-office-365"></a>Contrôles d’accès des administrateurs dans Office 365 

Microsoft a investi beaucoup dans les systèmes et les contrôles qui automatisent la plupart des opérations Office 365 tout en limitant intentionnellement l’accès au contenu client par Microsoft. Les êtres humains gouvernent le service et le logiciel fonctionne avec le service. Cela permet à Microsoft de gérer Office 365 à l’horizontale et de gérer les risques de menaces internes pour le contenu du client.

Par défaut, les ingénieurs Microsoft ne disposent d'aucun privilège administratif permanent et d'aucun accès permanent au contenu du client dans Office 365. Un ingénieur Microsoft peut disposer d’un accès limité, audité et sécurisé au contenu d’un client pendant une durée limitée. L’accès est uniquement nécessaire pour les opérations de service et uniquement lorsqu’il est approuvé par un membre de la direction générale Microsoft. Pour les clients titulaires d’une licence Lockbox client, le client fournit une approbation d’accès à son contenu hébergé sur Office 365.

Microsoft fournit des services en ligne à l’aide de plusieurs formes de remise en nuage :

- **Nuages publics :** Inclut des versions mutualisées d’Office 365, Azure et d’autres services hébergés en Amérique du Nord, Amérique du Sud, Europe, Asie, Australie, etc.
- **Clouds nationaux :** Comprend tous les nuages souverains et tiers gérés en dehors des États-Unis (sauf ceux notés précédemment), tels que Office 365 en Chine (géré par 21Vianet) et Office 365 en Allemagne (géré par Microsoft, mais sous un modèle dans lequel un tiers de confiance des données, Deutsche Telekom, contrôle et surveille l’accès de Microsoft aux données et systèmes clients qui contiennent des données client).
- **Clouds gouvernementaux :** Inclut Office 365 et Azure services disponibles pour les clients du secteur public américain.

Pour les besoins de cet article, les services Office 365 sont les suivants :

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive Entreprise](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype Entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Contrôles d’accès Office 365

À des fins de contrôle d’accès, Microsoft catégorise les données Office 365 en tant que données client ou d’autres types de données.

### <a name="customer-data"></a>Données client

Les données client sont toutes les données fournies par ou pour le compte d’un client lors de l’utilisation des services Office 365. Il s’agit de contenu client directement créé ou téléchargé par les utilisateurs d’Office 365, notamment :

- Messages électroniques
- Contenu SharePoint Online
- Messages instantanés
- Éléments de calendrier
- Documents
- Contacts
- Les informations identifiables de l’utilisateur final (EUII) (données propres à un utilisateur ou pouvant être liées à un utilisateur individuel, mais qui n’incluent pas de contenu client).

### <a name="other-types-of-data"></a>Autres types de données

Les autres types de données sont les suivants :

- **Données de compte :** Inclut des données d’administration (informations fournies par les administrateurs lorsqu’ils se connectent ou achètent des services) et des données de paiement (informations sur les instruments de paiement, telles que les informations de carte de crédit).
- **Informations identifiables de l’Organisation :** Inclut des données utilisées pour identifier un client, des données d’utilisation et ne pas être lié à un utilisateur individuel ou incluse dans le contenu du client.
- **Métadonnées système :** Inclut des journaux de service qui contiennent des paramètres de configuration, l’état du système, des adresses IP Microsoft et des informations techniques sur les abonnements et les clients.

Microsoft a établi des mécanismes de contrôle d’accès pour s’assurer que personne ne dispose d’un accès non approuvé aux données du client ou aux données de contrôle d’accès. Les données de contrôle d’accès gèrent l’accès à d’autres types de données ou fonctions au sein de l’environnement, y compris l’accès au contenu du client ou EUII, les mots de passe Microsoft, les certificats de sécurité et d’autres données liées à l’authentification. Les mécanismes de contrôle d’accès protègent également contre l’accès physique, logique ou distant non approuvé à l’environnement de production Office 365.

Il existe trois catégories de contrôles d’accès utilisés par Microsoft pour l’exploitation d’Office 365 :

- Contrôles d’isolation
- Contrôles du personnel
- Contrôles technologiques

Lorsqu’ils sont combinés, ces contrôles aident à empêcher et à détecter les actions malveillantes dans Office 365. Outre les contrôles d’isolation, de personnel et de technologie utilisés par Microsoft, il existe une quatrième catégorie de contrôles : ceux mis en œuvre par les clients.

Office 365 vous permet de gérer les données de la même manière que les données sont gérées dans les environnements locaux. La personne qui souscrit une organisation pour Office 365 devient automatiquement administrateur général. L’administrateur global a accès à toutes les fonctionnalités des portails de gestion et peut :

- Créer ou modifier des utilisateurs
- Attribuer des rôles d’administrateur à d’autres personnes
- Réinitialiser les mots de passe utilisateur
- Gérer les licences utilisateur
- Gérer les domaines
- Approuver les demandes de référentiel sécurisé du client

Il est recommandé que chaque organisation configure au moins deux comptes d’administrateur. Pour les grandes organisations d’entreprise, nous recommandons des comptes d’administrateur spécialisés qui remplissent différentes fonctions.

Pour plus d’informations sur l’attribution des rôles et des autorisations d’administrateur, consultez la rubrique [attribution de rôles d’administrateur dans office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) et [à propos des rôles d’administrateur Office 365](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).

## <a name="related-links"></a>Liens connexes

- [Contrôles d’isolation](office-365-isolation-controls.md)
- [Contrôles du personnel](office-365-personnel-controls.md)
- [Contrôles technologiques](office-365-technology-controls.md)
- [Surveillance et audit des contrôles d’accès](office-365-monitoring-and-auditing-access-controls.md)
- [Contrôles d’accès Yammer Entreprise](office-365-yammer-enterprise-access-controls.md)