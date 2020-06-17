---
title: Office 365 gouvernement américain GCC High Endpoints
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Si votre organisation utilise Office 365 et limite les ordinateurs de votre réseau à se connecter à Internet, vous trouverez ci-dessous les points de terminaison (noms de domaine complets, ports, URL, IPv4 et plages d’adresses IPv6) que vous devez inclure dans vos listes vertes de trafic sortant afin de vous assurer que vos ordinateurs peuvent utiliser correctement Office 365.
hideEdit: true
ms.openlocfilehash: 288e7140701b698979fa7e054d367d36fddb887d
ms.sourcegitcommit: f2a4b77c8c3932beb1a78bf2f5bf793fefb3fa49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "44747386"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 gouvernement américain GCC High Endpoints

 *S’applique à : Office 365 admin*

**Résumé :** Office 365 nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients utilisant Office 365 le gouvernement américain GCC High forfaits uniquement.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md) | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**Dernière mise à jour :** 06/16/2020- ![ abonnement au journal des ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [modifications](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) RSS <br/> |**Téléchargement :** liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Commencez par [gérer les points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données de points de terminaison sont mises à jour au début de chaque mois avec de nouvelles adresses IP et des URL publiées 30 jours avant d’être actives. Cela permet aux clients qui ne disposent pas encore de mises à jour automatiques d’effectuer leurs processus avant que la nouvelle connectivité ne soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si cela s’avère nécessaire pour traiter les escalades, les incidents de sécurité ou d’autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services Web basés sur REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au [service Web](office-365-ip-web-service.md) .

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Les colonnes de données affichées sont :

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **Er**: Ceci est **Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La communauté BGP incluant les préfixes de routage affichés s’aligne sur la zone de service répertoriée. Lorsque la valeur de ER est **non**, cela signifie que ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne doit pas être supposé qu’aucun itinéraire n’est annoncé pour un ensemble de points de terminaison où ER est **non**. Si vous envisagez d’utiliser Azure AD Connect, lisez la [section Considérations spéciales](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) pour vous assurer que vous disposez de la configuration d’Azure ad Connect appropriée.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Remarques à propos de ce tableau :

- Le centre de sécurité et de conformité (SCC) fournit la prise en charge d’Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités présentées via SCC, telles que la création de rapports, l’audit, la découverte électronique avancée, la DLP unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, l’importation de fichiers PST et l’exportation eDiscovery, ne prennent actuellement pas en charge Azure ExpressRoute avec uniquement les filtres d’itinéraires Office 365 en raison de leur dépendance vis-à-vis du stockage BLOB Azure. Pour utiliser ces fonctionnalités, vous devez disposer d’une connectivité séparée vers le stockage BLOB Azure à l’aide des options de connectivité Azure prises en charge, qui incluent une connectivité Internet ou Azure ExpressRoute avec des filtres d’itinéraires publics Azure. Vous devez évaluer la connectivité de ces deux fonctionnalités. L’équipe Office 365 information protection est consciente de cette limitation et travaille activement à la prise en charge d’Azure ExpressRoute pour Office 365, comme limité aux filtres d’itinéraires Office 365 pour ces deux fonctionnalités.

- Il existe des points de terminaison facultatifs supplémentaires pour les applications Microsoft 365 pour entreprise qui ne sont pas répertoriées et qui ne sont pas requises pour que les utilisateurs puissent lancer des applications Microsoft 365 pour les applications d’entreprise et modifier des documents. Les points de terminaison facultatifs sont hébergés dans des centres de données Microsoft et ne traitent, ne transmettent pas ou ne stockent pas de données client. Nous vous recommandons de diriger les connexions des utilisateurs vers ces points de terminaison vers le périmètre de sortie Internet par défaut.

