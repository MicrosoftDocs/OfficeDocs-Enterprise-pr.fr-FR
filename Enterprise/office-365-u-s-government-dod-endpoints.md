---
title: Points de terminaison US gouvernement DoD Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/17/2019
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
ms.openlocfilehash: 87577b62e4180d74652e973e2a4644536bbf4cea
ms.sourcegitcommit: 0c4f50aa55699b8390038efbb8b50dbe10f3eefe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28723391"
---
# <a name="office-365-us-government-dod-endpoints"></a>Points de terminaison US gouvernement DoD Office 365

*S’applique à : Administration d’Office 365*

 **Résumé :** Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients qui utilisent uniquement des plans Office 365 US gouvernement DoD.
  
> [!NOTE]
> Microsoft a publié un service web utilisant REST pour les entrées d’adresse IP et de FQDN sur cette page. Ce nouveau service vous permettra de configurer et de mettre à jour des périphériques de périmètre de réseau, tels que des pare-feu et serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste ou des modifications spécifiques. Ce service remplace le document XML dont le lien est fourni sur cette page et qui est obsolète depuis le 2 octobre 2018. Pour essayer ce nouveau service, accédez au [service web](office-365-ip-web-service.md).
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md) | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 01/17/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [abonnement du journal des modifications](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Télécharger :** la liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Commencer avec les [systèmes d’extrémité gérer Office 365](managing-office-365-endpoints.md) à comprendre nos recommandations pour la gestion de la connectivité réseau à l’aide de ces données. Données de points de terminaison sont mis à jour au début de chaque mois avec de nouvelles adresses IP et les URL publiées 30 jours avant active. Cela permet aux clients ayant mais pas encore ont des mises à jour pour effectuer leurs processus avant nouvelle connectivité automatisées. Points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour permettre l’escalade prise en charge, incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont générées à partir des services web basées sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez introduire directement au [service Web](office-365-ip-web-service.md) .

Les données de point de terminaison ci-dessous répertorient les exigences de connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Elles n’incluent pas les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides.

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office Online) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER**: il s’agit **Oui** si l’ensemble du point de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire illustrés s’aligne sur la zone service répertoriée. Lors de la restauration d’urgence est **non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de point de terminaison. Toutefois, il ne doit pas en être supposé qu’aucuns itinéraires ne sont publiés pour un jeu de point de terminaison où ER est **non**. Si vous prévoyez d’utiliser Azure AD Connect, lisez la [section Considérations spéciales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) pour vous assurer que vous disposez approprié configuration Azure AD se connecter.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports** : répertorie les ports TCP ou UDP associés aux adresses pour former le point de terminaison réseau. Vous remarquerez peut-être certains doublons dans les plages d’adresses IP lorsque plusieurs ports sont répertoriés.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Remarques à propos de ce tableau :

- La sécurité et le centre de conformité (SCC) prend en charge ExpressRoute Azure pour Office 365. Vaut pour de nombreuses fonctionnalités exposées par le biais du SCC telles que création de rapports, audit, eDiscovery avancée, DLP unifiée et gouvernance de données. Deux fonctionnalités spécifiques, importation PST et eDiscovery exporter, actuellement ne prennent pas charge ExpressRoute Azure avec uniquement les filtres de routage Office 365 en raison de leur dépendance sur le stockage Blob Azure. Pour utiliser ces fonctionnalités, vous devez connectivité séparée pour le stockage Blob Azure à l’aide des options de connectivité Azure pris en charge qui incluent la connectivité Internet ou ExpressRoute Azure avec des filtres d’itinéraires Public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour les deux de ces fonctionnalités. L’équipe de Protection des informations Office 365 a connaissance de cette limitation et travaille activement pour remettre prise en charge des ExpressRoute Azure pour Office 365 comme limitée à des filtres de routage Office 365 pour les deux de ces fonctionnalités.

- Il existe facultatifs points de terminaison supplémentaires pour Office 365 ProPlus qui ne figurent pas et ne sont pas nécessaires aux utilisateurs de lancer des applications Office 365 ProPlus et modifier des documents. Points de terminaison facultatifs sont hébergées dans des centres de données Microsoft et ne pas traiter, transmettre ou stocker les données du client. Il est recommandé que les connexions utilisateur à ces points de terminaison redirigés vers le périmètre de sortie Internet par défaut.
