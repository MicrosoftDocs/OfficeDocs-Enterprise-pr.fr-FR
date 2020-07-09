---
title: Autres exigences en matière de sécurité réseau pour Office 365 GCC High et DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Résumé : Office 365 GCC High et DoD ont des exigences de sécurité réseau supplémentaires'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371630"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Autres exigences en matière de sécurité réseau pour Office 365 GCC High et DOD

*Cet article s’applique à Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High et Microsoft 365 DOD.*

Office 365 GCC High et DOD sont des environnements de Cloud sécurisés pour répondre aux besoins du gouvernement des États-Unis et de ses fournisseurs et sous-traitants.  Ces environnements Cloud ont des restrictions réseau supplémentaires auxquelles les services sont autorisés à accéder.

Les clients de GCC High et DOD qui prévoient d’utiliser des identités fédérées ou une coexistence hybride peuvent exiger que Microsoft autorise l’accès entrant et/ou sortant à vos déploiements locaux existants.  Voici des exemples de ces activités :

* Utilisation d’identités fédérées (avec les services ADFS (Active Directory Federation Services) ou un STS pris en charge similaire)
* Coexistence hybride avec un déploiement Exchange Server ou Skype entreprise local
* Migration de contenu utilisateur existant à partir d’un système local

Pour permettre au service de communiquer avec vos points de terminaison locaux, vous **devez** envoyer un message électronique à Office 365 Engineering pour les modifications réseau.

> [!WARNING]
> Toutes les demandes ont un contrat SLA de **trois semaines** et ne peuvent pas être accélérées en raison des contrôles de sécurité et de conformité et des pipelines de déploiement requis.  Cela inclut les requêtes réseau de l’intégration initiale ainsi que toutes les modifications une fois que vous avez effectué la migration vers le service.  Assurez-vous que les équipes réseau connaissent cette chronologie et l’incluent dans leurs cycles de planification.

Veuillez envoyer un e-mail à la [liste d’autorisation du réseau gouvernemental Office 365](mailto:o365gwlt@microsoft.com) avec les informations suivantes :

* **Vers**: [liste d’autorisation du réseau gouvernemental Office 365](mailto:o365gwlt@microsoft.com)
* **De**: un administrateur de client : le courrier électronique d’envoi **doit** correspondre à un contact d’administrateur global dans votre client.
* **Message**de l’objet : Office 365 GCC High Network Request-contoso.onmicrosoft.US (remplacez ceci par le nom de votre client)

Le corps de votre message doit inclure les données suivantes :

* Votre nom de client Microsoft Online Services (par exemple, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Une liste de distribution de courrier électronique avec laquelle Microsoft communiquera pour les communications en cours liées aux changements de réseau et/ou au suivi des sous-réseaux non valides
* Indiquer si vous envisagez d’utiliser la coexistence hybride Microsoft teams avec vos déploiements locaux
* URL du système d’identité fédéré accessible en externe (par exemple, sts.contoso.com) et plage d’adresses IP dans la notation CIDR (par exemple, 10.1.1.0/28)
* URL de la liste de révocation de certificats PKI sur site et plage d’adresses IP dans la notation CIDR
* URL et plage d’adresses IP accessibles en externe pour le déploiement local d’Exchange Server dans la notation CIDR
* URL accessible en externe et plage d’adresses IP pour le déploiement local de Skype entreprise dans la notation CIDR

Pour des raisons de sécurité et de conformité, gardez à l’esprit les restrictions suivantes sur votre demande :

* Il existe quatre limitations de sous-réseau par client
* Les sous-réseaux doivent être en notation CIDR (par exemple, 10.1.1.0/28)
* Les plages de sous-réseau ne peuvent pas dépasser/24
* Nous **ne pouvons pas** prendre en charge les demandes pour autoriser l’accès aux services Cloud commerciaux (Office 365, Google G-suite, les services Web Amazon, etc.)

Une fois que votre demande a été reçue et approuvée par Microsoft, il existe un contrat SLA de trois semaines pour l’implémentation et ne peut pas être accéléré.  Vous recevrez un accusé de réception initial lorsque nous aurons reçu votre demande et un accusé de réception final une fois qu’elle est terminée.
