---
title: Points de terminaison Office 365 de l’Allemagne
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Si votre organisation utilise Office 365 et se limite aux ordinateurs de votre réseau de se connecter à Internet, vous trouverez ci-dessous les points de terminaison (noms de domaine complets, Ports, URL et IPv4 et IPv6 de plages d’adresses) que vous devez inclure dans votre sortant autoriser les listes vérifier votre les ordinateurs peuvent utiliser Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540318"
---
# <a name="office-365-germany-endpoints"></a>Points de terminaison Office 365 de l’Allemagne

 *S’applique à : Administration d’Office 365*

**Résumé :** Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients qui utilisent uniquement des plans **Office 365 Allemagne** .
  
> [!NOTE]
> Microsoft développe un service web basée sur REST pour l’adresse IP et les entrées de nom de domaine complet de cette page. Ce nouveau service vous aideront à configurer et mettre à jour des périphériques de périmètre de réseau tels que des pare-feu et des serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste, ou les modifications spécifiques. Ce service remplacera le document XML, flux RSS et l’adresse IP et les entrées de nom de domaine complet de cette page. Pour essayer ce nouveau service, accédez au [service Web](managing-office-365-endpoints.md#webservice). 
  
 **Points de terminaison office 365 :** [Dans le monde (y compris GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 exploité par 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Allemagne* | [Office 365 US gouvernement DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 US gouvernement GCC haute](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [liste des modifications apportées aux points de terminaison Office 365 Allemagne](office-365-germany-endpoints-change-log.md)||

Commencer avec les [systèmes d’extrémité gérer Office 365](managing-office-365-endpoints.md) à comprendre nos recommandations pour la gestion de la connectivité réseau à l’aide de ces données. Données de points de terminaison sont mis à jour au début de chaque mois avec de nouvelles adresses IP et les URL publiées 30 jours avant active. Cela permet aux clients qui ne pas mais ont des mises à jour pour effectuer leurs processus avant nouvelle connectivité automatisées. Points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour permettre l’escalade prise en charge, incidents de sécurité ou autres exigences opérationnelles immédiates. Vous pouvez toujours consulter la [liste des modifications apportées aux points de terminaison Office 365 Allemagne](office-365-germany-endpoints-change-log.md).

Les données affichées sur cette page ci-dessous sont générées à partir des services web basées sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez introduire directement au [service Web](managing-office-365-endpoints.md#webservice) .

Données de point de terminaison ci-dessous répertorient la configuration requise pour la connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Il n’inclut pas les connexions réseau à partir de Microsoft dans un réseau client, parfois appelé hybride ou les connexions réseau entrantes.

Les points de terminaison sont regroupées dans quatre zones de service. Les zones trois service premières peuvent être sélectionnés séparément pour la connectivité. La quatrième zone service est une dépendance courantes (appelée Office Online et Microsoft 365 courants) et doit toujours avoir la connectivité réseau.

Colonnes de données affichées sont les suivants :

- **ID**: numéro d’identification de la ligne, également appelée un ensemble de point de terminaison. Cet ID est identique à celle renvoyée par le service web pour l’ensemble du point de terminaison.

- **Catégorie**: indique si l’ensemble du point de terminaison est répertorié comme « Optimiser », « Autoriser » ou « Default ». Vous pouvez en savoir plus sur ces catégories et des conseils pour la gestion d’en [http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne affiche également les ensembles de point de terminaison sont requis pour la connectivité réseau. Pour les jeux de point de terminaison qui n’est pas requises pour disposent d’une connectivité réseau, nous fournir des notes dans ce champ pour indiquer les fonctionnalités serait manquantes si l’ensemble du point de terminaison est bloqué. Si vous sont à l’exception d’une zone de service, les jeux de point de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER**: il s’agit **Oui** si l’ensemble du point de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire illustrés s’aligne sur la zone service répertoriée. Lors de la restauration d’urgence est **non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de point de terminaison. Toutefois, il ne doit pas en être supposé qu’aucuns itinéraires ne sont publiés pour un jeu de point de terminaison où ER est **non**.

- **Adresses**: répertorie les noms de domaine complets ou noms de domaine générique et les plages d’adresses IP pour l’ensemble du point de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut-être inclure le nombre d’adresses IP spécifiques du réseau spécifié.
 
- **Ports**: répertorie les ports TCP ou UDP sont combinées avec les adresses de point de terminaison du réseau de formulaire. Vous pouvez remarquer des valeurs en double dans les plages d’adresses IP où il existe différents ports répertoriés.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

