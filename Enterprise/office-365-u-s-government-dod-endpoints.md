---
title: Points de terminaison DoD du gouvernement américain Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 'Résumé : Office 365 nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients utilisant Office 365 le gouvernement américain DoD plans uniquement.'
hideEdit: true
ms.openlocfilehash: c7b685adc7abfe5f561bdddc484c632780178dad
ms.sourcegitcommit: 653bd752db6be18f2f0d31e5abeb8ad734704772
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "37765708"
---
# <a name="office-365-us-government-dod-endpoints"></a>Points de terminaison DoD du gouvernement américain Office 365

*S’applique à : Office 365 admin*

 **Résumé :** Office 365 nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients utilisant Office 365 le gouvernement américain DoD plans uniquement.
  
> [!NOTE]
> Microsoft a publié un service web utilisant REST pour les entrées d’adresse IP et de FQDN sur cette page. Ce nouveau service vous permettra de configurer et de mettre à jour des périphériques de périmètre de réseau, tels que des pare-feu et serveurs proxy. Vous pouvez télécharger la liste des points de terminaison, la version actuelle de la liste ou des modifications spécifiques. Ce service remplace le document XML dont le lien est fourni sur cette page et qui est obsolète depuis le 2 octobre 2018. Pour essayer ce nouveau service, accédez au [service web](office-365-ip-web-service.md).
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md) | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 10/28/2019-abonnement au ![](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Journal des modifications](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) RSS <br/> |**Téléchargement :** liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Commencez par [gérer les points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données de points de terminaison sont mises à jour au début de chaque mois avec de nouvelles adresses IP et des URL publiées 30 jours avant d’être actives. Cela permet aux clients qui ne disposent pas encore de mises à jour automatiques d’effectuer leurs processus avant que la nouvelle connectivité ne soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si cela s’avère nécessaire pour traiter les escalades, les incidents de sécurité ou d’autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services Web basés sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au [service Web](office-365-ip-web-service.md) .

Les données de point de terminaison ci-dessous répertorient les conditions requises pour la connectivité entre l’ordinateur d’un utilisateur et Office 365. Il n’inclut pas les connexions réseau de Microsoft dans un réseau client, parfois appelé connexions réseau hybrides ou entrantes. Pour plus d’informations, consultez [la rubrique autres points de terminaison non inclus dans le service Web](additional-office365-ip-addresses-and-urls.md). 

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [http://aka.ms/pnc](http://aka.ms/pnc). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **Er**: Ceci est **Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La communauté BGP incluant les préfixes de routage affichés s’aligne sur la zone de service répertoriée. Lorsque la valeur de ER est **non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne doit pas être supposé qu’aucun itinéraire n’est annoncé pour un ensemble de points de terminaison où ER est **non**. Si vous envisagez d’utiliser Azure AD Connect, lisez la [section Considérations spéciales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) pour vous assurer que vous disposez de la configuration d’Azure ad Connect appropriée.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports**: Répertorie les ports TCP ou UDP qui sont combinées avec les adresses pour former le point de terminaison réseau. Vous remarquerez peut-être que certains duplication dans les plages d’adresses IP lorsqu’il y a des ports différents répertoriés.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Remarques à propos de ce tableau :

- Le centre de sécurité et de conformité (SCC) fournit la prise en charge d’Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités présentées via SCC, telles que la création de rapports, l’audit, la découverte électronique avancée, la DLP unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, l’importation de fichiers PST et l’exportation eDiscovery, ne prennent actuellement pas en charge Azure ExpressRoute avec uniquement les filtres d’itinéraires Office 365 en raison de leur dépendance vis-à-vis du stockage BLOB Azure. Pour utiliser ces fonctionnalités, vous devez disposer d’une connectivité séparée vers le stockage BLOB Azure à l’aide des options de connectivité Azure prises en charge, qui incluent une connectivité Internet ou Azure ExpressRoute avec des filtres d’itinéraires publics Azure. Vous devez évaluer la connectivité de ces deux fonctionnalités. L’équipe Office 365 information protection est consciente de cette limitation et travaille activement à la prise en charge d’Azure ExpressRoute pour Office 365, comme limité aux filtres d’itinéraires Office 365 pour ces deux fonctionnalités.

- Il existe des points de terminaison facultatifs supplémentaires pour Office 365 ProPlus qui ne sont pas répertoriés et qui ne sont pas requis pour que les utilisateurs puissent lancer des applications Office 365 ProPlus et modifier des documents. Les points de terminaison facultatifs sont hébergés dans des centres de données Microsoft et ne traitent, ne transmettent pas ou ne stockent pas de données client. Nous vous recommandons de diriger les connexions des utilisateurs vers ces points de terminaison vers le périmètre de sortie Internet par défaut.
