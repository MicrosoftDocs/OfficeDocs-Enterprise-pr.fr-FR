---
title: Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 'La connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur des publicités BGP de sous-réseaux IP spécifiques qui représentent des réseaux sur lesquels les points de terminaison Office 365 sont déployés. En raison de la nature internationale d’Office 365 et du nombre de services qui constituent Office 365, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. Réduction du nombre de sous-réseaux IP ; appelés préfixes IP tout au long de cet article, pour s’aligner sur la terminologie de gestion de réseau BGP, il répond aux objectifs finaux suivants pour les clients :'
ms.openlocfilehash: 13d2404182eb18b7c72a9aaefdb96464fd665a03
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997871"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365

La connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur des publicités BGP de sous-réseaux IP spécifiques qui représentent des réseaux sur lesquels les points de terminaison Office 365 sont déployés. En raison de la nature internationale d’Office 365 et du nombre de services qui constituent Office 365, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. Réduction du nombre de sous-réseaux IP ; appelés préfixes IP tout au long de cet article, pour s’aligner sur la terminologie de gestion de réseau BGP, il répond aux objectifs finaux suivants pour les clients :
  
- **Gérer le nombre de préfixes IP publiés acceptés** : les clients disposant d’une infrastructure réseau interne ou d’un opérateur réseau qui ne prend en charge qu’un nombre limité de préfixes IP et les clients disposant d’un opérateur réseau pour lesquels l’acceptation de préfixes au-dessus d’un nombre limité voudront évaluer le nombre total de préfixes déjà annoncés sur leur réseau 365 et

- **Gestion de la quantité de bande passante requise sur le circuit ExpressRoute Azure** : les clients peuvent souhaiter contrôler l’enveloppe de bande passante des services Office 365 sur le chemin d’accès ExpressRoute et sur le chemin d’accès Internet. Cela permet aux clients de réserver une bande passante ExpressRoute pour des applications spécifiques telles que Skype entreprise et d’acheminer les autres applications Office 365 sur le chemin d’accès Internet.

Pour aider les clients à ces objectifs, les préfixes IP d’Office 365 publiés sur ExpressRoute sont balisés avec des valeurs de communauté BGP spécifiques au service, comme illustré dans l’exemple ci-dessous.
  
> [!NOTE]
> Vous devez vous attendre à ce que le trafic réseau associé à d’autres applications soit inclus dans la valeur de la communauté. Il s’agit d’un comportement attendu pour un logiciel global en tant qu’offre de service avec des services et des centres de contenu partagés. Il a été réduit, dans la mesure du possible, avec les deux objectifs ci-dessus, la gestion du nombre de préfixes et/ou la bande passante.

|**Service**|**Valeur de la communauté BGP**|**Remarques**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Inclut les services Exchange et EOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype Entreprise\*  <br/> |12076:5030  <br/> |Skype entreprise Online & services Microsoft teams  <br/> |
|Autres services Office 365\*  <br/> |12076:5100  <br/> |Inclut Azure Active Directory (scénarios d’authentification et de synchronisation d’annuaires), ainsi que les services de portail Office 365  <br/> |
|\*L’étendue des scénarios de service inclus dans ExpressRoute est documentée dans l’article relatif aux [points de terminaison Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Des services supplémentaires et des valeurs communautaires BGP peuvent être ajoutés à l’avenir. [Consultez la liste actuelle des communautés BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Quels sont les scénarios les plus courants pour l’utilisation des communautés BGP ?

Les clients peuvent utiliser des communautés BGP pour réguler les groupes de préfixes IP acceptés par leur réseau via Azure ExpressRoute, influençant ainsi le nombre total de préfixes IP et l’enveloppe de bande passante attendue de certains services Office 365. Il est important de comprendre que tout Office 365 nécessite le trafic Internet lié indépendamment de l’utilisation d’Azure ExpressRoute ou des communautés BGP. Les trois scénarios suivants sont les utilisations les plus courantes de cette fonctionnalité.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scénario 1 : minimisation du nombre de préfixes IP Office 365

Contoso Corporation est une société 50 000 Person qui utilise actuellement Office 365 pour Exchange Online et SharePoint Online. En examinant les exigences d’ExpressRoute que contoso détermine ses périphériques réseau dans de nombreux emplacements régionaux ne peuvent pas gérer les tailles de table de routage au-delà de 100 entrées d’itinéraire supplémentaires. Contoso a passé en revue le nombre total de préfixes IP que ExpressRoute devait publier pour l’ensemble complet des services Office 365 et a conclu qu’il dépasse 100. Pour rester sous les entrées d’itinéraire supplémentaires 100, contoso étend l’utilisation de ExpressRoute pour Office 365 à la valeur de la communauté BGP SharePoint Online, 12076:5020, reçue via ExpressRoute Microsoft peering.

|**Balise communautaire BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive entreprise  <br/> | DNS, liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 non spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services Cloud Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/>  Exchange Online, Exchange Online Protection et Skype entreprise Online  <br/> |

> [!NOTE]
> Pour obtenir le nombre de préfixes inférieur de chaque service, un minimum de chevauchement entre les services est conservé. Il s’agit du comportement attendu.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scénario 2 : portée de la bande passante ExpressRoute et de la bande passante interne pour certains services Office 365

Fabrikam Inc, une grande entreprise multinationale avec un réseau hétérogène distribué, est un abonné de nombreux services Office 365, y compris ; Exchange Online, SharePoint Online et Skype entreprise online. L’infrastructure de routage interne de Fabrikam peut gérer des milliers de préfixes IP dans ses tables de routage ; Toutefois, Fabrikam souhaite uniquement mettre en service ExpressRoute et la bande passante interne pour les applications Office 365 les plus sensibles aux performances du réseau et utilisent leur bande passante Internet existante pour toutes les autres applications Office 365.
  
Pour cette raison, Fabrikam étend sa bande passante Azure ExpressRoute à la valeur de la communauté BGP Skype entreprise Online, 12076:5030, reçue via ExpressRoute Microsoft. Le reste du trafic réseau associé à Office 365 continue d’utiliser les points de sortie Internet.

|**Balise communautaire BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|Skype Entreprise  <br/> (12076:5030)  <br/> |Signalisation SIP Skype, téléchargements, voix, vidéo et partage de bureau  <br/> | DNS, liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 non spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services Cloud Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/>  Télémétrie Skype entreprise, conseils rapides pour les clients Skype, connectivité PIC (Public IM Connectivity)  <br/>  Exchange Online, Exchange Online Protection et SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scénario 3 : portée des services Azure ExpressRoute pour Office 365 uniquement

Woodgrove Bank est un client de plusieurs services de Cloud Computing Microsoft, y compris Office 365. Après avoir évalué la consommation et la capacité réseau, Woodgrove Bank décide de déployer Azure ExpressRoute comme chemin d’accès préféré pour les services Office 365 pris en charge. Les tables de routage peuvent prendre en charge l’ensemble complet des préfixes IP d’Office 365 et les circuits ExpressRoute Azure qu’ils ont configurés prennent en charge toutes les exigences de bande passante et de latence prévues.
  
Pour garantir le trafic réseau associé aux services de Cloud Computing Microsoft autres que Office 365, Woodgrove Bank étend l’utilisation de ExpressRoute pour Office 365 à tous les préfixes IP balisés avec Office 365 les valeurs communautaires BGP spécifiques, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Balise communautaire BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|Exchange, Skype entreprise & Microsoft Teams, SharePoint, &amp; autres services  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive entreprise  <br/> Signalisation SIP Skype, téléchargements, voix, vidéo et partage de bureau  <br/> Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/> | DNS, liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 non spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services Cloud Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Considérations clés relatives à l’utilisation des communautés BGP

Les clients qui choisissent de tirer parti des communautés BGP pour influencer la manière dont ExpressRoute est annoncé et propagé via le réseau du client doivent prendre en compte les éléments suivants :
  
- Lors de l’utilisation de communautés BGP dans la conception de votre réseau, il est important de s’assurer que la symétrie d’itinéraire est toujours maintenue. Dans certains cas, l’ajout ou la suppression de communautés BGP peut créer une situation dans laquelle le routage symétrique est rompu et la configuration de votre routage doit être mise à jour pour rétablir le routage symétrique.

- L’étendue d’Azure ExpressRoute avec les valeurs de communauté BGP est une action client. Microsoft publiera tous les préfixes IP associés à la relation d’homologation, quelle que soit la portée configurée par le client.

- Azure ExpressRoute ne prend pas en charge les actions sur le réseau de Microsoft en fonction des communautés BGP attribuées par le client.

- Les préfixes IP utilisés par Office 365 sont uniquement marqués avec des valeurs de communauté BGP spécifiques au service, les communautés BGP spécifiques de l’emplacement ne sont pas prises en charge. Les services Office 365 sont globaux, de sorte que le filtrage des préfixes basé sur l’emplacement du client ou des données dans le Cloud Office 365 n’est pas pris en charge. L’approche recommandée consiste à configurer votre réseau de sorte qu’il coordonne le chemin d’accès réseau le plus court ou le plus favori à partir de l’emplacement réseau de l’utilisateur dans le réseau global Microsoft, quel que soit l’emplacement physique de l’adresse IP du service Office 365 qu’il demande.

- Les préfixes IP inclus dans chaque valeur de communauté BGP représentent un sous-réseau contenant des adresses IP pour l’application Office 365 associée à la valeur. Dans certains cas, plusieurs applications Office 365 ont des adresses IP au sein d’un sous-réseau qui génèrent un préfixe IP existant dans plusieurs valeurs de la communauté. Cette opération est probable, même si elle est rare, en raison de la fragmentation de l’allocation et n’influe pas sur le nombre de préfixes ou sur les objectifs de gestion de bande passante Les clients sont encouragés à utiliser l’approche « autoriser ce qui est nécessaire » au lieu de « refuser ce qui n’est pas nécessaire » lorsqu’ils tirent parti des communautés BGP pour Office 365 afin de réduire l’impact.

- L’utilisation des communautés BGP ne modifie pas les exigences ou la configuration de connectivité réseau sous-jacente requises pour utiliser Office 365. Les clients qui souhaitent accéder à Office 365 sont toujours tenus de pouvoir accéder à Internet.

- L’étendue d’Azure ExpressRoute avec des communautés BGP affecte uniquement les itinéraires que votre réseau interne peut voir sur la relation d’homologation Microsoft. Vous devrez peut-être effectuer des configurations supplémentaires au niveau de l’application, telles que l’utilisation d’une configuration PAC ou WPAD en association avec le routage d’étendue.

- En plus de l’utilisation des communautés BGP attribuées par Microsoft, les clients peuvent choisir d’affecter leurs propres communautés BGP à des préfixes IP 365 Office apprisus via Azure ExpressRoute pour influencer le routage interne. Un cas d’utilisation populaire consiste à affecter une communauté BGP basée sur l’emplacement à tous les itinéraires appris via chaque emplacement d’homologation ExpressRoute, puis à utiliser ces informations en aval sur le réseau du client pour coordonner le chemin réseau préféré le plus court ou le plus favori dans le réseau Microsoft. L’utilisation de communautés BGP attribuées par le client avec ExpressRoute pour les scénarios Office 365 est en dehors de l’étendue du contrôle ou de la visibilité de Microsoft.

Voici un petit lien que vous pouvez utiliser pour revenir : [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365) .
  
## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Prise en charge des communautés BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)
