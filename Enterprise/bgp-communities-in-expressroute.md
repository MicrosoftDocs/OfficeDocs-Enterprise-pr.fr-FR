---
title: Utilisation de communautés BGP dans ExpressRoute pour les scénarios d’Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: "Connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur les publicités BGP de sous-réseaux IP spécifiques qui représentent les réseaux où les points de terminaison Office 365 sont déployés. En raison de la nature globale d’Office 365 et le nombre de services qui composent Office 365, les clients ont souvent besoin de gérer les publications qu'ils acceptent sur leur réseau. Réduction du nombre de sous-réseaux IP ; appelé préfixes IP dans le reste de cet article, pour aligner avec la terminologie de gestion de réseau BGP, sert les objectifs de fin suivants pour les clients :"
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540348"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Utilisation de communautés BGP dans ExpressRoute pour les scénarios d’Office 365

Connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur les publicités BGP de sous-réseaux IP spécifiques qui représentent les réseaux où les points de terminaison Office 365 sont déployés. En raison de la nature globale d’Office 365 et le nombre de services qui composent Office 365, les clients ont souvent besoin de gérer les publications qu'ils acceptent sur leur réseau. Réduction du nombre de sous-réseaux IP ; appelé préfixes IP dans le reste de cet article, pour aligner avec la terminologie de gestion de réseau BGP, sert les objectifs de fin suivants pour les clients :
  
- **Gérer les préfixes IP annoncés numéros acceptés** - clients disposant d’une infrastructure de réseau interne ou l’opérateur réseau qui prend en charge uniquement un nombre limité de préfixes IP et les clients qui ont un opérateur réseau que les frais d’acceptation de préfixes sera au-dessus d’un nombre limité à évaluer le nombre total de préfixes déjà publié sur leur réseau et sélectionnez les applications Office 365 sont mieux adaptées pour ExpressRoute.

- **Gérer la quantité de bande passante requise sur le circuit Azure ExpressRoute** - les clients peuvent souhaiter contrôler l’enveloppe de bande passante des services Office 365 sur le chemin d’accès ExpressRoute et le chemin d’accès Internet. Cela permet aux clients de réserver une bande passante ExpressRoute pour des applications spécifiques telles que Skype pour les entreprises et router les autres applications Office 365 sur le chemin d’accès Internet.

Pour aider les clients à ces objectifs, les préfixes d’Office 365 IP qui sont publiés sur ExpressRoute marqués avec service BGP Communauté des valeurs spécifiques comme indiqué dans l’exemple ci-dessous.
  
> [!NOTE]
> Vous pouvez être confronté certains types de trafic réseau associé avec d’autres applications à inclure dans la valeur de la Communauté. Ce comportement est normal pour un logiciel global en tant que Service offrant des centres de données et les services partagés. Cela a été réduite lorsque cela est possible avec les deux objectifs ci-dessus, la gestion count préfixe et/ou de bande passante à l’esprit.

|**Service**|**Valeur de la Communauté BGP**|**Remarques**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Inclut les services Exchange et EOP\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype pour les entreprises\*  <br/> |12076:5030  <br/> |Skype Entreprise Online  <br/> |
|autres services Office 365\*  <br/> |12076:5100  <br/> |Inclut Azure Active Directory (scénarios d’authentification et la synchronisation d’annuaires) ainsi que les services du portail Office 365  <br/> |
|\*L’étendue des scénarios de service inclus dans ExpressRoute est documenté dans l’article de [points de terminaison Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Autres services et les valeurs de la Communauté BGP peuvent être ajoutés à l’avenir. [Vous trouverez la liste actuelle des Communautés BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Quels sont les scénarios les plus courants pour l’utilisation de communautés BGP ?

Clients peuvent utiliser les Communautés BGP afin de réguler les groupes des préfixes IP qui sont acceptées par leur réseau par le biais de ExpressRoute Azure, par conséquent qui influencent le nombre total de préfixe IP et l’enveloppe de bande passante attendue de certains services Office 365. Il est important de comprendre que toutes les offres Office 365 nécessite que le trafic quel que soit l’utilisation de ExpressRoute Azure ou Communautés BGP liés à internet. Les trois scénarios suivants sont les utilisations les plus courantes de cette fonctionnalité.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scénario 1 : Réduisant le nombre de préfixes d’Office 365 IP

Contoso Corporation est une société de 50 000 personne qui utilise actuellement Office 365 pour Exchange Online et SharePoint Online. Dans la vérification ExpressRoute exigences que Contoso détermine son périphériques réseau à de nombreux emplacements régionaux ne peut pas gérer les tailles de tables de routage au-dessus de 100 entrées itinéraire supplémentaires. Contoso examiné le nombre total de préfixes IP ExpressRoute serait annoncer pour l’ensemble complet des services Office 365 et conclure qu’elle est supérieure à 100. Pour rester sous les 100 entrées itinéraire supplémentaires, Contoso portant sur l’utilisation de ExpressRoute pour Office 365 simplement la SharePoint Online BGP Communauté valeur, 12076:5020, reçu par le biais de Microsoft ExpressRoute peering.

|**Balise de la Communauté BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requises**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive entreprise  <br/> | DNS, la liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 pris en charge ne sont pas spécifiquement sur Azure ExpressRoute  <br/>  Tous les autres services de cloud Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office Online  <br/>  Exchange Online, Exchange Online Protection et Skype pour les entreprises en ligne  <br/> |

> [!NOTE]
> Pour obtenir le nombre inférieur de préfixe pour chaque service, un minimum de chevauchement des services est conservées. Ce comportement est normal.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scénario 2 : ExpressRoute portée et bande passante interne utilisent pour certains services Office 365

Fabrikam Inc, une grande entreprise multinationale avec un réseau hétérogène distribué, est un abonné de nombreux services Office 365, y compris ; Exchange Online, SharePoint Online et Skype pour les entreprises en ligne. Infrastructure de routage interne de Fabrikam peut gérer des milliers de préfixes IP dans ses tables de routage ; Toutefois, Fabrikam souhaite uniquement mettre en service ExpressRoute et bande passante interne pour les applications Office 365 qui respectent le plus les performances réseau et d’utiliser leur la bande passante Internet existante pour toutes les autres applications Office 365.
  
Pour cette raison, Fabrikam limite la bande passante ExpressRoute Azure à seulement Skype pour valeur Online BGP entreprises, 12076:5030, reçu par le biais de Microsoft ExpressRoute peering. Le trafic réseau associé à Office 365 continue à utiliser les points de sortie internet.

|**Balise de la Communauté BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requises**|
|:-----|:-----|:-----|
|Skype Entreprise  <br/> (12076:5030)  <br/> |Skype SIP signalisation, téléchargements, le partage de voix, vidéo et de bureau  <br/> | DNS, la liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 pris en charge ne sont pas spécifiquement sur Azure ExpressRoute  <br/>  Tous les autres services de cloud Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office Online  <br/>  Skype pour télémétrie Business, conseils rapides du client Skype, la connectivité PIC  <br/>  Exchange Online, Exchange Online Protection et SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scénario 3 : Étendue ExpressRoute Azure pour seulement les services Office 365

Woodgrove Bank est un client de plusieurs services de cloud Microsoft, y compris Office 365. Après l’évaluation de leur réseau la capacité et la consommation Woodgrove Bank décide de déployer ExpressRoute Azure sous le chemin d’accès par défaut pour les services Office 365 pris en charge. Les tables de routage peuvent prendre en charge l’ensemble des préfixes d’Office 365 IP et les circuits ExpressRoute Azure qu’ils ont mis en service prend en charge tous les besoins en matière de bande passante et latence projetées.
  
Pour vérifier le trafic réseau associé aux services de cloud Microsoft autres que Office 365, Woodgrove Bank portant sur l’utilisation de ExpressRoute pour Office 365 à tous les préfixes IP marqués avec les valeurs de la Communauté Office 365 spécifiques BGP, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Balise de la Communauté BGP utilisée**|**Fonctionnalité routable sur Azure ExpressRoute**|**Itinéraires Internet requises**|
|:-----|:-----|:-----|
|Exchange, Skype pour les entreprises, SharePoint, &amp; autres services  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive entreprise  <br/> Skype SIP signalisation, téléchargements, le partage de voix, vidéo et de bureau  <br/> Portail Office 365, authentification Office 365, &amp; Office Online  <br/> | DNS, la liste de révocation de certificats, &amp; demandes CDN  <br/>  Tous les autres services Office 365 pris en charge ne sont pas spécifiquement sur Azure ExpressRoute  <br/>  Tous les autres services de cloud Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Principales considérations sur l’utilisation de communautés BGP de planification

Les clients qui souhaitent tirer parti des Communautés BGP pour influencer la façon dont ExpressRoute est publié et propagée dans le réseau du client doivent prendre les points suivants en considération :
  
- Lors de l’utilisation de communautés BGP dans la conception de votre réseau, qu'il est important pour assurer la symétrie de l’itinéraire est conservé. Dans certains cas, l’ajout ou la suppression des Communautés BGP peut créer une situation où le routage symétrique est interrompu et votre configuration de routage doit être mis à jour pour rétablir le routage symétrique.

- Portée ExpressRoute Azure avec des valeurs de la Communauté BGP est une action du client. Microsoft annonce tous les préfixes IP associé à la relation homologation indépendamment de toute étendue configurée par le client.

- ExpressRoute Azure ne prend en charge toutes les actions du réseau Microsoft basé sur le client affecté Communautés BGP.

- Les préfixes IP utilisés par Office 365are marqué uniquement avec le service BGP Communauté des valeurs spécifiques, emplacement des Communautés BGP spécifiques ne sont pas pris en charge. Services Office 365 sont globales dans la nature, le filtrage des préfixes basées sur l’emplacement du client ou les données dans le nuage Office 365 ne sont pas pris en charge. L’approche recommandée consiste à configurer votre réseau pour coordonner la plus courte ou le chemin d’accès de réseau préférée à partir de l’emplacement réseau de l’utilisateur dans le réseau global Microsoft, quel que soit l’emplacement physique de l’adresse IP du service Office 365 recherchées.

- Les préfixes IP inclus dans chaque valeur de la Communauté BGP représentent un sous-réseau qui contient les adresses IP de l’application Office 365 associé à la valeur. Dans certains cas, plusieurs applications Office 365 a des adresses IP sur un sous-réseau entraînant un préfixe d’IP existants dans plusieurs valeurs de la Communauté. Il s’agit, bien que rarement, comportement attendu en raison de la fragmentation d’allocation et n’influe pas sur les objectifs de gestion de préfixe nombre ou la bande passante. Les utilisateurs sont invités à utiliser le « autoriser les éléments nécessaires » approche au lieu de « ce qui n’est pas nécessaire de refuser » en tirant parti des Communautés BGP pour Office 365 afin de réduire l’effet.

- L’utilisation de communautés BGP ne change pas la configuration requise de connectivité réseau ou configuration requise pour l’utilisation d’Office 365 sous-jacente. Les clients qui souhaitent accéder à Office 365 sont toujours requis pour pouvoir accéder à Internet.

- Portée ExpressRoute Azure avec des Communautés BGP n’affecte que les itinéraires de que votre réseau interne peut voir sur la relation homologation Microsoft. Vous devrez peut-être effectuer des configurations de niveau application supplémentaires telles que l’utilisation d’une configuration PAC ou WPAD conjointement avec la gamme étendue.

- Outre l’utilisation de Microsoft affecté Communautés BGP, clients peuvent choisir d’affecter leurs propres communautés BGP à Office 365 IP préfixes appris par le biais de ExpressRoute Azure pour influencer le routage interne. Un cas d’utilisation courants est assignation une Communauté BGP d’emplacement en fonction de tous les itinéraires appris par le biais de chaque ExpressRoute donné peering emplacement, puis en utilisant ces informations en aval dans le réseau du client pour coordonner la plus courte ou chemin d’accès réseau dans préféré Réseau de Microsoft. L’utilisation du client affecté ExpressRoute des Communautés BGP pour les scénarios d’Office 365 est en dehors de la portée de contrôle de Microsoft ou de visibilité.

Voici un lien court, vous pouvez utiliser pour revenir : [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Voir aussi

[Connectivité réseau à Office 365](network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[La qualité des médias et des performances pour la connectivité réseau dans Skype pour les entreprises en ligne](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute et QoS dans Skype pour les entreprises en ligne](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flux des appels à l’aide de ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Prise en charge pour les Communautés BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)
