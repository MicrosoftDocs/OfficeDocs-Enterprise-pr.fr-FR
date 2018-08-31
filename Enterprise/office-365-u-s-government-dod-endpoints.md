---
title: Points de terminaison US gouvernement DoD Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 'Résumé : Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients qui utilisent uniquement des plans Office 365 US gouvernement DoD.'
hideEdit: true
ms.openlocfilehash: 3faca62176b1467829f0333b76a57ce0d5124a96
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540340"
---
# <a name="office-365-us-government-dod-endpoints"></a>Points de terminaison US gouvernement DoD Office 365

*S’applique à : Administration d’Office 365*

 **Résumé :** Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients qui utilisent uniquement des plans Office 365 US gouvernement DoD.
  
> [!NOTE]
> Microsoft développe un service web basée sur REST pour l’adresse IP et les entrées de nom de domaine complet de cette page. Ce nouveau service vous aideront à configurer et mettre à jour des périphériques de périmètre de réseau tels que des pare-feu et des serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste, ou les modifications spécifiques. Ce service remplacera le document XML, flux RSS et l’adresse IP et les entrées de nom de domaine complet de cette page. Pour essayer ce nouveau service, accédez au [service Web](managing-office-365-endpoints.md#webservice).
  
 **Points de terminaison office 365 :** [Dans le monde (y compris GCC)](urls-and-ip-address-ranges.md)  |  [Office 365 exploité par 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Allemagne](office-365-germany-endpoints.md) | *Office 365 US gouvernement DoD* | [Office 365 US gouvernement GCC haute](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [abonnement du journal des modifications](https://aka.ms/dodendpointrss) <br/> |**Télécharger :** la liste complète au [format XML](https://aka.ms/usdodendpoints) <br/> |
   
 Commencer avec les [systèmes d’extrémité gérer Office 365](managing-office-365-endpoints.md) à comprendre nos recommandations pour la gestion de la connectivité réseau à l’aide de ces données. Données de points de terminaison sont mis à jour au début de chaque mois avec de nouvelles adresses IP et les URL publiées 30 jours avant active. Cela permet aux clients qui ne pas mais ont des mises à jour pour effectuer leurs processus avant nouvelle connectivité automatisées. Points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour permettre l’escalade prise en charge, incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont générées à partir des services web basées sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez introduire directement au [service Web](managing-office-365-endpoints.md#webservice) .

Données de point de terminaison ci-dessous répertorient la configuration requise pour la connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Il n’inclut pas les connexions réseau à partir de Microsoft dans un réseau client, parfois appelé hybride ou les connexions réseau entrantes.

Les points de terminaison sont regroupées dans quatre zones de service. Les zones trois service premières peuvent être sélectionnés séparément pour la connectivité. La quatrième zone service est une dépendance courantes (appelée Office Online et Microsoft 365 courants) et doit toujours avoir la connectivité réseau.

Colonnes de données affichées sont les suivants :

- **ID**: numéro d’identification de la ligne, également appelée un ensemble de point de terminaison. Cet ID est identique à celle renvoyée par le service web pour l’ensemble du point de terminaison.

- **Catégorie**: indique si l’ensemble du point de terminaison est répertorié comme « Optimiser », « Autoriser » ou « Default ». Vous pouvez en savoir plus sur ces catégories et des conseils pour la gestion d’en [http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne affiche également les ensembles de point de terminaison sont requis pour la connectivité réseau. Pour les jeux de point de terminaison qui n’est pas requises pour disposent d’une connectivité réseau, nous fournir des notes dans ce champ pour indiquer les fonctionnalités serait manquantes si l’ensemble du point de terminaison est bloqué. Si vous sont à l’exception d’une zone de service, les jeux de point de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER**: il s’agit **Oui** si l’ensemble du point de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire illustrés s’aligne sur la zone service répertoriée. Lors de la restauration d’urgence est **non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de point de terminaison. Toutefois, il ne doit pas en être supposé qu’aucuns itinéraires ne sont publiés pour un jeu de point de terminaison où ER est **non**. Si vous prévoyez d’utiliser Azure AD Connect, lisez la [section Considérations spéciales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) pour vous assurer que vous disposez approprié configuration Azure AD se connecter.

- **Adresses**: répertorie les noms de domaine complets ou noms de domaine générique et les plages d’adresses IP pour l’ensemble du point de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut-être inclure le nombre d’adresses IP spécifiques du réseau spécifié.
 
- **Ports**: répertorie les ports TCP ou UDP sont combinées avec les adresses de point de terminaison du réseau de formulaire. Vous pouvez remarquer des valeurs en double dans les plages d’adresses IP où il existe différents ports répertoriés.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Remarques à propos de ce tableau :

- La sécurité et le centre de conformité (SCC) prend en charge ExpressRoute Azure pour Office 365. Vaut pour de nombreuses fonctionnalités exposées par le biais du SCC telles que création de rapports, audit, eDiscovery avancée, DLP unifiée et gouvernance de données. Deux fonctionnalités spécifiques, importation PST et eDiscovery exporter, actuellement ne prennent pas charge ExpressRoute Azure avec uniquement les filtres de routage Office 365 en raison de leur dépendance sur le stockage Blob Azure. Pour utiliser ces fonctionnalités, vous devez connectivité séparée pour le stockage Blob Azure à l’aide des options de connectivité Azure pris en charge qui incluent la connectivité Internet ou ExpressRoute Azure avec des filtres d’itinéraires Public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour les deux de ces fonctionnalités. L’équipe de Protection des informations Office 365 a connaissance de cette limitation et travaille activement pour remettre prise en charge des ExpressRoute Azure pour Office 365 comme limitée à des filtres de routage Office 365 pour les deux de ces fonctionnalités.

- Il existe facultatifs points de terminaison supplémentaires pour Office 365 ProPlus qui ne figurent pas et ne sont pas nécessaires aux utilisateurs de lancer des applications Office 365 ProPlus et modifier des documents. Points de terminaison facultatifs sont hébergées dans des centres de données Microsoft et ne pas traiter, transmettre ou stocker les données du client. Il est recommandé que les connexions utilisateur à ces points de terminaison redirigés vers le périmètre de sortie Internet par défaut.