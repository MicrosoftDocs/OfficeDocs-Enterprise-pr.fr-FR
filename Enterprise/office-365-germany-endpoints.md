---
title: Points de terminaison Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/07/2019
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
ms.openlocfilehash: 05bbcb1cb4e6b90b3f7a61d84ae3488ce97245c2
ms.sourcegitcommit: e3fa9998321f6fa5d31217d107b672258993826e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2019
ms.locfileid: "27746134"
---
# <a name="office-365-germany-endpoints"></a>Points de terminaison Office 365 Germany

 *S’applique à : Administration d’Office 365*

**Résumé :** Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients qui utilisent uniquement des plans **Office 365 Allemagne** .
  
> [!NOTE]
> Microsoft a publié un service web utilisant REST pour les entrées d’adresse IP et de FQDN sur cette page. Ce nouveau service vous permettra de configurer et de mettre à jour des périphériques de périmètre de réseau, tels que des pare-feu et serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste ou des modifications spécifiques. Ce service remplace le document XML dont le lien est fourni sur cette page et qui est obsolète depuis le 2 octobre 2018. Pour essayer ce nouveau service, accédez au [service web](office-365-ip-web-service.md).
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md)  | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 01/07/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [abonnement du journal des modifications](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Commencer avec les [systèmes d’extrémité gérer Office 365](managing-office-365-endpoints.md) à comprendre nos recommandations pour la gestion de la connectivité réseau à l’aide de ces données. Données de points de terminaison sont mis à jour au début de chaque mois avec de nouvelles adresses IP et les URL publiées 30 jours avant active. Cela permet aux clients ayant mais pas encore ont des mises à jour pour effectuer leurs processus avant nouvelle connectivité automatisées. Points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour permettre l’escalade prise en charge, incidents de sécurité ou autres exigences opérationnelles immédiates. Vous pouvez toujours faire pour [Modifier l’abonnement de journal](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Les données affichées sur cette page ci-dessous sont générées à partir des services web basées sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez introduire directement au [service Web](office-365-ip-web-service.md) .

Les données de point de terminaison ci-dessous répertorient les exigences de connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Elles n’incluent pas les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides.

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office Online) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER** : cette option est définie sur **Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire indiqués s’aligne avec la zone de service répertoriée. Quand ER est défini sur **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, le fait qu’ER soit défini sur **Non** ne signifie pas pour autant qu’aucun itinéraire n’est proposé pour un ensemble de points de terminaison.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports**: Répertorie les ports TCP ou UDP qui sont combinées avec les adresses pour former le point de terminaison réseau. Vous remarquerez peut-être que certains duplication dans les plages d’adresses IP lorsqu’il y a des ports différents répertoriés.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

