---
title: URLs et plages d’adresses IP pour Office 365 géré par 21Vianet
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
description: Cet article s’applique à Office 365 géré par 21Vianet en Chine. Cet article répertorie les URLs et plages d’adresses IP utilisées par Office 365 géré par 21Vianet.
hideEdit: true
ms.openlocfilehash: 9767b231a815ef08a97feaa412aee8c5e43c556e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540321"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>URLs et plages d’adresses IP pour Office 365 géré par 21Vianet

 *S’applique à : Office 365 géré par 21Vianet- Administrateur Petite Entreprise, Office 365 géré par 21Vianet-Administrateur*

**Résumé**: les points de terminaison suivants (FQDNs, ports, URL, IPv4 et IPv6 préfixes) s’appliquent à Office 365 géré par 21 Vianet et sont prévus pour fournir des services de productivité aux organisations qui n’utilisent que ces offres.
  
> [!NOTE]
> Microsoft développe un service web basé sur REST pour les entrées d’adresse IP et de FQDN sur cette page. Ce nouveau service vous permettra de configurer et mettre à jour des périphériques de périmètre de réseau tels que des pare-feu et serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste ou modifications spécifiques. Ce service remplacera finalement le document XML sur cette page. Pour essayer ce nouveau service, accédez au [service Web](managing-office-365-endpoints.md#webservice). 
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md)  | *Office 365 géré par 21Vianet* | [Office 365 GermanyOffice 365 U.S. Government DoDOffice 365 U.S. Government GCC High
  
|||
|:-----|:-----|
|**Dernière mise à jour:** 1/8/2018 -![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [abonnement au journal des modifications](http://go.microsoft.com/fwlink/?LinkId=536386)||

Commencez avec[gestion des points de terminaison d’Office 365](managing-office-365-endpoints.md)afin de comprendre nos recommandations pour gérer la connectivité réseau à l’aide de ces données. Les données de points de terminaison sont mises à jour au début de chaque mois avec de nouvelles adresses IP et URLs publiées 30 jours avant d’être activé. Ainsi, pour les clients qui n’ont pas encore de mises à jour automatisées pour compléter leurs processus avant qu’une nouvelle connectivité soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si besoin pour les demandes du support d’adresse, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données contenues dans la page ci-dessous sont générées à partir des services web basés sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au[service Web](managing-office-365-endpoints.md#webservice).

Les données du point de terminaison ci-dessous répertorient la configuration requise pour la connectivité à partir d’ordinateur d’un utilisateur à Office 365. Il n’inclut pas de connexions réseau auprès de Microsoft dans un réseau client, parfois appelées hybrides ou des connexions réseau entrantes.

Les points de terminaison sont regroupées dans quatre zones de service. Les trois premières zones de service peuvent être sélectionnés indépendamment de la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office Online) et doit toujours avoir une connectivité de réseau.

Les colonnes de données affichées sont :

- **ID**: numéro d’identification de la ligne, également connue sous forme d’un jeu de point de terminaison. Cet identification est la même que celle retournée par le service web pour l’ensemble de point de terminaison.

- **Catégorie**:Indique si l’ensemble de point de terminaison est classé «Optimiser», «Autoriser» ou «Par défaut». Vous pouvez lire sur ces catégories et des instructions pour la gestion d’eux en[ http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne répertorie également les ensembles de point de terminaison qui sont nécessaires pour obtenir la connectivité réseau. Pour des ensembles de point de terminaison qui n’ont pas besoin d’avoir de connectivité réseau, nous fournissons des notes dans ce champ pour indiquer quelles fonctionnalités seraient manquantes si l’ensemble de point de terminaison est bloqué. Si vous excluez une zone de service entière, les ensembles de point de terminaison répertoriés comme  requis ne nécessitent pas de connectivité.

- **ER**: C’est un**Oui** si l’ensemble de point de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La Communauté BGP qui inclut les préfixes itinéraire illustrés s’aligne avec la zone de service répertoriée. Quand ER est un**non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de point de terminaison. Toutefois, il ne doit pas être supposé qu’aucun itinéraire n’est annoncé pour un ensemble de point de terminaison où ER est considéré comme un**non**.

- **Adresses**: Répertorie les FQDNs ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de point de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports**: Répertorie les ports TCP ou UDP qui sont combinées avec les adresses pour former le point de terminaison réseau. Vous remarquerez peut-être que certains duplication dans les plages d’adresses IP lorsqu’il y a des ports différents répertoriés.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]


