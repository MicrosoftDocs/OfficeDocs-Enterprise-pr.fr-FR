---
title: Contrôles de technologie Office 365
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
description: 'Résumé : vue d’ensemble des pratiques de contrôle technologique de Microsoft pour Office 365.'
ms.openlocfilehash: 1ddf4efdd8e2c2159f6d6c55cfeead1cfbd54395
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067381"
---
# <a name="office-365-technology-controls"></a>Contrôles de technologie Office 365 

Microsoft utilise plusieurs outils et technologies pour contrôler, gérer et auditer l’accès aux données client dans ses services en ligne. Ceux-ci s’appliquent à Exchange Online, SharePoint Online, Lockbox et Lockbox client, l’authentification multifacteur, et bien plus encore. Yammer utilise des contrôles similaires décrits dans [Yammer Enterprise Access Controls](office-365-yammer-enterprise-access-controls.md).

Les ingénieurs Office 365 disposent d’un accès permanent aux données client d’Office 365. Les ingénieurs doivent passer par un processus d’approbation Microsoft avant d’accéder aux données client pour les opérations de service. Si le client accorde la fonctionnalité de référentiel sécurisé client pour Exchange Online et SharePoint Online, l’accès aux données client nécessite l’approbation du client. Une fois approuvées, les comptes d’administration spécifiques aux services sont accessibles uniquement en temps réel pour les tâches requises par la demande de service.

## <a name="lockbox-and-customer-lockbox"></a>Bte post.

Bien que rare, un client peut demander de l’aide de Microsoft qui expose du contenu client à un ingénieur Microsoft. Pour contrôler l’accès à Exchange Online, Microsoft utilise un système de contrôle d’accès appelé Lockbox. Avant qu’un ingénieur Microsoft accède à des données ou des systèmes Exchange Online ou SharePoint Online, il doit soumettre une demande d’accès à l’aide de la boîte postale. Toutes les demandes de service pour Exchange Online et SharePoint Online sont gérées par le système bte post. Avec la zone de gestion des référentiels et le référentiel sécurisé client, tous les accès approuvés sont suivis à un utilisateur unique, ce qui rend les ingénieurs responsables de la gestion des données client.

> [!NOTE]
> Exchange Online inclut toutes les données Skype entreprise stockées dans les boîtes aux lettres des utilisateurs. La couverture Skype entreprise n’inclut pas les enregistrements de diffusion de réunion Skype ni le contenu téléchargé vers les réunions par les utilisateurs. SharePoint Online inclut OneDrive entreprise.

Lockbox traite les demandes d’autorisations qui accordent aux ingénieurs la possibilité d’exécuter des fonctions opérationnelles et administratives au sein du service. Les ingénieurs envoient des demandes par le biais du référentiel sécurisé et un responsable Microsoft doit approuver la demande avant que l’ingénieur puisse accéder aux données client. Après l’approbation du responsable, l’ingénieur dispose d’un accès limité au temps et limité à l’étendue aux données client pour fonctionner sur le problème du client.

Customer Lockbox for Office 365 vous aide à respecter les obligations de conformité si vous avez besoin de procédures en place pour autoriser l’accès aux données de façon explicite. Il s’agit d’une condition requise pour certaines normes de conformité, telles que FedRAMP et HIPAA. Le référentiel sécurisé du client vous insère dans le processus d’approbation de la boîte de réception et vous offre la possibilité de contrôler l’autorisation de Microsoft Access à votre contenu Exchange Online ou SharePoint Online pour les opérations de service.

Dans l’exemple rare où un ingénieur de service Microsoft a besoin d’accéder à vos données, vous autorisez uniquement l’accès aux données requises pour résoudre le problème et pour une durée limitée. Si vous rejetez une demande d’accès, les ingénieurs Microsoft n’ont pas accès à votre contenu et ne pourront pas effectuer les opérations de service. Si vous approuvez la demande, les ingénieurs Microsoft disposent d’un accès limité en temps réel à votre contenu via des interfaces de gestion contrôlées et contraintes.

Les actions effectuées par l’ingénieur du support technique sont consignées à des fins d’audit et sont accessibles via l' [API activité de gestion d’Office 365](https://msdn.microsoft.com/library/office/dn707383.aspx) et le [Centre de sécurité et de conformité](http://protection.office.com/).

>[!NOTE]
> Le référentiel sécurisé du client est disponible dans [Office 365 entreprise E5](https://products.office.com/business/office-365-enterprise-e5-business-software) en tant qu’achat de complément. Pour plus d'informations, voir [Demandes Customer Lockbox dans Office 365](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2).

## <a name="just-in-time-access"></a>Accès juste-à-temps

Microsoft utilise le principe d’accès juste-à-temps (JIT) pour Office 365 afin de limiter les risques de falsification des informations d’identification et les attaques latérales. JIT supprime l’accès administratif permanent aux services et remplace les droits avec la possibilité d’élever ces rôles à la demande. La suppression des droits d’accès permanents des administrateurs garantit que les informations d’identification sont disponibles uniquement lorsqu’elles sont nécessaires et réduit les risques de vol d’informations d’identification.

Le modèle d’accès JIT exige des ingénieurs qui demandent des privilèges élevés pour une période limitée afin d’effectuer des tâches d’administration. En outre, les ingénieurs utilisent des comptes temporaires créés avec des mots de passe complexes générés par l’ordinateur et accordent uniquement les rôles leur permettant d’effectuer les tâches nécessaires. Par exemple, l’accès administratif accordé par la boîte de réception est lié au temps et la durée d’accès octroyée dépend du rôle demandé. Un technicien spécifie la durée d’accès requise dans la demande au système bte post. Le système de boîte postale scellée rejette les demandes lorsque le temps demandé dépasse la durée maximale autorisée pour l’élévation. Après l’expiration, l’accès administratif est supprimé et le compte temporaire expire.

Lorsqu’ils sont autorisés et approuvés pour Access, les ingénieurs reçoivent un mot de passe d’administration unique en utilisant le système d’autorisation. Les nouveaux mots de passe sont générés chaque fois qu’une demande d’accès élevé est approuvée. Le mot de passe est copié dans un mot de passe sûr, il est distinct des informations d’identification de l’ingénieur pour l’environnement d’entreprise Microsoft et n’est adapté qu’à la session d’accès élevé approuvée.

## <a name="constrained-management-interfaces"></a>Interfaces de gestion contraintes

Les ingénieurs utilisent deux interfaces de gestion pour effectuer des tâches d’administration : le Bureau à distance via des passerelles de services Terminal Server sécurisées (TSGs) et PowerShell à distance. Au sein de ces interfaces de gestion, les stratégies logicielles et les contrôles d’accès placent des restrictions importantes sur les applications exécutées et sur les commandes et les cmdlets disponibles.

Les serveurs Office 365 restreignent les sessions simultanées à une session administrateur d’équipe par service, par serveur. TSGs n’autorise qu’une seule session simultanée pour les utilisateurs et n’autorise pas plusieurs sessions. À l’aide d’une seule session par serveur, TSGs permet aux administrateurs de services Office 365 de se connecter à plusieurs serveurs simultanément afin que les administrateurs puissent effectuer leurs tâches de manière efficace. Les administrateurs d’équipe de service n’ont pas d’autorisations sur le TSGs eux-mêmes. Le TSG est utilisé uniquement pour appliquer les exigences en matière d’authentification multifacteur (MFA) et de chiffrement. Une fois que l’administrateur de l’équipe de service se connecte à un serveur spécifique via un TSG, le serveur spécifique applique une limite de session d’un par administrateur.

Les restrictions d’utilisation et les exigences de connexion et de configuration pour le personnel Office 365 sont établies par les stratégies de groupe Active Directory. Ces stratégies incluent les caractéristiques suivantes :

- TSGs utilisent uniquement le chiffrement validé [FIPS](https://www.microsoft.com/en-us/TrustCenter/Compliance/FIPS) 140-2.
- Les sessions TSG se déconnectent au bout de 30 minutes d’inactivité.
- Les sessions TSG se déconnectent automatiquement après 24 heures.

Les connexions à TSGs nécessitent également l’authentification multifacteur à l’aide d’une carte à puce physique distincte et d’un compte distinct des informations d’identification d’entreprise Microsoft. Les ingénieurs reçoivent différentes cartes à puce pour différentes plateformes de gestion de plateformes et de secrets pour garantir le stockage sécurisé des informations d’identification. TSGs utilisez les stratégies de groupe Active Directory pour contrôler qui peut se connecter à des serveurs distants, le nombre de sessions autorisées et les paramètres de délai d’inactivité. Les stratégies supplémentaires limitent l’accès aux applications autorisées et limitent l’accès à Internet.

En plus de l’accès à distance à l’aide de TSGs spécialement configurés, Exchange Online permet aux utilisateurs disposant du rôle d’ingénieur de service d’accéder à certaines fonctionnalités administratives sur des serveurs de production à l’aide de PowerShell à distance. Pour ce faire, l’utilisateur doit être autorisé à accéder en lecture seule (débogage) à l’environnement de production Office 365. L’escalade des privilèges est activée de la même manière que pour TSGs à l’aide du processus bte post.

Pour l’accès à distance, chaque centre de contenu dispose d’une adresse IP virtuelle à charge équilibrée qui sert de point d’accès unique. Les cmdlets PowerShell distantes disponibles sont basées sur le niveau de privilège identifié dans la revendication d’accès obtenue lors de l’authentification. Ces applets de commande fournissent la seule fonctionnalité administrative accessible aux utilisateurs qui se connectent à l’aide de cette méthode. Remote PowerShell limite l’étendue des commandes disponibles pour l’ingénieur et s’appuie sur le niveau d’accès accordé via le processus de la boîte de réception. Par exemple, dans Exchange Online, Get-Mailbox peut être disponible, mais pas Set-Mailbox.
